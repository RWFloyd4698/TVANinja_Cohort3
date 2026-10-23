# Power Automate integration

Use flow `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`:

1. Receive scenario card output from the agent.
2. Save to `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/briefs`.
3. Route approval to `{{TVA_APPROVER_GROUP_EMAIL}}`.
4. Publish approved scenario cards to `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
5. Keep rejected outputs in revision status.
