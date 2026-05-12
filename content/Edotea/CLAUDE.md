# Edotea — LLM Wiki

Mode: F (Book/Course), adapted for a D&D campaign
Purpose: Persistent knowledge base for the D&D campaign **Edotea** — characters, lore, sessions, quests, items.
Owner: Peter
Created: 2026-05-11

## Structure

```
Edotea/
├── .raw/                         # Layer 1: immutable source documents
│   ├── session-transcripts/      # session audio → text
│   ├── player-handouts/          # in-character documents
│   ├── references/               # published material, splatbooks
│   ├── maps/                     # world & battle maps
│   ├── brainstorms/              # raw DM planning
│   └── assets/                   # everything else
│
├── wiki/                         # Layer 2: LLM-generated knowledge base
│   ├── index.md                  # master catalog
│   ├── log.md                    # operation history (append at TOP)
│   ├── hot.md                    # ~500-word recent context cache
│   ├── overview.md               # campaign overview
│   ├── characters/               # PCs, NPCs, antagonists
│   ├── locations/                # regions, cities, dungeons, planes
│   ├── factions/                 # governments, guilds, churches, criminals
│   ├── lore/                     # cosmology, history, gods, magic, cultures
│   ├── items/                    # magic items, artifacts, quest items
│   ├── sessions/                 # chronological session log
│   ├── quests/                   # active/pending/completed plotlines
│   ├── sources/                  # one summary per .raw/ document
│   ├── questions/                # filed Q&A
│   └── meta/                     # dashboard, conventions, lint reports
│
├── _templates/                   # frontmatter templates for each note type
├── _attachments/                 # images embedded in wiki pages
│
├── WIKI.md                       # Layer 3: the reference spec for this system
└── CLAUDE.md                     # this file
```

## Conventions

- All notes use YAML frontmatter (flat, no nesting): `type`, `status`, `created`, `updated`, `tags` minimum.
- Wikilinks use `[[Note Name]]` — filenames are unique, no paths needed.
- `.raw/` contains source documents — **never modify them**.
- `wiki/index.md` is the master catalog — update on every ingest.
- `wiki/log.md` is append-only — new entries go at the **TOP**, never edit past entries.
- `wiki/hot.md` is a ~500-word cache — overwrite completely each update.
- Spoiler-heavy content (DM-only) goes in `> [!warning]` callouts so it's visually flagged at the table.

## Note Types

| Type | Folder | When |
|------|--------|------|
| `character` | `characters/` | PC, NPC, antagonist |
| `location` | `locations/` | Anywhere with a name and a place on the map |
| `faction` | `factions/` | Any group that acts with shared agenda |
| `lore` | `lore/` | Worldbuilding concepts, history, gods, magic |
| `item` | `items/` | Magic items, artifacts, quest objects |
| `session` | `sessions/` | One per session played |
| `quest` | `quests/` | One per plotline |
| `source` | `sources/` | One per file in `.raw/` |
| `question` | `questions/` | Filed Q&A worth keeping |

## Operations

- **Ingest:** drop file in `.raw/`, say `"ingest [filename]"`. Claude reads it, summarizes into `wiki/sources/`, updates every relevant character/location/faction/lore/item page, updates index/log/hot.
- **Query:** ask anything — Claude reads `hot.md` → `index.md` → relevant pages, then answers with wikilinks.
- **File answer:** after a good Q&A exchange, say `"save that as a question"` to file it in `wiki/questions/`.
- **Lint:** say `"lint the wiki"` for a health check (orphans, dead links, frontmatter gaps).

## Wiki Knowledge Base

When working in *other* Claude Code projects that need Edotea context, point those projects at:
```
Path: D:\Documents\DnD\Edotea
Read order: wiki/hot.md → wiki/index.md → wiki/<folder>/_index.md → individual pages
```
