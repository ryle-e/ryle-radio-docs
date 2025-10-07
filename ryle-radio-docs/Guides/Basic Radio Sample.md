This sample is a basic demo intended to illustrate how a radio could be laid out, using all three default track types.

---
## Using the sample
First, install the sample through Unity's Package Manager. Navigate to `RyleRadio/Samples/BasicRadio`, and open `MainScene`. It should look like this: ![[Pasted image 20251002182350.png]]

## Description
### Scene
The scene is very simple, just containing some scene objects, some UI, and an object named Radio, which itself only has a RadioOutput (and its required AudioSource). 
![[Pasted image 20251002182945.png]]
Double click on the link to MainData at the bottom- this will take you to the most important part of the radio :)

![[Pasted image 20251007134404.png]]
This is our an example of a RadioData object. This is where the content played by any output for this radio is defined- basically where you tell the radio what it is and how it works.

A RadioData contains two parts- the advanced settings (which we will touch on later) and the list of Tracks- the latter of which we should talk about in its own section, as it's pretty much the only reason we have a RadioData object to begin with.
### The Tracks
The tracks in a RadioData are the different sets of audio it will play during runtime, depending on what tune you've provided to it. Tracks come in different types, but each contain some common values. Let's have a closer look at one :)
![[Pasted image 20251007134919.png]]
#### ID
The ID of a Track is an identifier used whenever you're choosing a specific track for something. For example, if you want to set up an object to broadcast a track in a specific area, you need to somehow choose which track to broadcast, right? The ID is how you tell the difference between tracks.
There's no set naming convention for tracks- I've used a really simple one here to show that this track plays music, old music, and is the first one that does so. You can set it up however you want, but I would generally recommend using something unique for each track unless you know what you're working with.
#### Range
The Range of a track is the domain of tunes where the track is playing. That is, if an Output has its tune within the range listed in this track, it will play the track. Range is by default locked between 0 and 1000, but this is (kind of) flexible. You can adjust the const value in RadioData to adjust it.

Let's say we have a song that we want to play when the user is at a tune of 500. We would move the center of the range to 500, and extend it on either side depending on how lenient we want the player to be. For example, we could set the minimum tune to 480 and the maximum to 520- this would mean that an Output at 490 can hear the song, as can an Output at 519.9!

This is, however, heavily influenced by the Gain curve.
#### Gain curve
The gain curve controls how high the gain on the track is when it's within the defined Range. If the curve is flat, a song will have the same volume at any tune within its range- but a bell curve would taper off the more distant the tune. Check out [[(Predicted) Common Issues and Questions#What does the **Gain curve** do?|What does the Gain curve do?]] for a better explanation!