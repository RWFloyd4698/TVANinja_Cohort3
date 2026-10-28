# Data and knowledge setup

## Knowledge folder target

- `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`

## Source loading (PDF workflow)

1. Open each source page in Edge.
2. Select **Print** > **Save as PDF**.
3. Upload PDFs to `Transmission-Projects`.
4. Load knowledge at least 2 days before workshop (indexing takes time).

### Exact source pages

1. `https://www.tva.com/energy/transmission/transmission-system-projects`
2. `https://www.tva.com/energy/transmission/transmission-projects/claysville-alabama`
3. `https://www.tva.com/energy/transmission/transmission-projects/jones-chapel-alabama`
4. `https://www.tva.com/energy/transmission/transmission-projects/star-gap--alabama-(fort-payne--dekalb-county)`
5. `https://www.tva.com/energy/transmission/transmission-projects/crossville--alabama-(dekalb-county)`
6. `https://www.tva.com/energy/transmission/transmission-projects/florence-alabama`

## Sample data loading

1. Import `sample-data/siting-stages-sample.csv` into `{{TVA_TRANSMISSION_LIST_NAME}}`.
2. Save the same rows as an `.xlsx` file and upload to `Transmission-Projects`.
3. Stage values must use the controlled list from docs/02.

## Verify in GCC

- If using SharePoint lists directly as knowledge, verify connector behavior in GCC tenant before class.
