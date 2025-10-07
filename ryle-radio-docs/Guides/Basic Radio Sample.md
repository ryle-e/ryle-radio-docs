This sample is a basic demo intended to illustrate how a radio could be laid out, using all three default track types.

---
## Accessing the sample
First, install the sample through Unity's Package Manager. Navigate to `RyleRadio/Samples/BasicRadio`, and open `MainScene`. It should look like this: ![[Pasted image 20251002182350.png]]

## Description
### Scene
The scene is very simple, just containing some scene objects, some UI, and an object named Radio, which itself only has a RadioOutput (and its required AudioSource). 
![[Pasted image 20251002182945.png]]
Double click on the link to MainData at the bottom- this will take you to the most important part of the radio :)

![[Pasted image 20251007134404.png]]
This is our an example of a RadioData object. This is where the content played by any output for this radio is defined- basically where you tell the radio what it is and how it works.

A RadioData contains two parts- the advanced settings (which we will touch on later) and the list of Tracks- the latter of which we should talk about in its own section, as it's pretty much the only reason we have a RadioData object to begin with.
### An average Track
The tracks in a RadioData are the different sets of audio it will play during runtime, depending on what tune you've provided to it. Tracks come in different types, but each contain some common values. Let's have a closer look at what a track contains :)
![[Pasted image 20251007134919.png]]
#### ID
The ID of a Track is an identifier used whenever you're choosing a specific track for something. For example, if you want to set up an object to broadcast a track in a specific area, you need to somehow choose which track to broadcast, right? The ID is how you tell the difference between tracks.
There's no set naming convention for tracks- I've used a really simple one here to show that this track plays music, old music, and is the first one that does so. You can set it up however you want, but I would generally recommend using something unique for each track unless you know what you're working with.
#### Range
The Range of a track is the domain of tunes where the track is playing. That is, if an Output has its tune within the range listed in this track, it will play the track. Range is by default locked between 0 and 1000, but this is (kind of) flexible. You can adjust a const value in RadioData to adjust it.
In this case, our track can only be heard when the user is at a tune between 33.2 and 246. Any Output with a tune value in this range will be able to hear it.

This is, however, heavily influenced by the Gain curve.
#### Gain curve
The gain curve controls how high the gain on the track is when it's within the defined Range. If the curve is flat, a song will have the same volume at any tune within its range- but a bell curve would taper off the more distant the tune. Check out [[(Predicted) Common Issues and Questions#What does the **Gain curve** do?|What does the Gain curve do?]] for a better explanation!
In this example, the gain curve is a hill shape- it means that the volume of the track will smoothly rise and fall depending on where in the range an Output's tune value is. This sounds consistent and balanced when changing tune over time.
#### Gain
The gain slider controls how loud the track is. The higher the gain, the louder the track. Simple!
To be more technical, the gain is the first thing applied to the track when calculating its output volume. If you want to change the volume of a track without modifying the track itself, this is your first target.
The gain on this particular track is fairly high- this is because the track, by default, is pretty quiet.
#### Attenuation
To explain attenuation, we need to introduce **Track priority**. Track priority is extremely simple- it's the order of the tracks in the RadioData. The track at the top of the list is highest priority, the track at the bottom is lowest. Giving it a separate name probably talks it up too much lol
Attenuation makes a track lower in volume when a higher priority track is playing. This is especially useful for background tracks or static, making them quieter when a song or other track starts playing over the top. The higher the attenuation value, the quieter the track gets.
On this particular track, the attenuation is set to 0. The track is the highest priority in the radio as well, so turning up attenuation would do nothing.

*Note: If anyone needs more complex attenuation layering, [[Contact|let me know]]! I've been debating adding attenuation layers(???), but I'm not sure if they're worth the effort if they'd never be used lol. For the moment, direct order priority works well :)*
#### Force global
For the moment, keep this ticked. This setting is explained further in [[Spatial Components Sample]].
#### Play on Init
Whether or not the track will start playing as soon as the game starts. More often than not, you'll be leaving this ticked- as we do on this particular example.
#### Track Type
This is where you select the content of the tracks. We'll have a closer look at this in a moment :)

### Specific tracks
Let's first look at what **Track types** are, and what they mean.

The track type defines the content of a particular track. When clicked on, you will see a dropdown listing a few different options:
- A track set to **Audio Clip** will allow you to specify an audio file that it will play. This is the most common choice.
- A track set to **Procedural** will allow you to generate new audio at runtime, such as static noise or a single tone. Useful for adding depth and complexity to a radio.
- A track set to **Station aka Multi-select** contains more tracks, and switches between them over time.
On this sample radio, there's at least one track of each type. Let's go over them!
#### music_old1 / music_old2 / music_new1 / music_new2
These are singular songs that play on the radio- they're the primary track that should be playing over everything else- the important audio, if you will.
- Their **IDs** provide some identification as to what each type of audio each track plays, and how "old" the tracks sound (sorry guys).
- Their **Ranges** are all different, and non-overlapping- this means that when tuning along the radio, they can all be heard at different times.
- Their **Gain curves** are all the same- smoothly fading the volume of each track in and out depending on the Output's tune.
- Their **Gain** values all depend on the specific track- some clips are quieter than others, so we give them a higher gain.
- Their **Attenuations** are all 0- they are the highest-priority audio, and every other track should be getting quieter when it plays- not the other way around. Therefore, we keep attenuation at 0.
- **Force global** is always true for this sample.
- **Play on Init** is also always true- we want this radio to play from the game's start.
- Their **Track types** are all **Audio Clip**. This means that every track uses a specific AudioClip that contains a different song. We can easily change which song each track plays just like a normal Unity AudioSource- try it yourself!
#### station_sfx
This is an example of a **Station**- a track that contains other tracks. In this case, we have a station that plays some 