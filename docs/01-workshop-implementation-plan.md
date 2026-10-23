# TVA Cohort 3 implementation plan

## Scope

Build customer-facing agents and workflows that TVA participants create themselves during the workshop, with Microsoft facilitation.

## Cohort work areas to support

- Nuclear
- Finance
- Generation team A
- Generation team B (dam management)
- Transmission
- IT
- CAO blended team (HR + community engagement + government relations)

## Non-negotiable constraints

1. Use only public TVA content plus customer-provided workshop content.
2. Keep all data and activity in Microsoft 365 (SharePoint, OneDrive, Teams, Outlook, Power Automate, Copilot Studio).
3. Do not include internal/private data (Vantage, internal email/chat exports, internal notes).
4. Require human approval before outbound communication.

## Workshop posture

- **Microsoft role:** facilitator and coach.
- **TVA role:** builder and owner of the final agents/flows in TVA tenant.
- **Outcome:** TVA leaves with working agents they built in their own environment.

## Required placeholders to replace before class

Use values from `00-workshop-fill-in-template.md`:

- `{{TVA_SHAREPOINT_SITE_URL}}`
- `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`
- `{{TVA_APPROVER_GROUP_EMAIL}}`
- `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`

## Build sequence

1. Provision M365 information architecture in SharePoint/OneDrive.
2. Ingest and organize source documents and project pages.
3. Build three Copilot Studio agents.
4. Build approval-backed Power Automate workflows.
5. Run scripted demo + safety tests.

## Deliverables

- Transmission Planning Navigator
- Strategic Alignment Briefing Agent
- Transmission Comment Triage Agent
- Three supporting Power Automate flows
- Demo runbook and acceptance checklist

## Portfolio alignment

- **Tier A (headline workshop agents):** the three deliverables above
- **Tier B (core extension set):** five full extension packs for role-based expansion
- **Tier C (advanced track):** five advanced packs for post-workshop iteration
