# Mogent User Stories

These stories describe the product jobs, not a promise that every acceptance
criterion is implemented. The supported project model is an authored
`mogent.build` or an intent-first `mogent.plan` sequenced into `mogent.build`.
Sources make libraries available; ordered `include` declarations select content.

`tools/native-stories` runs the current executable evidence for the supported
parts of US-1, US-2, US-4, and US-6 in isolated Go test fixtures. It is not a
substitute for real-repository dogfooding, and it does not claim unimplemented
criteria have passed.

## Core stories

### US-1 — Shared core for personal and professional use

**As** someone setting up agent guidance for personal and professional projects,
**I want** a small shared starting selection with understandable local deltas,
**so that** I can produce a useful `AGENTS.md` without first learning every
composition feature.

Current support:

- `mogent init` creates a minimal authored `mogent.build`; `mogent init --plan`
  creates intent-first `mogent.plan`.
- `mogent source add`, `source tree`, and `module include` make a selected
  source and module visible before `mogent build` writes outputs.
- `mogent sequence --file mogent.plan` produces the inspectable generated build
  without installing workspace outputs.

Acceptance status:

- [x] A minimal native project can select a source and build instructions and
  skill bundles (`tools/native-stories`: US-1).
- [ ] A reviewed personal/professional starter pair and its deltas are not yet
  specified or dogfooded.
- [ ] “Explains every field” needs a user-facing first-run evaluation, not only
  command help and [PLAN-FILES.md](PLAN-FILES.md).

### US-2 — Borrow, localize, and review upstream change

**As** a developer working across projects, **I want** to borrow reusable
practice, make a project-local copy when needed, and review later upstream
change, **so that** useful improvements do not require unmanaged copy/paste.

Current support:

- `module localize <source:path>` copies a selected physical input into
  `.mogent/local` and appends a replacing local include; `--dry-run` previews
  the operation.
- `drift` compares the current connected library with saved per-library and
  per-node build fingerprints, reporting changed, added, and removed modules.
- Localized inputs are not silently recopied from upstream.

Acceptance status:

- [x] Localization and upstream-change reporting have executable coverage
  (`tools/native-stories`: US-2).
- [ ] A guided reconciliation of a localized module with an upstream revision,
  including conflict presentation and acceptance, is not implemented.
- [ ] The one-command/friction-budget claim remains a real-project dogfood
  question; it is not established by fixture tests.

### US-3 — Multi-agent prompting and role overlays

**As** a manager coordinating guidance for multiple roles, **I want** shared
policy plus role-specific overlays, **so that** agents can share constraints
without receiving identical instructions.

Current support: ordered includes can compose multiple sources and destinations.

Not implemented: role-overlay modeling, a rule that an overlay may tighten but
not relax required policy, and defined cross-source precedence. Runtime
multi-agent coordination is out of scope.

### US-4 — Incremental adoption in an existing codebase

**As** a developer introducing Mogent into a repository with existing guidance
and skills, **I want** to inspect and adopt it incrementally, **so that** a
single source of truth can emerge without an unsafe rewrite.

Current support:

- `status`, `drift`, `show tree`, and `build --check` inspect managed output
  state without rewriting it.
- Builds protect managed outputs against direct drift; generated builds resist
  hand edits.

Acceptance status:

- [x] Generated-build and output-drift protection have executable coverage
  (`tools/native-stories`: US-4/US-6).
- [ ] Read-only capture/inventory of root, nested, role-specific guidance,
  `CLAUDE.md`, and existing skill trees is not implemented.
- [ ] Rule classification, duplicate/conflict detection, provenance-preserving
  import, and incremental adoption are not implemented.

## Review later

### US-5 — Library curator

**As** a library maintainer, **I want** to review proposals, publish revisions,
and deprecate modules with provenance, **so that** shared content remains
coherent as repositories contribute.

Not scheduled. Source browsing and deterministic source fingerprints are useful
prerequisites; proposal/review/publish/deprecation workflows are not implemented.
The CIWG/PromiseGrid application is tracked separately in
[user-stories-ciwg.md](user-stories-ciwg.md).

### US-6 — CI drift gate

**As** a CI maintainer, **I want** a checked-in output to fail verification when
it no longer reproduces from its project definition, **so that** hand edits and
unreviewed source changes are caught in review.

Current support: `mogent build --check` verifies all managed output bytes,
modes, and directory layout without writing. `mogent drift --all --diff` gives a
human-readable companion report.

Acceptance status:

- [x] The check behavior is covered by `tools/native-stories`: US-6.
- [ ] A documented CI-provider example and a real CI run remain to be dogfooded.

### US-7 — Retrieval and token cost

**As** an agent operating in a repository, **I want** to find relevant modules
or skills without loading every library payload, **so that** context remains
small and relevant.

Current support: `source tree`, `source search`, tag predicates, and
`source content` provide developer-directed discovery. Runtime retrieval,
context-budget measurement, and automatic on-demand loading are not implemented.

### US-8 — Authority auditor

**As** an organization reviewer, **I want** to determine which policy revision a
project used and whether required policy was relaxed, **so that** policy can be
audited rather than merely copied.

Current support: generated builds record resolved inputs, and output state stores
upstream fingerprints. Required-policy declarations, non-relaxation analysis,
and organization-level audit reports are not implemented.
