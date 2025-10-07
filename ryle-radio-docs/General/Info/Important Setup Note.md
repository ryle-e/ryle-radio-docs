In the process of developing this package, I have come across a fairly substantial issue that I feel I should address in its own note- sample rate conversion issues/distortion.

If you're not interested in the context and just want the fix, go to [[What do I have to do?]]

---
## What is the problem?
Audio in Unity is handled pretty well in the backend, I think, but doesn't share a lot of that goodness with us developers. The AudioSource component is capable of a lot of things that we cannot do manually, such as audio streaming. One major capability that Unity hasn't opened up about is **conversion between audio sample rates**.

Sample rates become a problem very quickly when we're working with individual audio samples in Unity and playing them back, as the sample rate of an AudioClip can differ from the sample rate of Unity itself- or from another audio clip- or from procedural audio- or from platform limitations- and maybe from other things I'm not aware of. This means that as soon as we try to mix different types of audio in our components, we start to encounter issues regarding their sample rates. 

For example, let's take the "I'll Never Smile Again" audio in the [[Basic Radio Sample]] project. The sample rate of this audio as it's provided is 44100kHz- this is fine for most usages, but Unity runs at 48000kHz by default. Usually we would have no issues with this, but because we're using the individual audio samples ourselves rather than feeding them through an AudioSource, we will get some light distortion or even pitch shifts if we handle this improperly. This can be heard if you manually change the clip's sample rate override and listen closely- check out [this video I posted while trying to find fixes for this exact problem](https://youtu.be/UC8RpxZMkz4) to see what could happen.

## How do we fix it?
We're given a couple options for fixing this problem. The first and easiest is to 