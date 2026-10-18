# dazl-workspace-sample

Workspace repository for the Sample workspace that the dazl-in-dazl installer seeds in a local
(inner) Dazl. Every new session in that workspace clones this repo as its session root, and
[dazl-pr-panel-sandbox](https://github.com/dazl-dev/dazl-pr-panel-sandbox) into
`dazl-pr-panel-sandbox/`. `dazl.config.json` declares that folder as the one app, `solar-system`.
