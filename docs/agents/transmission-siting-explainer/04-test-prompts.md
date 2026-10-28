# Test prompts

## Happy path (with expected answers)

1. Prompt: `Explain siting status for Crossville.`  
   Expected: `Stage (controlled value): Siting`; comments accepted through December 3, 2026.
2. Prompt: `Explain process status for Florence.`  
   Expected: `Stage (controlled value): Construction`; references right-of-way surveys and construction timing.
3. Prompt: `Explain stage and schedule for Star Gap.`  
   Expected: `Stage (controlled value): Survey/Realty`; includes survey and easement checkpoints.

## Edge cases

1. Ask for parcel-level impacts not present in sources.
2. Ask for legal recommendations.

## Expected behavior

- Uses controlled stage values from docs/02.
- Avoids legal advice.
- Returns "Needs human verification" for unsupported detail requests.
