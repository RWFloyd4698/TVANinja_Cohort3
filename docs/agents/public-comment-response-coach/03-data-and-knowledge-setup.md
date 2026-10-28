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

1. `https://www.tva.com/energy/transmission/transmission-projects/claysville-alabama`
2. `https://www.tva.com/energy/transmission/transmission-projects/jones-chapel-alabama`
3. `https://www.tva.com/energy/transmission/transmission-projects/star-gap--alabama-(fort-payne--dekalb-county)`
4. Customer-facing response policy PDFs in `Reference-Policies` **[Provided by TVA]**

## Sample data loading

1. Map `sample-data/public-comment-coach-sample.csv` into `{{TVA_PUBLICCOMMENTS_LIST_NAME}}` fields (`CommentId`, `ProjectName`, `CommentText`, `Category`, `DraftResponse`, `Status`, `SourceUrl`).
2. Save mapped sample rows as an `.xlsx` file and upload to `Transmission-Projects` (or `Reference-Policies`) for search.

## Verify in GCC

- If using SharePoint lists directly as knowledge, verify connector behavior in GCC tenant before class.
