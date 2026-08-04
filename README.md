# Connexis Cash (connexis-cash)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Connexis Cash is BNP Paribas's corporate digital banking and cash management platform. It gives multinational corporates a unified online channel for payment initiation, real-time payment tracking, account reporting, reconciliation, and liquidity management across BNP Paribas's global network. Connexis Cash also exposes PSD2-compliant Open Banking APIs through the BNP Paribas CIB developer portal so that third-party providers (TPPs) can retrieve account information and initiate payments on behalf of Connexis Cash users, as well as a Strong Customer Authentication (SCA) flow.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/connexis-cash/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/connexis-cash/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Account Information
- BNP Paribas
- Cash Management
- Corporate Banking
- Digital Banking
- Liquidity Management
- Open Banking
- Payments
- PSD2
- SCA
- STET

## Timestamps

- **Created:** 2024-01-01
- **Modified:** 2026-04-28

## APIs

### Connexis Cash PSD2 Account Information API (STET)

A PSD2-compliant Account Information Service (AISP) API exposed by BNP Paribas Corporate and Institutional Banking. Third-party providers consume this REST/JSON API, which follows the STET PSD2 standard, to retrieve account information for Connexis Cash users. Production uses OAuth2 Authorization Code Grant with QWAC certificates; the sandbox uses Client Credentials. Onboarded TPPs must supply QWAC certificates, callback URLs, and EBA reference codes.

- **Human URL:** [https://developers.cib.bnpparibas.com/index.php/api-docs/account-information-psd2-stet-mock](https://developers.cib.bnpparibas.com/index.php/api-docs/account-information-psd2-stet-mock)
- **Base URL:** `https://psd2.api.cib.bnpparibas.com/gb-account-information-psd2-stet`

#### Tags

- AISP
- PSD2
- REST
- STET

#### Properties

- [Documentation](https://developers.cib.bnpparibas.com/index.php/api-docs/account-information-psd2-stet-mock)
- [Developer  Portal](https://developers.cib.bnpparibas.com/)
- [Production](https://psd2.api.cib.bnpparibas.com/gb-account-information-psd2-stet)
- [Fallback](https://connexis.bnpparibas.com/)
- [Postman Collection](collections/connexis-cash.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/connexis-cash.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Connexis Cash Strong Customer Authentication (SCA)

A documented Strong Customer Authentication flow that BNP Paribas provides for Connexis Cash to satisfy PSD2 SCA requirements. TPPs integrate the SCA flow into their PSD2 journeys so that Connexis Cash users authenticate with two factors before consenting to share account data or initiate payments.

- **Human URL:** [https://developers.cib.bnpparibas.com/index.php/docs/sca](https://developers.cib.bnpparibas.com/index.php/docs/sca)

#### Tags

- PSD2
- SCA
- Security

#### Properties

- [Documentation](https://developers.cib.bnpparibas.com/index.php/docs/sca)
- [Developer  Portal](https://developers.cib.bnpparibas.com/)
- [Postman Collection](collections/connexis-cash.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/connexis-cash.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Connexis Cash Digital Banking Platform

The Connexis Cash digital banking application itself. While not a public REST API, it is the user-facing platform that powers payment initiation, real-time tracking, reconciliation, account reporting, and liquidity management for BNP Paribas corporate customers, with web and mobile apps and host-to-host connectivity options.

- **Human URL:** [https://cashmanagement.bnpparibas.com/solutions/digital-channels](https://cashmanagement.bnpparibas.com/solutions/digital-channels)

#### Tags

- Cash Management
- Digital Channel
- Mobile

#### Properties

- [Documentation](https://cashmanagement.bnpparibas.com/solutions/digital-channels)
- [i O S  App](https://apps.apple.com/us/app/connexis-cash-mobile/id1053068521)
- [Postman Collection](collections/connexis-cash.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/connexis-cash.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Website](https://cashmanagement.bnpparibas.com/solutions/digital-channels)
- [Developer  Portal](https://developers.cib.bnpparibas.com/)
- [Open  Banking  Tracker](https://www.openbankingtracker.com/provider/connexis-cash)
- [B N P  Paribas  C I B](https://cib.bnpparibas/)
- [Mobile  App](https://apps.apple.com/us/app/connexis-cash-mobile/id1053068521)
- [Support](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
