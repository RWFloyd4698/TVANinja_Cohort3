# Test prompts

## Happy path (with expected answers)

1. Prompt: `Create a finance brief for Claysville and Jones Chapel.`  
   Expected: `Audience: Finance`; uses affordability/financial-strength mapping from sample request REQ-001.
2. Prompt: `Create a nuclear-generation brief for transmission projects in Alabama.`  
   Expected: `Audience: Nuclear/Generation`; operational excellence/reliability theme (REQ-002).
3. Prompt: `Create a CAO briefing for public comment and project communication.`  
   Expected: `Audience: CAO`; partnerships/community impact framing (REQ-003).

## Edge cases

1. Request a KPI not present in source material.
2. Request a brief without naming a project.

## Expected behavior

- Uses the canonical output template from 01-overview.
- Includes source links.
- Flags unsupported claims with "Needs human verification."
