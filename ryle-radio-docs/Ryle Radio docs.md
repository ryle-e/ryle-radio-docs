## Intro
Ryle Radio is a radio-like audio tool for Unity projects. It is intended to emulate the function of a real-world radio, with tuning, spatial broadcasters, and more.

It allows for you to set up several `RadioTracks` at specific frequencies, tune between them on a `RadioPlayer` attached to an `AudioSource`. These tracks could contain an `AudioClip`, or procedural audio, or even other `RadioTracks` to select from. Combining many tracks allows you to develop a complex (or simple) system of audio that can be moved through at runtime.

![[Pasted image 20250922182711.png]] 
![[Pasted image 20250922183059.png]]
## Features
- Tracks linked to specific frequencies (known internally as `tune`)
- Gain interaction with frequencies
- 