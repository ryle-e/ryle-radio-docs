TL;DR, FMOD is optionally used with Ryle Radio to stream audio files at runtime. It does not have any further integration yet, however it's a definite consideration for future- if it'd be used by others, I am happy to implement :)

---

## What is used?
The package [FMOD for Unity](https://assetstore.unity.com/packages/tools/audio/fmod-for-unity-2-02-161631) is used in Ryle Radio to allow for runtime audio streaming. 

Inside [[ClipRadioTrack]], we access data from the provided AudioClip using the built-in method [`GetData(...)`](https://docs.unity3d.com/6000.2/Documentation/ScriptReference/AudioClip.GetData.html). However, this method requires that the entire audio clip is decompressed before the data can be obtained- that is, the clip has to be loaded at the game startup. With only a few short audio clips this can be negligible, but once you start using longer tracks or full songs, a significant amount of waiting happens whenever you start the game or Play Mode- quickly becoming a major detriment to development.

The solution that Unity gives us to this problem is the 