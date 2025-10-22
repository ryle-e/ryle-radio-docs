## Known issues
- Start and end rests on station tracks don't work - *High prio*
- New RadioTrackWrappers get linked when added in a RadioData and mirror values in their child RadioTrack - *Mid prio, attempted to fix by creating RadioDataEditor but that doesn't appear to have done it*
- Stations keep opening their dropdowns every time the inspector is switched - *Low prio, maybe mid if it gets too annoying*
- Distortion when converting between sample rates at playback time - *Low prio, [[Sample Rates- an important note#How do we fix it?|partially fixed and sufficiently workaround-able]], but would prefer a future comprehensive fix*

---
## Future features
- A type of RadioTrack that adds simple effects and filters- e.g: distortion, lowpass, something that resembles interference
- More procedural audio types
- Weighted track selection in stations

---
## Added features
- Track attenuation- making some tracks quieter when another is playing (see [[1. Basic Radio Sample#Attenuation|Attenuation]])
- Stations- tracks of tracks?
- Spatial broadcasters
- Dead zones (insulators)