---
tags:
  - main
title: Main Page
nav_order: "9"
---

This is the documentation for Ryle Radio!
## Intro
Ryle Radio is a radio-like audio tool for Unity projects. It is intended to emulate the function of a real-world radio, with tuning, spatial broadcasters, and more!

It allows you to set up several [Tracks](1.%20Basic%20Radio%20Sample#Specific%20tracks) at specific frequencies, tune between them on a `RadioListener` attached to an `AudioSource`. These tracks could contain an `AudioClip`, or procedural audio, or even other `RadioTracks` to select from. Combining many tracks allows you to develop a complex (or simple) system of audio that can be moved through at runtime.

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
- Built-in no-code event interactions (play, pause, stop, reset)
- Open classes for custom components and functionality
- Dynamic, automatic modularity- all you need to do is implement
- Premade samples and full documentation
- Open-source!

I am a little worried that the way I wrote this feature list doesn't make total sense lol, so check out the [[Contact]] section to contact me with any questions :)

## Limitations
- **All audio output from a radio is reduced to mono**- does reflect real life radios, but could be annoying for more complex audio layouts. Theoretically you could use a different radio for each side as a workaround, but this would take a lot of effort to set up
- **Some parts can't be modified at runtime**- specifically Observers and adding new tracks to stations (the latter of which you technically can do but may require some tinkering, and can easily be worked-around)

## Links
- GitHub repo
- Asset Store page

## Navigating the docs
Start by checking out the [[1. Basic Radio Sample]] and other samples, followed by [[(Predicted) Common Issues and Questions]]. Any other questions or issues, [[Contact|contact me]]!

## Thanks!
This is my first open-source package and my second ever published Unity package, so I hope it works for you and does what you need it to !!   :)))