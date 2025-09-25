***Note:** When referring to "tracks" in this documentation, this is usually what we're referring to- all information about the [[RadioTrack]] can be accessed here too AND in the inspector, hence we generally refer to this class as the whole track with the RadioTrack as the "track class" or something similar.*

These are the containers for [[RadioTrack]]s, specifically for use in the Unity GUI. We keep it separate from RadioTracks so that we can use generic values independently of which track is chosen ([[#gain]], [[#attenuation]], etc). As well as this, using a wrapper allows the user to choose which track they want using a dropdown in the inspector.

When you first create a track, it will look like this:
![[Pasted image 20250925190155.png]]
This is a basic blank slate for you to input information into. See below for information about each variable.

## Inspector Variables
### ID
The ID of a track is a unique value used when referring to it in other radio-related components, or when accessing it in your own custom code. Set it to something distinct enough that you'll know what the track is when you see it listed somewhere, e.g "low static", "scary music"

### Range
In simple terms, think of the frequency of a radio station in real life- let's say 100.1FM, for example. When you're tuning a radio to this frequency, you can still hear the station when your radio's frequency is in the immediate area of 100.1FM, but quieter (or more distorted). The range value here allows you to manually choose the size of this area- the range in which you can hear this track.

In this package, the frequency of the radio is called Tune, (mainly to keep it separate enough from real-world frequency that we can customize the min/max values if we so choose)

