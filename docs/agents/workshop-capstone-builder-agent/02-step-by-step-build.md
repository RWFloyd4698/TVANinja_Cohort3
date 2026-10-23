# Step-by-step build (participant)

1. Open Copilot Studio in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Create agent `Workshop Capstone Builder Agent`.
3. Add knowledge from:
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategy`
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
   - `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Powerhouse-Stories`
4. Add instructions:
   - Use only approved TVA public sources and workshop sample data.
   - If data is missing, state "Needs human verification."
   - Build a capstone packet with explicit approval steps.
5. Add triggers:
   - "Assemble final implementation pack for this team."
   - "Generate a rollout-ready capstone checklist."
6. Configure output format:
   - Agent summary
   - Data setup
   - Flow wiring
   - Governance controls
   - Test and acceptance checklist
7. Save, publish, and run test prompts from `04-test-prompts.md`.
