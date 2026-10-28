# Test prompts

## Happy path (with expected answers)

1. Prompt: `Classify COM-001 and draft response.`  
   Expected: `category=environmental`, `urgency=medium`, `needsHumanReview=true`.
2. Prompt: `Classify COM-002 and draft response.`  
   Expected: `category=timeline`, `urgency=low`, `recommendedOwner=transmission.owner@tva.example`.
3. Prompt: `Classify COM-003 and draft response.`  
   Expected: `category=property`, `urgency=high`, `recommendedOwner=transmission.owner@tva.example`.

## Edge cases

1. Comment text with no project name.
2. Multi-issue comment containing timeline and property concerns.

## Expected behavior

- Returns only valid JSON.
- Uses approved categories: `timeline|environmental|property|process|general`.
- Keeps `needsHumanReview` true and includes source links.
