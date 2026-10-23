# Power Automate integration

Flow: `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}` (or TVA equivalent orchestrator flow)

1. Trigger from new intake item.
2. Call orchestrator agent for route and urgency.
3. Create Planner task and assign owner.
4. Send approval for outbound communication.
5. Persist audit fields in SharePoint.
