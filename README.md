# Intelerad (intelerad)

Intelerad Medical Systems is an enterprise medical imaging company. Its platform spans diagnostic PACS (**IntelePACS**), the **InteleViewer** / zero-footprint web-based DICOM viewer, a vendor-neutral archive (**VNA**), and the cloud image-exchange platform **InteleShare** - the product formed after Intelerad **acquired Ambra Health (Ambra Image Exchange / DICOM Grid) in 2021**.

The InteleShare / Ambra platform exposes a documented public **"v3 Services" REST-like API** plus a **Storage API** for programmatically managing DICOM studies, patients, orders, radiology reports, HL7 message flows, routing, webhooks, and multi-tenant namespaces. Integration is built on medical-imaging interoperability standards - **DICOM and DICOMweb (WADO-RS / QIDO-RS / STOW-RS)**, **HL7 v2 (ORM orders, ORU results, ADT demographics)**, and **FHIR** - with a **Gateway** that routes DICOM and HL7 between on-premise systems and the cloud, and EHR/RIS integrations (Epic, Cerner, Athena).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/intelerad/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/intelerad/refs/heads/main/apis.yml)

## Access Model (Read This First)

- The **InteleShare / Ambra v3 Services API** and **Storage API** are **publicly documented** at [access.dicomgrid.com/api/v3/api.html](https://access.dicomgrid.com/api/v3/api.html). They are RPC-style: clients POST (or GET) to action endpoints under a resource namespace, and every response carries a `status` field of `OK` or `ERROR`. Authentication uses a session id (`sid`) from `/session/login`, HTTP Basic auth, or OAuth tokens.
- **Actual API usage is account- and contract-gated.** You need a provisioned InteleShare / Ambra account and appropriate role/namespace permissions; there is no open, self-service sign-up or public pricing for API access.
- The **core PACS / RIS / viewer APIs** (IntelePACS, InteleViewer, InteleRIS) are **partner- and contract-gated** with no open public reference; they are reached through Intelerad's Gateway and standards-based interfaces (DICOM, DICOMweb, HL7, FHIR) rather than a public developer portal.
- The OpenAPI in this repo is **honestly modeled** (`x-endpoints-modeled: true`) from the public v3 reference and the InteleShare HL7 Guide. Paths are representative, not byte-exact; treat Intelerad's own reference as authoritative.

## Tags

- Medical Imaging
- PACS
- Enterprise Imaging
- Radiology
- DICOM
- DICOMweb
- HL7
- FHIR
- Healthcare
- Interoperability
- Image Exchange

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

Logical APIs modeled from the public InteleShare / Ambra v3 Services and Storage API reference:

### InteleShare Studies API

Manage DICOM studies in the cloud - list, get, share, route, tag, and delete studies, retrieve metadata and images, push/pull pixel data. Instance access is also available over DICOMweb (WADO-RS retrieve, QIDO-RS query, STOW-RS store).

- **API Reference:** [https://access.dicomgrid.com/api/v3/api.html](https://access.dicomgrid.com/api/v3/api.html)
- **Base URL:** `https://access.dicomgrid.com/api/v3`

### InteleShare Storage API

The raw DICOM image / study binary layer - upload (STOW-style ingest), retrieve rendered or original images and frames, wrap/unwrap DICOM, and manage thumbnails.

- **API Reference:** [https://access.dicomgrid.com/api/v3/storage/storage_api.html](https://access.dicomgrid.com/api/v3/storage/storage_api.html)
- **Base URL:** `https://access.dicomgrid.com/api/v3/storage`

### InteleShare Patients API

Create, list, get, and update patient records and demographics, manage PHI and patient-portal (PHR) access, and reconcile / normalize patient identity across sources.

- **Base URL:** `https://access.dicomgrid.com/api/v3`

### InteleShare Orders and Worklist API

Manage healthcare orders and scheduled procedures that drive the radiology worklist - create, list, get, update, and cancel orders, typically fed by inbound HL7 ORM order messages.

- **Base URL:** `https://access.dicomgrid.com/api/v3`

### InteleShare Reports API

Create, list, get, and publish radiology reports and report templates attached to a study, and exchange results via HL7 ORU result messages.

- **Base URL:** `https://access.dicomgrid.com/api/v3`

### InteleShare HL7 Integration API

Configure HL7 message templates and transforms and exchange clinical data via the InteleShare Gateway - inbound and outbound ORM (orders), ORU (results/reports), and ADT (demographics) messages.

- **HL7 Guide:** [InteleShare 3.24.2.0 HL7 Guide (PDF)](https://www.intelerad.com/en/wp-content/uploads/sites/2/2024/05/InteleShare-3.24.2.0-HL7-Guide.pdf)
- **Base URL:** `https://access.dicomgrid.com/api/v3`

### InteleShare Webhooks and Routing API

Register webhooks for platform events and manage study distribution - routes, destinations (query/retrieve targets), and storage nodes that move studies between the cloud and connected DICOM systems.

- **Base URL:** `https://access.dicomgrid.com/api/v3`

### InteleShare Namespaces and Accounts API

Administer the multi-tenant structure - accounts, namespaces (tenant scoping and access control), users, invitations, roles, and API tokens, plus session management (login/logout, OAuth, CSRF).

- **Base URL:** `https://access.dicomgrid.com/api/v3`

## Standards

- **DICOM / DICOMweb** - WADO-RS (retrieve), QIDO-RS (query), STOW-RS (store); zero-footprint FDA-cleared HTML5 viewer.
- **HL7 v2** - ORM (orders), ORU (results/reports), ADT (patient demographics) via the Gateway.
- **FHIR** - modern REST interoperability for clinical data exchange.

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/intelerad-medical-systems)
- [Website](https://www.intelerad.com/)
- [Documentation (v3 API Reference)](https://access.dicomgrid.com/api/v3/api.html)
- [Plans](plans/intelerad-plans-pricing.yml)
- [Rate Limits](rate-limits/intelerad-rate-limits.yml)
- [Fin Ops](finops/intelerad-finops.yml)
- [Blog](https://www.intelerad.com/en/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
