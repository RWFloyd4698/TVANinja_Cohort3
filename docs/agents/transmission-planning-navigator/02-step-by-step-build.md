# Step-by-step build (participant)

## Prerequisites

- Copilot Studio access to `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`
- SharePoint library `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`
- Transmission list `{{TVA_TRANSMISSION_LIST_NAME}}`

## Build steps

1. Open Copilot Studio in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Create agent named `Transmission Planning Navigator`.
3. Set description: "Customer-facing transmission planning assistant for TVA public project information."
4. Add knowledge:
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`
5. Paste these core instructions:

```text
You are a customer-facing transmission planning assistant.
Use only approved TVA public sources.
Summarize project stage, schedule, and process in plain language.
Do not invent milestones or status.
If any fact is missing, state "Needs human verification."
```

6. Create topic: `Project status summary`.
7. Add trigger phrases:
   - "Summarize the [project] transmission project"
   - "What stage is [project] in?"
   - "Show schedule milestones for [project]"
8. Add output template:

```text
Transmission Project Snapshot
- Project:
- State/County:
- Current stage:
- Reliability/load rationale:
- Public comment status:
- Key schedule milestones:
- Source links:
- Notes requiring human verification:
```

9. Save and publish.
10. Run tests from `04-test-prompts.md`.
