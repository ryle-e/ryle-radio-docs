## Known issues
- Start and end rests on station tracks don't work - *High prio*
- Gain value of a higher priority track directly affects attenuation of lower priority tracks- that is, if the gain is low on a high prio track, anything underneath it that attenuates will be louder than it should be - *Mid prio*
- Stations keep opening their dropdowns every time the inspector is switched - *Low prio, maybe mid if it gets too annoying*
- Distortion when converting between sample rates at playback time - *Low prio, [[Sample Rates- an important note#How do we fix it?|partially fixed and sufficiently workaround-able]], but would prefer a future comprehensive fix*

---
## Future features
- A type of RadioTrack that adds simple effects and filters- e.g: distortion, lowpass, something that resembles interference
- More procedural audio types

---
## Added features
- Track attenuation- making some tracks quieter when another is playing (see )
- Stations- tracks of tracks?
- Spatial broadcasters
- Dead zones