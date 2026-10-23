# Data and knowledge setup

## SharePoint folder target

`{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`

## Load sequence

1. Add transmission index reference page URL list.
2. Add project detail reference list (at least 10 projects).
3. Add strategic-plan excerpt notes with source links.
4. Load sample list rows from `sample-data/transmission-projects-sample.csv`.

## Minimum required list columns

- `ProjectName`
- `State`
- `County`
- `Stage`
- `ScheduleText`
- `PublicCommentStatus`
- `SourceUrl`
- `LastValidatedOn`

## Quality checks

1. Every row has a source URL.
2. Stage is one of: Planning, Siting, Environmental Review, Survey/Realty, Construction, In Service, Needs human verification.
3. At least one row is flagged as public comment open/active.
