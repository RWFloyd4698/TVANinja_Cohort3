# Data and knowledge setup

## Knowledge folder targets

- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`
- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Generation`

## Source loading (PDF workflow)

1. Open each source page in Edge.
2. Select **Print** > **Save as PDF**.
3. Upload PDFs to the mapped folder above.
4. Load knowledge at least 2 days before workshop (indexing takes time).

### Exact source pages

1. `https://tva-azr-eastus-cdn-ep-tvawcm-prd.azureedge.net/cdn-tvawcma/docs/default-source/about-tva/guidelines-reports/tva-strategic-plan-%28fy26-fy30%29.pdf?sfvrsn=871adc06_1`
2. `https://www.tva.com/energy/transmission/transmission-system-projects`
3. `{{TVA_IRP_2026_EXEC_SUMMARY_URL}}` **[Provided by TVA]**

## Sample data loading

1. Map `sample-data/tradeoff-scenarios-sample.csv` into `{{TVA_BRIEFREQUESTS_LIST_NAME}}` rows (`RequestId` from `ScenarioId`, `Audience`, `PriorityTheme`, `ProjectsIncluded`, `DraftBrief`, `ApprovalStatus`).
2. Save mapped sample rows as an `.xlsx` file and upload to `Strategic-Plan` or `Generation` for grounding.

## Verify in GCC

- If using SharePoint lists directly as knowledge, verify connector behavior in GCC tenant before class.
