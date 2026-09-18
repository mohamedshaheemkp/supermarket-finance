# AI Collaboration Handoff

Read this after `ARCHITECTURE.md` and `DECISIONS.md`, before touching any code.
This file changes often — it reflects *current* state, not history (history lives in `DECISIONS.md` and git log).

## Current phase
`DEMO` — presenting a concept to the supermarket owner, who is not yet
reachable for real requirements. The demo is not the production system.
See `DECISIONS.md` for why.

## Live demo
https://mohamedshaheemkp.github.io/supermarket-finance/

## What the demo currently models
Revenue → COGS (inventory valuation) → Gross Profit → Operating Expenses →
Net Profit, plus a separate Cash Position panel. Single HTML file, no
backend, no persistence beyond browser localStorage for convenience.

## Scope guardrails — do not assume or build
- Database / backend
- Authentication or multi-user accounts
- POS integration
- Real inventory quantity tracking
- Supplier ledger
- Payroll system
- Hosting beyond static GitHub Pages
- Multi-month data storage

These are unblocked only after the owner's requirements are gathered
(see the 18 open questions in `ARCHITECTURE.md`). Any of the above requires
a new entry in `DECISIONS.md` first, not just an implementation.

## Immediate priorities (presentation polish only)
1. "Reset to sample data" control
2. Print / PDF-friendly report view
3. Basic input validation (block negative numbers from producing nonsense totals)
4. Light branding — presenter name/business, not anonymous
5. Clear "DEMO — SAMPLE DATA" labeling on the page itself, not just in docs
6. Mobile usability pass

## Collaboration roles
- ChatGPT — architecture, product reasoning, review, technical direction
- Claude — implementation, repo work, testing
- Antigravity — integration/execution against repo state
- GitHub — single source of truth; not chat history

## Before making changes
1. Read `ARCHITECTURE.md`
2. Read `DECISIONS.md`
3. Read this file
4. Inspect the current implementation in the repo — don't assume it matches an old chat description
