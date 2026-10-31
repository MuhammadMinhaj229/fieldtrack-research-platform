# Roadmap and Open Questions

> Draft planning document. Milestones are proposals, not commitments.

## Phase 0 — Discovery and approval

- [ ] Confirm research-team users and roles (SSRs, assessors, supervisors, study administrators).
- [ ] Map the current participant contact and follow-up process.
- [ ] Confirm protocol-defined participant statuses and permitted transitions.
- [ ] Confirm milestone date anchors and reminder rules.
- [ ] Review REDCap project structure, API permissions and system-of-record boundary.
- [ ] Agree participant identifier strategy and data minimisation.
- [ ] Confirm hosting, data residency, SSO and security requirements.
- [ ] Obtain institutional, ethics and data-governance approvals as applicable.
- [ ] Confirm accessibility, tablet/browser support and network conditions.

## Phase 1 — MVP

- [ ] Institutional authentication / approved login.
- [ ] Role and study/site/block access controls.
- [ ] Assessor allocation list.
- [ ] Assessor dashboard with defined unique-participant metrics.
- [ ] Due-today and overdue task queues.
- [ ] Participant operational timeline.
- [ ] Call action that opens device dialler where permitted.
- [ ] Manual structured contact outcome recording.
- [ ] Callback scheduling.
- [ ] Append-only contact attempt history.
- [ ] Basic supervisor view.
- [ ] Audit events for all consequential actions.
- [ ] Automated tests using synthetic data.

## Phase 2 — Configurable operations

- [ ] Study workflow configuration.
- [ ] Site/block filters and supervisor assignment management.
- [ ] Versioned reminder and milestone rules.
- [ ] Approved notifications.
- [ ] Operational reports and exports with access controls.
- [ ] Better exception handling and integration monitoring.
- [ ] Administrative configuration UI.

## Phase 3 — Approved integration

- [ ] REDCap API integration approved by administrator.
- [ ] Server-side secrets management.
- [ ] Mapping between FieldTrack operational references and REDCap records.
- [ ] Integration audit trail and failure/retry handling.
- [ ] Reconciliation and data quality checks.
- [ ] Production deployment and recovery testing.

## Phase 4 — Offline capability (only if required)

- [ ] Written offline use case and risk assessment.
- [ ] Approved locally stored fields and retention.
- [ ] Managed-device and encryption strategy.
- [ ] Secure sync and conflict-resolution design.
- [ ] Lost-device and remote-revocation tests.
- [ ] Audit reconciliation after sync.

## Open questions requiring team decisions

### Workflow and protocol
1. What exactly counts as an approach, a successful contact and an interested participant?
2. Can participants be assigned to more than one assessor or team?
3. What are the approved contact-attempt limits and spacing rules?
4. What is the exact anchor for the proposed 40-day follow-up: birth, recruitment, survey completion or another event?
5. What are the later child follow-up milestones, if any?
6. Which statuses are protocol-defined and which are purely operational?

### Data and REDCap
7. Which participant fields are needed in FieldTrack at all?
8. Does FieldTrack store phone numbers or only a protected reference to contact information?
9. Which REDCap project(s), forms and API operations are required?
10. Who approves and manages the REDCap integration identity?
11. How should actor attribution be represented in REDCap and FieldTrack audit records?

### Security and deployment
12. Which institutional identity provider and MFA policy apply?
13. Which hosting environment and region are approved?
14. Is offline use genuinely required? If yes, what operational problem must it solve?
15. Are devices institution-managed or personally owned?
16. What are retention, archival, deletion and incident-response requirements?

### Product and operations
17. Is supervisor access limited to a site/team or can it span a study?
18. Which reports are required by investigators and project coordinators?
19. Are notifications allowed, and through which approved channel?
20. Who will own support, training, configuration and production operations?

## Definition of MVP readiness

The MVP is ready for a controlled pilot only when:
- Workflow and status definitions are signed off by the study team.
- Access-control tests demonstrate cross-study and cross-site isolation.
- Audit history is complete for critical actions.
- No secrets or real participant data are present in the repository.
- Synthetic-data tests pass.
- Security and governance reviews approve the pilot environment.
- Users have tested the workflow against realistic scenarios.
