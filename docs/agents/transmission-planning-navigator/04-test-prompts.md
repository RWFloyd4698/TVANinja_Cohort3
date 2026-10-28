# Test prompts

## Happy path (with expected answers)

1. Prompt: `Summarize the Claysville, Alabama transmission project.`  
   Expected: `Current stage: In Service`; `Public comment status: Closed`.
2. Prompt: `Summarize Crossville and state whether comments are open.`  
   Expected: `Current stage: Siting`; `Public comment status: Open`.
3. Prompt: `List schedule milestones for Star Gap.`  
   Expected: `Current stage: Survey/Realty`; surveys Summer-Fall 2025; easement purchases Fall 2026-Winter 2026-2027; includes source link.

## Edge cases

1. Summarize a project not in knowledge.
2. Provide schedule details where source text is missing.

## Expected behavior

- Uses the canonical output template.
- Returns source links for each response.
- Uses "Needs human verification" for unknown values.
