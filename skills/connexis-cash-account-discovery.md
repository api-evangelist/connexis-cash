---
name: connexis-cash-account-discovery
description: >-
  Discover which BNP Paribas Connexis Cash accounts an AISP has been granted access to, and resolve
  each one to the ASPSP resourceId that every other call needs. Use this first — nothing else in the
  Connexis Cash PSD2 surface works without a resourceId.
api: Connexis Cash PSD2 Account Information API (STET)
spec: openapi/connexis-cash-account-information-psd2-stet-mock-openapi.yml
operations:
  - accountsGet
scope: aisp
generated: '2026-09-05'
method: generated
source: openapi/connexis-cash-account-information-psd2-stet-mock-openapi.yml
---

# Account discovery

## When to use this

You have an OAuth2 token with the `aisp` scope for a Connexis Cash user (the PSU) and need to know
which accounts you can read. Everything else — balances, transactions — is keyed on an identifier that
only this call returns.

## Before you call

- **Token.** Sandbox: `client_credentials` against
  `https://api.sandbox.cib.bnpparibas.com/oauth2/v1/token`. Production: `authorization_code` against
  `https://api.cib.bnpparibas.com/oauth2/v1/token`, with `client_id` set to the `organizationIdentifier`
  from your eIDAS certificate's distinguished name.
- **Transport.** Production requires mutual TLS with a QWAC. Without a client certificate the gateway
  answers `400 No required SSL certificate was sent` before your token is ever read.
- **Headers.** `X-Request-ID` is required (max 70 chars — generate a UUID and keep it, you will need it
  for support). `Signature` is required. `Digest` is optional. Forward the `PSU-*` context headers when
  the call is PSU-initiated.

## Steps

1. `GET /v2/accounts` (`accountsGet`).
2. Read `accounts[]` from the HAL envelope. For each account keep:
   - `resourceId` — **this is the identifier every other operation takes.** It is *not* the IBAN.
   - `accountId.iban`, `bicFi`, `currency`, `name` — for display and reconciliation.
   - `cashAccountType` (CACC cash, CARD card-based, …) and `usage` (ORGA corporate, PRIV private).
   - `_links.balances` and `_links.transactions` — prefer following these hrefs over building paths.
3. If `_links.next` is present, follow it. Do not increment `pageNumber` by hand.
4. `connectedPsu` names the person who granted the access. Log it; you will want it in an audit trail.

## Errors

| Status | What it means here | Do this |
|---|---|---|
| 401 | Token missing or expired (access tokens live ~1799s) | Re-mint and retry once |
| 403 | Authenticated, but the scope or consent does not cover this | Check `aisp` scope and that the PSU completed SCA |
| 404 | No resource | Nothing to read; do not retry |
| 429 | Throttled — **no Retry-After is returned** | Exponential backoff with jitter |
| 500 / 503 | ASPSP trouble | Retry with backoff; quote `X-Request-ID` to `dl.cib.api.psd2.support@bnpparibas.com` |

The 401/404/429 responses echo `x-correlation-id`; the others echo `X-Request-ID`. Capture both.

## Safety

This is a `GET`. It is safe, repeatable and has nothing to undo. There is no write operation anywhere
on this contract.
