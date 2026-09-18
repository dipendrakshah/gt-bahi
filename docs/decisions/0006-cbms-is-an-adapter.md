# ADR 0006 — CBMS / prize.ird.gov.np are adapters, not the product

- Status: accepted
- Date: 2026-09-18
- Supersedes: implicit “we post to IRD” language in early drafts of `02`, `13`, `16`

## Context

Digital payments auto-enter the Taxpayer Incentive Prize Programme (`prize.ird.gov.np`). That is a **buyer lottery** fed by PSPs, not the merchant sales book.

Tigg, eAccounting (eZone), Lekhapal, BUSY and other listed engines already issue tax invoices and sync headers to CBMS. IRD does not receive payments, purchases, or inventory through that pipe.

## Decision

Bahi’s job is **order ↔ matched payment ↔ stock ↔ invoice**.  
Filing (CBMS) and lottery (prize portal) are **output adapters**.

Default path: emit the issued invoice into an already-listed engine. Native IRD listing is optional and only if a paying ICP cannot file without it.

Do not sell “we post to IRD.” Rails already post payments to the prize programme. Billing incumbents already post invoices to CBMS.

## Consequences

P1 north star is matcher + invoice-from-order, not CBMS certification. Pricing cannot assume we replace Tigg’s listing fee.
