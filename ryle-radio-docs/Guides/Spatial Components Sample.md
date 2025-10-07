This sample uses a simpler radio than [[Basic Radio Sample]], but introduces the spatial components- RadioBroadcasters and RadioInsulators.

---
## Accessing the sample
First, install the sample through Unity's Package Manager. Navigate to `RyleRadio/Samples/SpatialComponents`, and open `MainScene`. It should look like this: ![[Pasted image 20251007233425.png]]

## Description
### Scene
The scene is our focus in this sample, unlike the previous. Selecting the Radio object shows a RadioOutput again, this time with a far simpler RadioData linked to it, that simply plays the same track as constant- but this time with one difference: **Force Global** is unticked. 
![[Pasted image 20251007233604.png]] 
Having this option unticked forces us to use spatial RadioBroadcasters for our audio, instead of it being audible everywhere. Let's have a closer look at some objects in the scene for more information.

### Broadcaster
The Broadcaster object contains a couple of child objects- circles, and a single **RadioBroadcaster** component. This component is the first of our spatial components that we use.
![[Pasted image 20251007234023.png]]
A **RadioBroadcaster** creates a spherical area where certain tracks are audible- think radio towers in real life. The closer you are to the tower, the clearer the audio it's broadcasting becomes. It works the same in Ryle Radio, but this time you have far more control over the tower's range, falloff, and broadcasted track! Let's go over the variables on this component.
#### Data
This is a reference to a RadioData object that this broadcaster is linked to. Each broadcaster can only be linked to one radio, so just add more components if necessary. It needs to be linked in order to choose a track to broadcast- you'll see this pattern a few times from hereon.
#### Affected Tracks
This is a multiselect variable that allows 