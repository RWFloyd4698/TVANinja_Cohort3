# Step-by-step build (participant)

## 1. Prerequisites (roles/licenses)

1. Copilot Studio maker access in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Permission to `{{TVA_SHAREPOINT_SITE_URL}}` and `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`.
3. Power Automate access for tool wiring (premium connector availability in GCC should be verified by TVA).
4. Named approvers: `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.

## 2. Create agent (name + description)

1. Name: `Transmission Planning Navigator`.
2. Description: `Customer-facing transmission planning assistant for TVA public project information.`

## 3. Turn on generative orchestration

1. In agent settings, enable generative orchestration.
2. Save settings before adding knowledge and tools.

## 4. Knowledge (SharePoint paths + Authenticate with Microsoft)

1. Add knowledge source: `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`.
2. Add knowledge source: `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`.
3. When prompted, select **Authenticate with Microsoft**.

## 5. Instructions (paste-ready)

Paste exactly:

```text
You are a customer-facing transmission planning assistant for TVA workshop scenarios.

Guardrails:
- Use only approved TVA public sources and workshop sample data.
- Never use internal/private data.
- Never invent project facts, dates, or statuses.
- If any required detail is missing or unclear, state "Needs human verification."

Always respond in this exact format:
Transmission Project Snapshot
- Project:
- State/County:
- Current stage:
- Reliability/load rationale:
- Public comment status:
- Key schedule milestones:
- Source links:
- Notes requiring human verification:
```

## 6. Test in the test pane (3 prompts with expected answers)

1. Prompt: `Summarize the Claysville, Alabama transmission project.`  
   Expected: `Current stage: In Service`, `Public comment status: Closed`.
2. Prompt: `What stage is Crossville in and is comment intake open?`  
   Expected: `Current stage: Siting`, `Public comment status: Open`.
3. Prompt: `List schedule milestones for Star Gap.`  
   Expected includes surveys and easement sequence from sample data, with source link.

## 7. Add flow as a tool

1. In **Tools**, create/select flow `{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`.
2. Use trigger **When an agent calls the flow**.
3. Inputs: `projectName`, `stateCounty`, `currentStage`, `publicCommentStatus`, `scheduleMilestones`, `draftSummary`, `sourceLinks`.
4. Returned outputs: `status`, `draftId`, `publishedArtifactLink`.

## 8. Publish (Teams + Microsoft 365 Copilot)

1. Publish the agent in Copilot Studio.
2. Share to Teams channel context `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
3. Publish to Microsoft 365 Copilot for tenant testing.

## 9. Troubleshooting (3 common issues)

1. **No grounded citations**: confirm PDFs are indexed in `Transmission-Projects` and `Strategic-Plan`.
2. **Flow tool not visible**: confirm environment match between agent and flow.
3. **Approval fails**: switch from group mailbox to named users `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
