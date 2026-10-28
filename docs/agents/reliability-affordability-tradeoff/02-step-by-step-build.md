# Step-by-step build (participant)

## 1. Prerequisites (roles/licenses)

1. Copilot Studio maker access in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Permission to `{{TVA_BRIEFREQUESTS_LIST_NAME}}` and knowledge folders.
3. Power Automate access for brief approval flow integration.
4. Named approvers: `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.

## 2. Create agent (name + description)

1. Name: `Reliability & Affordability Tradeoff Agent`.
2. Description: `Customer-facing agent for balanced reliability and affordability briefing language.`

## 3. Turn on generative orchestration

1. Enable generative orchestration.
2. Save settings.

## 4. Knowledge (SharePoint paths + Authenticate with Microsoft)

1. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`.
2. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`.
3. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Generation`.
4. When prompted, select **Authenticate with Microsoft**.

## 5. Instructions (paste-ready)

Paste exactly:

```text
You are a reliability-affordability tradeoff briefing assistant.

Guardrails:
- Use only approved TVA public sources and workshop sample data.
- Never use internal/private data.
- Never invent cost, ROI, or reliability values.
- If data is missing or unclear, state "Needs human verification."

Always respond in this exact format:
Reliability-Affordability Tradeoff Brief
- Audience:
- Project or initiative:
- Reliability considerations:
- Affordability considerations:
- Recommended framing:
- Source links:
- Notes requiring human verification:
```

## 6. Test in the test pane (3 prompts with expected answers)

1. Prompt: `Create a finance tradeoff brief for Claysville.`  
   Expected: `Audience: Finance`; project stage references In Service/Closed.
2. Prompt: `Create an operations tradeoff brief for Crossville.`  
   Expected: includes Siting/Open context and schedule dependency notes.
3. Prompt: `Compare Jones Chapel and Star Gap tradeoff framing.`  
   Expected: both mapped to Survey/Realty status with source-grounded rationale.

## 7. Add flow as a tool

1. In **Tools**, create/select flow `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`.
2. Use trigger **When an agent calls the flow**.
3. Inputs: `requestId`, `audience`, `projectName`, `tradeoffBrief`.
4. Returned outputs: `approvalStatus`, `publishedArtifactLink`, `flowRunId`.

## 8. Publish (Teams + Microsoft 365 Copilot)

1. Publish in Copilot Studio.
2. Share to Teams context `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
3. Publish to Microsoft 365 Copilot.

## 9. Troubleshooting (3 common issues)

1. **Numerical claims are invented**: reinforce no-fabrication guardrail.
2. **Audience drift**: include audience in every test prompt.
3. **Flow approval status not updating**: verify list permissions on `{{TVA_BRIEFREQUESTS_LIST_NAME}}`.
