---
title: Changelog
parent: General
nav_order: "1"
tags:
  - changelog
  - updates
  - history
---
### 1.1.0
Added WebGL support with one main caveat: clicking sounds during playback. This is a consequence of WebGL's audio system (and its inability to stream audio during runtime), and is quite annoying. It can be generally ignored if you're putting filters on your audio playback, but you might need a click removal filter of some kind if it gets particularly bad.
Also added some more exposed variables to `RadioTrackWrapper` for usage in my game using this package: [pale broadcast]([pale broadcast by ryle e](https://ryle-e.itch.io/pale-broadcast)).

### 1.0.1
Added [com.utilities.audio](https://github.com/RageAgainstThePixel/com.utilities.audio) by RageAgainstThePixel for WebGL support as `OnAudioFilterRead` is not supported in WebGL.

### 1.0.0 - Initial Release
First release of Ryle Radio!