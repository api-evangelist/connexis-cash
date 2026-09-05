---
name: connexis-cash-transaction-retrieval
description: >-
  Page through booked and pending transactions for a BNP Paribas Connexis Cash account without
  double-counting or dropping entries — the date filter is asymmetric and the cursor is not the page number.
api: Connexis Cash PSD2 Account Information API (STET)
spec: openapi/connexis-cash-account-information-psd2-stet-mock-openapi.yml
operations:
  - accountsGet
  - accountsTransactionsGet
scope: aisp
generated: '2026-09-05'
method: generated
source: openapi/connexis-cash-account-information-psd2-stet-mock-openapi.yml
---

# Transaction retrieval

## The two traps

1. **`entryDateFrom` is inclusive; `entryDateTo` is exclusive.** The provider's own wording:
   transactions with an imputation date equal to `entryDateFrom` *are* included; transactions equal to
   `entryDateTo` are *not*. Windowing day-by-day with both bounds set to the same date returns nothing.
2. **`afterEntryReference` is the cursor, not `pageNumber`.** It takes the technical `entryReference` of
   the last entry you processed and returns only entries with a greater identifier. This is what makes
   incremental sync safe across runs; `pageNumber` is not.

## Steps

1. Get `resourceId` from `accountsGet`.
2. `GET /v2/accounts/{accountResourceId}/transactions` (`accountsTransactionsGet`), or follow
   `_links.transactions`.
3. Optional query parameters: `entryDateFrom`, `entryDateTo` (both date-time), `afterEntryReference`
   (max 40 chars), `pageNumber`, `pageSize`.
4. Read `transactions[]`. Per entry:
   - `status` — `BOOK` (booked) or `PDNG` (pending). **Pending entries can change or disappear.** Never
     reconcile against a pending entry as if it were settled.
   - `creditDebitIndicator` — `CRDT` or `DBIT`. The `transactionAmount.amount` is unsigned; the sign
     lives in this field.
   - `bookingDate`, `valueDate`, `transactionDate` — three different dates. Pick the one your accounting
     rule actually means.
   - `entryReference` — persist this. It is your resume point.
   - `remittanceInformation` — unstructured free text.
5. Follow `_links.next` until it is absent. `_links.parent-list` takes you back to the account list;
   `_links.balances` jumps to the same account's balances.

## Incremental sync pattern

Store the highest `entryReference` you have seen per account. On the next run pass it as
`afterEntryReference` and leave the date filters off. Re-fetch the pending window separately, because a
`PDNG` entry that later books may arrive with a new reference.

## Errors

`400` on a malformed date or page value. `429` with no `Retry-After` — back off. `408 Request Timeout`
on wide windows: narrow the date range or reduce `pageSize` and retry, which is safe because the call is
a `GET`.

## Safety

`GET` only. Safe, repeatable, nothing to undo.
