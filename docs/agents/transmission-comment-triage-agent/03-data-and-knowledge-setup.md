# Data and knowledge setup

## SharePoint target

List: `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`

## Minimum columns

- `CommentId`
- `SubmittedOn`
- `ProjectName`
- `CommentText`
- `Category`
- `Urgency`
- `NeedsHumanReview`
- `DraftResponse`
- `Owner`
- `Status`
- `SourceUrl`

## JSON output contract

```json
{
  "commentId": "string",
  "projectName": "string",
  "category": "timeline|environmental|property|process|general",
  "urgency": "low|medium|high",
  "needsHumanReview": true,
  "recommendedOwner": "string",
  "nextStep": "string",
  "draftResponse": "string",
  "notesRequiringHumanVerification": "string",
  "sourceLinks": ["string"]
}
```

## Data load steps

1. Import `sample-data/public-comments-sample.csv` into `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
2. Verify each row includes `ProjectName` and `CommentText`.
3. Run agent triage on at least 3 records and confirm JSON parses in flow.
