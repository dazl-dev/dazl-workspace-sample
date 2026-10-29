# dazl-workspace-sample

Workspace repository for the Sample workspace that the dazl-in-dazl installer seeds in a local
(inner) Dazl. Every new session in that workspace clones this repo as its session root, and
[dazl-pr-panel-sandbox](https://github.com/dazl-dev/dazl-pr-panel-sandbox) into
`dazl-pr-panel-sandbox/`. `dazl.config.json` declares that folder as the one app, `solar-system`.

## Workflows

Dazl discovers the workflows in `workflows/` and the agents their steps run in `agents/`. Start one
from the workflow picker in the chat box. All of them target `dazl-pr-panel-sandbox/`, whose checks
are `npm test` and `npm run build` (it has no lint or typecheck script).

| Workflow    | Input                    | What it does                                                                               |
| ----------- | ------------------------ | ------------------------------------------------------------------------------------------ |
| PR Review   | PR number or URL         | Reviews correctness, tests and style, runs the checks, summarizes findings. Read-only.     |
| CI Fix Loop | PR or checked-out branch | Fixes failing checks; a verifier re-runs them and loops up to 5 rounds, then the run pauses. |
| Test Writer | Optional file or feature | Adds `node:test` tests for untested paths; a reviewer loops up to 3 rounds.                |
| Review and Fix | PR, branch or diff     | Six parallel reviewers (correctness, security, architecture, tests, UX, performance), a fixer for their findings, then a PR babysitter. |
| Bug Fix     | Bug report               | Clarifies the bug, investigates, reproduces it, runs Implement Code Fix, validates, waits for a human review, then a PR babysitter. |
| Implement Code Fix | Bug folder (from Bug Fix) | Fixes the root cause with a regression test, then runs Review and Fix on it.          |
| New Feature | Feature request          | Spec with review; for UI, screens, before snapshots and mockups with approval; then implementation, code review, evidence, final approval and a PR babysitter. |
| UX Fix      | UX problem               | Spec, before snapshots, mockups with design approval, implementation, code review, after evidence per viewport, final approval, then a PR babysitter. |
| PR Prism    | PR or diff               | Read-only multi-lens review (architecture, code risk, conventions, style) into a report under `docs/reviews/pr-prism/`. |
| Architecture Atlas | Prompt            | Read-only whole-system architecture review with diagrams, as a report.                    |
| System Blueprint | Prompt              | Read-only structural system map, as a report.                                             |
| Journey Lens | Prompt                  | Read-only review of selected user flows and the code decisions behind them, as a report.  |

PR Review, CI Fix Loop, Test Writer, PR Prism, Architecture Atlas, System Blueprint and Journey Lens
never commit, push or comment on a pull request. Review and Fix, Bug Fix, New Feature and UX Fix do
publish through the PR babysitter. Review and Fix pushes its fixes to the pull request branch (or
opens a draft PR against `main` when only a branch was reviewed). The other three squash the run
branch onto `main` as `fix/<slug>` or `feat/<slug>` and open a draft PR against `main`; New Feature
also opens one in this repo for its spec folder. The babysitter then fixes failing checks and review
threads until the PR is green. It never merges or force-pushes. Every agent runs on the `dazl`
harness, and they share `agents/shared/workspace-context.md`, which describes this workspace and
`dazl-pr-panel-sandbox/`.
