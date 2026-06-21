# Demo Engineering Guide — Changelog

The record of changes to the guide. Each entry is appended when a suggestion is
applied (by the in-page "Suggest a change" feature or by hand), newest first.

Entry format:

```
## <UTC timestamp> — <Section N: Title>
- Source file: sections/<n>-<slug>.html
- Change type: <reword | fix | add | remove | diagram | other>
- Original: "<short quote of the original>"
- Suggestion: "<what the reader asked for>"
- Applied: <one line on what changed>
- Status: applied
```

---

## 2026-06-21T20:53:04Z — All sections (1–23): baseline content authored
- Source files: sections/1-about.html … sections/23-key-links.html (all 23 fragments)
- Change type: add
- Original: "TODO: <title>." placeholder lead in every section
- Suggestion: Write source-grounded baseline content for the whole guide.
- Applied: Authored all 23 sections from the sources of truth via a four-phase
  workflow (research → generate → synthesize → audit) with one subagent per
  section. Every factual claim is grounded in the platform/web/infra repos, the
  Engineering Wiki (articles 1001–1009), or the Help Center; claims that could
  not be verified were omitted or flagged in-page. House style enforced:
  `pal validate` is clean (0 errors, 0 warnings) and `pal build` succeeds.
- Status: applied

## 2026-06-21T20:53:04Z — Source-conflict handling (Sections 2, 3, 5, 6, 16, 22, 23)
- Source files: sections/2-architecture.html, 3-onboarding.html, 22-glossary.html, 23-key-links.html (and cross-refs)
- Change type: fix
- Original: n/a (baseline authoring decision)
- Suggestion: Reconcile contradictions between sources without contradicting the canonical one.
- Applied: ADR numbering follows the wiki (canonical for ADRs) — ADR-001 = "API
  gateway as the single entrypoint", ADR-002 = "Schema-per-service in a shared
  Postgres"; the guide notes that `platform/docs/architecture.md` swaps these.
  "ADR-003" (trunk-based development) is referenced by wiki 1004 but its text is
  not in the sources, so it is described as a practice and flagged as unknown.
  The Help Center's "overdue" wording is documented as phrasing, not an invoice
  status value (the enum is draft|open|paid|void).
- Status: applied

## 2026-06-21T20:53:04Z — Section 21: secrets table reconciled with Section 18
- Source file: sections/21-security.html
- Change type: fix
- Original: "DATABASE_URL … platform-db/url … billing" (attributed to billing only)
- Suggestion: Match the per-pod secret attribution to the Kubernetes manifests.
- Applied: `DATABASE_URL` (from `platform-db/url`) is consumed by both the
  accounts and billing pods (per infra/kubernetes/accounts.yaml and billing.yaml);
  updated the table and the secret-injection diagram to show both, agreeing with
  Section 18.
- Status: applied

## 2026-06-21 — Baseline
- The initial version of Demo Engineering Guide, scaffolded with palimpsest.
- Status: baseline
