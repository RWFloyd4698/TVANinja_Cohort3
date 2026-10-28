# Power Automate integration

## Flow

`{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`

## Agent -> flow tool wiring

1. In Copilot Studio tools, create/use flow with trigger **When an agent calls the flow**.
2. Inputs: `commentId`, `projectName`, `commentText`, `category`, `urgency`, `sourceUrl`.
3. Return outputs: `draftResponse`, `recommendedOwner`, `status`, `flowRunId`.

## List-triggered wiring (Flow 2 pattern)

1. SharePoint trigger: new item in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
2. Call published response/triage agent with Copilot Studio connector **execute-agent** action (premium; **verify in GCC**).
3. Fallback if execute-agent is unavailable: Teams-triggered agent-to-flow handoff.

## Build sequence

1. Update item fields in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
2. Set `AgentVersion = Triage v1.0`.
3. Create Planner task in plan `{{TVA_PLANNER_PLAN_ID}}` and bucket `{{TVA_PLANNER_BUCKET_ID}}` **[Provided by TVA]**.
4. Map owner email to Planner assignee.
5. Start approval assigned to `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
6. Note: group-mailbox approvals can fail in some tenants; use named users (semicolon-separated).
7. If approved, set `Status = Approved for Response`; if rejected, set `Status = Revision Required`.
8. Persist `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
