# 15 — Unit economics and break-even

Snapshot assumptions: Kathmandu, late 2026 start, lean team, NPR.

## Burn model

### Team v1 (months 0–12)

| Seat | Role | Loaded cost / month (order of magnitude) |
|---|---|---|
| 1 | Founder-engineer | 150–250k |
| 1 | Engineer | 120–200k |
| 1 | Engineer / integrations | 120–200k |
| 1 | Compliance-minded accountant / PM | 80–150k |
| 0.5–1 | CS + onboarding | 50–100k |

Plus cloud, SMS, Meta API, Fonepay commercial, office/internet, CA consult: 100–200k.

**Planning burn: NPR 1.0–1.6 million / month.**

Do not hire sales before 80 paying accounts unless a founder cannot sell.

## ARPU model

| Mix in year 2 | Share | ARPU |
|---|---|---|
| Start | 20% | 2,000 |
| Operate | 60% | 5,500 (sub + some attach) |
| Firm | 15% | 10,000 |
| CA seats residual | 5% | 3,000 blended |

**Planning blended ARPU: NPR 6,000 / month.**

If realized ARPU < 3,000 after 40 customers, the package is wrong or the ICP is kirana. Stop and change ICP, do not “add AI.”

## Contribution

Gross margin target ≥ 75% on subscription. Attach margin after rail costs ≥ 60%. Implementation is cash, not margin strategy.

Support load: if CS tickets per org per month > 4 after month 2 of tenure, the product is not ready to scale accounts.

## Break-even math

`accounts_needed = monthly_burn / ARPU`

| Burn | ARPU 4,000 | ARPU 6,000 | ARPU 8,000 |
|---|---|---|---|
| 1.0M | 250 | 167 | 125 |
| 1.3M | 325 | 217 | 163 |
| 1.6M | 400 | 267 | 200 |

## Sales velocity needed (base)

Assume month 6 is first meaningful conversions (before that: design partners at discount).

- 10 net new paying / month from month 6–12 → ~70 by month 12 (not enough)
- 15 / month year 2 → ~250 by month 24

**Base case cash-flow break-even: month 24–30.**  
**Optimistic (existing CA book or seller community): month 18–24.**  
**12 months: only if burn stays ~4 people *and* a channel drops 15+ orgs in Q2.**

Calendar: start Oct 2026 → base break-even **late 2028 / FY 2085**.

## Design-partner phase (months 0–6)

- 8–12 brands
- Heavily discounted or free software
- Paid only if we do implementation labor
- Goal is CBMS-quality invoices and matcher precision, not revenue

Do not count design partners as “paying accounts” in investor or self-deception dashboards.

## Sensitivity that kills the company

1. Building storefront for six months before matcher
2. Hiring to 10 people at NPR 2.5M burn with 30 customers
3. Lifetime plans at NPR 15k
4. Support burden from restaurants
5. IRD listing delayed and marketing already claimed approval

## Cash needed

18 months of 1.3M burn ≈ **NPR 2.3 crore** before break-even if revenue ramps linearly from month 6. Revenue reduces this. Bootstrapping is possible if founders take below-market pay and design partners pay implementation. Otherwise raise a small Nepal/regional round only after 40 paying orgs — not before a demo.
