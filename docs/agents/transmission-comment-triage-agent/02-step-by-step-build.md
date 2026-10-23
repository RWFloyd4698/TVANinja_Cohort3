# Step-by-step build (participant)

## Prerequisites

- Copilot Studio access to `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`
- SharePoint list `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`
- Flow name `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`

## Build steps

1. Open Copilot Studio in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Create agent named `Transmission Comment Triage Agent`.
3. Add knowledge:
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Reference-Policies`
4. Paste instructions:

```text
Classify transmission-related stakeholder comments.
Return category, urgency, owner recommendation, and a draft response.
Keep language neutral, factual, and customer-facing.
Always require human review and approval before any outbound response.
```

5. Create topic: `Triage incoming comment`.
6. Add trigger phrases:
   - "Classify this transmission comment"
   - "Draft response for this public comment"
   - "Who should own this transmission concern?"
7. Add JSON output contract from `03-data-and-knowledge-setup.md`.
8. Add action handoff note to `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`.
9. Save and publish.
10. Run tests from `04-test-prompts.md`.
