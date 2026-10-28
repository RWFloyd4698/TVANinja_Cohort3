# Data and knowledge setup

## Knowledge folder targets

- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Reference-Policies` **[Provided by TVA]**

## Source loading (PDF workflow)

1. Open each source page in Edge.
2. Select **Print** > **Save as PDF**.
3. Upload PDFs to the mapped folder above.
4. Load knowledge at least 2 days before workshop (indexing takes time).

### Exact source pages

1. `https://www.tva.com/energy/transmission/transmission-system-projects`
2. `https://www.tva.com/energy/transmission/transmission-projects/claysville-alabama`
3. `https://www.tva.com/energy/transmission/transmission-projects/jones-chapel-alabama`
4. `https://www.tva.com/energy/transmission/transmission-projects/star-gap--alabama-(fort-payne--dekalb-county)`
5. Customer-facing messaging policy PDFs in `Reference-Policies` **[Provided by TVA]**

## SharePoint list targets

- `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`
- `RoutingRules`

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

## Sample data loading

1. Import `sample-data/public-comments-sample.csv` into `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
2. Save the same rows as an `.xlsx` file and upload to `Transmission-Projects` for knowledge search.
3. Import `../it-workflow-orchestrator/sample-data/workflow-routing-rules-sample.csv` into `RoutingRules`.

## Verify in GCC

- If using SharePoint lists directly as knowledge, verify connector behavior in GCC tenant before class.
