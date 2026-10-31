# Technology Evaluation and Open-Source References

> These are candidate tools and reference projects. Check current maintenance, release activity, security advisories, compatibility and licence terms before adopting any dependency.

## 1. Proposed stack

| Layer | Candidate | Why it is being considered | Decision |
|---|---|---|---|
| Frontend | React + TypeScript + Vite | Familiar component ecosystem and maintainable typed UI | Proposed |
| PWA caching | Workbox | Service-worker tooling for app shell and static assets | Proposed |
| Local browser DB | Dexie.js | IndexedDB abstraction; only for approved local data | Conditional |
| Backend | FastAPI | Python API framework with validation and OpenAPI | Proposed |
| Database | PostgreSQL | Relational integrity and transactional workflow records | Proposed |
| REDCap API | PyCap | Python client for REDCap API | Conditional on approval |
| Validation | Pandera | Useful for tabular data validation in supporting pipelines | Optional |
| Background jobs | Celery or institutional scheduler | Reliable due-task processing | To evaluate |
| Deployment | Docker | Reproducible service packaging | Proposed |
| Infrastructure as code | Terraform AWS modules | Reusable infrastructure patterns if AWS is selected | Conditional |

## 2. Direct repository links

### Application foundations
- [React](https://github.com/facebook/react) — UI library.
- [TypeScript](https://github.com/microsoft/TypeScript) — typed JavaScript.
- [Vite](https://github.com/vitejs/vite) — frontend build tooling.
- [FastAPI](https://github.com/fastapi/fastapi) — Python API framework.
- [PostgreSQL](https://github.com/postgres/postgres) — relational database.
- [Docker](https://github.com/moby/moby) — container runtime / ecosystem.

### PWA and local persistence
- [Workbox](https://github.com/GoogleChrome/workbox) — service worker and caching libraries.
- [Dexie.js](https://github.com/dexie/Dexie.js) — IndexedDB wrapper.
- [PouchDB](https://github.com/pouchdb/pouchdb) — local database and replication model; evaluate carefully before choosing.
- [Capacitor SQLite](https://github.com/capacitor-community/sqlite) — native SQLite option for a future managed mobile wrapper; review encryption support and platform constraints.

### REDCap and data validation
- [PyCap](https://github.com/redcap-tools/PyCap) — Python client for REDCap API.
- [Pandera](https://github.com/unionai-oss/pandera) — dataframe schema and validation.
- [Great Expectations](https://github.com/great-expectations/great_expectations) — data quality validation framework.

### Field research / health workflow references
- [CommCare HQ](https://github.com/dimagi/commcare-hq) — mature case-management and frontline data collection reference.
- [CommCare Android](https://github.com/dimagi/commcare-android) — Android field application reference.
- [DHIS2 Capture App](https://github.com/dhis2/capture-app) — health programme data capture patterns.
- [OpenSRP FHIR Core](https://github.com/opensrp/fhircore) — FHIR-oriented health workflow reference; likely more complex than FieldTrack needs.

### Infrastructure and security
- [Terraform AWS Modules](https://github.com/terraform-aws-modules) — AWS infrastructure modules.
- [Checkov](https://github.com/bridgecrewio/checkov) — infrastructure-as-code security scanning.
- [AWS CDK](https://github.com/aws/aws-cdk) — infrastructure defined in code if AWS CDK is preferred.

## 3. Reference project selection guidance

Do not clone a large platform and attempt to customise it before the workflow is understood.

Recommended approach:
1. Build a small FieldTrack domain model and API.
2. Borrow interaction and workflow ideas from CommCare and DHIS2.
3. Use PyCap only after REDCap API permissions are agreed.
4. Keep the PWA online-first; introduce offline sync only with a written threat model.
5. Adopt libraries rather than importing entire reference applications unless there is a clear maintenance and licensing reason.

## 4. Licence review

Before adding a dependency:
- Read its repository LICENSE file and third-party notices.
- Check licences for plugins, examples, icons, fonts and copied assets independently.
- Record the dependency version and licence in a software bill of materials.
- Review security advisories and dependency maintenance.
- Obtain institutional/legal review where required.

A repository being public on GitHub does not automatically mean its code is permissively licensed or suitable for reuse.
