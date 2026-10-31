# FieldTrack — Research Participant Follow-up Platform

> **Status: Draft architecture — not approved for production or implementation.**

FieldTrack is a proposed configurable platform for research teams coordinating participant outreach, callbacks, hospital visits and longitudinal follow-ups across studies, sites, blocks and field assessors.

It is intended for SSRs / research assessors and supervisors. It is **not** intended to replace REDCap or become an unapproved clinical research database.

## Goals

- Give assessors a clear view of their assigned participants and next actions.
- Record contact attempts as an immutable history, not overwrite previous activity.
- Schedule and surface callbacks and study milestones.
- Give supervisors a study/site-level view of workload and progress.
- Support configurable workflows so the platform is not hard-coded for one study.
- Integrate with REDCap only through an institution-approved, server-side integration.

## Draft documentation

- [Architecture and system components](docs/ARCHITECTURE.md)
- [Data model and workflow](docs/DATA_MODEL_AND_WORKFLOWS.md)
- [Security, privacy and governance](docs/SECURITY_AND_GOVERNANCE.md)
- [Technology choices and open-source references](docs/TECHNOLOGY_AND_REFERENCES.md)
- [Implementation roadmap and open decisions](docs/ROADMAP_AND_OPEN_QUESTIONS.md)

## Proposed technology direction

| Layer | Candidate | Role |
|---|---|---|
| Web client | React + TypeScript + Vite | Assessor and supervisor UI |
| PWA | Workbox | App-shell caching and installability |
| Local operational storage | Dexie.js / IndexedDB | Only if approved; no sensitive offline data by default |
| API | Python FastAPI | Authentication-aware application API |
| Operational database | PostgreSQL | Assignments, workflow state, tasks and audit metadata |
| REDCap client | PyCap | Server-side API integration |
| Background jobs | Celery or institution-approved scheduler | Due-task generation and reminders |
| Infrastructure | Docker + Terraform | Reproducible deployment |

These are candidate technologies, not final selections. The institution's security, hosting, identity and data-governance requirements take precedence.

## Core design principles

1. **REDCap remains the system of record** for research data unless the institution formally decides otherwise.
2. **Least privilege:** assessors only see participants assigned to their permitted study/site/block scope.
3. **Auditability:** contact attempts, status changes, reassignment and data sync events are attributable and timestamped.
4. **Configuration over hard-coding:** stages, outcomes, reminder intervals and assignment rules are study-configurable.
5. **Online-first:** offline handling of identifiable data is excluded from the MVP until formally approved.
6. **Data minimisation:** operational screens should use pseudonymous participant codes wherever possible.

## Current scope

The initial proposal covers:
- Assessor dashboard and assigned participant queues.
- Contact action and manual outcome recording.
- Callback scheduling and contact history.
- Hospital / milestone workflow tracking.
- Basic supervisor overview and reassignment.
- Audit events and operational reporting.

It does not yet define the final clinical protocol, exact follow-up date anchors, production hosting, identity provider, REDCap permissions or offline policy.

## Important

This repository contains planning documentation only. Do not commit participant information, phone numbers, clinical data, REDCap exports, API tokens, credentials, production configuration or institutional confidential material.

See [Open questions](docs/ROADMAP_AND_OPEN_QUESTIONS.md) before implementation.
