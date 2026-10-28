# Power Automate integration

## Flow

`{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`

## Agent -> flow tool wiring

1. In Copilot Studio tools, create/use flow with trigger **When an agent calls the flow**.
2. Inputs: `projectName`, `stateCounty`, `currentStage`, `publicCommentStatus`, `scheduleMilestones`, `draftSummary`, `sourceLinks`.
3. Return outputs: `status`, `draftId`, `publishedArtifactLink`, `flowRunId`.

## Build sequence

1. Create item in `{{TVA_TRANSMISSION_DRAFTS_LIST_NAME}}` with `Status = Draft`.
2. Set `AgentVersion = Navigator v1.0`.
3. Start approval assigned to `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
4. Note: group-mailbox approvals can fail in some tenants; use named users (semicolon-separated).
5. If approved, set `Status = Published` and post approved output to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
6. If rejected, set `Status = Needs Revision`.
7. Persist `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
