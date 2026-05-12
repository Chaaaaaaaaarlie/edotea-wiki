---
type: meta
title: "Conventions"
created: 2026-05-11
updated: 2026-05-11
tags:
  - meta
status: evergreen
---

# Conventions

## Frontmatter
Every wiki page begins with flat YAML:

```yaml
---
type: <character|location|faction|lore|item|session|quest|source|question|overview|meta>
title: "Human-Readable Title"
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags:
  - <relevant-tag>
status: <seed|developing|mature|evergreen>
related:
  - "[[Other Page]]"
sources:
  - "[[Source Title]]"
---
```

No nested objects — Obsidian's Properties UI does not support them.

## Filenames
- Title Case with spaces: `Lord Halric of Ashvale.md`
- Folders are lowercase with dashes: `wiki/locations/`
- Unique filenames so `[[wikilinks]]` work without paths

## Wikilinks
- Always `[[Page Name]]`, never `[text](path/file.md)`
- When you link A → B, consider whether B should link back to A

## Status Lifecycle
- `seed` — stub, just placeholder
- `developing` — has content, still being built out
- `mature` — comprehensive
- `evergreen` — index/meta pages that never "finish"

## Callouts
- `> [!gap]` — knowledge gap, needs evidence
- `> [!contradiction]` — two sources disagree
- `> [!key-insight]` — important takeaway
- `> [!stale]` — info may be out of date

## Writing Style
- Declarative present tense ("The Iron Court rules Vethalin" not "It is said that...")
- Cite sources inline: `(Source: [[Session 03 — The Bone Bridge]])`
- Spoilers: prefix the heading with `## 🔒` and wrap content in `> [!warning]`
