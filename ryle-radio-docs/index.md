## Intro
Ryle Radio is a radio-like audio tool for Unity projects. It is intended to emulate the function of a real-world radio, with tuning, spatial broadcasters, and more.

It allows for you to set up several `RadioTracks` at specific frequencies, tune between them on a `RadioListener` attached to an `AudioSource`. These tracks could contain an `AudioClip`, or procedural audio, or even other `RadioTracks` to select from. Combining many tracks allows you to develop a complex (or simple) system of audio that can be moved through at runtime.

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
- Integrated attenuation (making tracks quieter when others are playing at the same time)
- Code integration for modifying radios, tracks, etc in user code
- Open classes for custom components and functionality
- Premade samples and full documentation
- Open-source!

I am a little worried that the way I wrote this feature list doesn't make total sense lol, so check out the [[#Contact, Contribute]] section to contact me with any questions :)

## Limitations
- **All audio is reduced to mono**- does reflect real life radios, but could be annoying for more complex audio layouts. Theoretically you could use a different radio for each side as a workaround, but this would take a lot of effort to set up
- **Some parts can't be modified at runtime**- specifically observers and adding new tracks to stations (the latter of which you technically can do but may require some tinkering, and can easily be worked-around)

## Contact, Contribute
You can contact me at `rjdwalrus@gmail.com` for any questions, suggestions, issues, or really anything else! The package itself is in a public Git repository, so feel free to add issues or discussions there.

This is the first open-source package I have developed, and so I'm not too well-versed in the contributions process outside of simple collaboration. If you want to add anything to the package or make any changes, feel free to make a pull request! I'll update the Asset Store version semi-frequently when changes are made.

## Thanks!
This is my first open-source package and my second ever published Unity package, so I hope it works for you and does what you need it to !!   :)))