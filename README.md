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

No workflow commits, pushes or comments on a pull request; the run's changes stay on its branch.
