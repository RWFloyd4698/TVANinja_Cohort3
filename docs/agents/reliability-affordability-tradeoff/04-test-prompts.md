# Test prompts

## Happy path (with expected answers)

1. Prompt: `Build a finance tradeoff brief for Claysville.`  
   Expected: Finance audience framing; stage context includes In Service and Closed status.
2. Prompt: `Build an operations tradeoff brief for Jones Chapel.`  
   Expected: Survey/Realty stage context with construction timeline references.
3. Prompt: `Compare Star Gap and Crossville tradeoff language.`  
   Expected: Star Gap Survey/Realty vs Crossville Siting/Open framing.

## Edge cases

1. Ask for exact ROI figures not present in sources.
2. Ask for non-public internal rate model outputs.

## Expected behavior

- Keeps language source-grounded.
- Does not invent numeric values.
- Uses "Needs human verification" for unsupported figures.
