# CrowCode

**A single Claude Skill that routes to 599 bundled sub-skills** — AI-agency
workflows, product integrations (HubSpot, Linear, Sentry, PostHog,
Anthropic), API/database/security/testing/performance engineering,
business & marketing frameworks, crypto analytics, UI/UX design, and a
universal token-and-cost optimization playbook (`1my`).

Instead of loading one narrow capability, CrowCode ships as a **router**:
a short top-level `SKILL.md` that reads the request, picks the right
domain, and points the model at the exact sub-skill file to open —
keeping token overhead low while still giving access to hundreds of
battle-tested playbooks.

## Why a router instead of one big skill

A single `SKILL.md` is meant to describe one coherent capability and stay
under ~500 lines, because the model decides whether to open it based on
that one description. Flattening 599 unrelated skills into one file would
make triggering unreliable and blow past any reasonable size budget.
CrowCode instead keeps:

- **`SKILL.md`** — a short index (< 100 lines): what this bundle covers,
  how to navigate it, and a table of all 19 categories.
- **`references/<category>.md`** — one file per category, listing every
  skill in it with a one-line "use when" and its exact path.
- **`skills/<category>/<name>/INSTRUCTIONS.md`** — the actual sub-skill
  body (renamed from `SKILL.md` so the package still validates as a
  single-`SKILL.md` skill), plus its own `scripts/`, `references/`, and
  `assets/` untouched.

The `ai-agency` category (231 skills) gets one more layer —
`references/ai-agency.md` is a family index (apex, atlas, buzz, cortex,
crest, hyperflow, form, deal, ink, keep, …) pointing to
`references/ai-agency/<family>.md` for that family's skill list — so no
single reference file ever gets unwieldy.

## Categories

| Category | Skills | Covers |
|---|---|---|
| **1my** | 1 | Universal token/cost optimization: context minimization, prompt caching, model tiering, batch processing, tool-call discipline, multi-project cost audits |
| ai-agency | 231 | Notion-based AI agency dispatch board + Apex/Atlas/Buzz/Cortex/Crest/Hyperflow and 40+ workflow families: planning, recon, review, docs, marketing/devrel, strategy, sales, QA, monitoring |
| anthropic-pack | 30 | Building on the Anthropic API: hello-world, cost tuning, prod checklists, incident runbooks, migrations, reliability patterns |
| api-development | 26 | REST/GraphQL API design, validation, mocking, versioning, migration, SDK generation, event emission |
| business-tools | 28 | CRO methodology, StoryBrand messaging, brand strategy, EOS/Traction, influence psychology, marketing planning |
| crypto | 26 | On-chain analytics, portfolio tracking, trading signal generation, liquidity pool analysis |
| database | 26 | Migrations, schema design, indexing, sharding, replication, backups, audit logging, ORM/seed generation |
| hubspot-pack | 10 | HubSpot auth, bulk migration, deal pipeline automation, multi-portal setups, warehouse sync, webhooks |
| linear-pack | 24 | Linear install/auth, webhooks, CI integration, RBAC, rate limits, SDK patterns, incident runbooks |
| packages | 3 | Conventional-commit generation, LLM prompt optimization, security audits |
| performance | 24 | SLA/SLI tracking, real-user monitoring, response-time tracking, log analysis, performance budgets |
| posthog-pack | 24 | PostHog core workflows, incident runbooks, performance tuning, RBAC, cost tuning, webhooks |
| rtk-develop | 12 | Code simplification, TDD (incl. Rust), shipping, security guardian, PR/issue triage, design patterns |
| security | 52 | Compliance reporting, CORS validation, input validation scanning, access-control auditing, agent safety preflight |
| sentry-pack | 30 | Sentry install/auth, migrations, rate limits, policy guardrails, performance tuning, RBAC, incident runbooks |
| skill-enhancers | 9 | file-to-code, zero-tech-debt, calendar-to-workflow, web-to-github-issue, search-to-slack, skill/agent creator |
| testing | 32 | Load balancer, browser compatibility, coverage analysis, accessibility scanning, mutation testing |
| token-optimizer-main | 4 | token-coach, fleet-auditor, token-optimizer, token-dashboard |
| ui-ux-pro-max-skill-main | 7 | Banner design, design systems, branding, general design, slide decks, UI styling |

**Total: 599 skills across 19 categories, ~38 MB unpacked.**

## Installation

**claude.ai / Claude API (Skills feature):**
Download [`CrowCode.skill`](./CrowCode.skill) and upload it via the Skills
settings panel, or through the Skills API. It's a single valid skill
package (one `SKILL.md` at the root, no nested `SKILL.md` files — every
sub-skill body is named `INSTRUCTIONS.md` instead so the package still
passes upload validation).

**Claude Code:**
Clone this repo (or copy the `CrowCode/` source folder) into
`.claude/skills/CrowCode/` in your project. Claude Code loads nested
skills directly from the filesystem, so the full `skills/` tree is usable
as-is.

```bash
git clone https://github.com/<your-username>/CrowSkill.git
cp -r CrowSkill/CrowCode ~/.claude/skills/CrowCode
```

## Repository layout

```
CrowCode.skill        # packaged, ready-to-upload skill (zip)
CrowCode/              # unpacked source — same content, browsable
├── SKILL.md            # router — start here
├── references/         # one index file per category
│   ├── 1my.md
│   ├── ai-agency.md     # + ai-agency/<family>.md for the 231-skill category
│   ├── anthropic-pack.md
│   └── ...
└── skills/              # the actual skills, one folder per <category>/<name>
    ├── 1my/
    ├── ai-agency/
    └── ...
```

## Provenance

These skills were merged from several separately-sourced packs and
deduplicated by content hash and name — exact copies that existed only
because a project mirrored its own skills into multiple internal folders
(`.claude/skills`, `plugins/*/skills`, `cli/assets/skills`) were collapsed
to one canonical copy. Some product-integration families
(`anthropic-pack`, `linear-pack`, `sentry-pack`, `posthog-pack`) share a
near-identical internal template (hello-world, cost-tuning,
prod-checklist, incident-runbook, etc.) generated per product — that's
expected, not a duplication bug.

## License

See [`LICENSE`](./LICENSE). Individual bundled skills retain the
licensing terms of their original source where specified in their own
files.
