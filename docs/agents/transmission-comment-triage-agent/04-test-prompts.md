# Test prompts

## Happy path

1. "Resident asks whether wetlands are impacted near their property."
2. "Stakeholder asks why project timeline changed."
3. "Comment asks who to contact for right-of-way questions."

## Edge cases

1. Comment without project name.
2. Multi-issue comment (timeline + environmental + property).

## Expected behavior

- Correct category and urgency.
- Draft response is neutral and factual.
- `needsHumanReview` is always true.
