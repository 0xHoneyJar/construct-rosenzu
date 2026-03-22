---
name: designing-thresholds
description: "Design transitions between routes as spatial thresholds — departure, door, arrival"
user_invocable: true
trigger: "/threshold"
---

# Designing Thresholds

> Moving between routes should feel like crossing a doorway, not clicking a link.

## What This Skill Does

1. **Analyzes route pairs** — which routes connect, and in which direction
2. **Classifies direction** — deeper (focusing), wider (expanding), home (returning), sideways (crossing)
3. **Designs threshold patterns** for each transition:
   - **Departure signal** — current room acknowledges you're leaving
   - **The door** — a moment of in-between (Ma — purposeful pause, 0.3-0.5s)
   - **Arrival signal** — new room welcomes you (direction-aware)
4. **Identifies shared elements** that should persist across thresholds (landmarks)
5. **Generates implementation plan** using View Transitions API or framework-specific tools

## Direction Framework

```
going deeper  (/ → /bazi → reveal)     descending, focusing, narrowing
going wider   (/bazi → /collection)    surfacing, expanding, breathing
going home    (any → /)                returning, lightening
going sideways (/chat → /make)         walking across a courtyard
```

## What Persists (Landmarks)

- Wordmark / logo
- User's element tint / identity color
- Navigation structure
- Avatar / profile indicator

## What Changes (District Signals)

- Background atmosphere
- Content layout
- Ambient motion speed
- Sound texture (future)

## Workflow

```
/threshold                           → analyze all route transitions
/threshold /bazi → /collection       → design specific transition
/threshold --direction deeper        → show all "going deeper" transitions
/threshold --persist                 → list what should persist across all thresholds
```

## Implementation Targets

- SvelteKit: `onNavigate` hook + View Transitions API
- Next.js: `useTransitionRouter` or View Transitions
- CSS: `@view-transition` rule, `::view-transition-*` pseudo-elements
- Fallback: CSS `opacity` + `translateY` transitions
