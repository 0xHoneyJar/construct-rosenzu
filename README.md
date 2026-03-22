# Rosenzu (路線図)

> Spatial awareness for web worlds. Routes are rooms. Transitions are doors. Navigation is wayfinding.

Rosenzu makes web apps feel like places you walk through, not tabs you click between. It gives you a vocabulary for thinking about routes as rooms, navigation as pathways, and transitions as doorways.

Named for 路線図 (rosenzu) — Japanese for "route map." Tokyo subway diagrams are humanity's finest spatial wayfinding artifacts.

## Install

```bash
npx constructs install rosenzu
```

## Skills

| Command | What it does |
|---------|-------------|
| `/map` | Scan your routes and build a spatial topology map |
| `/room` | Name a feature's room before building its furniture |
| `/furnish` | Define a room's emotional profile in measurable parameters |
| `/spatial-audit` | Check spatial coherence across routes and devices |
| `/threshold` | Design transitions between routes as doorways |

## The Idea

Every web app is a building. Most developers treat it as a filing cabinet — flat, alphabetical, utilitarian. Rosenzu treats it as architecture — rooms with atmosphere, hallways with direction, landmarks for orientation.

### The Five Elements (Kevin Lynch)

| Element | Web Translation |
|---------|----------------|
| **Paths** | Navigation flows, scroll journeys, route sequences |
| **Edges** | Section dividers, viewport boundaries |
| **Districts** | Themed route groups with distinct atmospheres |
| **Nodes** | Hub pages, homepages, convergence points |
| **Landmarks** | Persistent UI: logos, nav bars, identity indicators |

### Depth-Distance (Bill Hillier)

How many rooms from the entrance?

```
Depth 0 — The Courtyard (homepage)
Depth 1 — Main Streets (primary routes)
Depth 2 — Inner Rooms (personal/social spaces)
Depth 3 — Inner Sanctums (rituals, settings, craft)
```

Shallow = discovery. Deep = ritual. The deeper you go, the more the world asks of you.

### Two Modes, One Building

| Mode | When | Feel |
|------|------|------|
| **Atmospheric** | First visit, exploration | High ceilings, soft light, inviting |
| **Utility** | Returning user, task-oriented | Good desks, sharp tools, efficient |

Same foundation. Same plumbing. Different furniture.

## The Spatial Stack (v0.2)

Five layers make a web world feel like a building:

| Layer | What | How |
|-------|------|-----|
| **Topology** | Floor plan | Depth-distance mapping, fog of war, device adaptation |
| **Hallway** | State between rooms | Reactive DB carries identity before you arrive |
| **Doors** | Transitions | View Transitions API, directional thresholds, Ma pauses |
| **Materials** | Room emotion | KANSEI profiles → design tokens (warmth, motion, shadow) |
| **Entities** | Composition | ECS — rooms, cards, identities as composable data |

Key insight: **a spinner is a failed hallway.** Loading states should feel like walking through a door, not waiting for a server.

Grounded in 175+ web queries across RuneScape dungeoneering, KANSEI engineering, Convex world state, View Transitions API, and ECS architecture research.

## Origin

Born from [purupuru](https://purupuru.world) — a ghibli-warm world where bears roam, honey flows, and five elements hold everything in balance. The need to make routes feel like rooms in Tsuheji led to rosenzu.

Grounded in research: Kevin Lynch (_Image of the City_), Bill Hillier (Space Syntax), Christopher Alexander (_A Pattern Language_), Don Carson (environmental storytelling), and spatial web design patterns from 16 practitioners.

## Composes With

- **[Artisan](https://github.com/0xHoneyJar/construct-artisan)** — taste tokens (materials, motion, color) applied per-district as atmospheric signatures
- **[K-Hole](https://github.com/0xHoneyJar/construct-k-hole)** — researches spatial design patterns that expand the vocabulary

## License

MIT
