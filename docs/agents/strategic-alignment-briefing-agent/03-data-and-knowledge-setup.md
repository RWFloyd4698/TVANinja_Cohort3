# Data and knowledge setup

## Knowledge folder targets

- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`
- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Powerhouse-Stories`
- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Generation`

## Source loading (PDF workflow)

1. Open each source page in Edge.
2. For HTML sources, select **Print** > **Save as PDF**. For PDF sources (Strategic Plan and IRP Executive Summary), download the PDF directly.
3. Upload PDFs to the mapped folder above.
4. Load knowledge at least 2 days before workshop (indexing takes time).

### Exact source pages

1. `https://tva-azr-eastus-cdn-ep-tvawcm-prd.azureedge.net/cdn-tvawcma/docs/default-source/about-tva/guidelines-reports/tva-strategic-plan-%28fy26-fy30%29.pdf?sfvrsn=871adc06_1`
2. `https://www.tva.com/energy/transmission/transmission-system-projects`
3. `https://www.tva.com/the-powerhouse`
4. `https://tva-azr-eastus-cdn-ep-tvawcm-prd.azureedge.net/cdn-tvawcma/docs/default-source/environment/environmental-stewardship/integrated-resource-plan/2026-final-irp/final-2026-irp---executive-summary.pdf?sfvrsn=d3463090_3` (landing page: `https://www.tva.com/environment/final-2026-integrated-resource-plan`)

## Sample data loading

1. Import `sample-data/brief-requests-sample.csv` into `{{TVA_BRIEFREQUESTS_LIST_NAME}}`.
2. Save the same rows as an `.xlsx` file and upload to `Strategic-Plan` (or `Generation`) for search-friendly grounding.
3. Confirm one sample each for Finance, Nuclear/Generation, and CAO.

## Verify in GCC

- If using SharePoint lists directly as knowledge, verify connector behavior in GCC tenant before class.
