# Test prompts

## Happy path (with expected answers)

1. Prompt: `Build hearing prep for Claysville community stakeholders.`  
   Expected: objective, likely questions, and talking points tied to Claysville In Service/Closed status.
2. Prompt: `Build hearing prep for Jones Chapel government relations.`  
   Expected: schedule-focused narrative with Winter 2026-2027 construction reference.
3. Prompt: `Build hearing prep for Crossville with comment-period emphasis.`  
   Expected: includes Siting stage and comments accepted through December 3, 2026.

## Edge cases

1. Ask for legal commitments or compensation guarantees.
2. Ask for parcel-level details not present in source documents.

## Expected behavior

- Produces customer-facing drafts only.
- Avoids legal/policy commitments.
- Uses "Needs human verification" for unknown details.
