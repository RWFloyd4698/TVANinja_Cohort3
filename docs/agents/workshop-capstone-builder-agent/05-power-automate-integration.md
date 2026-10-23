# Power Automate integration

Use flow `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}` and `{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`:

1. Save capstone draft outputs to `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/briefs`, `{{TVA_BRIEFREQUESTS_LIST_NAME}}`, and `{{TVA_TRANSMISSION_DRAFTS_LIST_NAME}}` as applicable.
2. Route approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
3. Publish approved artifacts in `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
4. Keep rejected artifacts as `Needs Revision` and re-run the capstone build prompt.
5. Persist audit fields on all written list items: `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
