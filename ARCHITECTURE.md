# Supermarket Finance System — Architecture

## Status
`DEMO` — built on assumed figures, no confirmed requirements from the owner yet.
This doc is the source of truth once real requirements land; update it, don't fork it.

## Workflow
```
ChatGPT ──────────────► Claude ──────────────► GitHub repo
architecture/review     implementation/testing   source of truth
        ▲                                              │
        └────────────── Antigravity agent ◄────────────┘
                    (syncs repo state, runs tasks)
```
- ChatGPT owns architecture calls and review; Claude owns implementation and tests.
- Antigravity's agent is the integration point between the repo and both assistants — it should read this file and `DECISIONS.md` before acting on either assistant's output.
- Nothing here is final until it's merged. Chat history is not a source of truth; this repo is.

## Problem statement
Answer, for any closed period:
> How much money came in, where did it go, what do we owe, what are we owed,
> what is inventory worth, and what did we actually profit?

## Core principle
**Money movement ≠ profit.** Purchases, sales, and inventory must be tracked
separately and reconciled at close — not netted directly into a single cash total.

## Modules
| # | Module | Owns |
|---|--------|------|
| 1 | Sales / Revenue | Daily sales by channel (cash/card/other) |
| 2 | Purchases / Suppliers | Invoices, payment status, payables |
| 3 | Employees / Payroll | Salary components, monthly payroll run |
| 4 | Operating Expenses | Categorized recurring costs |
| 5 | Inventory | Opening/closing stock value (qty tracking: TBD) |
| 6 | Cash & Accounts | Cash drawer, bank accounts, receivables/payables |
| 7 | Month-End Close | Aggregates 1–6 into the financial report below |

## Financial model
```
COGS          = Opening Inventory + Purchases − Closing Inventory
Gross Profit  = Total Revenue − COGS
Net Profit    = Gross Profit − Total Operating Expenses

Net Cash Pos. = Cash + Bank + Card Settlements Pending
                + Receivables − Payables
```
Net Profit and Net Cash Position are reported separately — never collapse
one into the other in the UI or the data model.

## Current implementation
- Single-file interactive demo (`supermarket-close-demo.html`): editable sample
  figures, live-calculated Revenue → COGS → Gross Profit → Opex → Net Profit,
  plus a separate Cash Position panel. In-browser state only, no persistence
  layer, no historical months. Not the production data model.

## Open / deferred decisions
See `DECISIONS.md`. Not yet decided: database, backend framework, hosting,
multi-month storage, auth/roles, inventory qty-tracking depth, currency/locale,
Arabic-language support.

## Blocked on
The 18 requirements questions (POS integration, supplier credit terms,
payroll structure, expense categories, inventory depth, accounts/cash
handling, user roles, language) — owner not yet reachable. Demo exists to
get in front of the owner and extract these answers, not to be extended
further without them.
