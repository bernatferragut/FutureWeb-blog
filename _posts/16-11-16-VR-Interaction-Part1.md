### Introduction

> From all the parts a VR Project can be built, Interaction is the central spine of any VR Project.
> It's crucial to get it right and to investigate to use it the best possible way.

## Interaction in VR
> A different way of interacting with virtual objects.
1.  With headset strapped on, it’s hard to look around
2.  Mouse + Keyboard, won’t be the best way to interact

## Easy to Develop

1. Look Around ( 3D Head Movement )
2. Gaze Interaction
3. GamePad Interaction

Hard to Develop
NATURAL INTERACTION AVAILABLE NOW
- Oculus Touch
- Vive Controller
- Google Daydream
- Leap Motion

EXPERIMENTAL INTERACTION (DIY)
— Voice Controller
- Custom Electronic
- ? (…)

1- Look around in VR
- The most basic thing you can do inside VR 
- Replacing traditionalFPS camera, controlled by mouse, with your head.
- Results in a natural, immersive experience
- Used in many VR videos
- Minimum interaction, but can still produces excellent experience.
*** As an example 360 PHOTOS

2- GAZE Interaction
- Using eyes as an input (?)
- Activating an object by looking at it for a certain period
- (optional) use Gaze Reticle to help user find its view’s crosshair.

2.1 GAZE in Google SDK: 
- Use GvrGaze script
- in Assets/GoogleVR/Scripts/UI/ GvrGaze Drag it to the Camera
- Implement IGvrGazePointer and IGvrGaze Responder to INTERACT with the object.

Google VR > Unity > Class Reference > Interfaces > 
1. IgvrGazePointer
2. IGvrGazeResponder
=================================

THE MOST INTERESTING BECAUSE:
- EASY
- AVAILABLE
- MOBILE and CHEAP ( Google Cardboard )
- BASIC & WORTH the TIME TO STUDY

ARE:
1. HEAD ROTATION
2. GAZE: OnGazeEnter / OnGazeExit / OnGazeTrigger
3. GAZE + TIMER
4. TELETRANSPORT
5. AUTOWALK
