# Intelerad (intelerad)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
