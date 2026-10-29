# TODO-kozuj — Native Adoption Safety And Invalid-Selection Recovery

Status: ready

This TODO records two failures observed in a disposable native CLI walkthrough
on 2026-10-29. They block real existing-repository adoption; neither was run
against Teacher_Bot, Seam, or another user repository.

## Evidence

1. In a fresh directory containing an unmanaged `AGENTS.md`, the walkthrough
   ran `mogent init --plan`, added a local source and one leaf include, then
   ran `mogent build`. The command succeeded and replaced the pre-existing
   `AGENTS.md` without a refusal, adoption command, or confirmation.
2. `mogent module include demo:guidance` accepted a directory reference whose
   child had the actual destination. `show issues` then reported `UNDEFINED:
   guidance has no destination`. `mogent module remove demo:guidance` failed
   before editing because its managed-output preview composed the unresolved
   selection first.

Related records:

- [User story US-4](../docs/user-stories.md#us-4--incremental-adoption-in-an-existing-codebase)
- [Dogfood warning](../docs/DOGFOOD.md)
- [Current conversation checkpoint](../docs/convo/head.md)

## Work

- [ ] **kozuj.1 — Refuse or explicitly adopt unmanaged output before writing.**
  Define and implement the native build behavior when a prospective managed path
  already exists but has no Mogent ownership state. It must preserve the existing
  bytes by default and give an actionable, explicit adoption/replacement path.
  Cover root-file and skill-tree ownership; distinguish an already-managed path
  with ordinary drift from an unmanaged path. Do not infer that a matching file
  is safe to take over merely because its bytes happen to match expected output.

- [ ] **kozuj.2 — Permit syntax-level removal of an invalid direct include.**
  `module remove <exact-ref>` must be able to remove that declaration even if
  the current selection cannot compose. A normal removal can report that output
  diff is unavailable while the input remains invalid; `--dry-run` must show the
  corrected project declaration without writing. Preserve the current exact-direct
  semantics and do not use this recovery path to remove an ancestor or guess
  among duplicate declarations.

## Acceptance

- A disposable project with a pre-existing unmanaged `AGENTS.md` or unmanaged
  `.agents/skills` member is not modified by bare `mogent build`; its output
  identifies the path and the explicit next action.
- The chosen explicit adoption/replacement action is previewable and has focused
  CLI tests proving that only the intended managed paths change.
- A plan containing a direct include that produces a resolver error can run
  `module remove` for that exact include and become valid when no other error
  remains.
- Focused CLI tests cover the original two walkthrough commands, and a fresh
  disposable walkthrough demonstrates repair before another real-repository
  adoption attempt.
