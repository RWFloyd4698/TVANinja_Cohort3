# Step-by-step build (participant)

## 1. Prerequisites (roles/licenses)

1. Copilot Studio maker access in `{{TVA_COPILOT_STUDIO_ENVIRONMENT}}`.
2. Permission to SharePoint lists `{{TVA_PUBLICCOMMENTS_LIST_NAME}}` and `RoutingRules`.
3. Power Automate + Planner access (premium connector availability should be verified in GCC).
4. Named approvers: `{{TVA_APPROVER_USERS}}` **[Provided by TVA]**.
5. Planner plan/bucket: `{{TVA_PLANNER_PLAN_ID}}` / `{{TVA_PLANNER_BUCKET_ID}}` **[Provided by TVA]**.

## 2. Create agent (name + description)

1. Name: `IT Workflow Orchestrator Agent`.
2. Description: `Workflow routing assistant for intake classification, owner mapping, and approval-gated orchestration.`

## 3. Turn on generative orchestration

1. Enable generative orchestration.
2. Save settings.

## 4. Knowledge (SharePoint paths + Authenticate with Microsoft)

1. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Reference-Policies`.
2. Add `{{TVA_SHAREPOINT_SITE_URL}}/{{TVA_KNOWLEDGE_LIBRARY_NAME}}/Transmission-Projects`.
3. Add data from SharePoint list `RoutingRules` (verify in GCC).
4. When prompted, select **Authenticate with Microsoft**.

## 5. Instructions (paste-ready)

Paste exactly:

```text
You are an IT workflow routing assistant for customer-facing transmission intake workflows.

Guardrails:
- Use only approved TVA public sources and workshop sample data.
- Never use internal/private data.
- Never bypass required approvals.
- If data is missing or unclear, state "Needs human verification."

Return only valid JSON.
Always respond in this exact format:
{
  "intakeId": "",
  "category": "",
  "urgency": "",
  "recommendedOwner": "",
  "nextAction": "",
  "approvalRequired": true,
  "notesRequiringHumanVerification": "",
  "sourceLinks": []
}
```

## 6. Test in the test pane (3 prompts with expected answers)

1. Prompt: `Route COM-001 for wetlands concern.`  
   Expected: `category=environmental`, `urgency=medium`, owner mapped by rules.
2. Prompt: `Route COM-003 right-of-way concern.`  
   Expected: `category=property`, `urgency=high`, `recommendedOwner=transmission.owner@tva.example`.
3. Prompt: `Route timeline escalation for Jones Chapel.`  
   Expected: `category=timeline`, `urgency=low`, approval required true.

## 7. Add flow as a tool

1. In **Tools**, create/select flow `{{FLOW_PUBLICCOMMENT_TRIAGE_NAME}}`.
2. Use trigger **When an agent calls the flow**.
3. Inputs: `intakeId`, `projectName`, `commentText`.
4. Returned outputs: `status`, `owner`, `plannerTaskId`, `approvalDecision`.

## 8. Publish (Teams + Microsoft 365 Copilot)

1. Publish in Copilot Studio.
2. Share to Teams context `{{TVA_TEAMS_WORKSHOP_CHANNEL}}`.
3. Publish to Microsoft 365 Copilot.

## 9. Troubleshooting (3 common issues)

1. **JSON parse fails**: ensure output contains JSON only, no prose.
2. **Routing misses owner**: confirm `RoutingRules` list is loaded and accessible.
3. **Planner assignment fails**: ensure owner email resolves to a user in planner plan.
