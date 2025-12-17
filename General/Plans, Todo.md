---
title: Plans, Todo
parent: General
nav_order: "1"
tags:
  - todo
  - plans
---

## Known issues
- Start and end rests on station tracks don't work - *High prio*
- New RadioTrackWrappers get linked when added in a RadioData and mirror values in their child RadioTrack - *Mid prio, attempted to fix by creating RadioDataEditor but that doesn't appear to have done it*
- Stations keep opening their dropdowns every time the inspector is switched - *Low prio, maybe mid if it gets too annoying*
- Distortion when converting between sample rates at playback time - *Low prio, [can currently be worked around](Info/Sample%20Rates-%20an%20important%20note.md#How%20do%20we%20fix%20it?), but would prefer a future comprehensive fix*

---
## Future features
- A type of RadioTrack that adds simple effects and filters- e.g: distortion, lowpass, something that resembles interference
- More procedural audio types
- Weighted track selection in stations
- Converting the entire package to pure C#, and make Unity integration an extension, not core. Aww yeah, this is the fun one :)

---
## Added features
- Track attenuation- making some tracks quieter when another is playing (see [](../Guides/1.%20Basic%20Radio%20Sample.md#Attenuation|Attenuation))
- Stations- tracks of tracks?
- Spatial broadcasters
- Dead zones (insulators)
- WebGL support (kinda)