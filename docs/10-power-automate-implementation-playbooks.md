# Power Automate implementation playbooks

## Flow 1: Transmission update draft approval

### Trigger

- Manual trigger from Teams or Copilot action.

### Build steps (participant)

1. Open Power Automate in tenant `{{TVA_TENANT_NAME}}`.
2. Create cloud flow named `{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`.
3. Add trigger: manual trigger or Copilot action input.
4. Add SharePoint action: create item in `{{TVA_TRANSMISSION_LIST_NAME}}`.
5. Add approval action assigned to `{{TVA_APPROVER_GROUP_EMAIL}}`.
6. Add condition branch for approve/reject.
7. Approve branch: post to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}` and set record `Published`.
8. Reject branch: set record `Needs Revision` and notify requestor.

### Steps

1. Receive agent draft payload.
2. Create item in `TransmissionProjects` or `ExecutiveBriefRequests`.
3. Start and wait for approval (assigned approver group).
4. If approved, post final update to Teams and write final status.
5. If rejected, set status `Needs Revision` and notify requestor.

## Flow 2: Public comment triage routing

### Trigger

- New item in `PublicComments` list.

### Build steps (participant)

1. Create flow named `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`.
2. Trigger: new SharePoint item in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
3. Call Copilot Studio triage action.
4. Parse JSON and update list item fields.
5. Create Planner task for `{{TVA_DEFAULT_OWNER_CAO}}` or mapped owner.
6. Send approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
7. On approval, mark `Approved for Response`.
8. On rejection, mark `Revision Required`.

### Steps

1. Call triage agent action.
2. Parse JSON output.
3. Update item with category/urgency/owner draft.
4. Create Planner task for owner.
5. Send approval card for response draft.
6. On approval, publish approved response path; else return for edit.

## Flow 3: Strategic brief pack publisher

### Trigger

- New request in `ExecutiveBriefRequests`.

### Build steps (participant)

1. Create flow named `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`.
2. Trigger: new item in `{{TVA_BRIEFREQUESTS_LIST_NAME}}`.
3. Call Strategic Alignment Briefing Agent action.
4. Write result file to `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/briefs`.
5. Approval step assigned to `{{TVA_APPROVER_GROUP_EMAIL}}`.
6. If approved, post link to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
7. Persist audit metadata to SharePoint.

### Steps

1. Call Strategic Alignment Briefing Agent.
2. Create .docx or markdown artifact in SharePoint library.
3. Start approval workflow.
4. Publish approved brief link to Teams channel.

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
