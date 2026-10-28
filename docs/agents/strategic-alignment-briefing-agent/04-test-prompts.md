# Test prompts

## Happy path (with expected answers)

1. Prompt: `Create a finance brief for Claysville and Jones Chapel.`  
   Expected: `Audience: Finance`; `Strategic priority mapping:` includes Financial Strength.
2. Prompt: `Create a nuclear-generation brief for transmission projects in Alabama.`  
   Expected: `Audience: Nuclear/Generation`; `Strategic priority mapping:` includes Operational Excellence.
3. Prompt: `Create a CAO briefing for public comment and project communication.`  
   Expected: `Audience: CAO`; `Strategic priority mapping:` includes Powerful Partnerships.

## Edge cases

1. Request a KPI not present in source material.
2. Request a brief without naming a project.

## Expected behavior

- Uses the canonical output template from 01-overview.
- Includes source links.
- Flags unsupported claims with "Needs human verification."
