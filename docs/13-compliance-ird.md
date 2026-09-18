# 13 — Compliance requirements (product, not legal advice)

Bahi does not ship as “nice invoices.” It ships as software a CA will risk their letterhead on. This file is a *requirements backlog*. Confirm every threshold and format against current IRD notices before implementation. Rules move.

## Non-negotiable product behaviors

1. **Bikram Sambat on every fiscal document** with AD stored alongside.
2. **Fiscal year Shrawan–Ashadh.** Invoice serials reset (or follow the approved scheme) by FY.
3. **13% VAT** as a first-class tax code, plus exempt and zero-rated buckets. Do not hardcode a single rate if law changes — configure, but ship 13% correct.
4. **IRD-shaped sales and purchase books.** Nepali + English field labels where the market expects them.
5. **PAN** on party records; validate format; require on invoices when law/org policy says so.
6. **TDS** as a withholding concept on applicable purchases/services, with heading codes configurable.
7. **Immutable issued invoices.** Edit = credit/debit note + reason. Reprints labeled as copies.
8. **CBMS path.** Either native approved integration or an officially accepted vendor/bridge. Failed syncs are a first-class queue, not a log line.
9. **No delete of audit trail.** Users, API, MCP all land in the same trail.
10. **Access control** so a packer cannot rewrite yesterday’s VAT.

## Computerized billing / CBMS (as understood in 2025–26 market practice)

Public commentary and vendor pages commonly cite:

- Computerized billing obligations above turnover thresholds (figures cited in market content include NPR 10 crore general and NPR 5 crore for some hospitality/ISP categories — **verify**).
- Live or scheduled CBMS sync obligations that tighten at higher turnover (figures cited include NPR 25 crore — **verify**).
- Technical expectations: SQL-backed integrity, sequential FY numbering, restricted reprints, annex-style reports, Web API to CBMS.

Bahi’s roadmap assumes we will either:

- A) obtain listing as IRD-recognized billing software, or
- B) partner with an already-listed engine for issue+sync while Bahi remains the operational order master.

**Decision is open** (`19-open-questions.md`). Do not market “IRD approved” until it is true.

## Government free e-billing risk

In 2026 there was public reporting that the state may offer its own e-billing client. If that ships, **commodity invoice UI dies**. Operational capture of orders + payments remains valuable. Do not build our moat as “we print Annex 5 prettier.”

## Payroll / labour

Out of scope as a module. If we post salary journals:

- Do not claim SSF/PF filing
- Do not compute Labour Act gratuity as a product promise without a specialist

## Data and consumer rules

Watch the e-commerce registration / platform-id regime (Blanxer publishes an e-commerce platform id). If Bahi hosts storefronts or checkout, there may be registration duties. Confirm with counsel before widget GA.

## Calendar and language

- UI: English first, Nepali labels on fiscal reports day one
- Numbers: NPR, grouping familiar to Nepali accounts staff
- Timezone: Asia/Kathmandu only for fiscal “today”

## Accountant acceptance tests (gate for GA)

Give five CAs a sample org. They must produce, without WhatsApping an engineer:

- Sales book for a BS month
- VAT worksheet that ties to issued invoices
- List of credit notes
- Unmatched payments
- A CBMS or equivalent exception list

If they cannot, we are not generally available.
