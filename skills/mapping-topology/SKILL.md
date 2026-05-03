---
name: mapping-topology
description: "Map an app's route topology — discover districts, depth levels, navigation flows, and dead ends"
allowed-tools: [Bash, Read, Grep, Glob, Edit, Write]
user-invocable: true
trigger: "/map"
---

# Mapping Topology

> Build a spatial map of your web app. Routes become rooms. Navigation becomes pathways. Dead ends get flagged.

## What This Skill Does

1. **Scans route structure** — finds all routes in the project (SvelteKit, Next.js, Remix, etc.)
2. **Classifies each route** using Lynch's 5 Elements:
   - Is it a **path** (navigation flow)?
   - Is it an **edge** (boundary between areas)?
   - Is it a **district** (themed zone with atmosphere)?
   - Is it a **node** (convergence point)?
   - Is it a **landmark** (fixed orientation point)?
3. **Assigns depth-distance** — how many rooms from the entrance (homepage = depth 0)
4. **Identifies device priority** — which routes matter more on mobile vs desktop
5. **Flags dead ends** — routes with no hallway out
6. **Generates a topology map** as a Mermaid diagram + structured table

## Input

The project's route directory. Auto-detected from framework:
- SvelteKit: `src/routes/`
- Next.js: `app/` or `pages/`
- Remix: `app/routes/`

Optional: a `topology.md` file if one already exists (used as baseline).

## Output

A topology document with:
- Route table (code name, room name, depth, device priority, Lynch classification)
- Mermaid graph showing connections and depth
- Dead end warnings
- Device importance matrix
- Suggested room names for unnamed routes

## Workflow

```
/map                          → full topology scan
/map --routes-only            → just the route table, no analysis
/map --device mobile          → mobile-priority view
/map --device desktop         → desktop-priority view
/map --check topology.md      → diff current routes against existing topology doc
```

## Example Output

```
| Route | Room Name | Depth | Type | Mobile | Desktop |
|-------|-----------|-------|------|--------|---------|
| /     | Courtyard | 0     | Node | High   | High    |
| /bazi | The Mirror| 1     | District | Highest | High |
| /me   | The Alcove| 2     | District | High (tab) | Low (dropdown) |
```
