## This workspace

You work in the dazl-in-dazl workspace. It has two repositories, each with its own git history and its own agent instructions. Read them before you judge or change code in a repository:

- `dazl/`: the Dazl editor and web app (React Router, Radix UI). Instructions: `dazl/AGENTS.md`, `dazl/CLAUDE.md`, `dazl/.github/copilot-instructions.md`, plus skills under `dazl/.agents/`.
- `api-server/`: the backend that `dazl` calls through the typed `@dazl/api-client` SDK in `api-server/sdk/`. Instructions: `api-server/.github/copilot-instructions.md`.

Workspace-wide lessons live in `.agents/skills/` at the workspace root. Load the ones whose description matches your task.

A feature's documents live at the workspace root under `specs/features/<feature-slug>/`: `spec.md`, then `mockups/` when the feature changes UI. Read the slug from the spec step's output (or the existing folder) and never rename it.

A UX fix's documents live at the workspace root under `specs/ux-fixes/<ux-slug>/`, with the same layout as a feature: `spec.md`, then `mockups/`. In a UX Fix run, read every mention of `specs/features/<feature-slug>/` as `specs/ux-fixes/<ux-slug>/`. Read the slug from the clarify step's output and never rename it.

A bug's documents live at the workspace root under `specs/bugs/<bug-slug>/`: `bug.md`, then `investigation.md`, `reproduction.md`, `validation.md` and `pr-log.md` as the Bug Fix workflow runs. Read the slug from the clarify step's output and never rename it.

A change to an api-server endpoint or field that dazl uses has to change both repositories: the server, its SDK types, and the dazl caller. dazl never makes raw or untyped SDK calls.

Access in this product follows workspace, project and session membership and roles. api-server enforces every access check; dazl hiding something in the UI is not a check.
