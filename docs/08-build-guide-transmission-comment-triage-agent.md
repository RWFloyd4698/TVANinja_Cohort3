# Build guide: Transmission Comment Triage Agent

## Copilot Studio build steps (participant)

1. Go to Copilot Studio in environment `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Create agent: `Transmission Comment Triage Agent`.
3. Add knowledge:
   - Transmission project pages and process descriptions
   - Approved response policy snippets in `Reference-Policies`
4. Add instructions:

```text
Classify incoming public comments about transmission projects.
Provide category, urgency, owner recommendation, and a draft response.
Keep language factual, neutral, and source-grounded.
Always set needsHumanReview=true and never send direct outreach.
```

5. Create topic: `Triage incoming comment`.
6. Configure structured output as the JSON contract in the overview doc.
7. Add action handoff note: "Send output to Power Automate Flow: `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`".
8. Save and publish.
9. Test with varied comment types.

## Demo prompts

1. "Resident asks if this project affects wetlands near their property."
2. "Comment asks why project schedule moved and who to contact."
3. "Comment expresses concern about right-of-way impacts."

## Placeholder values participants must set

- `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`
- `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`
- `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`
