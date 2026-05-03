---
name: auditing-spatial
description: "Audit spatial coherence — consistent nav clearance, device adaptation, district signals, dead ends"
allowed-tools: [Bash, Read, Grep, Glob, Edit, Write]
user-invocable: true
trigger: "/spatial-audit"
---

# Auditing Spatial Coherence

> A spatially coherent app feels like one building. An incoherent one feels like a folder of documents.

## What This Skill Does

1. **Nav clearance audit** — checks that all pages properly clear the fixed navigation
   - Finds pages using `calc(var(--nav-height) + ...)` vs pages using global clearance
   - Flags inconsistent top padding across routes
   - Checks for double-padding (page + app-root both adding nav clearance)

2. **Device adaptation audit** — checks that routes adapt to device topology
   - Desktop: are showcase routes (panoramic content) promoted in nav?
   - Mobile: does the tab bar flow match user priority?
   - Are any routes hidden on both desktop AND mobile nav?
   - Do immersive routes properly hide chrome?

3. **District signal audit** — checks that routes feel like distinct rooms
   - Does each route have its own atmospheric color/treatment?
   - Are OG images set per-route (district identity for sharing)?
   - Do page titles follow a consistent naming pattern?

4. **Dead end audit** — checks that every route has a way out
   - Can users reach every route from the homepage within 3 clicks?
   - Does every route have contextual navigation to adjacent rooms?
   - Are there orphan routes not in any nav?

5. **Landmark audit** — checks that orientation points persist
   - Is the wordmark/logo visible on all non-immersive routes?
   - Does the user's identity (element, avatar) persist across transitions?
   - Is the nav structure consistent (same order, same items)?

## Output

A scored report:

```
Spatial Coherence Score: 7/10

PASS  Nav clearance — all pages use app-root padding
PASS  Landmark persistence — wordmark visible everywhere
WARN  District signals — 3 routes have no atmospheric tint
WARN  Dead ends — /changelog has no adjacent room links
FAIL  Device adaptation — /world not in desktop nav
FAIL  OG coverage — /changelog missing og:title
```

## Workflow

```
/spatial-audit                → full audit
/spatial-audit --nav          → nav clearance only
/spatial-audit --districts    → district signals only
/spatial-audit --dead-ends    → dead end check only
/spatial-audit --score        → just the score, no details
```
