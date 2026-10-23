# Power Automate integration

Flow: `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`

1. Trigger on new comment item.
2. Call agent for draft response.
3. Route to `{{TVA_APPROVER_GROUP_EMAIL}}`.
4. On approval, set `Status = Approved for Response` and publish via defined channel/process.
5. On rejection, set `Status = Revision Required`.
6. Persist audit fields in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`: `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
