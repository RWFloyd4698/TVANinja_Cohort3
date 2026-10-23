# Data and knowledge setup

## SharePoint folder target

`{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`

## Load sequence

1. Upload strategic plan PDF and a text extract with section headers.
2. Upload a curated transmission project reference table.
3. Add optional Powerhouse story references for narrative examples.
4. Load sample requests from `sample-data/brief-requests-sample.csv`.

## Minimum list/library requirements

- Strategic priorities and objective statements present.
- At least 3 source citations available for each sample briefing output.
- One example each for Finance, Nuclear/Generation, and CAO.
- `{{TVA_BRIEFREQUESTS_LIST_NAME}}` includes `RequestId`, `RequestedBy`, `Audience`, `DueDate`, `PriorityTheme`, `ProjectsIncluded`, `DraftBrief`, `ApprovalStatus`, `PublishedLink`, and audit fields.

## Quality checks

1. Every brief references at least one strategic priority.
2. No private/internal sources are present.
3. Audience language is adapted by role.
