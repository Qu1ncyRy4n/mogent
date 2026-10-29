# NOW

- **Goal:** Dogfood native source browsing and upstream-change visibility without automatic selection rewrites.
- **Current stage:** CS-W024 — Source/tag discovery is dogfooded; resolved catalog filters now cover selected and available content. Canonical module vocabulary and a compact plan-file guide now match the implementation. A disposable story walkthrough found that fresh native build lacks unmanaged-output adoption protection. The next planned presentation refinement is tree-first text search with optional flat rows and content context.
- **One active item:** CS-W024 — Resume tree/snippet search presentation, then dogfood it before a real selection write.
- **Next concrete action:** Define and implement `source search <term>` tree output, `--flat`, and content/context display. Keep `auto_inherit` as a separately logged selection-policy slice.
- **Blocked by:** none.
- **Do not:** Rebuild or alter Teacher_Bot’s committed generated outputs; run native `build` against a real pre-existing unmanaged `AGENTS.md` until adoption safety is fixed; resolve overlap automatically; implement `auto_inherit` before its membership/audit persistence is designed; touch Seam's active development; discard the inference stash; or treat historical checkpoints as current.
- **Last verified:** 2026-10-29: disposable CLI walkthroughs exercised native init/source/include/build/check/status, localization, upstream-change drift, direct-output drift, and the existing-output path. Happy-path build/check/status and localization/drift worked; direct drift was detected; the existing-output build overwrote unmanaged `AGENTS.md` (safety failure). `tools/native-stories` separately passed its supported fixture scenarios. 2026-10-23: full `go test ./...` passed for the prior vocabulary/help slice.
- **Working-tree/commit state:** `754ee0f` implements canonical `module include`/`module remove` aliases, updates help/reference output, and adds `docs/PLAN-FILES.md`; `1e2df16` refreshes native user-story coverage and adds `tools/native-stories`. The current documentation-only slice records the walkthrough evidence and adoption-safety gap; it awaits an atomic local commit. The proposed `auto_inherit` policy remains recorded but unimplemented. No push requested.

---
Everything below is history/reference. Resume only from the NOW panel above.

[Work](work.md) · [Decisions](decisions.md) · [Topic archives](archive/README.md)
