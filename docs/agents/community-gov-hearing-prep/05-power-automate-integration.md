# Power Automate integration

Flow: `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`

1. Trigger from hearing prep request list item.
2. Generate draft hearing pack.
3. Route to `{{TVA_APPROVER_GROUP_EMAIL}}`.
4. On approval, set `ApprovalStatus = Published` and publish pack to SharePoint and Teams.
5. On rejection, set `ApprovalStatus = Needs Revision`.
6. Persist audit fields in `{{TVA_BRIEFREQUESTS_LIST_NAME}}`: `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
