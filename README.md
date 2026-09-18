# Bahi

**Working name.** *Bahi* (बही) is the bound account book. The product is a Nepal-first **order-to-VAT system of record**: every sale — website, counter, or chat — becomes stock movement, a matched payment, and an IRD-correct invoice.

This repository is the founding document set, not production code. Read `docs/00-index.md` first.

## One-sentence thesis

Do not build another storefront or another chatbot. Own the ledger that tells the truth about stock, money, and tax — then expose that ledger through API and MCP so storefronts, CAs, and agents plug in.

## What this is not

- Not Shopify for Nepal
- Not Tally with a nicer theme
- Not Meta Business Agent
- Not an MCP wrapper around someone else's books

## Docs map

| Doc | Purpose |
|---|---|
| [docs/00-index.md](docs/00-index.md) | How to read this repo |
| [docs/01-original-scenario.md](docs/01-original-scenario.md) | Full originating conversation and constraints |
| [docs/02-problem-and-thesis.md](docs/02-problem-and-thesis.md) | Problem, wedge, why now |
| [docs/03-market-americas.md](docs/03-market-americas.md) | Reference stack that started the analysis |
| [docs/04-market-nepal.md](docs/04-market-nepal.md) | Nepal layer map and maturity |
| [docs/05-front-door-competitors.md](docs/05-front-door-competitors.md) | Blanxer, Zalient, and clone pack |
| [docs/06-icp-and-positioning.md](docs/06-icp-and-positioning.md) | Who we sell to first |
| [docs/07-product-principles.md](docs/07-product-principles.md) | Design and company rules |
| [docs/08-product-scope.md](docs/08-product-scope.md) | Modules, objects, workflows |
| [docs/09-non-goals.md](docs/09-non-goals.md) | Explicit refusals |
| [docs/10-architecture.md](docs/10-architecture.md) | System shape |
| [docs/11-api-and-mcp.md](docs/11-api-and-mcp.md) | Public API and MCP server |
| [docs/12-storefront-and-chat.md](docs/12-storefront-and-chat.md) | How front doors attach |
| [docs/13-compliance-ird.md](docs/13-compliance-ird.md) | VAT, CBMS, BS calendar, payroll edges |
| [docs/14-business-model.md](docs/14-business-model.md) | Pricing and revenue mix |
| [docs/15-unit-economics.md](docs/15-unit-economics.md) | Burn, ARPU, break-even |
| [docs/16-roadmap.md](docs/16-roadmap.md) | Phased roadmap to month 36 |
| [docs/17-go-to-market.md](docs/17-go-to-market.md) | CA channel, seller groups, implementation |
| [docs/18-risks.md](docs/18-risks.md) | Kill criteria and failure modes |
| [docs/19-open-questions.md](docs/19-open-questions.md) | Unresolved decisions |
| [docs/20-glossary.md](docs/20-glossary.md) | Terms |
| [docs/research/sources.md](docs/research/sources.md) | Research notes and citations |
| [docs/decisions/](docs/decisions/) | Architecture / product ADRs |

## Status

- Date frozen in these docs: **18 September 2026**
- Code: none yet
- GitHub: https://github.com/dipendrakshah/gt-bahi
- Correction after IRD discussion: see `docs/decisions/0006-cbms-is-an-adapter.md`

## License

Proprietary until decided. See `LICENSE`.
