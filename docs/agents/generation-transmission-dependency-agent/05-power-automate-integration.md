# Power Automate integration

Use flow `{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`:

1. Receive dependency summary draft from agent.
2. Save to `{{TVA_TRANSMISSION_LIST_NAME}}`.
3. Route approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
4. Publish approved summary to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
5. Keep rejected outputs in `Needs Revision`.
