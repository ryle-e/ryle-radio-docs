## Intro
Ryle Radio is a radio-like audio tool for Unity projects. It is intended to emulate the function of a real-world radio, with tuning, spatial broadcasters, and more.

It allows for you to set up several `RadioTracks` at specific frequencies, tune between them on a `RadioPlayer` attached to an `AudioSource`. These tracks could contain an `AudioClip`, or procedural audio, or even other `RadioTracks` to select from. Combining many tracks allows you to develop a complex (or simple) system of audio that can be moved through at runtime.

![[Pasted image 20250922182711.png]] 
![[Pasted image 20250922183059.png]]
## Features
- Tracks linked to specific frequencies (known internally as `tune`)
- Gain interacts with played frequencies (user-defined falloff)
- Spatial broadcasters (areas where certain tracks can be heard)
- Spatial insulators (areas where certain tracks can't be heard)
- Linked to Unity's audio system (sources, mixers, reverb, etc)
- Built-in observer events (detect when a track is audible, etc)
- Premade procedural audio (noise, waveforms)
- Stations- multiple tracks in one, switching between them over time or on request

## Limitations
- **All audio is reduced to mono**- does reflect real life radios, but could be annoying for more complex audio layouts. Theoretically you could use a different radio for each side as a workaround, but this would take a lot of effort to set up
- **Some parts can't be modified at runtime**- specifically