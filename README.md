# Notes + Kanbn workspace template

VS Code markdown notes + Kanbn boards. **All project, product and component names below are examples — replace them locally.**

## Layout

```
.vscode/settings.json   Todo Tree tag config (the tag registry lives here)
.kanbn/                 ONE folder, ALL boards
  index.md              main / overview board
  <project>.md          one board file per project (H1 + ## columns)
  tasks/                shared task pool — a task can appear on more than one board
projects/<project>/
  daily/                one dated capture note per day
  decisions.md
  status.md
  workstreams/          one note per workstream
  design-checklist.md   design projects only
resources/components.md registry of components + their KIND
templates/              copy-from templates for the files above
RUNBOOK.md              setup + the daily rep
```

Kanbn globs `*.md` inside the single `.kanbn/` folder; a file is a board if it has an H1.
Boards in per-project subfolders are NOT discovered. All boards share `.kanbn/tasks/`.

## Folders vs tags

Projects are the only note folder. Product and component cross-cut projects
(many-to-many), so they are tags, never folders.

## Tags

Four routing tags, inline at the END of a keeper line in the daily note:

| tag | goes to |
| --- | --- |
| `#todo` | a card on that project's Kanbn board |
| `#decision` | that project's `decisions.md` |
| `#status` | that project's `status.md` |
| `#workstream` | that workstream's note |

Two optional classification axes, only on lines you would actually filter by:
`#prod-<name>` and `#c-<component>`.

Component KIND (functional module / platform component / service) is not a tag
prefix — it is recorded once in `resources/components.md`.

Todo Tree matches `(#)($TAGS)\b` case-insensitively over `**/*.md`. No space
after `#`, so `## Headings` are safe. `todo-tree.general.tags` is the registry:
a tag that is not listed simply will not light up.
