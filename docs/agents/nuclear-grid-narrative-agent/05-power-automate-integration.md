# Power Automate integration

Use flow `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`:

1. Receive draft narrative from agent.
2. Save to `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/briefs` and link to `{{TVA_BRIEFREQUESTS_LIST_NAME}}`.
3. Route approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
4. On approval, set `ApprovalStatus = Published` and publish to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
5. On rejection, set `ApprovalStatus = Needs Revision`.
6. Persist audit fields in `{{TVA_BRIEFREQUESTS_LIST_NAME}}`: `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
