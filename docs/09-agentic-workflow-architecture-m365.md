# Agentic workflow architecture (M365)

## Design principle

Agent reasons and drafts. Flow executes and governs.

## M365 architecture

1. **Copilot Studio agents**
   - Transmission Planning Navigator
   - Strategic Alignment Briefing Agent
   - Transmission Comment Triage Agent
2. **SharePoint**
   - Source libraries and system-of-record lists
3. **Power Automate**
   - Routing, approval, task creation, and audit trails
4. **Teams/Outlook**
   - Human review and approved notifications

## Workshop placeholders (replace before lab)

- `{{TVA_SHAREPOINT_SITE_URL}}`
- `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`
- `{{TVA_APPROVER_GROUP_EMAIL}}`
- `{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`
- `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`
- `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`

## Workflow patterns

### Pattern A: Draft and approval

1. Agent drafts structured output.
2. Flow writes draft to SharePoint list.
3. Flow creates approval in Teams/Outlook.
4. On approval, publish/send; on reject, return for revision.

### Pattern B: Triage and assignment

1. Agent classifies incoming item.
2. Flow creates Planner task and sets owner.
3. Flow posts to Teams operations channel with SLA metadata.

### Pattern C: Executive briefing pack

1. Agent composes role-based briefing.
2. Flow stores document in SharePoint library.
3. Flow posts summary and link to Teams.

## Security and governance controls

- Data Loss Prevention policies for connectors.
- Least-privilege service account for flows.
- Mandatory approval for outbound content.
- Logging: run ID, approver, status, timestamp.
