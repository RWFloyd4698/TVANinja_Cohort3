# Build guide: Transmission Planning Navigator

## Copilot Studio build steps (participant)

1. Go to Copilot Studio in environment `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Select **Create** > **New agent**.
3. Agent name: `Transmission Planning Navigator`.
4. Description: customer-facing assistant for TVA transmission project understanding.
5. Open **Knowledge** and add:
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`
6. Open **Instructions** and paste:

```text
You are a customer-facing TVA transmission planning assistant.
Use only approved public sources provided in this environment.
Explain project purpose, process stage, and schedule in clear language.
If data is missing or ambiguous, explicitly state what needs human verification.
Do not use or reference internal/private data.
```

7. Create topic: `Project status summary`.
8. Add trigger phrases:
   - "Summarize the [project] transmission project"
   - "What stage is [project] in?"
   - "What are the schedule milestones for [project]?"
9. Add structured response template (from overview doc).
10. Turn on citation/source reference option if available in environment.
11. Save and publish.
12. Run the 3 test prompts below and capture screenshots for workshop evidence.

## Suggested prompts for demo

1. "Summarize the Claysville, Alabama transmission project."
2. "Explain the transmission siting process in plain language."
3. "Which projects are open for public comment?"

## Placeholder values participants must set

- `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`
- `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`
- `{{TVA_SHAREPOINT_SITE_URL}}`

## Cohort mapping examples

- Transmission: stage/schedule/status quick answers.
- Generation and dam management teams: interdependency awareness for line/substation upgrades.
- IT and CAO teams: standardized public messaging and workflow handoff.
