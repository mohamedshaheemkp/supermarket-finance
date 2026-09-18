# Decision Log

ADR-style. Newest at top. Never edit a closed entry — supersede it with a new one and link back.

---

## 2026-09-18 — Defer tech stack selection
**Status:** Accepted
**Context:** No confirmed requirements yet (POS integration, data volume, multi-user needs, hosting constraints all unknown).
**Decision:** No DB/backend/hosting choice until the 18 requirements questions are answered. Choosing now risks over- or under-building.
**Consequence:** The demo stays a static, single-file, no-backend artifact until requirements land.

---

## 2026-09-18 — Build a demo before gathering requirements
**Status:** Accepted
**Context:** Owner is not currently reachable, blocking the normal requirements-first flow.
**Decision:** Build a minimal interactive demo on assumed/sample figures, to be used as a conversation prop to extract real requirements from the owner — not as a basis to keep building on.
**Consequence:** Demo scope is intentionally shallow (no persistence, no multi-month data, no real inventory qty tracking). Do not extend it feature-by-feature; replace it once real requirements exist.

---

## 2026-09-18 — Split workflow: ChatGPT (architecture/review) / Claude (implementation/testing) / Antigravity (integration)
**Status:** Accepted
**Context:** Multi-assistant workflow already in use; needed a durable record instead of chat-only context.
**Decision:** GitHub repo is the single source of truth. `ARCHITECTURE.md` and this file are the shared context both assistants read before acting, rather than relying on conversation history.
**Consequence:** Any assistant (or the Antigravity agent) picking up this repo cold should read these two files first.

---

## Template for new entries
```
## YYYY-MM-DD — <short title>
**Status:** Proposed | Accepted | Superseded by <link>
**Context:** why this decision was needed
**Decision:** what was decided
**Consequence:** what this changes going forward
```
