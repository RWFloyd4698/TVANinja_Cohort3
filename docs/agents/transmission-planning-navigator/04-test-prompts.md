# Test prompts

## Happy path (with expected answers)

1. Prompt: `Summarize the Claysville, Alabama transmission project.`  
   Expected: `Current stage: In Service`; `Public comment status: Closed`.
2. Prompt: `Summarize Crossville and state whether comments are open.`  
   Expected: `Current stage: Siting`; `Public comment status: Open`.
3. Prompt: `Summarize COM context for Star Gap milestones.`  
   Expected: `Current stage: Survey/Realty`; schedule includes survey/easement milestones.

## Edge cases

1. Summarize a project not in knowledge.
2. Provide schedule details where source text is missing.

## Expected behavior

- Uses the canonical output template.
- Returns source links for each response.
- Uses "Needs human verification" for unknown values.
