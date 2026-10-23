# Power Automate integration

Flow: `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`

1. Trigger from new brief request.
2. Call agent for tradeoff analysis text.
3. Send to approver group.
4. On approval, set `ApprovalStatus = Published` and publish brief to Teams + SharePoint.
5. On rejection, set `ApprovalStatus = Needs Revision`.
6. Persist audit fields in `{{TVA_BRIEFREQUESTS_LIST_NAME}}`: `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
