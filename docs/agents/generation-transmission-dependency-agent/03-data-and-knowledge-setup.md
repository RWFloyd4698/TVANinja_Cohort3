# Data and knowledge setup

1. Load TVA public transmission project pages into `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`.
2. Load TVA public generation context pages into `{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Generation`.
3. Import sample rows from `sample-data/generation-transmission-dependencies-sample.csv`.
4. Confirm fields match the CSV exactly:
   - `DependencyId`
   - `GenerationWorkstream`
   - `TransmissionProject`
   - `DependencySummary`
   - `Owner`
   - `SourceUrl`
   - `NeedsHumanVerification`
5. Save the mapped rows as an `.xlsx` and upload it to the `Generation` folder so the agent can search sample records.
6. Ensure every row can be traced to public TVA material; otherwise mark `Needs human verification`.
