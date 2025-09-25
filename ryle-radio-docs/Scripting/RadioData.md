This is the data object on which the whole radio is based, containing the tracks that are played at runtime.

***Note:** I generally refer to this object as just "the radio" throughout these docs.*

## Usage
To create a `RadioData`, select `Assets/Ryle Radio/RadioData` in files. Add an item to the list of [[RadioTrackWrapper|tracks]], and start setting up your radio! If you like, you can also modify gizmo colours of components that reference this radio.

To use this radio in a game scene, you need to have a [[RadioListener]] to play it out loud. This listener links to a Unity AudioSource (although this [[RadioListener#Possible future expansion|could be extended]]), and plays according to a [[RadioListener#Tune|Tune]] value (see [[RadioTrackWrapper#Range|the range value on a track]]). You can have as many Listeners as you like, playing in any different areas (see [[RadioListener#Multiple Listeners|Multiple Listeners]]).

---
## Inspector Variables
### Tracks
[[RadioTrackWrapper|Tracks]] are the backbone of your radio, they're where you supply information about what audio your radio produces. To create one, you simply add to the `Tracks` list in the RadioData inspector. You can then assign values information such as [[RadioTrackWrapper#ID|an ID]], [[RadioTrackWrapper#Gain|gain]], etc.

Most information about tracks are in the [[RadioTrackWrapper]] docs.

### Advanced Settings
#### Gizmo Colours
When a component that references this radio has gizmos, e.g [[RadioBroadcaster]]s, the colours defined here are used- this means that if you have several broadcasters, for example, you can easily discern which broadcaster is associated with which radio.

---
##