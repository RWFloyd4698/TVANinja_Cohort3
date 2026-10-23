# Step-by-step build (participant)

1. Open Copilot Studio in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Create agent `Strategic Priority Mapper Agent`.
3. Add knowledge from `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategy`.
4. Add instructions:
   - Use only approved TVA public sources and workshop sample data.
   - If data is missing, state "Needs human verification."
   - Show rationale for each mapping decision.
5. Add triggers:
   - "Map this initiative to TVA strategic priorities."
   - "Create an evidence-based alignment scorecard."
6. Configure output format:
   - Initiative summary
   - Priority mapping
   - Confidence level
   - Missing evidence
   - Source links
7. Save, publish, and run test prompts from `04-test-prompts.md`.
