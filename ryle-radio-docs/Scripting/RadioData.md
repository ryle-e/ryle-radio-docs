This is the data object on which the whole radio is based, containing the tracks that are played at runtime.

## Usage
To create a `RadioData`, select `Assets/Ryle Radio/RadioData` in files.

Add an item to the list of [[RadioTrackWrapper|tracks]], and start setting up your radio!

If you like, you can also modify gizmo colours of components that reference this radio.
### Tracks
[[RadioTrackWrapper|Tracks]] are the backbone of your radio, they're where you supply information about what audio your radio produces. To create one, you simply add to the `Tracks` list in the RadioData inspector. You can then assign values information such as [[RadioTrackWrapper#ID|an ID]], [[RadioTrackWrapper#Gain|gain]], [[RadioTrackWrapper#Attenuation|attenuation]], and 