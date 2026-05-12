---
type: meta
title: "Dashboard"
created: 2026-05-11
updated: 2026-05-11
tags:
  - meta
status: evergreen
---

# Wiki Dashboard

Requires the **Dataview** plugin.

## Recent Activity
```dataview
TABLE type, status, updated FROM "wiki" SORT updated DESC LIMIT 15
```

## Seed Pages (Need Development)
```dataview
LIST FROM "wiki" WHERE status = "seed" SORT updated ASC
```

## Characters by Type
```dataview
TABLE character_type, status FROM "wiki/characters" WHERE type = "character" SORT character_type, file.name
```

## Active Quests
```dataview
TABLE status, priority FROM "wiki/quests" WHERE status = "active" SORT priority ASC
```

## Recent Sessions
```dataview
TABLE session_number, date FROM "wiki/sessions" SORT session_number DESC LIMIT 10
```

## Entities Missing Sources
```dataview
LIST FROM "wiki/characters" OR "wiki/locations" OR "wiki/factions" OR "wiki/items" WHERE !sources OR length(sources) = 0
```

## Open Questions
```dataview
LIST FROM "wiki/questions" WHERE status != "answered"
```
