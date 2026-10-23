# Build guide: Strategic Alignment Briefing Agent

## Copilot Studio build steps (participant)

1. Go to Copilot Studio in environment `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Select **Create** > **New agent**.
3. Name: `Strategic Alignment Briefing Agent`.
4. Connect knowledge:
   - `Knowledge-Public/Strategic-Plan`
   - `Knowledge-Public/Transmission-Projects`
   - `Knowledge-Public/Powerhouse-Stories`
5. Add instructions:

```text
You generate customer-facing strategic briefs grounded in TVA public strategy and project sources.
Connect responses to strategic priorities and measurable outcomes when available.
Tailor output to audience role (Transmission, Nuclear, Finance, IT, Generation, CAO).
Do not fabricate metrics. Clearly flag assumptions and missing source data.
```

6. Create topic: `Build role-based briefing`.
7. Add input collection prompts:
   - Audience/work area
   - Priority theme
   - Projects/initiatives in scope
   - Desired format (1-pager, bullets, talk track)
8. Add output template from overview.
9. Save and publish.
10. Run tests for Finance, Nuclear, and CAO audiences.

## Suggested prompts

1. "Create a finance-oriented brief for transmission expansion and affordability."
2. "Create a CAO brief that connects reliability projects to community impact."
3. "Draft a nuclear/generation talk track linked to operational excellence."

## Placeholder values participants must set

- `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`
- `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`
- `{{WORKSHOP_DATE}}`
