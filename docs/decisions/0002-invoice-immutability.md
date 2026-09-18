# ADR 0002 — Issued invoices are immutable

- Status: accepted
- Date: 2026-09-18

## Context

IRD computerized billing practice forbids silent edits. CAs will not adopt a system that updates issued rows.

## Decision

Fiscal fields on issued invoices cannot be UPDATEd. Corrections are credit/debit notes. Reprints are labeled copies. API and MCP obey the same rule.

## Consequences

More UI work on notes. Fewer catastrophic audit conversations.
