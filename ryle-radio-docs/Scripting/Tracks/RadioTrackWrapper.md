***Note:** When referring to "tracks" in this documentation, this is usually what we're referring to- all information about the [[RadioTrack]] can be accessed here too AND in the inspector, hence we generally refer to this class as the whole track with the RadioTrack as the "track class" or something similar.*

These are the containers for [[RadioTrack]]s, specifically for use in the Unity GUI. We keep it separate from RadioTracks so that we can use generic values independently of which track is chosen ([[#gain]], [[#attenuation]], etc). As well as this, using a wrapper allows the user to choose which track they want using a dropdown in the inspector.

When you first create a track, it will look like this:
![[Pasted image 20250925185018.png]]
This is a blank slate