# Deployment Readiness Checklist (Enterprise)

Target Environment: Production (High Availability)
Compliance Level: HIPAA-Adjacent (Caregiving)

## 1. Security & Identity [CRITICAL]
- [x] Admin routes protected by Firebase Auth verifyIdToken.
- [x] Firestore Security Rules strictly enforce per-session isolation.
- [x] P0 Hard Consent Gate implemented at both Client and Server levels.
- [x] Auth token rotation verified.
- [ ] PII Masking verified in logging service.

## 2. Integration & RAG [CRITICAL]
- [x] Pinecone/Vector DB Grounding implemented (Staged for external KB).
- [x] Answer-absent refusal logic enforced (Absolute Prohibition rules).
- [x] Dual-LLM Validation Gate integrated before CRM push.
- [x] Transition proofs (deterministic verifier) recorded in audit logs.

## 3. CRM & Survivability [BLOACKER]
- [x] Durable Lead Staging queue created (`leadStaging` collection).
- [x] Staging tracks `syncStatus`, `syncAttempts`, and `correlationId`.
- [ ] External Orchestration (Make/Airtable) environment variables verified.
- [x] Primary sync fallback logic (GHL) captures `crmRecordId`.

## 4. ESC Protocols [STABILITY]
- [x] ESC-01 through ESC-07 fully implemented.
- [x] ESC-03 Critical Distress triggers synchronous audit log alert.
- [x] ESC-07 Technical Failure allows graceful manual fallback.
- [x] AI knows and prioritizes protocols over standard responses.

## 5. Operations & Docs [COMPLIANCE]
- [x] Structured JSON logging with correlation IDs.
- [x] Crisis Response SOP included in RUNBOOK.md.
- [x] Audit log schema covers LEAD_VALIDATION_FAILURE and ESCALATION_TRIGGERED.
- [x] Remediation report for Option A vs Option B finalized.
