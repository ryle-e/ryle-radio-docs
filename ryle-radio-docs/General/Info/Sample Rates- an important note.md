In the process of developing this package, I have come across a fairly substantial issue that I feel I should address in its own note- sample rate conversion issues/distortion.

If you don't mind a little bit of distortion on your AudioClip tracks, you can safely ignore this note. If you just want the fix, go straight to [[#How do we fix it?]]

---
## What is the problem?
Audio in Unity is handled pretty well in the backend, I think, but doesn't share a lot of that goodness with us developers. The AudioSource component is capable of a lot of things that we cannot do manually, such as audio streaming. One major capability that Unity hasn't opened up about is **conversion between audio sample rates**.

Sample rates become a problem very quickly when we're working with individual audio samples in Unity and playing them back, as the sample rate of an AudioClip can differ from the sample rate of Unity itself- or from another audio clip- or from procedural audio- or from platform limitations- and maybe from other things I'm not aware of. This means that as soon as we try to mix different types of audio in our components, we start to encounter issues regarding their sample rates. 

The correct way for me to fix this is to use a ratio between the Clip's sample rate and the project's sample rate, and proceed through the clip using that instead of going through one sample at a time. I have done this, and the issue was still present (though changing the progress to a double instead of a float improved it a lot- rounding errors I suppose). It's very possible that I've messed up my code for this, so if you're good at audio- please check it out and prove me stupid :)))

For example, let's take the "I'll Never Smile Again" audio in the [[Basic Radio Sample]] project. The sample rate of this audio as it's provided is 44100kHz- this is fine for most usages, but Unity runs at 48000kHz by default. Usually we would have no issues with this, but because we're using the individual audio samples ourselves rather than feeding them through an AudioSource, we will get some light distortion or even pitch shifts if we handle this improperly. This can be heard if you manually change the clip's sample rate override and listen closely- check out [this video I posted while trying to find fixes for this exact problem](https://youtu.be/UC8RpxZMkz4) to see what could happen.

## How do we fix it?
If it's not something you can or are willing to ignore, we're given a couple options for fixing this problem. My recommendation is to use the first method: **Forcing sample rates on clips**.
### Forcing sample rates on clips
This is a tiny bit complex, but is the least drastic solution to the problem. You can either go about this the integrated way, or the manual way.

I'll also put a note here to say: different build platforms use different base sample rates. This is just a consequence of how the platforms work- make sure you check each individual version and potentially repeat a below method with other build targets selected in case you're having any issues.
#### Integrated way
The Integrated way is built-in to RadioData objects. Opening the Advanced Settings tab will show the following:
![[Pasted image 20251007184437.png]]
Make sure **Force sample rate on Clips** is ticked. If you want to provide your own sample rate, enter it in the box, otherwise leave it at 0. When **Forced sample rate** is set to 0, it will automatically use the default sample rate for the current build type. Press the button to assign the sample rate on all AudioClips referenced in the RadioData!

Please note two things about this method:
1. This affects ALL the AudioClips referenced, even those in Stations- there is no way to exclude clips from this except for removing them from the radio temporarily. Please make sure that you're okay with this change being applied to every applicable clip.
2. The default sample rate matches the current build target. If you're [[(Predicted) Common Issues and Questions#My track has distortion in a build for a specific platform!|having distortion on specific platforms]], my recommendation is to hit the Force button again after the platform has been targeted in Build Settings. If this does not help, [[Contact|contact me]] :)

#### Manual way
The manual way requires you to trawl individually through applicable audio clips and override the sample rate yourself. This is substantially slower, but a lot safer than universally overriding sample rates.

To do this, select an AudioClip in the inspector. Select a target platform, select the Override toggle. Select `Override Sample Rate` on Sample Rate Setting, then select a sample rate below.
![[Pasted image 20251007190243.png]]