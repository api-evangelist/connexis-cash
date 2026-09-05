---
name: connexis-cash-balance-reporting
description: >-
  Pull the balance report for one BNP Paribas Connexis Cash account and interpret the ISO 20022 balance
  types correctly — which is the difference between a treasury figure you can act on and one you cannot.
api: Connexis Cash PSD2 Account Information API (STET)
spec: openapi/connexis-cash-account-information-psd2-stet-mock-openapi.yml
operations:
  - accountsGet
  - accountsBalancesGet
scope: aisp
generated: '2026-09-05'
method: generated
source: openapi/connexis-cash-account-information-psd2-stet-mock-openapi.yml
---

# Balance reporting

## Steps

1. Run **connexis-cash-account-discovery** (`accountsGet`) and take the `resourceId` of the account you
   want. Do not pass the IBAN here — it will 404.
2. `GET /v2/accounts/{accountResourceId}/balances` (`accountsBalancesGet`), or better, follow the
   `_links.balances` href the account returned.
3. Read `balances[]`. Each entry carries:
   - `balanceAmount` — `{amount, currency}`; the amount is a **string**, so parse it as a decimal, never
     as a float.
   - `balanceType` — the ISO 20022 balance status. `CLBD` is the closing booked balance. Do not assume a
     single balance is "the" balance; an account can return several types and they mean different things.
   - `name` — the bank's own label for the balance (e.g. "Ledger Booked 2018-06-20").
   - `referenceDate` — what date the figure is as of.
   - `lastChangeDateTime` and `lastCommittedTransaction` — useful when you need an instant balance and
     have to prove freshness.

## Do not

- Do not sum balances of different `balanceType` values. They are alternative views of the same account.
- Do not compare amounts across `currency` values without converting.
- Do not cache a balance without its `referenceDate`.

## Errors

Same set as account discovery, plus `400 Invalid status value`. On a 400 here, check that you passed a
`resourceId` and not an IBAN or an alias. `429` arrives with no `Retry-After` — back off on your own
schedule. See `errors/connexis-cash-problem-types.yml`.

## Safety

`GET` only. Safe and repeatable; nothing to reverse.
