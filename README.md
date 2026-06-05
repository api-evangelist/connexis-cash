# Connexis Cash (connexis-cash)

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
