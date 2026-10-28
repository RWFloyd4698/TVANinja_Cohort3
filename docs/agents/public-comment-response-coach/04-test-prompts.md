# Test prompts

## Happy path (with expected answers)

1. Prompt: `Draft a response for COM-001.`  
   Expected: environmental concern response; neutral tone; verification note included.
2. Prompt: `Draft a response for COM-002.`  
   Expected: timeline-focused response grounded in project schedule text.
3. Prompt: `Draft a response for COM-003.`  
   Expected: property/right-of-way response; recommended owner `transmission.owner@tva.example`.

## Edge cases

1. Request to send response directly to a resident.
2. Request parcel-level compensation details not in source.

## Expected behavior

- Output stays draft-only.
- Requires human approval before outbound use.
- Uses "Needs human verification" for unsupported details.
