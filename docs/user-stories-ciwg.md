# CIWG / PromiseGrid Consolidation User Story

## Consolidate agents and skills across CIWG and PromiseGrid repositories

**As a** CIWG/PromiseGrid maintainer, **I want** duplicated guidance and skills
across the related repositories consolidated into a versioned, composable
library, **so that** a shared rule is authored and corrected once while each
repository explicitly chooses its own composition.

This is a curation/adoption story, not a claim that current Mogent can perform
the migration automatically. It uses the native project model: a repository
owns `mogent.build`, or owns `mogent.plan` plus its generated `mogent.build`;
`source` declarations connect libraries and ordered `include` declarations
select content.

## Scope

- **CIWG:** `grid-examples`, `cswg`, `mob-sandbox`, `decomk-conf-cswg`,
  `FAB26-Presentation`, `promisegrid-dev-guide`, and their template chain.
- **PromiseGrid:** `wire-lab`, `grid-poc`, `promisegrid`, and relevant
  `stevegt/*` repositories.
- Existing captures in `docs/other_repo_agents/` are evidence for review, not
  authoritative input to overwrite back into their source repositories.

## Acceptance criteria and present status

- [ ] Produce one reviewed inventory classifying captured sections and skills as
  universal, organization-wide, project-specific, or person/machine-specific.
  The curation question is recorded in
  [library-curation/open-questions.md](library-curation/open-questions.md).
- [ ] Extract approved shared modules and physical skill bundles into a library,
  preserving source repository and revision provenance.
- [ ] For each pilot repository, author a native `mogent.plan` or
  `mogent.build`, preview it with `mogent show tree` and `mogent build --check`,
  then build only with owner approval. Compare resulting output with the
  repository’s existing guidance and record intentional differences.
- [ ] Surface divergence as reviewable differences; do not normalize or replace
  a repository’s existing policy silently.
- [ ] Add a new participating repository by connecting the approved source and
  making explicit includes, rather than copying protocol text.

## Prerequisites and boundaries

The read-only capture/import/classification features in US-4 are not implemented,
so the first inventory remains curator-led. Likewise, policy non-relaxation and
organization audit required by US-8 are future work. Do not use this story to
modify an external repository or publish a library without the relevant owner
approval.
