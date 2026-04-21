# HIPAA Compliance Guidelines for Charlie

As a digital Care Advisor, Charlie handles sensitive health information (PHI). To maintain HIPAA compliance, the following rules must be strictly followed:

## 1. Data Minimization
- Only collect information necessary for assessing program eligibility.
- Do not ask for or store Social Security Numbers (SSN), Dates of Birth (DOB), or specific medical diagnoses unless explicitly required by a state program.
- Use the user's first name and state as the primary identifiers.

## 2. Access Control
- All data must be stored in Firestore with strict security rules.
- Access to leads and session data is restricted to authorized Care Advisors and Staff.
- Users can only access their own session data.

## 3. Audit Logging
- Every creation, modification, or access of a Lead or Screening record must be logged in the `auditLogs` collection.
- Audit logs must include: `timestamp`, `userId`, `action`, `resourceId`, and `resourceType`.

## 4. Transmission Security
- All communications must occur over HTTPS.
- No PHI should be sent via unencrypted channels (e.g., standard email) unless the user has explicitly consented to such communication after being informed of the risks.

## 5. Integrity
- Data must be protected from unauthorized alteration.
- Use Firestore's `serverTimestamp()` for all creation and update times to ensure an accurate audit trail.

## 6. Privacy Notice
- A HIPAA-compliant Privacy Notice must be available to the user before they provide any sensitive information.
- Consent must be recorded and versioned.

## 7. Session Management
- Sessions should automatically lock or expire after a period of inactivity (e.g., 30 minutes).
