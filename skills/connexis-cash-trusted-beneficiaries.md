---
name: connexis-cash-trusted-beneficiaries
description: >-
  Read the PSU's trusted (whitelisted) beneficiaries from BNP Paribas Connexis Cash, and read the
  isTrusted flag the way PSD2 actually defines it rather than the way it looks.
api: Connexis Cash PSD2 Account Information API (STET)
spec: openapi/connexis-cash-account-information-psd2-stet-mock-openapi.yml
operations:
  - trustedBeneficiariesGet
scope: aisp
generated: '2026-09-05'
method: generated
source: openapi/connexis-cash-account-information-psd2-stet-mock-openapi.yml
---

# Trusted beneficiaries

## Steps

1. `GET /v2/trusted-beneficiaries` (`trustedBeneficiariesGet`). It is PSU-level, not account-level — no
   `accountResourceId` is required.
2. Read `beneficiaries[]`. Per entry:
   - `id` — the beneficiary identifier (max 35 chars).
   - `creditor` — party identification: name, postal address, identification.
   - `creditorAccount` — `{iban, other}`.
   - `creditorAgent` — `{bicFi}` plus clearing-system member identification.
   - `isTrusted` — see below.
3. Follow `_links.next` while present.

## Reading `isTrusted` correctly

The contract is explicit and it is not intuitive: *"The ASPSP having not implemented the trusted
beneficiaries list must not set this flag."* So the field is three-valued in practice:

- `true` — the ASPSP confirms the beneficiary is on the PSU's trusted list.
- `false` — the ASPSP confirms it is not.
- **absent** — the ASPSP does not implement the list at all. This is **not** the same as `false`.

Treat an absent `isTrusted` as "unknown", never as "untrusted". A whitelist you inferred from a missing
field is a whitelist you invented.

Under the PSD2 RTS a beneficiary on the trusted list can attract an SCA exemption on a later payment.
That makes this list a security-relevant input, not just a convenience — do not surface it to a user as
"verified" beyond what the flag actually says.

## Errors

`401`, `403`, `404`, `405`, `406`, `429`, `500`. There is no `400` and no `503` declared on this
operation. `429` carries no `Retry-After`.

## Safety

`GET` only. This skill reads the trusted list; it cannot add to it. No operation on this contract can.
