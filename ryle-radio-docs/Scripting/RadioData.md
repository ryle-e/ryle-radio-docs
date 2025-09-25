This is the data object on which the whole radio is based, containing the tracks that are played at runtime.

***Note:** I generally refer to this object as just "the radio" throughout these docs.*

## Usage
To create a `RadioData`, select `Assets/Ryle Radio/RadioData` in files. Add an item to the list of [[RadioTrackWrapper|tracks]], and start setting up your radio! If you like, you can also modify gizmo colours of components that reference this radio.

To use this radio in a game scene, you need to have a [[RadioListener]] to play it out loud. This listener links to a Unity AudioSource (although this [[RadioListener#Possible future expansion|could be extended]]), and plays according to a [[RadioListener#Tune|Tune]] value (see [[RadioTrackWrapper#Range|the range value on a track]]). You can have as many Listeners as you like, playing in any different areas (see [[RadioListener#Multiple Listeners|Multiple Listeners]]).

---
## Inspector Values
### Tracks
[[RadioTrackWrapper|Tracks]] are the backbone of your radio, they're where you supply information about what audio your radio produces. To create one, you simply add to the `Tracks` list in the RadioData inspector. You can then assign values information such as [[RadioTrackWrapper#ID|an ID]], [[RadioTrackWrapper#Gain|gain]], etc.

Most information about tracks are in the [[RadioTrackWrapper]] docs.

### Advanced Settings
#### Gizmo Colours
When a component that references this radio has gizmos, e.g [[RadioBroadcaster]]s, the colours defined here are used- this means that if you have several broadcasters, for example, you can easily discern which broadcaster is associated with which radio.

---
## Methods
### Try to Get Track
![[Pasted image 20250925195246.png]]
- Returns bool - whether or not a track has been found
- **idOrName** - the ID or name of the track you're trying to get
- out **trackW** - the track that you have found (if this method returns true- if it returns false, this will be null)
- **useID** - whether you have provided an ID or a name to the method- true if ID, false if name
 
This is the main way you will access tracks in code. If you ever need to change or access any values in a specific track, you simply need to enter its ID or name into this method and store the **trackW** output.

![[Pasted image 20250925195022.png]]
or
![[Pasted image 20250925195105.png]]

### (static) Name to ID

## Variables