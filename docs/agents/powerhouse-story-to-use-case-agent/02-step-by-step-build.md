# Step-by-step build (participant)

1. Open Copilot Studio in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Create agent `Powerhouse Story-to-Use-Case Agent`.
3. Add knowledge from `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Powerhouse-Stories`.
4. Add instructions:
   - Use only approved TVA public sources and workshop sample data.
   - If data is missing, state "Needs human verification."
   - Produce implementation-ready scenario cards only.
5. Add triggers:
   - "Convert this TVA story into an agent + flow use case."
   - "Recommend owner, trigger, approval path, and KPI."
6. Configure output format:
   - Story title
   - Proposed agent
   - Proposed flow
   - Data model
   - Approver path
   - KPI
   - Source links
7. Save, publish, and run test prompts from `04-test-prompts.md`.
