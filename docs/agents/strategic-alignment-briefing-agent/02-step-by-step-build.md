# Step-by-step build (participant)

## Prerequisites

- Copilot Studio access to `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`
- SharePoint library `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`

## Build steps

1. Open Copilot Studio in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Create agent named `Strategic Alignment Briefing Agent`.
3. Description: "Customer-facing briefing agent for TVA strategic alignment."
4. Add knowledge:
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Powerhouse-Stories` (optional)
5. Paste instructions:

```text
You create customer-facing strategic briefs using TVA public sources.
Map responses to strategic priorities and practical outcomes.
Tailor output for the selected audience role.
Do not invent metrics or timelines.
If source data is missing, state "Needs human verification."
```

6. Create topic: `Build role-based briefing`.
7. Add trigger phrases:
   - "Create a finance briefing for this project"
   - "Generate a CAO stakeholder talking brief"
   - "Create an operations-aligned strategy brief"
8. Add output template:

```text
Strategic Alignment Brief
- Audience:
- Priority theme:
- Strategic alignment:
- Reliability/affordability implications:
- Stakeholder message:
- Source references:
- Needs human verification:
```

9. Save and publish.
10. Run tests from `04-test-prompts.md`.
