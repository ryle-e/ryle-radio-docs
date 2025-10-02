TL;DR, FMOD is optionally used with Ryle Radio to stream audio files at runtime. It does not have any further integration yet, however it's a definite consideration for future- if it'd be used by others, I am happy to implement :)

---

## Why is it used?
Inside [[ClipRadioTrack]], we access data from the provided AudioClip using the built-in method [`GetData(...)`](https://docs.unity3d.com/6000.2/Documentation/ScriptReference/AudioClip.GetData.html). However, this method requires that the entire audio clip is decompressed before the data can be obtained- that is, the clip has to be loaded at the game startup. With only a few short audio clips this can be negligible, but once you start using longer tracks or full songs, a significant amount of waiting happens whenever you start the game or Play Mode- quickly becoming a major detriment to development.

The solution that Unity gives us to this problem is the [Streaming load type](https://docs.unity3d.com/6000.2/Documentation/ScriptReference/AudioClipLoadType.html). Normally, this would allow the audio to be loaded in small chunks over time, making big audio files load significantly faster. Unfortunately, this does not work for us- in order to use `GetData(...)`, the whole clip needs to be loaded, as previously described. Attempting to use Streaming (or even CompressedInMemory) spits back errors at runtime.

This leaves as with an issue, then- how do we stream audio for big files? The answer I've gone with is FMOD.

## What does it do?
 [FMOD for Unity](https://assetstore.unity.com/packages/tools/audio/fmod-for-unity-2-02-161631) is an incredibly popular third-party audio system that allows for complex audio in a Unity project, though the base FMOD works with countless engines and systems. It also provides low-level audio loading and streaming that we can utilise in Ryle Radio.

We load the selected AudioClip into FMOD, then over time stream chunks into a buffer that we play through Unity. The only difference you'll notice is that your game starts up faster :)

## When should I use it?
If you're using large audio files, e.g: songs, ambience, it could be worthwhile using this integration in order to reduce load times. You may be able to get by without it by using [`AudioClip.loadInBackground`]