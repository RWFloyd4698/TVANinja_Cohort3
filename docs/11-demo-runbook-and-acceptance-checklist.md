# Demo runbook and acceptance checklist

## 45-minute demo sequence

1. **Context (5 min)**  
   Explain customer-facing + M365-only constraints and governance model.
2. **Transmission agent (12 min)**  
   Run project summary and stage/schedule prompt.
3. **Strategic briefing agent (10 min)**  
   Generate audience-specific brief (Finance, Nuclear, CAO variant).
4. **Comment triage agent + flow (10 min)**  
   Process a sample public comment through approval.
5. **Q&A + expansion scenarios (8 min)**  
   Discuss nuclear, generation, IT, and CAO adaptation patterns.
6. **Presenter package support**  
   Use [presenter/index.html](../presenter/index.html) for tabbed walkthrough and workflow simulation visuals.

## Hands-on workshop mode (participant-led)

1. Facilitator explains objective and constraints (5 min).
2. Participants complete `00-workshop-fill-in-template.md` (5 min).
3. Participants build one agent from scratch in pairs (25-35 min).
4. Participants connect one flow with approval (20-30 min) or connect a pre-staged flow.
5. Debrief and share working builds by work area (10 min).

**Assumption:** if workshop time is capped at 45-50 minutes, facilitators pre-stage the flow and participants perform only trigger/action wiring and test runs.

## Pre-class setup (facilitator)

- [ ] SharePoint site exists: `{{TVA_SHAREPOINT_SITE_URL}}`
- [ ] Library folders created in `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`
- [ ] Lists created and sample rows loaded:
  - `{{TVA_TRANSMISSION_LIST_NAME}}`
  - `{{TVA_TRANSMISSION_DRAFTS_LIST_NAME}}`
  - `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`
  - `{{TVA_BRIEFREQUESTS_LIST_NAME}}`
- [ ] Use the [facilitator checklist workbook](facilitator/pre-class-facilitator-checklist.xlsx) as the authoritative pre-class tracker.
- [ ] Use the [SharePoint list import kit](sharepoint-import-kit/sharepoint-list-import-kit.xlsx) to seed list rows and validate schema mapping.
- [ ] Copilot Studio environment access validated: `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`
- [ ] Approver group configured: `{{TVA_APPROVER_GROUP_EMAIL}}`
- [ ] Teams channel ready: `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`
- [ ] Power Automate connections pre-created for SharePoint, Teams, Planner, Outlook, Approvals, Copilot Studio actions

## Acceptance checklist

### Data and governance

- [ ] All source content is public TVA or customer-provided.
- [ ] All artifacts are stored in SharePoint/OneDrive.
- [ ] No internal/private source references exist.
- [ ] Outbound messages require approval.

### Agent quality

- [ ] Agent responses include source-grounded language.
- [ ] Missing data is flagged, not fabricated.
- [ ] Transmission lifecycle explanation is accurate.
- [ ] Role-based briefing adapts by work area.

### Workflow quality

- [ ] Approval branches work for approve/reject.
- [ ] SharePoint records persist complete audit fields.
- [ ] Planner/Teams notifications route to expected owners.
- [ ] Failed runs surface actionable errors.

## Expansion backlog after workshop

1. Nuclear outage communication variant.
2. Dam-management seasonal operations variant.
3. Finance rate-impact explainer variant.
4. IT service incident and dependency briefing variant.
5. CAO community hearing preparation variant.
