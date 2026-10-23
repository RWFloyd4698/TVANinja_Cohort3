# Power Automate integration

## Flow name

`{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`

## Purpose

Take the agent project snapshot and route it through approval before distribution.

## Steps

1. Trigger from Copilot action.
2. Create SharePoint item in `{{TVA_TRANSMISSION_LIST_NAME}}`.
3. Start approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
4. If approved:
   - Post to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`
   - Mark status `Published`
5. If rejected:
   - Mark status `Needs Revision`
   - Notify requestor.

## Required payload fields

- `ProjectName`
- `Stage`
- `ScheduleText`
- `PublicCommentStatus`
- `SourceUrl`
