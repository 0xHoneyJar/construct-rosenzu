---
name: naming-rooms
description: "Map features to locations — name the room before building the furniture"
user_invocable: true
trigger: "/room"
---

# Naming Rooms

> If you can't name the room, you don't know where the feature lives.

## What This Skill Does

Takes a feature description and helps you decide where it belongs in your app's spatial topology.

1. **Asks**: What does this feature DO? (verb)
2. **Asks**: Who uses it? (audience)
3. **Asks**: How deep is the commitment? (depth level)
4. **Classifies**: Is this a new room, an alcove off an existing room, or furniture in an existing room?
5. **Names the room** using the project's spatial vocabulary
6. **Maps it** to the topology — where does it connect, what's adjacent?

## The Decision Tree

```
Is this feature a full experience (own URL, distinct purpose)?
  YES → New room. Name it. Assign depth. Connect to adjacent rooms.
    Does it need its own atmosphere (different from neighbors)?
      YES → It's a District. Give it a tint, a feel word, a layout.
      NO  → It's an alcove off an existing District.
  NO → It's furniture in an existing room.
    Which room does it belong in?
    Is it always visible or revealed by interaction?
```

## Three Names

Every room gets three names:

| Layer | Purpose | Example |
|-------|---------|---------|
| **Code name** | URL path, used in code | `/forge` |
| **Room name** | Human name, used in docs and discussion | Heart's Hearth |
| **Feel word** | One word that captures the room's atmosphere | craft |

## Workflow

```
/room "mint your element card"        → where does this feature live?
/room "daily element check"           → suggest a room or attach to existing
/room --list                          → show all named rooms in the topology
/room --unnamed                       → find routes without room names
```

## Rules

1. **Routes are rooms.** Prefer separate routes over modals or inline panels.
2. **Rooms have names.** Not just paths — names that evoke the space.
3. **Adjacent rooms are visible.** Each room should hint at what's next door.
4. **Depth matches commitment.** Settings are depth 2. The homepage is depth 0.
5. **The world is the architecture.** If the project has lore, room names come from the lore.
