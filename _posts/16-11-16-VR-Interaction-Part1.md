### Introduction

> From all the parts a VR Project can be built, Interaction is the central spine of any VR Project.
> It's crucial to get it right and to investigate to use it the best possible way.

![vrinteraction](https://cloud.githubusercontent.com/assets/17754060/20348478/fa83a120-abdb-11e6-8b65-d7e0a3fcbb73.png)

## Interaction in VR
> A different way of interacting with virtual objects.

1.  With headset strapped on, it’s hard to look around
2.  Mouse + Keyboard, won’t be the best way to interact

## Easy to Develop

1. **Look Around ( 3D Head Movement )**
2. **Gaze Interaction**
3. GamePad Interaction

## Hard to Develop
> Natural Interaction available now

1. Oculus Touch
2. Vive Controller
3. **Google Daydream**
4. Leap Motion

## Experimental Interaction (DIY)
1. Voice Controller
2. Custom Electronic
3. ? (…)

## A) LOOK AROUND in VR
1. The most basic thing you can do inside VR 
2. Replacing traditionalFPS camera, controlled by mouse, with your head.
3. Results in a natural, immersive experience
4. Used in many VR videos
5. Minimum interaction, but can still produces excellent experience.
** As an example 360 PHOTOS**

## B) GAZE Interaction in VR
1. Using eyes as an input (?)
2. Activating an object by looking at it for a certain period
3. (optional) use Gaze Reticle to help user find its view’s crosshair.

### B.1 GAZE in Google SDK: 
1. Use GvrGaze script
2. in Assets/GoogleVR/Scripts/UI/ GvrGaze Drag it to the Camera
3. Implement IGvrGazePointer and IGvrGaze Responder to INTERACT with the object.

### B.2 Google VR > Unity > Class Reference > Interfaces > 
1. IgvrGazePointer
2. IGvrGazeResponder

> In the next post we will study **Look Around** and **Gaze** in depth
