# 07 — Product principles

These are binding until an ADR replaces them.

## 1. The invoice is a consequence, not a data-entry screen

If a human has to retype an Instagram order into a billing form, Bahi has failed. The sales document *becomes* the invoice.

## 2. Issued fiscal documents are immutable

IRD rule internalized: no silent edit after issue. Corrections are credit/debit notes with reason. The UI must make this obvious and unscary.

## 3. Dual calendar is native

Every document stores BS and AD. Fiscal year is Shrawan–Ashadh. Reports default to BS. API can request either.

## 4. Money is a first-class object

A payment is not a checkbox on an invoice. It has rail, reference, amount, fee, settlement batch, and match state (`unmatched`, `suggested`, `matched`, `disputed`).

## 5. Stock is promised only from the ledger

Chat agents and storefronts may not invent availability. They query `get_stock`. If offline, they fail closed or use a last-known snapshot with an explicit flag.

## 6. API before pixel-perfect admin

If the Woo plugin and the CA export work, the marketing site can stay ugly for six months. The opposite is death.

## 7. MCP is the same contract as the API

No special MCP-only verbs that skip permissions, audit log, or tenant isolation. An agent is a user with a token.

## 8. One ICP per quarter

If a hospital asks for ward billing, the answer is no until the D2C loop is default-alive.

## 9. Compliance is a product manager, not an afterthought hire

Someone who has filed VAT in Nepal reviews every invoice state machine before it ships.

## 10. NPR on every price list we show customers

No USD stickers on the website.

## 11. Be boring in the database, expressive in clients

Postgres-shaped truth. Chat, MCP, and widgets are replaceable. The journal is not.

## 12. Kill features that do not change match-rate or invoice-latency

Vanity dashboards, theme editors, and “AI CEO summaries” wait.
