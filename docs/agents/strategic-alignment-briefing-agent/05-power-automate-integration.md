# Power Automate integration

## Flow

`{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`

## Agent -> flow tool wiring

1. In Copilot Studio tools, create/use flow with trigger **When an agent calls the flow**.
2. Inputs: `requestId`, `requestedBy`, `audience`, `dueDate`, `priorityTheme`, `projectsIncluded`, `draftBrief`.
3. Return outputs: `approvalStatus`, `publishedArtifactLink`, `flowRunId`.

## List-triggered wiring (Flow 3 pattern)

1. SharePoint trigger: new item in `{{TVA_BRIEFREQUESTS_LIST_NAME}}`.
2. Call published agent with Copilot Studio connector **execute-agent** action (premium; **verify in GCC**).
3. Fallback if execute-agent is unavailable: Teams-triggered agent-to-flow handoff.

## Build sequence

1. Write generated brief artifact to `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/briefs`.
2. Set `AgentVersion = StrategicBrief v1.0` on request row.
3. Start approval assigned to `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
4. Note: group-mailbox approvals can fail in some tenants; use named users (semicolon-separated).
5. If approved, set `ApprovalStatus = Published` and post link to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
6. If rejected, set `ApprovalStatus = Needs Revision`.
7. Persist `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
