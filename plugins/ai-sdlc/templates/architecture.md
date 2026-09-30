# Architecture Context (multi-repo)

This file is the project's component-repository registry. The SDLC loop reads it to
decide which repositories a change touches and where to stage code.

## Repositories

List every component repository a change may touch. `/ai-sdlc:ai-sdlc-init` clones each
entry whose `remote:` is a real URL into its `local:` path under `.repo/`, skipping any
that already exist. The entry below is a USAGE EXAMPLE with a sentinel host
(`example.com`); it is never cloned. Replace it with your real repositories, or delete it
and add your own.

- name: example-service
  remote: git@example.com:ai-native-sdlc/example-service.git
  local: .repo/example-service
  role: example entry — replace with a real service
  depends_on: []

## Conventions

- Code for a change is staged under `.repo/<name>/` (cloned by `ai-sdlc-init`, or manually).
- Cross-repo impact is recorded in each change's `spec.md` under `## Repo impact`.
- This file is committed; `.repo/` is git-ignored in the control repo.
