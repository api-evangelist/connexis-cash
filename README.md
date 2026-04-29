# Connexis Cash (connexis-cash)

Connexis Cash is BNP Paribas's corporate digital banking and cash management platform. It gives multinational corporates a unified online channel for payment initiation, real-time payment tracking, account reporting, reconciliation, and liquidity management across BNP Paribas's global network. Connexis Cash also exposes PSD2-compliant Open Banking APIs through the BNP Paribas CIB developer portal so that third-party providers (TPPs) can retrieve account information and initiate payments on behalf of Connexis Cash users, as well as a Strong Customer Authentication (SCA) flow.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/connexis-cash/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party
- **Classification:** Company

## Tags

- Account Information, BNP Paribas, Cash Management, Corporate Banking, Digital Banking, Liquidity Management, Open Banking, Payments, PSD2, SCA, STET

## Timestamps

- **Created:** 2024-01-01
- **Modified:** 2026-04-28

## APIs

### Connexis Cash PSD2 Account Information API (STET)

A PSD2-compliant Account Information Service (AISP) API exposed by BNP Paribas Corporate and Institutional Banking. Third-party providers consume this REST/JSON API, which follows the STET PSD2 standard, to retrieve account information for Connexis Cash users. Production uses OAuth2 Authorization Code Grant with QWAC certificates; the sandbox uses Client Credentials. Onboarded TPPs must supply QWAC certificates, callback URLs, and EBA reference codes.

**Human URL:** [https://developers.cib.bnpparibas.com/index.php/api-docs/account-information-psd2-stet-mock](https://developers.cib.bnpparibas.com/index.php/api-docs/account-information-psd2-stet-mock)

#### Tags

- AISP, PSD2, REST, STET

#### Properties

- [Documentation](https://developers.cib.bnpparibas.com/index.php/api-docs/account-information-psd2-stet-mock)
- [Developer Portal](https://developers.cib.bnpparibas.com/)
- [Production Endpoint](https://psd2.api.cib.bnpparibas.com/gb-account-information-psd2-stet)
- [Fallback](https://connexis.bnpparibas.com/)

#### Features

- PSD2 STET Compliance
- OAuth2 Authorization Code Grant (production)
- Client Credentials (sandbox)
- QWAC Certificate Authentication
- Account Balances Retrieval
- Transaction Listing
- Full-AISP Consent Model

#### Use Cases

- Aggregate Connexis Cash balances into TPP dashboards
- Build accounting tools that pull bank data automatically
- Power treasury software with multi-bank account access

### Connexis Cash Strong Customer Authentication (SCA)

A documented Strong Customer Authentication flow that BNP Paribas provides for Connexis Cash to satisfy PSD2 SCA requirements.

**Human URL:** [https://developers.cib.bnpparibas.com/index.php/docs/sca](https://developers.cib.bnpparibas.com/index.php/docs/sca)

#### Tags

- PSD2, SCA, Security

#### Properties

- [Documentation](https://developers.cib.bnpparibas.com/index.php/docs/sca)
- [Developer Portal](https://developers.cib.bnpparibas.com/)

#### Features

- Two-Factor Authentication
- PSD2 SCA Compliance
- Redirect Authentication Flow

#### Use Cases

- Authenticate users for AISP/PISP consent
- Satisfy PSD2 SCA in Open Banking integrations

### Connexis Cash Digital Banking Platform

The Connexis Cash digital banking application itself. While not a public REST API, it is the user-facing platform that powers payment initiation, real-time tracking, reconciliation, account reporting, and liquidity management for BNP Paribas corporate customers, with web and mobile apps and host-to-host connectivity options.

**Human URL:** [https://cashmanagement.bnpparibas.com/solutions/digital-channels](https://cashmanagement.bnpparibas.com/solutions/digital-channels)

#### Tags

- Cash Management, Digital Channel, Mobile

#### Properties

- [Documentation](https://cashmanagement.bnpparibas.com/solutions/digital-channels)
- [iOS App](https://apps.apple.com/us/app/connexis-cash-mobile/id1053068521)

#### Features

- Payment Initiation
- Real-Time Tracking
- Reconciliation
- Liquidity Management
- Mobile Companion App
- Host-to-Host Connectivity

#### Use Cases

- Centralize global cash visibility for treasury teams
- Initiate and authorize cross-border payments
- Reconcile inflows and outflows across BNP Paribas accounts

## Common Properties

- [Website](https://cashmanagement.bnpparibas.com/solutions/digital-channels)
- [Developer Portal](https://developers.cib.bnpparibas.com/)
- [Open Banking Tracker](https://www.openbankingtracker.com/provider/connexis-cash)
- [BNP Paribas CIB](https://cib.bnpparibas/)
- [Mobile App](https://apps.apple.com/us/app/connexis-cash-mobile/id1053068521)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
