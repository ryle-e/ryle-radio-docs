These are some questions I feel could end up being common, and would prefer to have easily answerable than requiring you to trawl through documentation :)
1. [[#Questions]]
	1. [[#How do I use Ryle Radio?]]
	2. [[#How do I work with it in code?]]
	3. [[#How do I work with it without coding?]]
	4. [[#What does the **Gain curve** do?|What does the Gain curve do?]]
2. [[#Issues]]
	1. [[#My Audio Clip sounds distorted when played through a radio?]]
	2. [[#My project takes ages to start up after adding the radio!]]
	3. [[#I can't hear my track/my track is quiet!]]
	4. [[#My track has distortion in a build for a specific platform!]]
---
## Questions
### How do I use Ryle Radio?
Glad you asked! :)

I would recommend looking through the [[1. Basic Radio Sample]] to begin with, as that contains some good starter information about what a successful radio looks like. Once you've got that down pat, check out the [[2. Spatial Components Sample]] to learn about Broadcasters and Insulators, and finally [[Observers and Interactors Sample]] to learn about implementing more complex functionality without any code.

### How do I work with it in code?
# CHANGE THIS 
First of all, make sure it wouldn't just be easier to use [[3. Interaction Components Sample|Observers and Interactors as described in the sample]]. If you're playing, pausing, stopping or resetting tracks, watching for changes, or mirroring radio values, you can likely do it with those components. Because there aren't any samples that hook into Ryle Radio through custom code, your best bet is first checking out the code documentation and scripts themselves- particularly with the [[RadioObserver|Observers]] and [[RadioInteractor|Interactors]] to get a general feel of how to link in with radios.

It's very possible, if not likely, that this documentation won't be enough for the specific thing you're trying to do :( If this happens to be the case, [[Contact|contact me]]! I'm very happy to lend a hand with specific issues or plans, and very open to introducing new features if necessary. 

### How do I work with it without coding?
Check out [[3. Interaction Components Sample]]! The components you likely need are explained and used in there :)

### What does the **Gain curve** do?
The gain curve can be a little confusing if you haven't worked with non-linear blending or curves like this before. It effectively tells outputs that are tuning through this radio how loud to make a particular track within the tune range.

![[Pasted image 20251007150555.png]]
For example, this is a track in [[1. Basic Radio Sample]]. The gain curve is how loud this track will be when tuned to the \[33.2 - 246.0] range.
Let's say we have a RadioOutput using this radio with its tune set to about 140. That value places us right in the center of the track's range, which places us right in the center of the gain curve. Because the curve is high at that point, the track will be loud. If we use a tune value of about 60, though, we're lower down on the gain curve- the track will be quieter.

This curve can be useful for tracks that are limited to a very small range, by making them easier to hear at the edges of the range:![[Pasted image 20251007151057.png]]
Or perhaps we want it to be fully audible as soon as the range is reached:![[Pasted image 20251007151140.png]]
Or maybe the tune range reaches all the way to the end of the range, and we want it to be loudest at the end:
![[Pasted image 20251007151227.png]]
The possibilities are endless :)

---
## Issues
### My Audio Clip sounds distorted when played through a radio?
This is a known problem related to conversion between sample rates.  [[Sample Rates- an important note#How do we fix it?|Here's some solutions I've put together for this specific issue]], and [[Plans, Todo#Known issues|the issue itself is logged here]].

### My project takes ages to start up after adding the radio!
This is most likely due to the audio being decompressed on game startup. When a Radio is initialized, it needs to load all of the AudioClips it contains into memory (a limitation of [AudioClip.GetData(..)]([Unity - Scripting API: AudioClip.GetData](https://docs.unity3d.com/6000.2/Documentation/ScriptReference/AudioClip.GetData.html)))- this can end up creating a significant amount of load time for the project as it's decompressing many clips at once!

We can fix this in two primary ways: enabling the **Load in background** toggle in the AudioClip, or by streaming the audio directly at runtime. The latter option is not possible using built-in Unity tools, and so we [[FMOD and Ryle Radio|need to use the package FMOD to do so]]. The **Load in background** toggle *should* work fine with Ryle Radio, but if you have any issues please [[Contact|contact me]] :)

### I can't hear my track/my track is quiet!
Throwing together some possible reasons why this could be happening:
- Is the **Tune** value on your RadioOutput inside your track's **Tune range**?
- Is the **Gain** value on your track high enough?
- Is the **Gain curve** correct? See [[#What does the **Gain curve** do?|what does the Gain curve do?]]
- If there are tracks above the quiet one and their tune ranges overlap, is the **Attenuation** on your quiet track too high?
- Is **Force global** selected on your track (or if you're using Broadcasters for this track, deselected)?
- Is **Play on Init** selected on your track? If not, are you playing it yourself (either through a [[RadioInteractor]] or your own code)?
- If it's an AudioClip, is the clip itself loud enough?
If none of these help/fix, [[Contact|contact me]] and I'll happily try to work it out!

### My track has distortion in a build for a specific platform!
This is usually another [[Sample Rates- an important note|sample rate issue]]. Specifically, this could be because different platforms may use different sample rates in their audio. The workaround for this issue is a little exhaustive, but necessary: force the AudioClips to a specific sample rate depending on the platform.

To do this, assign the new build target in Build Settings, then [[Sample Rates- an important note#Forcing sample rates on clips|force the sample rates as usual]]. This should, ideally, work for the selected platform- if it does not, please [[Contact|contact me]] and I'll see if I can help out :)