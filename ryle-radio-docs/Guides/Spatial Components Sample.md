This sample uses a simpler radio than [[Basic Radio Sample]], but introduces the spatial components- RadioBroadcasters and RadioInsulators.

---
## Accessing the sample
First, install the sample through Unity's Package Manager. Navigate to `RyleRadio/Samples/SpatialComponents`, and open `MainScene`. It should look like this: ![[Pasted image 20251007233425.png]]

## Description
### Scene
The scene is our focus in this sample, unlike in [[Basic Radio Sample|the previous]]. Selecting the Radio object shows a RadioOutput again, this time with a far simpler RadioData linked to it, that simply plays the same track as constant- but this time with one difference: **Force Global** is unticked. 
![[Pasted image 20251007233604.png]] 
Having this option unticked forces us to use spatial RadioBroadcasters for our audio, instead of it being audible everywhere. Let's have a closer look at some objects in the scene for more information.

### Broadcasters
The Broadcaster object contains a couple of child objects- circles, and a single **RadioBroadcaster** component. This component is the first of our spatial components that we use.
![[Pasted image 20251007234023.png]]
A **RadioBroadcaster** creates a spherical area where certain tracks are audible- think radio towers in real life. The closer you are to the tower, the clearer the audio it's broadcasting becomes. It works the same in Ryle Radio, but this time you have far more control over the tower's range, falloff, and broadcasted track! Let's go over the variables on this component.
#### Data
This is a reference to a RadioData object that this broadcaster is linked to. Each broadcaster can only be linked to one radio, so just add more of them if necessary. It needs to be linked in order to choose a track to broadcast- you'll see this pattern a few times from hereon.
#### Affected Tracks
This is a multiselect variable that allows us to choose tracks that are affected by this broadcaster. For example, if we have three different tracks playing music at different tune values, we can broadcast all three at once with this one component!
#### Broadcast Radius
The broadcast radius is the range in which this broadcaster applies. There are two values here, though, as there are two radii we need to know.
The first radius is the "inner radius" of the broadcaster- if an output is within this radius, it will hear the track at maximum broadcast power. The output could be anywhere, but so long as it's within this many units of the broadcaster, it will hear the track.
The second radius is the "outer radius".  If an output is outside of this radius, it will be unable to hear the track- this is therefore the maximum range of the broadcaster. 
If an output is between the inner and outer radii, though, it will be progressively quieter depending on how far between them it is. That is, if you move an output from the inner radius to the outer, it will get progressively quieter until it's eventually inaudible.
#### Distance Falloff
The distance falloff is a curve showing exactly how the track will get quieter when moving between the broadcast radii. It's the shape of the volume between the inner and outer radius. For example, if it's a smooth graph like this, it'll get quieter smoothly when moving between the radii. ![[Pasted image 20251008143627.png]]
For a linear graph like this, it'll get quieter linearly between the radii. ![[Pasted image 20251008143659.png]]
Something like this, though, would mean that an output between the radii would keep the track loud right up until it gets close to the outer radius- at which point it would start getting quieter. ![[Pasted image 20251008143753.png]]

