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

## Hands-on workshop mode (participant-led)

1. Facilitator explains objective and constraints (5 min).
2. Participants complete `00-workshop-fill-in-template.md` (5 min).
3. Participants build one agent from scratch in pairs (15 min).
4. Participants connect one flow with approval (15 min).
5. Debrief and share working builds by work area (5 min).

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
