# Step-by-step build (participant)

## 1. Prerequisites (roles/licenses)

1. Copilot Studio maker access in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Permission to `{{TVA_PUBLICCOMMENTS_LIST_NAME}}` and knowledge folders.
3. Power Automate + Planner access for routing and approvals.
4. Named approvers: `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.

## 2. Create agent (name + description)

1. Name: `Public Comment Response Coach`.
2. Description: `Draft-only coach for customer-facing response options to public transmission comments.`

## 3. Turn on generative orchestration

1. Enable generative orchestration.
2. Save settings.

## 4. Knowledge (SharePoint paths + Authenticate with Microsoft)

1. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`.
2. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Reference-Policies`.
3. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Powerhouse-Stories` (optional context).
4. When prompted, select **Authenticate with Microsoft**.

## 5. Instructions (paste-ready)

Paste exactly:

```text
You are a draft-only public response coach for transmission comments.

Guardrails:
- Use only approved TVA public sources and workshop sample data.
- Never use internal/private data.
- Never send or publish messages directly.
- If data is missing or unclear, state "Needs human verification."

Always respond in this exact format:
Public Response Draft
- Comment ID:
- Category/Urgency:
- Draft response:
- Verification notes:
- Recommended owner:
- Source links:
- Notes requiring human verification:
```

## 6. Test in the test pane (3 prompts with expected answers)

1. Prompt: `Draft a response for COM-001.`  
   Expected: environmental framing and verification note; neutral customer tone.
2. Prompt: `Draft a response for COM-002.`  
   Expected: timeline concern response; references schedule wording and source URL.
3. Prompt: `Draft a response for COM-003 and recommend owner.`  
   Expected: property concern; recommended owner is `transmission.owner@tva.example`.

## 7. Add flow as a tool

1. In **Tools**, create/select flow `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`.
2. Use trigger **When an agent calls the flow**.
3. Inputs: `commentId`, `projectName`, `commentText`, `draftResponse`.
4. Returned outputs: `status`, `owner`, `approvalDecision`, `publishedArtifactLink`.

## 8. Publish (Teams + Microsoft 365 Copilot)

1. Publish in Copilot Studio.
2. Share to Teams context `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
3. Publish to Microsoft 365 Copilot.

## 9. Troubleshooting (3 common issues)

1. **Response tone too technical**: reinforce plain-language instruction.
2. **Owner recommendation missing**: verify comment category and routing rules in knowledge.
3. **Approval dead-ends**: use named approvers `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
