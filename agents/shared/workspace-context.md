## This workspace

You work in the Sample workspace. The session root is the `dazl-workspace-sample` repository (remote dazl-dev/dazl-workspace-sample, default branch `main`). It holds the workflows, the agents and their shared rules. It has one code repository:

- `dazl-pr-panel-sandbox/`: its own git repository (remote dazl-dev/dazl-pr-panel-sandbox, default branch `main`, so the base is `origin/main`). A throwaway repo for exercising the Dazl Git panel and pull request tabs: each open pull request covers one state (failing checks, draft, merge conflict, inline review comments). It is a Vite + React Router app in plain JavaScript (`.js`/`.jsx`, no TypeScript), managed with npm (`package-lock.json`). Read its `README.md` before you judge or change code there.
  - `app/`: the solar system app (`/`, `/planets`, `/planets/:planetId`), with plain CSS in `app/styles.css`.
  - `src/`: the cart module (`cart.js`) that the pull requests change, tested in `src/cart.test.js`.

Its checks are exactly `npm test` (`node --test`; tests are `*.test.js` files next to the code, written with `node:test` and `node:assert/strict`) and `npm run build` (`vite build`). There is no type check, lint or formatter script and no GitHub Actions workflow; do not add one. Run the checks inside the repository directory (or the pinned work directory). The repository has no AGENTS.md, CLAUDE.md, CONTRIBUTING.md or pull request template; follow the style of the code around the change and of its recent commits (`git log --oneline -10`: short imperative subjects, no Conventional Commits prefix).

There is no backend, no authentication and no user data: the app is static, and the cart works on in-memory values. Judge security and access findings against that.
