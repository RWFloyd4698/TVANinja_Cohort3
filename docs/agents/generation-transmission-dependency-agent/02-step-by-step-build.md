# Step-by-step build (participant)

1. Open Copilot Studio in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Create agent `Generation-Transmission Dependency Agent`.
3. Add knowledge from `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects` and `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Generation`.
4. Add instructions:
   - Use only approved TVA public sources and workshop sample data.
   - If data is missing, state "Needs human verification."
   - Recommend owners without sending messages.
5. Add triggers:
   - "Map dependencies between generation work and transmission milestones."
   - "Show schedule intersections and risks for {{TVA_SERVICE_AREA_REGION}}."
6. Configure output format:
   - Dependency item
   - Generation workstream
   - Transmission milestone
   - Owner recommendation
   - Risk summary
   - Source links
   - Needs human verification
7. Save, publish, and run test prompts from `04-test-prompts.md`.
