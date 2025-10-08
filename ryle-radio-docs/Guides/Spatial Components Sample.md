This sample uses a simpler radio than [[Basic Radio Sample]], but introduces the spatial components- RadioBroadcasters and RadioInsulators.

---
## Accessing the sample
First, install the sample through Unity's Package Manager. Navigate to `RyleRadio/Samples/SpatialComponents`, and open `MainScene`. It should look like this: ![[Pasted image 20251007233425.png]]

## Description
### Scene
The scene is our focus in this sample, unlike in [[Basic Radio Sample|the previous]]. Selecting the Radio object shows a RadioOutput again, this time with a far simpler RadioData linked to it, that simply plays the same track as constant- but this time with one difference: **Force Global** is unticked. 
![[Pasted image 20251007233604.png]] 
Having this option unticked forces us to use spatial **RadioBroadcasters** for our audio, instead of it being audible everywhere. What is a RadioBroadcaster you ask? Have a look here!

### Broadcasters
The Broadcaster object contains a couple of child objects- circles, and a single **RadioBroadcaster** component. This component is the first of our spatial components that we use.
![[Pasted image 20251007234023.png]]
A **RadioBroadcaster** (usually known hereon as a broadcaster) creates a spherical area where certain tracks are audible- think radio towers in real life. The closer you are to the tower, the clearer the audio it's broadcasting becomes. It works the same in Ryle Radio, but this time you have far more control over the tower's range, falloff, and broadcasted track! Let's go over the variables on this component.
#### Data
This is a reference to a RadioData object that this broadcaster is linked to. Each broadcaster can only be linked to one radio, so just add more of them if necessary. It needs to be linked in order to choose a track to broadcast- you'll see this pattern a few times from hereon.
#### Affected Tracks
This is a multiselect variable that allows us to choose tracks that are affected by this broadcaster. For example, if we have three different tracks playing music at different tune values, we can broadcast all three at once with this one component!
#### Broadcast Radius
The broadcast radius is the range in which this broadcaster applies. There are two values here, though, as there are two radii we need to know.
The first radius is the "inner radius" of the broadcaster- if an output is within this radius, it will hear the track at maximum broadcast power. The output could be anywhere, but so long as it's within this many units of the broadcaster, it will hear the track.
The second radius is the "outer radius".  If an output is outside of this radius, it will be unable to hear the track- this is therefore the maximum range of the broadcaster. 
If an output is between the inner and outer radii, though, it will be progressively quieter depending on how far between them it is. That is, if you move an output from the inner radius to the outer, it will get progressively quieter until it's eventually inaudible.
You can see the two radii in the scene view when the broadcaster is selected! You can also drag them in the scene view like you would a normal collider. ![[Pasted image 20251008144020.png]]
#### Distance Falloff
The distance falloff is a curve showing exactly how the track will get quieter when moving between the broadcast radii. It's the shape of the volume between the inner and outer radius. For example, if it's a smooth graph like this, it'll get quieter smoothly when moving between the radii. ![[Pasted image 20251008143627.png]]
For a linear graph like this, it'll get quieter linearly between the radii. ![[Pasted image 20251008143659.png]]
Something like this, though, would mean that an output between the radii would keep the track loud right up until it gets close to the outer radius- at which point it would start getting quieter. ![[Pasted image 20251008143753.png]]
It's a lot easier to understand how the falloff works when playing with it in realtime. Try moving it around with the scene in playmode, and see how the track changes when the radio is between the broadcast radii with different falloffs.

### This particular Broadcaster
We can see that the broadcaster we have in this scene is set up to broadcast just one track- the music. It uses a generic falloff and a set broadcast radius. The blue circles in the scene are indicators to illustrate the radii of the broadcaster.
Try entering playmode and moving the radio around in the blue area. You'll notice that while it's inside the inner circle, the music track is loud and audible. Once you move it between the inner and outer circles, it starts getting quieter depending on how close to the edge of the outer circle you are. Finally, once you move the radio out of the outer circle, the track is no longer audible.
That explains Broadcasters! Try implementing them with your own tracks by modifying the [[#Affected Tracks]] value on the radio to include any new tracks you create.

Wait, what's that? What the hell is that orange square? Yes! This is our other type of spatial component in Ryle Radio, and is effectively the opposite of a broadcaster. It's called a **RadioInsulator**!

### Insulators
**RadioInsulators** (known usually hereon as insulators) create a cubic area in which a track is *quieter*, rather than louder. Imagine you have a radio station broadcasting a song to a town, but one guy in the town puts his radio into a lead box. Why he has a lead box to begin with is up for debate, but the radio inside the box isn't going to hear the song because the lead insulates it from radio waves. 
This is just like how they work in Ryle Radio. An insulator has the opposite effect to a broadcaster by preventing the track from being audible while an output is inside the assigned area. As such, now that we know how broadcasters work, it'll be a lot easier for us to understand insulators.