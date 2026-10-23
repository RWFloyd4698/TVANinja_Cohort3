# Agent overview: Transmission Comment Triage Agent

## Purpose

Classify and draft responses for public-facing transmission comments, then route to human review.

## Primary users

- Transmission project communications teams
- Community engagement/government relations
- CAO and HR/comms support

## Core capabilities

1. Classify comments (timeline, environmental, property, process, general concern).
2. Assign urgency and recommended owner.
3. Draft response options in plain language.
4. Output structured JSON for Power Automate.

## Boundaries

- Draft-only assistant.
- No auto-send; human approval required.
- Public-source content only.

## Output JSON contract

```json
{
  "commentId": "string",
  "projectName": "string",
  "category": "timeline|environmental|property|process|general",
  "urgency": "low|medium|high",
  "needsHumanReview": true,
  "recommendedOwner": "string",
  "draftResponse": "string",
  "sourceLinks": ["string"]
}
```
