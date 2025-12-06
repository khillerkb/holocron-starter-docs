<!-- Copied/merged guidance for agent workflows in this workspace. Keep concise and actionable. -->
# Copilot instructions for holocron-starter-docs

This repository holds documentation and content for Holocron starter docs. The workspace also contains related tooling and example agent guidance in sibling folders (see `../agents/AGENTS.md`). Use the notes below to be productive immediately.

1. Quick start (developer session)
   - Install deps at repo root if needed: `npm install` (this repo is docs-focused; other workspace packages may use pnpm/yarn).
   - Run the local site in dev mode: `npm run dev`. This enables hot-reload — prefer this for iterative changes.
   - Do NOT run production builds (`npm run build`) inside an interactive agent session; it can break HMR and slow iteration (see `/Users/bkh223/Documents/GitHub/agents/AGENTS.md` guidance).

2. Where to look for the most important content
   - Docs/content: `rules-and-workflows/` — includes `index.mdx`, `rules.mdx`, `workflows.mdx`, `best-practices.mdx` and `meta.json` (frontmatter and `meta.json` control nav and page order).
   - Repo README: `README.md` at repository root contains high-level notes.
   - Workspace-level agent guidance: `agents/AGENTS.md` (in the workspace root) contains agent-specific workflow tips (hot-reload, dependency handling, commands).

3. File and content conventions you must preserve
   - MDX pages use YAML/MDX frontmatter: keep `title`, `description`, and `icon` fields intact when editing (see `rules-and-workflows/*.mdx`).
   - `meta.json` lists pages and controls navigation; update it when adding/removing docs pages.
   - Examples (in `rules.mdx`) show canonical YAML shapes for rules: triggers, conditions, actions. If changing schema, search the docs and update all examples and `meta.json`.

4. Common tasks and examples
   - Add a new doc page: create `rules-and-workflows/<slug>.mdx` with frontmatter and add the filename (without extension) to `rules-and-workflows/meta.json` `pages` array.
   - Update examples: prefer editing the example YAML blocks in `rules.mdx` to keep real examples consistent with UI/schema.

5. Build / test / lint notes
   - Linting and tests (if present) are run with `npm run lint` and `npm run test` respectively. If you add packages elsewhere in the workspace, update the appropriate lockfile and restart the dev server.

6. Integration and boundaries
   - This repo is documentation-first. Production runtime, rule engines, and API integrations live outside this repo (look for service repos in the workspace).
   - When adding references to external APIs or runtime behavior, include links or pointers to the implementation repo and any relevant API examples.

7. Agent-specific constraints
   - Keep edits atomic and focused: small doc updates or single example fixes are preferred.
   - When modifying navigation or adding/removing pages, update `meta.json` and run the dev server to verify the site navigation updates correctly.

If anything below is unclear or you need more details (build steps, package manager conventions, or where runtime services live), tell me which area you want expanded and I'll iterate.
