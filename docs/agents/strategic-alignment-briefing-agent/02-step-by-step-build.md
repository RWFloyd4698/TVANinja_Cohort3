# Step-by-step build (participant)

## 1. Prerequisites (roles/licenses)

1. Copilot Studio maker access in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Permission to `{{TVA_SHAREPOINT_SITE_URL}}` and `{{TVA_KNOWLEDGE_LIBRARY_NAME}}`.
3. Power Automate access for flow tool wiring (premium connector availability should be verified in GCC).
4. Named approvers: `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.

## 2. Create agent (name + description)

1. Name: `Strategic Alignment Briefing Agent`.
2. Description: `Customer-facing briefing agent that maps TVA project narratives to strategic priorities.`

## 3. Turn on generative orchestration

1. Enable generative orchestration in agent settings.
2. Save settings.

## 4. Knowledge (SharePoint paths + Authenticate with Microsoft)

1. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`.
2. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`.
3. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Powerhouse-Stories`.
4. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Generation`.
5. When prompted, select **Authenticate with Microsoft**.

## 5. Instructions (paste-ready)

Paste exactly:

```text
You are a customer-facing strategic briefing assistant for TVA workshop scenarios.

Guardrails:
- Use only approved TVA public sources and workshop sample data.
- Never use internal/private data.
- Never fabricate metrics, dates, or outcomes.
- If required data is missing or unclear, state "Needs human verification."

Always respond in this exact format:
Strategic Alignment Brief
- Audience:
- Topic:
- Strategic priority mapping:
- Key supporting evidence:
- Risks and constraints:
- Recommended next action:
- Source links:
- Needs human verification:
```

## 6. Test in the test pane (3 prompts with expected answers)

1. Prompt: `Create a finance brief for Claysville and Jones Chapel.`  
   Expected includes `Audience: Finance` and `Strategic priority mapping:` including Financial Strength.
2. Prompt: `Create a briefing for Nuclear/Generation audience.`  
   Expected includes `Audience: Nuclear/Generation` and `Strategic priority mapping:` including Operational Excellence.
3. Prompt: `Create a CAO briefing for public comment communications.`  
   Expected includes `Audience: CAO` and `Strategic priority mapping:` including Powerful Partnerships.

## 7. Add flow as a tool

1. In **Tools**, create/select flow `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`.
2. Use trigger **When an agent calls the flow**.
3. Inputs: `requestId`, `audience`, `priorityTheme`, `projectsIncluded`, `draftBrief`.
4. Returned outputs: `approvalStatus`, `publishedArtifactLink`, `flowRunId`.

## 8. Publish (Teams + Microsoft 365 Copilot)

1. Publish in Copilot Studio.
2. Share to Teams context `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
3. Publish to Microsoft 365 Copilot.

## 9. Troubleshooting (3 common issues)

1. **Audience output drifts**: verify prompt explicitly sets audience.
2. **No strategic references**: confirm Strategic-Plan PDFs are indexed.
3. **Flow publish errors**: verify `{{TVA_APPROVER_USERS}}` and list permissions.
