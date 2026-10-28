# Step-by-step build (participant)

## 1. Prerequisites (roles/licenses)

1. Copilot Studio maker access in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Permission to `{{TVA_PUBLICCOMMENTS_LIST_NAME}}`.
3. Power Automate + Planner access (premium connector availability in GCC should be verified by TVA).
4. Named approvers: `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
5. Planner plan/bucket: `{{TVA_PLANNER_PLAN_ID}}` / `{{TVA_PLANNER_BUCKET_ID}}` **[Provided by TVA]**.

## 2. Create agent (name + description)

1. Name: `Transmission Comment Triage Agent`.
2. Description: `Draft-only comment triage assistant for customer-facing transmission responses.`

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
You are a draft-only transmission comment triage assistant.

Guardrails:
- Use only approved TVA public sources and workshop sample data.
- Never use internal/private data.
- Never auto-send responses.
- If data is missing or unclear, state "Needs human verification."

Return only valid JSON.
Always respond in this exact format:
{
  "category": "",
  "urgency": "",
  "recommendedOwner": "",
  "nextStep": "",
  "draftResponse": "",
  "needsHumanReview": true,
  "notesRequiringHumanVerification": "",
  "sourceLinks": []
}
```

## 6. Test in the test pane (3 prompts with expected answers)

1. Prompt: `Classify: How will this affect nearby wetlands and creeks? (Claysville)`  
   Expected: `category=environmental`, `urgency=medium`.
2. Prompt: `Classify: Why did the schedule move and when will construction begin? (Jones Chapel)`  
   Expected: `category=timeline`, `urgency=low`.
3. Prompt: `Classify: Who do I contact about right-of-way access concerns? (Star Gap)`  
   Expected: `category=property`, `urgency=high`, `recommendedOwner=transmission.owner@tva.example`.

## 7. Add flow as a tool

1. In **Tools**, create/select flow `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`.
2. Use trigger **When an agent calls the flow**.
3. Inputs: `commentId`, `projectName`, `commentText`.
4. Returned outputs: `status`, `owner`, `plannerTaskId`, `approvalDecision`.

## 8. Publish (Teams + Microsoft 365 Copilot)

1. Publish in Copilot Studio.
2. Share to Teams context `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
3. Publish to Microsoft 365 Copilot.

## 9. Troubleshooting (3 common issues)

1. **Invalid JSON returned**: tighten instruction order and remove prose from output.
2. **Owner not assigned in Planner**: verify owner email exists in tenant and maps to Planner assignee.
3. **Approvals stuck**: use named approvers `{{TVA_APPROVER_USERS}}` instead of distribution groups.
