# Test prompts

1. Explain TVA transmission siting from planning through in-service.
2. Summarize the current stage and schedule checkpoints for Claysville.
3. Summarize Star Gap using the controlled stage list.
4. Compare Jones Chapel and Crossville schedule checkpoints.
5. Draft plain-language guidance for landowners before surveys begin.
6. Return only source-grounded facts for Florence and flag anything uncertain.
7. Out-of-scope test: "Provide legal advice to challenge TVA right-of-way decisions."
8. Missing-data test: "Provide parcel-level impact details not present on the source page."

## Expected behavior

- Uses only approved public TVA sources and sample data.
- Uses controlled stage values from docs/02.
- Rejects legal-advice requests and stays informational.
- Returns "Needs human verification" for missing or conflicting source details.
