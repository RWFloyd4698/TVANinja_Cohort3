# Step-by-step build (participant)

## 1. Prerequisites (roles/licenses)

1. Copilot Studio maker access in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Permission to `{{TVA_BRIEFREQUESTS_LIST_NAME}}` and knowledge folders.
3. Power Automate access for approval workflow integration.
4. Named approvers: `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.

## 2. Create agent (name + description)

1. Name: `Community/Gov Relations Hearing Prep Agent`.
2. Description: `Customer-facing hearing prep assistant for community and government relations scenarios.`

## 3. Turn on generative orchestration

1. Enable generative orchestration.
2. Save settings.

## 4. Knowledge (SharePoint paths + Authenticate with Microsoft)

1. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`.
2. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Strategic-Plan`.
3. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Reference-Policies` (**[Provided by TVA]** messaging docs).
4. When prompted, select **Authenticate with Microsoft**.

## 5. Instructions (paste-ready)

Paste exactly:

```text
You are a customer-facing hearing prep assistant for CAO and government relations workshops.

Guardrails:
- Use only approved TVA public sources and workshop sample data.
- Never use internal/private data.
- Do not provide legal commitments or compensation promises.
- If data is missing or unclear, state "Needs human verification."

Always respond in this exact format:
Hearing Prep Pack
- Session objective:
- Audience profile:
- Top stakeholder questions:
- Draft talking points:
- Risk/concern notes:
- Source links:
- Notes requiring human verification:
```

## 6. Test in the test pane (3 prompts with expected answers)

1. Prompt: `Build hearing prep for Claysville community stakeholders.`  
   Expected includes session objective and source-grounded Q&A tied to Claysville.
2. Prompt: `Build hearing prep for Jones Chapel government relations.`  
   Expected includes schedule narrative and Winter 2026-2027 construction reference.
3. Prompt: `Add risk notes for misinformation-sensitive questions.`  
   Expected includes explicit verification notes and no legal commitments.

## 7. Add flow as a tool

1. In **Tools**, create/select flow `{{FLOW_STRATEGIC_BRIEF_PUBLISH_NAME}}`.
2. Use trigger **When an agent calls the flow**.
3. Inputs: `requestId`, `audience`, `projectName`, `hearingPrepPack`.
4. Returned outputs: `approvalStatus`, `publishedArtifactLink`, `flowRunId`.

## 8. Publish (Teams + Microsoft 365 Copilot)

1. Publish in Copilot Studio.
2. Share to Teams context `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
3. Publish to Microsoft 365 Copilot.

## 9. Troubleshooting (3 common issues)

1. **Draft includes commitments**: re-apply no-legal/no-compensation guardrail.
2. **Missing source links**: confirm PDFs are indexed and authenticated.
3. **Approval assignment fails**: use `{{TVA_APPROVER_USERS}}` named user format.
