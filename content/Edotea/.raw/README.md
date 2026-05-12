# .raw — Source Documents

**Read-only.** Never modify files in this directory. Source documents are the ground truth; the `wiki/` is generated from them.

## Subfolders

- `session-transcripts/` — recordings or written-up notes of actual sessions
- `player-handouts/` — letters, journals, maps shown to players in-character
- `references/` — published material, splatbooks, modules, monster manuals being mined
- `maps/` — image files: world maps, regional maps, battle maps
- `brainstorms/` — raw DM planning, unstructured thoughts before they become lore
- `assets/` — anything else: audio clips, character art, etc.

## How to use

1. Drop a file in the appropriate subfolder.
2. Say in chat: **"ingest [filename]"** — Claude will read it, summarize it into `wiki/sources/`, and update every relevant character / location / faction / lore page.
3. The original file in `.raw/` stays untouched.

## What goes here, what doesn't

| Goes in `.raw/` | Goes in `wiki/` |
|---|---|
| Raw transcripts | Session recap pages |
| The actual handout | Notes about what the handout says |
| Published module text | Your synthesized version filtered for this campaign |
| Brainstorm dumps | Structured lore pages |
