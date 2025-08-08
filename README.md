*** Begin Patch
*** Add File: /Users/fxbravo/galactoids/.cursor/README-RULES.md
+### Rules — How they guide our development (for humans)
+
+This document explains the “Rules” used by the assistant to interpret your requests and choose the right workflow. It is intentionally short, visual, and practical.
+
+### TL;DR
+- 🧭 Purpose: turn any request into the right action plan with clear guardrails.
+- 🏷️ First move: always classify the request (cleanup, feature, bugfix, exploration, migration, optimization, compliance).
+- 🧰 Then: apply the context’s guardrails (what’s allowed/forbidden, success metric).
+- ✅ Finally: implement small edits, run lint/tests/build, and summarize impact.
+
+### Decision Flow
+```mermaid
+flowchart TD
+  A[📥 User request] --> B[🔎 Keyword scan]
+  B --> C{🧩 Classify}
+  C -->|cleanup| D1[🧽 Cleanup guardrails]
+  C -->|feature| D2[✨ Feature guardrails]
+  C -->|bugfix| D3[🛠️ Bugfix guardrails]
+  C -->|exploration| D4[🧪 Exploration guardrails]
+  C -->|migration| D5[🚚 Migration guardrails]
+  C -->|optimization| D6[⚡ Optimization guardrails]
+  C -->|compliance| D7[🔒 Compliance guardrails]
+  D1 --> E[🧾 Plan minimal edits]
+  D2 --> E
+  D3 --> E
+  D4 --> E
+  D5 --> E
+  D6 --> E
+  D7 --> E
+  E --> F[🔁 Run lint / test / build]
+  F --> G[📊 Validate success metrics]
+  G --> H[🧩 Output: Summary + Action Plan]
+```
+
+### Categories (how we choose them)
+- 🧽 Cleanup: refactor, clean, debt, duplicate, simplify, merge
+- ✨ Feature: add, new, implement, create, develop, build, feature
+- 🛠️ Bugfix: fix, bug, error, broken, issue, not working, problem
+- 🧪 Exploration: test, try, experiment, prototype, PoC, evaluate, explore
+- 🚚 Migration: migrate, upgrade, update, port, move to, switch to
+- ⚡ Optimization: optimize, performance, speed, memory, faster, improve
+- 🔒 Compliance: security, GDPR, accessibility, legal, audit, compliance
+
+If ambiguous: pick dominant objective. If unclear: ask 1–3 concise questions. If conflicting: list interpretations, then confirm. Safe default: bugfix.
+
+### Guardrails per context (what changes are allowed)
+- 🧽 Cleanup
+  - Mode: strict veto
+  - Files: must decrease or stay the same
+  - Forbidden: new files, new abstractions, unrelated refactors
+  - Must: define exact problem, measure before/after, reuse good code
+  - Success: lower complexity
+
+- ✨ Feature
+  - Mode: reasonable oversight
+  - Files: increase allowed if justified
+  - Must: follow existing patterns; justify new files
+  - Prefer: extend existing modules when possible
+  - Success: working feature without debt
+
+- 🛠️ Bugfix
+  - Mode: minimal change only
+  - Files: no increase
+  - Prefer: modify existing only, smallest possible change
+  - Forbidden: refactor while fixing, formatting noise
+  - Success: bug fixed, no regressions
+
+- 🧪 Exploration
+  - Mode: temporary freedom
+  - Files: temporary increase OK
+  - Must: mark as experimental; plan cleanup after
+  - Success: approach validated or cleaned up
+
+- 🚚 Migration
+  - Mode: structured transition
+  - Files: temporary duplication allowed
+  - Must: keep compatibility; have a migration plan
+  - Phases: prepare → migrate → cleanup old
+  - Success: old fully removed
+
+- ⚡ Optimization
+  - Mode: measured improvement
+  - Files: increase only with measurable gain
+  - Must: benchmark before, measure after
+  - Forbidden: “optimize” without metrics
+  - Success: proven performance gain
+
+- 🔒 Compliance
+  - Mode: necessary additions only
+  - Files: increase allowed for compliance
+  - Must: show legal requirement; minimal implementation
+  - Success: compliance with minimal impact
+
+### Universal safeguards (always enforced)
+- 🧱 Debt prevention: no action without a clear problem; prefer modification over creation; measure complexity impact; do not change working code without strong justification.
+- 🧪 Quality gates: file ≤ 800 lines, class ≤ 300, function ≤ 50; tests pass after changes; no dead code.
+- 🔧 Ops discipline: run lint/test/build after substantive edits; avoid long-running tasks without backgrounding; don’t leak secrets in logs.
+- 🔤 Types discipline: no explicit `any` in production; warnings allowed in tests only; prefer `unknown` + type guards.
+
+### Outputs (what you’ll see in replies)
+- CategoryDetection
+  - Required: category, short justification (≤100 chars), keywords_found
+- ActionPlan
+  - Required: actions[], file_impact (decrease | same | increase_justified | increase_temporary), risk_level (low | medium | high)
+
+### Principles we follow
+- ♻️ SOLID, DRY, KISS, YAGNI, NEVER_CREATE_IF_EXISTS
+- 🧱 Stack-aware: NPM, Netlify, Supabase
+- 🧭 Minimal, reversible edits; prefer extending existing code
+
+### How to keep it small (token-friendly)
+- Short keywords instead of long sentences
+- One diagram for the whole flow
+- Tables/lists over paragraphs
+- Only the minimum outputs needed for action
+
+### FAQ
+- “Can we completely ban `any`?” → We avoid it by default. In tests/mocks it can be tolerated locally; in production interfaces it’s not allowed.
+- “What happens if I ask multiple things at once?” → The assistant chooses the dominant category and may ask 1–3 clarifying questions.
+- “Do we touch CI/infra?” → Yes, if needed to pass quality gates (lint/test/build) but under the current context’s guardrails.
+
+---
+If you want a one-pager prompt version of these Rules (for copy/paste), ask: “Give me the compact Rules prompt”.
+
*** End Patch
