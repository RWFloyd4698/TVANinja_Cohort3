# Data and knowledge setup

## Knowledge folder targets

- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`
- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`

## Source loading (PDF workflow)

1. Open each source page in Edge.
2. For HTML sources, select **Print** > **Save as PDF**. For PDF sources (Strategic Plan and IRP Executive Summary), download the PDF directly.
3. Upload PDFs to the mapped folder above.
4. Load knowledge at least 2 days before workshop (indexing takes time).

### Exact source pages

1. `https://www.tva.com/energy/transmission/transmission-system-projects`
2. `https://www.tva.com/energy/transmission/transmission-projects/claysville-alabama`
3. `https://www.tva.com/energy/transmission/transmission-projects/jones-chapel-alabama`
4. `https://www.tva.com/energy/transmission/transmission-projects/star-gap--alabama-(fort-payne--dekalb-county)`
5. `https://www.tva.com/energy/transmission/transmission-projects/crossville--alabama-(dekalb-county)`
6. `https://www.tva.com/energy/transmission/transmission-projects/florence-alabama`
7. `https://tva-azr-eastus-cdn-ep-tvawcm-prd.azureedge.net/cdn-tvawcma/docs/default-source/about-tva/guidelines-reports/tva-strategic-plan-%28fy26-fy30%29.pdf?sfvrsn=871adc06_1`

## Sample data loading

1. Import `sample-data/transmission-projects-sample.csv` into `{{TVA_TRANSMISSION_LIST_NAME}}`.
2. Save the same rows as an `.xlsx` file and upload to `Transmission-Projects` so the agent can search them as knowledge.
3. Keep sample set at 5 projects for workshop demos.

## Verify in GCC

- If using SharePoint lists directly as knowledge, verify connector behavior in GCC tenant before class.
