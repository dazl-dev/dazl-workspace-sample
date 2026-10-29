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

PR Review, CI Fix Loop and Test Writer never commit, push or comment on a pull request; the run's
changes stay on its branch. Review and Fix is copied from the outer dazl-in-dazl workspace: its fixer
and PR babysitter commit and push to the PR branch, its agents run on the Codex harness, and
`agents/shared/workspace-context.md` still describes that workspace's `dazl/` and `api-server/` repos.
