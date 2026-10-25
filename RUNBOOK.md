# Runbook

## One-time setup

1. Install the two VS Code extensions (marketplace only — no npm, brew or CLI):
   - **Todo Tree** (Gruntfuggly)
   - **Kanbn** (gordonlarrigan.vscode-kanbn)
2. Todo Tree needs ripgrep. If the bundled one is not found, set
   `todo-tree.ripgrep` to a ripgrep path in your **user** settings (not this
   workspace file, so the path does not travel with the repo).
3. Open this folder as the VS Code workspace. The Todo Tree panel should light
   up on the tags.
4. Boards already exist as files in `.kanbn/`. Open the Command Palette and use
   the Kanbn **board picker** to switch between them. Never run the `kanbn` CLI.

## Add a project

1. Create `.kanbn/<project>.md` by copying an existing board file; change the H1.
2. Create `projects/<project>/` with `daily/`, `decisions.md`, `status.md`,
   `workstreams/`, and `design-checklist.md` if it is a design project. Copy
   from `templates/`.

## Add a component

1. Add it under the right KIND section in `resources/components.md`.
2. Add its `c-<name>` tag to `todo-tree.general.tags` in `.vscode/settings.json`.

## The rep

**During the day** — capture freely in `projects/<project>/daily/<YYYY-MM-DD>.md`.
Tag keeper lines inline while the context is live.

**At laptop-close** (cue: closing the laptop) —

1. Open today's note. Search `#`.
2. For each tagged line:
   - `#todo` → make a card on that project's board, then **delete the line from
     the journal**. Cut, not copy.
   - `#decision` / `#status` / `#workstream` → cut and paste into the matching file.
3. No tags today? Close anyway — still a rep.
4. Tick **laptop-close rep ran** in the daily note.

Partial is complete. Build nothing more.

## Subtasks vs separate cards

Kanbn's task editor has a subtasks field (it writes a `## Sub-tasks` checklist
into the task file). Use subtasks when the steps serve ONE deliverable and never
move between columns independently. Use separate cards when a piece needs its
own status.
