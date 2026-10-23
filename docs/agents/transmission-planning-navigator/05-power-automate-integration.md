# Power Automate integration

## Flow name

`{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`

## Purpose

Take the agent project snapshot and route it through approval before distribution.

## Steps

1. Trigger from Copilot action.
2. Create SharePoint draft item in `{{TVA_TRANSMISSION_DRAFTS_LIST_NAME}}` with `Status = Draft`.
3. Start approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
4. If approved:
   - Post to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`
   - Mark `Status = Published`
5. If rejected:
   - Mark `Status = Needs Revision`
   - Notify requestor.
6. Persist audit fields on the same draft item:
   - `FlowRunId`
   - `AgentVersion`
   - `Approver`
   - `ApprovalDecision`
   - `DecisionTimestamp`
   - `PublishedArtifactLink`

## Required payload fields

- `ProjectName`
- `Stage`
- `ScheduleText`
- `PublicCommentStatus`
- `SourceUrl`
