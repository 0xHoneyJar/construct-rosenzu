---
name: furnishing-rooms
description: "Given a room name + KANSEI target, output the material specification — tokens, tints, motion, thresholds"
allowed-tools: [Bash, Read, Grep, Glob, Edit, Write]
user-invocable: true
trigger: "/furnish"
---

# Furnishing Rooms

> Define a room's emotional profile in measurable parameters. Not vibes — tokens.

## What This Skill Does

Takes a room definition and outputs a complete material specification:

1. **KANSEI profile** — emotional target decomposed into measurable parameters
2. **Atmospheric tokens** — CSS custom properties for warmth, motion, shadow, easing
3. **Element tint mapping** — which element colors this room (user's, daily, neutral)
4. **Adjacent room signals** — what material hints appear at the edges (environmental storytelling)
5. **View Transition config** — shared elements, direction type, Ma duration
6. **Hallway subscriptions** — what Convex state flows in from adjacent rooms

## KANSEI Parameters

Each room gets a profile with measurable values:

| Parameter | Range | Controls |
|-----------|-------|----------|
| Warmth | 0.0 - 1.0 | Background tint chroma, shadow hue temperature |
| Motion speed | 200ms - 3000ms | Default animation duration in this room |
| Shadow depth | 0.0 - 0.25 | Shadow alpha, elevation intensity |
| Easing character | settle / bounce / breathe / puru-out | Default easing curve |
| Information density | sparse / standard / rich | Content layout density |
| Sound texture | silent / ambient / ritual | Future: WebAudio layer |

### Velocity = Emotion

| Speed | Emotion | Use For |
|-------|---------|---------|
| 200ms | Playful, responsive | Workshops, creation tools |
| 400ms | Trustworthy, reliable | Galleries, social spaces |
| 700ms+ | Sacred, intentional | Rituals, reveals, personal spaces |
| 3000ms | Breathing, alive | Ambient backgrounds, idle states |

## Output Format

```yaml
room: The Mirror
route: /bazi
depth: 1
kansei:
  feel_word: ritual
  warmth: 0.70
  motion: 700ms
  shadow: 0.18
  easing: puru-out
  density: sparse
  sound: ritual
tokens:
  --room-bg: var(--puru-cloud-base)
  --room-tint: var(--puru-{user-element}-tint)
  --room-motion: 700ms
  --room-shadow: oklch(0.55 0.02 85 / 0.18)
  --room-ease: var(--ease-puru-out)
threshold:
  from_courtyard:
    direction: deeper
    shared_elements: [wordmark, element-kanji]
    ma: 400ms
  to_gallery:
    direction: wider
    shared_elements: [wordmark, element-badge]
    ma: 300ms
hallway:
  reads: [worldIdentity.element, todaysElementId]
  writes: [worldIdentity.element, worldIdentity.discoveredAt]
adjacent_signals:
  - target: /collection
    hint: "museum lighting fades in at page bottom"
  - target: /soul
    hint: "guardian silhouette appears at reveal completion"
```

## Workflow

```
/furnish "The Mirror"                → full material spec for /bazi
/furnish "The Gallery" --tokens-only → just the CSS custom properties
/furnish --all                       → furnish every named room
/furnish --diff                      → compare current CSS against KANSEI targets
```

## Composes With

- **Artisan** — provides the taste token vocabulary. Furnish references tokens from taste.md.
- **K-Hole** — KANSEI research informs parameter choices.
- **Observer** — user behavior data validates whether the room's emotion lands as intended.
