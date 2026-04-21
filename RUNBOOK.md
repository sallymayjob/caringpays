# CaringPays Enterprise Operations Runbook

## Incident Response Standard Operating Procedures (SOP)

### Incident Level: CRITICAL (ESC-03 Triggered)
**Symptom:** User expresses intent of self-harm or danger.
- **Auto-Action:** System locks conversation and outputs specialized welfare resource payload.
- **Manual Step:**
  1. Access Firebase Console -> `auditLogs` collection.
  2. Filter by `type: ESCALATION` AND `severity: CRITICAL`.
  3. Notify the Clinical Review Team with the `sessionId`.
  4. DO NOT attempt to resume AI conversation.

### Incident Level: HIGH (CRM Sync Failure)
**Symptom:** Logs show `CRM Sync Failed` or records remain in `RETRY_PENDING`.
- **Diagnosis:** Check GHL API keys or Airtable rate limits.
- **Recovery:**
  1. Go to Admin Dashboard -> Sync Queue tab.
  2. Identify `Failed` or `Retry Pending` records.
  3. Export failed records as CSV and manually upload to GHL if automatic retry fails 5 times.
  4. Reset `syncStatus` to `QUEUED` to force manual retry via system.

## Performance & Guardrails
### Answer-Absent Hallucinations
- **Metric:** False positive hallucination rate.
- **Adjustment:** If Charlie is guessing, tighten the `Grounding` prompt in `src/services/geminiService.ts` or add specific exclusion keywords to the dynamic context.

### Validation Gate Rejections
- **Symptom:** Real leads are being rejected with `VALIDATION_FAILED`.
- **Adjustment:** Review `ENTERPRISE_VALIDATION_SERVICE` prompt. Loosen the "Relevancy" threshold if high-intent users are getting blocked due to complex phrasing.

## Secrets Management
- `GEMINI_API_KEY`: Rotation every 90 days.
- `GHL_API_KEY`: Per-location rotation.
- Firestore Security Rules: Deploy via `firebase deploy --only firestore:rules` after every blueprint update.
