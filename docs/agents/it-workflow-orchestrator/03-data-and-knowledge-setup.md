# Data and knowledge setup

## Knowledge/list targets

- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Reference-Policies` **[Provided by TVA]**
- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
- SharePoint list `RoutingRules`

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
5. Process and escalation PDFs in `Reference-Policies` **[Provided by TVA]**

## Sample data loading

1. Import `sample-data/workflow-routing-rules-sample.csv` into `RoutingRules`.
2. Save the same rows as an `.xlsx` file and upload to `Reference-Policies` for searchable grounding.
3. Import/confirm sample comments in `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.

## JSON output contract

```json
{
  "intakeId": "string",
  "category": "timeline|environmental|property|process|general",
  "urgency": "low|medium|high",
  "recommendedOwner": "string",
  "nextAction": "string",
  "approvalRequired": true,
  "notesRequiringHumanVerification": "string",
  "sourceLinks": ["string"]
}
```

## Verify in GCC

- If using SharePoint lists directly as knowledge, verify connector behavior in GCC tenant before class.
