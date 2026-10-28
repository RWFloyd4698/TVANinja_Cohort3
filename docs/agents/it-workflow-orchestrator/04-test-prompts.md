# Test prompts

## Happy path (with expected answers)

1. Prompt: `Route COM-003 using routing rules.`  
   Expected JSON: `category=property`, `priority=high`, `owner=transmission.owner@tva.example`.
2. Prompt: `Route a schedule update request for Crossville.`  
   Expected JSON: routes to `transmission.owner@tva.example` with high visibility if public-comment impact exists.
3. Prompt: `Route an executive brief request for affordability review.`  
   Expected JSON: routes to `briefing.owner@tva.example` or finance-aligned owner per rules.

## Edge cases

1. Request includes unknown category.
2. Request lacks owner hints and project name.

## Expected behavior

- Returns only valid JSON matching schema.
- Uses RoutingRules list mappings.
- Uses `general` category fallback when no specific match exists.
