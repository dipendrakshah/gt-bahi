# 19 — Open questions

Do not silently assume answers. Resolve with an ADR in `docs/decisions/`.

## Identity

1. Keep working name **Bahi** or rename before first invoice PDF goes to a customer?
2. Domain, trademark in Nepal, company vehicle (Pvt. Ltd. already or new)?

## Compliance path

3. Native IRD listing vs bridge through an already-listed billing engine?
4. Who is the named compliance officer on the company file?
5. What exact turnover thresholds apply to *our* ICP this FY? (Verify, do not copy vendor blogs.)

## Architecture

6. Catalog master: Bahi or the storefront? (Recommendation: Bahi for stock/price, storefront may cache.)
7. Event sourcing vs audit table + immutable fiscal rows?
8. Where does production data live (region, vendor)?
9. Multi-tenant DB isolation strategy (row-level vs schema-per-tenant)? Recommendation: row-level + tenant_id until we have a reason.

## Rails

10. First production rail: Fonepay only, or Fonepay + eSewa same month?
11. Commercial contract path for Fonepay as a platform vs each merchant’s own merchant-id?

## Agents

12. Self-hosted model vs hosted API for the order-taker? (Recommendation: hosted API, log everything, tight tools.)
13. Do we ever allow MCP `issue_invoice` for any tier in year 1?

## GTM

14. Design partner list of 20 names — who writes it this week?
15. Implementation done by founders only until when?
16. Public repo vs private? (This clone started private-intent.)

## Economics

17. Attach as % or per-match fee for the first 50 customers?
18. Will we offer a yearly prepaid discount larger than ~15%?

## Scope temptations already visible

19. Pharmacy batch/expiry — only if two paying firms demand it
20. Payroll journals — only if a CA desk cannot live without them
21. Daraz order import — year 2 at earliest
