---
title: FAQ / Common Issues and Questions
parent: Info
nav_order: "1"
tags:
  - faq
  - issues
---

These are some questions I feel could end up being common, and would prefer to have easily answerable than requiring you to trawl through documentation :)
If you've got a question not answered here, check relevant Samples

1. [Questions](#questions)
	1. [How do I use Ryle Radio?](#how%20do%20I%20use%20ryle%20radio)
	2. [How do I work with it in code?](#how%20do%20I%20work%20with%20it%20in%20code)
	3. [How do I work with it without coding?](#how%20do%20I%20work%20with%20it%20coding)
	4. [What does the Gain Curve do?](#what%20does%20the%20gain%20curve%20do)
2. [Issues](#issues)
	1. [My AudioClip sounds distorted when played through a radio!](#my%20Audio%20Clip%20sounds%20distorted%20when%20played%20through%20a%20radio)
	2. [My project takes ages to start up after adding the radio!](#My%20project%20takes%20ages%20to%20start%20up%20after%20adding%20the%20radio)
	3. [I can't hear my track/my track is quiet!](#I%20can't%20hear%20my%20track/my%20track%20is%20quiet!)
	4. [My track has distortion in a build for a specific platform!](#My%20track%20has%20distortion%20in%20a%20build%20for%20a%20specific%20platform)

---
## Questions
### How do I use Ryle Radio?
Glad you asked! :)

I would recommend looking through the [1. Basic Radio Sample](../../Guides/1.%20Basic%20Radio%20Sample.md) to begin with, as that contains some good starter information about what a successful radio looks like. Once you've got that down pat, check out the [2. Spatial Components Sample](../../Guides/2.%20Spatial%20Components%20Sample.md) to learn about Broadcasters and Insulators, and finally [Observers and Interactors Sample](Observers%20and%20Interactors%20Sample) to learn about implementing more complex functionality without any code.

### How do I work with it in code?
First of all, make sure it wouldn't just be easier to use [Observers and Interactors as described in the sample](../../Guides/3.%20Interaction%20Components%20Sample.md). If you're playing, pausing, stopping or resetting tracks, watching for changes, or mirroring radio values, you can likely do it with those components. Because there aren't any samples that hook into Ryle Radio through custom code, your best bet is checking out the [source documentation](https://ryle-e.github.io/ryle-radio-scripting-docs/index.html)- particularly for the [Observers](https://ryle-e.github.io/ryle-radio-scripting-docs/d1/d58/class_ryle_radio_1_1_components_1_1_radio_observer.html) and [Interactors](https://ryle-e.github.io/ryle-radio-scripting-docs/d3/d85/class_ryle_radio_1_1_components_1_1_radio_interactor.html) to get a general feel of how to link in with radios.

It's very possible, if not likely, that this documentation won't be enough for the specific thing you're trying to do :( If this happens to be the case, [contact me](../Contact.md)! I'm very happy to lend a hand with specific issues or plans, and very open to introducing new features if necessary. 

### How do I work with it without coding?
Check out [3. Interaction Components Sample](../../Guides/3.%20Interaction%20Components%20Sample.md)! The components you likely need are explained and used in there :)

### What does the **Gain curve** do?
The gain curve can be a little confusing if you haven't worked with non-linear blending or curves like this before. It effectively tells outputs that are tuning through this radio how loud to make a particular track within the tune range.

![Pasted image 20251007150555](../../Images/Info/Pasted%20image%2020251007150555.png)
For example, this is a track in [1. Basic Radio Sample](../../Guides/1.%20Basic%20Radio%20Sample.md). The gain curve is how loud this track will be when tuned to the \[33.2 - 246.0] range.
Let's say we have a RadioOutput using this radio with its tune set to about 140. That value places us right in the center of the track's range, which places us right in the center of the gain curve. Because the curve is high at that point, the track will be loud. If we use a tune value of about 60, though, we're lower down on the gain curve- the track will be quieter.

This curve can be useful for tracks that are limited to a very small range, by making them easier to hear at the edges of the range:![Pasted image 20251007151057](../../Images/Info/Pasted%20image%2020251007151057.png)
Or perhaps we want it to be fully audible as soon as the range is reached:![Pasted image 20251007151140](../../Images/Info/Pasted%20image%2020251007151140.png)
Or maybe the tune range reaches all the way to the end of the range, and we want it to be loudest at the end:
![Pasted image 20251007151227](../../Images/Info/Pasted%20image%2020251007151227.png)
The possibilities are endless :)

---
## Issues
### My Audio Clip sounds distorted when played through a radio?
This is a known problem related to conversion between sample rates.  [](Sample%20Rates-%20an%20important%20note.md#How%20do%20we%20fix%20it?|Here's%20some%20solutions%20I've%20put%20together%20for%20this%20specific%20issue), and [](../Plans,%20Todo.md#Known%20issues|the%20issue%20itself%20is%20logged%20here).

### My project takes ages to start up after adding the radio!
This is most likely due to the audio being decompressed on game startup. When a Radio is initialized, it needs to load all of the AudioClips it contains into memory (a limitation of [AudioClip.GetData(..)]([Unity - Scripting API: AudioClip.GetData](https://docs.unity3d.com/6000.2/Documentation/ScriptReference/AudioClip.GetData.html)))- this can end up creating a significant amount of load time for the project as it's decompressing many clips at once!

We can fix this in two primary ways: enabling the **Load in background** toggle in the AudioClip, or by streaming the audio directly at runtime. The latter option is not possible using built-in Unity tools, and so we [need to use the package FMOD to do so](FMOD%20and%20Ryle%20Radio.md). The **Load in background** toggle *should* work fine with Ryle Radio, but if you have any issues please [contact me](../Contact.md) :)

### I can't hear my track/my track is quiet!
Throwing together some possible reasons why this could be happening:
- Is the **Tune** value on your RadioOutput inside your track's **Tune range**?
- Is the **Gain** value on your track high enough?
- Is the **Gain curve** correct? See [what does the Gain curve do?](#What%20does%20the%20**Gain%20curve**%20do?)
- If there are tracks above the quiet one and their tune ranges overlap, is the **Attenuation** on your quiet track too high?
- Is **Force global** selected on your track (or if you're using Broadcasters for this track, deselected)?
- Is **Play on Init** selected on your track? If not, are you playing it yourself (either through a [RadioInteractor](RadioInteractor) or your own code)?
- If it's an AudioClip, is the clip itself loud enough?
If none of these help/fix, [contact me](../Contact.md) and I'll happily try to work it out!

### My track has distortion in a build for a specific platform!
This is usually another [sample rate issue](Sample%20Rates-%20an%20important%20note.md). Specifically, this could be because different platforms may use different sample rates in their audio. The workaround for this issue is a little exhaustive, but necessary: force the AudioClips to a specific sample rate depending on the platform.

To do this, assign the new build target in Build Settings, then [](Sample%20Rates-%20an%20important%20note.md#Forcing%20sample%20rates%20on%20clips|force%20the%20sample%20rates%20as%20usual). This should, ideally, work for the selected platform- if it does not, please [contact me](../Contact.md) and I'll see if I can help out :)