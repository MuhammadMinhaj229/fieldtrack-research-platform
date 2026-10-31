# Security, Privacy and Governance

> Mandatory review document. This draft is not a substitute for institutional security review, ethics approval, data-protection review or REDCap administrator approval.

## 1. Data classification first

Before implementation, the study team must classify every field as:
- Public project information.
- Internal operational information.
- Pseudonymous participant information.
- Direct identifiers (for example, name, phone number or address).
- Sensitive research / clinical information.

FieldTrack should collect and display the minimum information required for operational follow-up. Do not assume pseudonymous data is automatically non-sensitive.

## 2. REDCap integration safeguards

- Keep REDCap API credentials exclusively on the backend.
- Never place API tokens in JavaScript bundles, browser local storage, source control, mobile app configuration or assessor devices.
- Use an institution-approved integration identity and minimum required project permissions.
- Confirm whether REDCap API activity is attributed to the integration account and maintain a separate FieldTrack actor-level audit trail.
- Apply record-level and instrument-level permissions where supported and required.
- Use TLS and protect secrets using an approved secrets manager.
- Rotate and revoke credentials through an approved operational process.
- Log integration events without logging tokens or unnecessary participant payloads.

Do not build a shared-token architecture until the REDCap administrator and institution have explicitly approved it.

## 3. Authentication and authorisation

Candidate roles:
- Platform administrator: platform configuration and account administration.
- Study administrator: study-specific configuration and workforce management.
- Supervisor: permitted site/team progress and reassignment.
- Assessor / SSR: own assigned participants and allowed workflow actions.
- Auditor: read-only access to authorised audit records.

Enforce authorisation on every backend request. The client must never be trusted to enforce study, site, block or participant boundaries.

Use institutional SSO where available. Define session expiry, logout, account deactivation, MFA requirements and shared-device behaviour.

## 4. Local storage and offline risk

The MVP is online-first.

Do not store direct identifiers, phone numbers, clinical responses or REDCap records in IndexedDB or service-worker caches without written approval and a documented threat model.

If offline capability is required, specify:
- Which fields may be stored locally.
- Device encryption and mobile device management.
- Key management and protection against rooted/jailbroken devices.
- Local retention and automatic expiry.
- Remote revocation and lost-device response.
- Secure sync and conflict resolution.
- Audit reconciliation after reconnection.
- Shared-device logout and local data purge.

Browser storage can be cleared or evicted. A PWA does not guarantee durable local storage or create a protected user-visible folder.

## 5. Audit trail

Record at least:
- Authenticated actor.
- Action and affected entity reference.
- Timestamp (server-generated; store timezone consistently).
- Before/after state or a controlled change summary.
- Reason where required.
- Request / correlation identifier.
- Source device or session metadata only where proportionate and approved.

Audit events should be append-only for ordinary application users. Restrict audit access and define retention. Avoid collecting intrusive telemetry such as GPS or call recordings unless there is a separately approved, justified need.

## 6. Notes and communications

- Define allowed operational note content.
- Avoid clinical notes or unnecessary sensitive narrative.
- Do not record or monitor calls by default.
- The app may open the phone dialler, but cannot reliably know whether a call was answered.
- Notifications must not reveal sensitive participant details on lock screens or shared devices.
- Confirm consent, communication preferences and study-specific contact rules.

## 7. Infrastructure and operations

- Use institution-approved hosting and data residency.
- Separate development, staging and production.
- Use private networking and least-privilege service identities.
- Encrypt traffic and database/backups at rest.
- Patch dependencies and scan container images.
- Store secrets outside source control.
- Monitor authentication failures, access denials, integration failures and unusual data access.
- Test backups and restoration.
- Define incident response and breach escalation procedures.

## 8. Governance checklist

Before real data is used, obtain decisions / approvals for:
- Study protocol and ethics / institutional review requirements.
- Data controller / custodian and permitted purpose.
- Data dictionary and classification.
- REDCap project/API permissions.
- Hosting provider, region and data residency.
- Identity provider and role mapping.
- Retention, archival and deletion.
- Offline storage and device management.
- Notification channels and participant contact policy.
- Audit retention and access.
- Vendor / processor agreements where applicable.
- Security assessment and operational ownership.

## 9. Non-negotiable development rule

Use synthetic data only in local development, demos, screenshots, automated tests and public repository examples. Never commit participant data, exports, credentials, tokens, private keys, database dumps or confidential institutional documents.
