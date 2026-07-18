---
name: crowcode
description: >-
  CrowCode is a master index of 599 bundled sub-skills covering universal
  AI token-and-cost optimization (1my), AI-agency workflows (Apex/Atlas/
  Buzz/Cortex/Crest/Hyperflow and 40+ other families), Anthropic platform
  ops, API development, business & marketing frameworks, crypto/Web3
  analytics, database engineering, HubSpot, Linear, Sentry and PostHog
  integrations, performance/observability, security & compliance, testing,
  and UI/UX design. ALWAYS consult this skill first whenever a request
  touches any of those domains — especially anything about reducing token
  usage or AI/API costs — mentions one of the tools/products by name
  (HubSpot, Linear, Sentry, PostHog, Notion agency ops, Kobiton, etc.), or
  asks to run/build/audit/migrate/design/optimize something that could
  match a bundled specialist skill — even if the user doesn't say "skill"
  or name CrowCode explicitly. Do not try to answer such requests from
  general knowledge before checking here for a more specific, battle-
  tested workflow.
---

# CrowCode

CrowCode is a **router**, not a single workflow. It bundles 599 previously
separate skills, deduplicated and organized by domain under `skills/`. This
file never grows past a short index — the actual instructions live one hop
away in `references/` and `skills/`.

## How to use this skill

1. **Identify the domain** of the user's request from the category table
   below.
2. **Open the matching `references/<category>.md` file.** It lists every
   skill in that category with a one-line "use when" description and its
   exact path under `skills/<category>/<name>/INSTRUCTIONS.md`.
3. **Read the specific `INSTRUCTIONS.md`** that matches the task (it's a
   full sub-skill body, just renamed from `SKILL.md` so this package stays
   a single valid `.skill` file), then follow its instructions exactly as
   if it had been the top-level skill. Treat its own `scripts/`,
   `references/`, and `assets/` subfolders normally.
4. If more than one skill looks relevant (e.g. a Sentry + performance task),
   read both and combine them — don't guess, open the files.
5. If nothing in the index matches, say so plainly and fall back to general
   knowledge rather than forcing a bad fit.

`ai-agency` is large enough that it gets an extra layer: read
`references/ai-agency.md` first — it's a family index (apex, atlas, buzz,
cortex, crest, hyperflow, form, deal, ink, keep, …) pointing to
`references/ai-agency/<family>.md` for that family's actual skill list.

## Category index

| Category | Skills | Covers | Index file |
|---|---|---|---|
| 1my | 1 | Universal token/cost optimization playbook: context minimization, prompt caching, model tiering, batch processing, tool-call discipline, output-length discipline, multi-project cost audits | `references/1my.md` |
| ai-agency | 231 | Notion-based AI agency dispatch board (agency-os) + Apex/Atlas/Buzz/Cortex/Crest/Hyperflow and 40+ other workflow families: planning, recon, review, docs, marketing/devrel, strategy, sales, QA, monitoring | `references/ai-agency.md` (→ per-family files) |
| anthropic-pack | 30 | Building on the Anthropic API: hello-world, cost tuning, prod checklists, incident runbooks, migrations, reliability patterns, observability | `references/anthropic-pack.md` |
| api-development | 26 | REST/GraphQL API design, validation, mocking, versioning, migration, SDK generation, event emission | `references/api-development.md` |
| business-tools | 28 | CRO methodology, StoryBrand messaging, brand strategy, EOS/Traction, influence psychology, OpenBB terminal, one-page marketing plan | `references/business-tools.md` |
| crypto | 26 | On-chain analytics, portfolio tracking, trading signal generation, liquidity pool analysis | `references/crypto.md` |
| database | 26 | Migrations, schema design, indexing, sharding, replication, backups, audit logging, ORM/seed/stored-procedure generation | `references/database.md` |
| hubspot-pack | 10 | HubSpot auth, bulk migration, deal pipeline automation, multi-portal setups, warehouse sync, webhooks, dedup | `references/hubspot-pack.md` |
| linear-pack | 24 | Linear install/auth, webhooks, CI integration, RBAC, rate limits, SDK patterns, incident runbooks | `references/linear-pack.md` |
| packages | 3 | Conventional-commit generation, LLM prompt optimization, and security audits (from devops-automation, AI/ML-engineering, and security-pro packs) | `references/packages.md` |
| performance | 24 | SLA/SLI tracking, real-user monitoring, response-time tracking, log analysis, performance budgets | `references/performance.md` |
| posthog-pack | 24 | PostHog core workflows, incident runbooks, performance tuning, RBAC, cost tuning, webhooks | `references/posthog-pack.md` |
| rtk-develop | 12 | Code simplification, TDD (incl. Rust), shipping, security guardian, PR/issue triage, design patterns | `references/rtk-develop.md` |
| security | 52 | Compliance reporting, CORS validation, input validation scanning, access-control auditing, agent safety preflight | `references/security.md` |
| sentry-pack | 30 | Sentry install/auth, migrations, rate limits, policy guardrails, performance tuning, RBAC, incident runbooks | `references/sentry-pack.md` |
| skill-enhancers | 9 | Cross-cutting helpers: file-to-code, zero-tech-debt, calendar-to-workflow, web-to-github-issue, search-to-slack, skill/agent creator | `references/skill-enhancers.md` |
| testing | 32 | Load balancer, browser compatibility, coverage analysis, accessibility scanning, mutation testing, interactive device sessions | `references/testing.md` |
| token-optimizer-main | 4 | token-coach, fleet-auditor, token-optimizer, token-dashboard for LLM token/cost reduction | `references/token-optimizer-main.md` |
| ui-ux-pro-max-skill-main | 7 | Banner design, design systems, branding, general design, slide decks, UI styling | `references/ui-ux-pro-max-skill-main.md` |

## Notes on provenance

These skills were merged from 18 separately-sourced packs. Some pack
families (anthropic-pack, linear-pack, sentry-pack, posthog-pack) share a
near-identical internal template (hello-world, cost-tuning, prod-checklist,
incident-runbook, etc.) generated per-product — that's expected, not a
duplication bug. Exact-duplicate files that existed only because a project
mirrored its own skills into multiple internal folders (`.claude/skills`,
`plugins/*/skills`, `cli/assets/skills`) were already deduplicated during
packaging; only one canonical copy of each skill is included here.
