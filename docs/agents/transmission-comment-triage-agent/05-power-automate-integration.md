# Power Automate integration

## Flow

`{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`

## Agent -> flow tool wiring

1. In Copilot Studio tools, create/use flow with trigger **When an agent calls the flow**.
2. Inputs: `commentId`, `projectName`, `commentText`, `sourceUrl`.
3. Return outputs: `category`, `urgency`, `recommendedOwner`, `draftResponse`, `needsHumanReview`, `flowRunId`.

## List-triggered wiring (Flow 2 pattern)

1. SharePoint trigger: new item in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
2. Call published triage agent with Copilot Studio connector **execute-agent** action (premium; **verify in GCC**).
3. Fallback if execute-agent is unavailable: Teams-triggered agent-to-flow handoff.
4. Triage instructions must include: **Return only valid JSON.**
5. Parse JSON with this exact schema:

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

## Build sequence

1. Update item fields in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
2. Set `AgentVersion = Triage v1.0`.
3. Create Planner task in plan `{{TVA_PLANNER_PLAN_ID}}` and bucket `{{TVA_PLANNER_BUCKET_ID}}` **[Provided by TVA]**.
4. Map `recommendedOwner` email to Planner assignee.
5. Start approval assigned to `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
6. Note: group-mailbox approvals can fail in some tenants; use named users (semicolon-separated).
7. If approved, set `Status = Approved for Response`; if rejected, set `Status = Revision Required`.
8. Persist `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
