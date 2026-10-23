# Power Automate integration

## Flow name

`{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`

## Purpose

Generate, review, and publish a strategic brief into M365 with approval and audit trail.

## Steps

1. Trigger from new request in `{{TVA_BRIEFREQUESTS_LIST_NAME}}`.
2. Call agent action and receive draft brief.
3. Write artifact to `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/briefs`.
4. Start approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
5. If approved:
   - Update `ApprovalStatus` to `Published`
   - Post link to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`
6. If rejected:
   - Set `ApprovalStatus` to `Needs Revision`
   - Notify requestor.
7. Persist audit fields on the request row:
   - `FlowRunId`
   - `AgentVersion`
   - `Approver`
   - `ApprovalDecision`
   - `DecisionTimestamp`
   - `PublishedArtifactLink`

## Required payload fields

- `RequestId`
- `Audience`
- `DueDate`
- `PriorityTheme`
- `ProjectsIncluded`
- `DraftBrief`
