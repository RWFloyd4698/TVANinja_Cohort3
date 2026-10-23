# Power Automate implementation playbooks

## Flow 1: Transmission update draft approval

**What the flow does:** routes a transmission update draft through approval, then publishes or returns for revision.

### Build sequence (participant)

1. Open Power Automate in tenant `{{TVA_TENANT_NAME}}`.
2. Create cloud flow named `{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`.
3. Add trigger: manual trigger from Teams or Copilot action input.
4. Add SharePoint action: create item in `{{TVA_TRANSMISSION_LIST_NAME}}`.
5. Add approval action assigned to `{{TVA_APPROVER_GROUP_EMAIL}}`.
6. Add condition branch for approve/reject.
7. Approve branch: post to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}` and set record status `Published`.
8. Reject branch: set status `Needs Revision` and notify requestor.

## Flow 2: Public comment triage routing

**What the flow does:** triages public comments, routes ownership, and enforces human approval before response.

### Build sequence (participant)

1. Create flow named `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`.
2. Trigger on new SharePoint item in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
3. Call Copilot Studio triage action.
4. Parse JSON output and update list item fields.
5. Create Planner task for `{{TVA_DEFAULT_OWNER_CAO}}` or mapped owner.
6. Send approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
7. On approval, mark `Approved for Response` and publish via approved channel.
8. On rejection, mark `Revision Required` and return to owner.

## Flow 3: Strategic brief pack publisher

**What the flow does:** creates a strategic brief draft, routes approval, and publishes approved artifacts.

### Build sequence (participant)

1. Create flow named `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`.
2. Trigger on new item in `{{TVA_BRIEFREQUESTS_LIST_NAME}}`.
3. Call Strategic Alignment Briefing Agent action.
4. Write result file to `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/briefs`.
5. Send approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
6. If approved, post link to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}` and set request status `Published`.
7. If rejected, set status `Needs Revision` and notify requestor.
8. Persist audit metadata to SharePoint.

## Required connector set

- SharePoint
- Approvals
- Teams
- Office 365 Outlook
- Planner
- Copilot Studio (agent actions)

## Audit fields to persist

- `FlowRunId`
- `AgentVersion`
- `Approver`
- `ApprovalDecision`
- `DecisionTimestamp`
- `PublishedArtifactLink`
