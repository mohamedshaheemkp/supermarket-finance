# CLAUDE.md

Instructions for Claude (or Claude Code) working in this repository.

## Read order, every session
1. `ARCHITECTURE.md` — what the system is and why
2. `DECISIONS.md` — accepted decisions; never re-litigate a closed one, supersede it
3. `HANDOFF.md` — current phase and immediate priorities
4. The actual files in the repo — don't trust a prior chat's description of them over what's committed

## Working rules for this repo
- Scope is currently limited to presentation polish on the demo (see `HANDOFF.md`
  → Immediate priorities). Do not add backend, database, auth, or persistence
  without a new `DECISIONS.md` entry authorizing it first.
- The demo (`docs/index.html`) must stay a single self-contained HTML file
  unless a decision explicitly changes that.
- Update `DECISIONS.md` when a real architectural or scope decision is made —
  not for routine implementation choices.
- Don't hand-maintain a separate changelog file; git commit messages are the
  changelog. Write them like it.
- If a request from the user or another AI's handoff note would violate the
  scope guardrails in `HANDOFF.md`, flag it rather than silently implementing it.
