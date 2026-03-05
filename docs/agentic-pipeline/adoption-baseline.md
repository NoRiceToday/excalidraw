# Stage 1 adoption baseline (documentation-first)

Canonical source followed: `ai-agents-pipeline/docs/agents/adopting-in-another-repo.md`

## Step outcomes

| Doc step | Executed action | Outcome |
|---|---|---|
| Copy `ai-implement.yml`, `ai-review.yml`, `ai-rework.yml` | Copied all 3 files into `excalidraw/.github/workflows/` | Pass |
| Copy `.opencode/agents/` | Copied `implementer.md`, `reviewer.md`, `reworker.md` into `excalidraw/.opencode/agents/` | Pass |
| Add secrets (`SKAINET_TOKEN`, `PERSONAL_ACCESS_TOKEN`) | Not part of Stage 1 local scope | Deferred |
| Configure GitHub Actions settings | Not part of Stage 1 local scope | Deferred |
| Copy `mise.toml` and `lefthook.yml` | Copied both files into Excalidraw root | Pass |
| Run `mise install` | Tools installed and validated with `actionlint` | Pass |
| Hook wiring for existing Husky repo | Kept Husky as owner and invoked Lefthook via `.husky/pre-commit` | Pass |

## Post-setup deviation applied for runtime compatibility

- Deviation: Added explicit `GITHUB_TOKEN` and `GH_TOKEN` (from `PERSONAL_ACCESS_TOKEN`) to `opencode github run` steps in:
  - `.github/workflows/ai-implement.yml`
  - `.github/workflows/ai-review.yml`
  - `.github/workflows/ai-rework.yml`
- Reason: First live smoke test run failed in implement stage with:
  - `undefined is not an object (evaluating 'octoRest.rest')`
- Validation plan:
  - Re-run `/oc implement` issue trigger after merging this workflow fix.
  - Confirm implement run can progress beyond OpenCode invocation and create a PR.
