# ADR 0003 — MCP is not a backdoor

- Status: accepted
- Date: 2026-09-18

## Context

MCP is fashionable in 2026. Risk: agents issue invoices or move money with a looser policy than the UI.

## Decision

MCP tools map 1:1 to API permissions. `issue_invoice` defaults deny for agents. Every tool call is audited.

## Consequences

Demos are less magical. We will not get a viral “Claude filed my VAT” clip. Good.
