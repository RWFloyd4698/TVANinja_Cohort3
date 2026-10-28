# Step-by-step build (participant)

## 1. Prerequisites (roles/licenses)

1. Copilot Studio maker access in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Permission to `{{TVA_SHAREPOINT_SITE_URL}}` and `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`.
3. Power Automate access for tool wiring.
4. Named approvers: `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.

## 2. Create agent (name + description)

1. Name: `Transmission Siting Explainer`.
2. Description: `Customer-facing explainer for TVA transmission siting process and milestones.`

## 3. Turn on generative orchestration

1. Enable generative orchestration.
2. Save settings.

## 4. Knowledge (SharePoint paths + Authenticate with Microsoft)

1. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`.
2. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Reference-Policies`.
3. When prompted, select **Authenticate with Microsoft**.

## 5. Instructions (paste-ready)

Paste exactly:

```text
You are a customer-facing transmission siting explainer.

Guardrails:
- Use only approved TVA public sources and workshop sample data.
- Never use internal/private data.
- Do not provide legal advice.
- If data is missing or unclear, state "Needs human verification."

Always respond in this exact format:
Siting Explanation Brief
- Project:
- Stage (controlled value):
- Stage summary:
- Schedule checkpoints:
- Stakeholder guidance:
- Source links:
- Notes requiring human verification:
```

## 6. Test in the test pane (3 prompts with expected answers)

1. Prompt: `Summarize Crossville siting stage and comment period.`  
   Expected: `Stage (controlled value): Siting`; includes comments accepted through December 3, 2026.
2. Prompt: `Summarize Florence project process status.`  
   Expected includes `Stage: Construction` and schedule checkpoints from sample data.
3. Prompt: `Explain what landowners should expect during Survey/Realty.`  
   Expected plain-language survey/easement explanation grounded to sample schedule rows.

## 7. Add flow as a tool

1. In **Tools**, create/select flow `{{FLOW_TRANSMISSION_UPDATE_APPROVAL_NAME}}`.
2. Use trigger **When an agent calls the flow**.
3. Inputs: `projectName`, `stage`, `scheduleCheckpoints`, `draftSummary`, `sourceLinks`.
4. Returned outputs: `status`, `draftId`, `publishedArtifactLink`.

## 8. Publish (Teams + Microsoft 365 Copilot)

1. Publish in Copilot Studio.
2. Share to Teams context `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
3. Publish to Microsoft 365 Copilot.

## 9. Troubleshooting (3 common issues)

1. **Stage not in controlled list**: enforce stage values from docs/02.
2. **No source links returned**: confirm project PDFs were indexed.
3. **Approval routing fails**: use named users `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
