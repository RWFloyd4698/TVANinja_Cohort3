# Data sources and M365 information architecture

## Required public sources

1. TVA main site: `https://www.tva.com/`
2. TVA Powerhouse: `https://www.tva.com/the-powerhouse`
3. TVA FY26-FY30 strategic plan PDF:  
   `https://tva-azr-eastus-cdn-ep-tvawcm-prd.azureedge.net/cdn-tvawcma/docs/default-source/about-tva/guidelines-reports/tva-strategic-plan-%28fy26-fy30%29.pdf?sfvrsn=871adc06_1`
4. TVA transmission index:  
   `https://www.tva.com/energy/transmission/transmission-system-projects`
5. TVA transmission project detail pages by state/project slug.

## Step-by-step setup (participants)

1. Open SharePoint site `{{TVA_SHAREPOINT_SITE_URL}}`.
2. Create library `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`.
3. Create folders exactly as listed below.
4. Upload public source files/pages into the matching folders.
5. Create the four SharePoint lists with exact column names.
6. Validate at least 5 transmission project rows exist in `{{TVA_TRANSMISSION_LIST_NAME}}`.
7. Save one test file in `{{TVA_ONEDRIVE_WORKSHOP_FOLDER}}` to confirm OneDrive permissions.

## SharePoint structure (required)

Create site `{{TVA_SHAREPOINT_SITE_URL}}` with:

- **Document Library:** `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`
  - `Strategic-Plan/`
  - `Transmission-Projects/`
  - `Generation/`
  - `Powerhouse-Stories/`
  - `Reference-Policies/`
- **Controlled stage values (use only these in all Stage columns):**
  - `Planning`
  - `Siting`
  - `Environmental Review`
  - `Survey/Realty`
  - `Construction`
  - `In Service`
  - `Needs human verification`
- **List:** `{{TVA_TRANSMISSION_LIST_NAME}}`
  - Columns: `ProjectName`, `State`, `County`, `Stage`, `ScheduleText`, `PublicCommentStatus`, `SourceUrl`, `LastValidatedOn`
- **List:** `{{TVA_TRANSMISSION_DRAFTS_LIST_NAME}}`
  - Columns: `DraftId`, `SubmittedOn`, `ProjectName`, `State`, `County`, `Stage`, `ScheduleText`, `PublicCommentStatus`, `DraftSummary`, `SourceUrl`, `Status`, `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`
- **List:** `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`
  - Columns: `CommentId`, `SubmittedOn`, `ProjectName`, `CommentText`, `Category`, `Urgency`, `NeedsHumanReview`, `DraftResponse`, `Owner`, `Status`, `SourceUrl`, `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`
- **List:** `{{TVA_BRIEFREQUESTS_LIST_NAME}}`
  - Columns: `RequestId`, `RequestedBy`, `Audience`, `DueDate`, `PriorityTheme`, `ProjectsIncluded`, `DraftBrief`, `ApprovalStatus`, `PublishedLink`, `FlowRunId`, `AgentVersion`, `Approver`, `ApprovalDecision`, `DecisionTimestamp`, `PublishedArtifactLink`

## OneDrive structure (optional personal working area)

- `/TVANinjaCohort3/working-drafts/`
- `/TVANinjaCohort3/demo-exports/`

## Data refresh cadence

- Transmission project list: weekly
- Strategic plan source: monthly verification
- Powerhouse story references: weekly
- List health check (missing URLs, stale records): before every workshop

## Data quality minimums

1. Every project must have `SourceUrl`.
2. Every project must have `Stage` and `PublicCommentStatus`.
3. Strategic-plan excerpts must include citation to section/page context.
4. No row may include internal notes, customer-private details, or non-public references.
