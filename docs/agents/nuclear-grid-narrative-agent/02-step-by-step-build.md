# Step-by-step build (participant)

1. Open Copilot Studio in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Create agent `Nuclear & Grid Narrative Agent`.
3. Add knowledge from `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategy` and `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Generation`.
4. Add instructions:
   - Use only approved TVA public sources and workshop sample data.
   - If data is missing, state "Needs human verification."
   - Do not create unverified operational claims.
5. Add triggers:
   - "Build a nuclear-grid reliability narrative for an executive audience."
   - "Summarize how this narrative maps to TVA strategic priorities."
6. Configure output format:
   - Narrative paragraph
   - Priority mapping
   - Assumptions and evidence gaps
   - Source links
7. Save, publish, and run test prompts from `04-test-prompts.md`.
