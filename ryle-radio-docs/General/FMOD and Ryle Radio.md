TL;DR, FMOD is optionally used with Ryle Radio to stream audio files at runtime. It does not have any further integration yet, however it's a definite consideration for future- if it'd be used by others, I am happy to implement :)

---

## What is used?
The package [FMOD for Unity](https://assetstore.unity.com/packages/tools/audio/fmod-for-unity-2-02-161631) is used in Ryle Radio to allow for runtime audio streaming. Inside [[ClipRadioTrack]], we access data from the provided AudioClip using the built-in method `GetData(...)`.