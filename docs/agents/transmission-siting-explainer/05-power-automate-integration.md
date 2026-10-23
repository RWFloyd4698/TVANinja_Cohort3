# Power Automate integration

Use flow `{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`:

1. Receive siting summary draft from agent.
2. Save to `{{TVA_TRANSMISSION_DRAFTS_LIST_NAME}}` with `Status = Draft`.
3. Send for approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
4. On approval, set `Status = Published` and post approved output to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
5. On rejection, set `Status = Needs Revision`.
6. Persist audit fields on the draft item: `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`.
