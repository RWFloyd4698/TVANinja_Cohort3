# Power Automate integration

## Flow name

`{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`

## Purpose

Route triaged comments into owner workflow with approval gating.

## Steps

1. Trigger: new item in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
2. Call triage agent and parse JSON.
3. Update list item with category/urgency/draft response.
4. Create Planner task for owner (`{{TVA_DEFAULT_OWNER_CAO}}` or mapped owner).
5. Send approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
6. On approve:
   - Mark status `Approved for Response`
   - Post update to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`
7. On reject:
   - Mark status `Revision Required`
   - Notify assigned owner.
8. Persist audit fields in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`:
   - `FlowRunId`
   - `AgentVersion`
   - `Approver`
   - `ApprovalDecision`
   - `DecisionTimestamp`
   - `PublishedArtifactLink`
