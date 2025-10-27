---
title: What is Ryle Radio
parent: Info
nav_order: "0"
tags:
  - about
  - main
---

In short terms, Ryle Radio is a package to emulate the functionality of real world radio that playing to receiver devices.

In practice, this means that you can have an end user move a value across a range and hear different things depending on where that value is, much like tuning frequencies on a receiver. Developers using Ryle Radio can define what is heard and where in the range it is audible.

![RadioData example](Images/Guides/Basic-Radio-Sample/20251007134404.png)

---
## Features
Audio types in Ryle Radio are called **[](../../Guides/1.%20Basic%20Radio%20Sample.md#Specific%20tracks|Tracks)**. Tracks can be Unity AudioClips, procedural audio (e.g: noise, waveforms), and even custom structures named [](../../Guides/1.%20Basic%20Radio%20Sample.md#station_sfx|Stations), which contain multiple other audio types and switch between them automatically. Together these Tracks can form a complex system of audio that can be tuned through at runtime, creating an interactive and easily usable system for players to engage with audio.

The package contains **Broadcasters**, points that cause tracks to play louder (or at all) depending on the proximity of an output- effectively an object that broadcasts the track. It also contains **Insulators**, which are the reverse- areas where tracks are quieter.

It also contains **Observers**, which are built-in scripts allowing you to tie functionality into the radio, such as invoking events when a particular track is audible, or when an output leaves a certain tune range. These work with **Interactors**, which provide a no-code solution to playing, pausing, etc., tracks.

---

This package is built to be modular and expandable too, allowing easy creation of custom track types and components that slots nicely into the inspector.

**Most importantly, Ryle Radio is open-source and free on the Asset Store!** Feel free to try it out to see if it fits your requirements, and, if you feel so inclined, check out the code! I would much appreciate feedback as this is my first open-source package, so any thoughts or contributions are very welcomed :)

That's it! Hope the package works for you :))))