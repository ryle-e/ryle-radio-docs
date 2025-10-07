These are some questions I feel could end up being common, and would prefer to have easily answerable than requiring you to trawl through documentation :)
1. [[#Questions]]
	1. [[#How do I use Ryle Radio?]]
	2. [[#How do I work with it in code?]]
	3. [[#How do I work with it without coding?]]
2. [[#Issues]]
---
## Questions
### How do I use Ryle Radio?
Glad you asked! :)

I would recommend looking through the [[Basic Radio Sample]] to begin with, as that contains some good starter information about what a successful radio looks like. Once you've got that down pat, check out the [[Spatial Components Sample]] to learn about Broadcasters and Insulators, and finally [[Observers and Interactors Sample]] to learn about implementing more complex functionality without any code.

### How do I work with it in code?
First of all, make sure it wouldn't just be easier to use [[Observers and Interactors Sample|Observers and Interactors as described in the sample]]. If you're just playing or stopping tracks, watching for changes, or mirroring radio values, you can likely do it with those components. Because there aren't any samples that hook into Ryle Radio through custom code, your best bet is first checking out the code documentation and scripts themselves- particularly with the [[RadioObserver|Observers]] and [[RadioInteractor|Interactors]] to get a general feel of how to link in with radios.

It's very possible, if not likely, that this documentation won't be enough for the specific thing you're trying to do :( If this happens to be the case, [[Contact|contact me]]! I'm very happy to lend a hand with specific issues or plans, and very open to introducing new features if necessary. 

### How do I work with it without coding?
Check out the [[Observers and Interactors Sample]]! The components you likely need are explained and used in there :)

---
## Issues
### My Audio Clip sounds distorted when played through a radio?
This is a known problem related to conversion between sample rates.  [[Important Setup Note#How do we fix it?|Here's some solutions I've put together for this specific issue]], and [[Plans, Todo#Known issues|the issue itself is logged here]].

### My project takes ages to start up after adding the radio!
This is most likely due to the audio being decompressed on game startup. When a Radio is initialized, it needs to load all of the AudioClips it contains into memory (a limitation of [AudioClip.GetData(..)]([Unity - Scripting API: AudioClip.GetData](https://docs.unity3d.com/6000.2/Documentation/ScriptReference/AudioClip.GetData.html)))- this can end up creating a significant amount of load time for the project as it's decompressing many clips at once!

We can fix this in two primary ways: enabling the **Load in background** toggle in the AudioClip, or by streaming the audio directly at runtime. The latter option is not possible using built-in Unity tools, and so we [[FMOD and Ryle Radio|need to use the package FMOD to do so]]. The **Load in background** toggle *should* work fine with Ryle Radio, but if you have any issues please [[Contact|contact me]] :)

### I can't hear my track/my track is quiet!
Throwing together some possible reasons why this could be happening:
- Is the **Gain** value on your track high enough?
- If there are tracks above the quiet one and their tune ranges overlap, is the **Attenuation** on your quiet track too high?
- 