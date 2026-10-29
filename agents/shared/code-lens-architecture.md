## Architecture checklist

Read the repository's own instructions first (AGENTS.md, CLAUDE.md, CONTRIBUTING.md, `.agents/` skills, `.github/` instruction files) and compare the change with them and with the code around it. Look for responsibilities in the wrong layer or module, dependencies pointing the wrong way, duplicated logic that should reuse an existing helper, dead code left behind, leaky abstractions, needless complexity, and weakened type safety (`any`, unchecked casts, non-null assertions hiding real cases).

Cite the convention or existing code you compare against for every convention finding; personal preference is not a finding. Suggest the smallest edit that removes the problem, never a refactor larger than the change itself.
