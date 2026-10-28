# Power Automate implementation playbooks

## Shared wiring standards (all flows)

1. **Agent -> flow tool pattern (Copilot Studio):**
   - Create flow with trigger **When an agent calls the flow**.
   - Define explicit inputs and outputs.
   - Add flow as a tool in the agent.
2. **List-triggered pattern (Flow 2, Flow 3):**
   - Trigger from SharePoint list item creation.
   - Call published agent with Copilot Studio connector **execute-agent** action (**verify in GCC**, premium connector).
   - Fallback if execute-agent is unavailable in tenant: use agent-to-flow trigger from Teams and map response back to list item.
3. **Approvals:**
   - Assign named approvers as semicolon-separated users: `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**
   - Group email approvals can fail in some tenants; prefer named users.
4. **Planner prerequisites (Flow 2):**
   - Plan ID: `{{TVA_PLANNER_PLAN_ID}}` **[Provided by TVA]**
   - Bucket ID/Name: `{{TVA_PLANNER_BUCKET_ID}}` **[Provided by TVA]**
   - Owner email from routing output maps to Planner assignee.
5. **Agent versioning:**
   - Persist fixed text values in list rows:
     - `Navigator v1.0`
     - `Triage v1.0`
     - `StrategicBrief v1.0`
6. **Status vocabulary:**
   - Flow 1 / Flow 3: `Draft`, `Published`, `Needs Revision`
   - Flow 2: `Approved for Response`, `Revision Required`

## Flow 1: Transmission update draft approval

**What the flow does:** receives agent-generated transmission snapshots, stores drafts, routes approval, and publishes approved outputs.

### Build sequence (participant)

1. Create cloud flow `{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}` with trigger **When an agent calls the flow**.
2. Define inputs:
   - `projectName` (text)
   - `stateCounty` (text)
   - `currentStage` (text)
   - `publicCommentStatus` (text)
   - `scheduleMilestones` (text)
   - `draftSummary` (text)
   - `sourceLinks` (text)
3. Create SharePoint item in `{{TVA_TRANSMISSION_DRAFTS_LIST_NAME}}` with `Status = Draft`.
4. Set `AgentVersion = Navigator v1.0`.
5. Start approval assigned to `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
6. If approved:
   - Set `Status = Published`
   - Post approved summary to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`
7. If rejected:
   - Set `Status = Needs Revision`
8. Persist `FlowRunId`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
9. Return outputs to agent:
   - `status`
   - `draftId`
   - `publishedArtifactLink`

## Flow 2: Public comment triage routing

**What the flow does:** triages public comments with agent output, creates owner tasks, and gates responses through approval.

### Build sequence (participant)

1. Create cloud flow `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}` with SharePoint trigger on `{{TVA_PUBLICCOMMENTS_LIST_NAME}}` new item.
2. Call published triage/orchestrator agent using Copilot Studio connector **execute-agent** (**verify in GCC**).
3. Agent output requirement for triage + IT orchestrator: **Return only valid JSON.**
4. Parse agent output with this schema:

```json
{
  "type": "object",
  "properties": {
    "commentId": { "type": "string" },
    "projectName": { "type": "string" },
    "category": { "type": "string", "enum": ["timeline", "environmental", "property", "process", "general"] },
    "urgency": { "type": "string", "enum": ["low", "medium", "high"] },
    "needsHumanReview": { "type": "boolean" },
    "recommendedOwner": { "type": "string" },
    "nextStep": { "type": "string" },
    "draftResponse": { "type": "string" },
    "notesRequiringHumanVerification": { "type": "string" },
    "sourceLinks": {
      "type": "array",
      "items": { "type": "string" }
    }
  },
  "required": ["category", "urgency", "recommendedOwner", "draftResponse", "needsHumanReview"]
}
```

5. Update list item fields in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
6. Set `AgentVersion = Triage v1.0`.
7. Create Planner task in `{{TVA_PLANNER_PLAN_ID}}` / `{{TVA_PLANNER_BUCKET_ID}}` **[Provided by TVA]** and assign from `recommendedOwner`.
8. Start approval assigned to `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
9. If approved, set `Status = Approved for Response`; if rejected, set `Status = Revision Required`.
10. Persist `FlowRunId`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.

## Flow 3: Strategic brief pack publisher

**What the flow does:** generates strategic briefs from requests, routes approval, and publishes approved artifacts.

### Build sequence (participant)

1. Create cloud flow `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}` with SharePoint trigger on `{{TVA_BRIEFREQUESTS_LIST_NAME}}` new item.
2. Call published strategic briefing agent using Copilot Studio connector **execute-agent** (**verify in GCC**).
3. If execute-agent is unavailable, use Teams-triggered agent-to-flow fallback and map output into request row.
4. Write generated brief artifact to `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/briefs`.
5. Update request row and set `AgentVersion = StrategicBrief v1.0`.
6. Start approval assigned to `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
7. If approved:
   - Set `ApprovalStatus = Published`
   - Post published link to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`
8. If rejected:
   - Set `ApprovalStatus = Needs Revision`
9. Persist `FlowRunId`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.

## Required connector set

- SharePoint
- Approvals
- Teams
- Office 365 Outlook
- Planner
- Copilot Studio (agent actions, premium; **verify in GCC**)

## Audit fields to persist

- `FlowRunId`
- `AgentVersion`
- `Approver`
- `ApprovalDecision`
- `DecisionTimestamp`
- `PublishedArtifactLink`
