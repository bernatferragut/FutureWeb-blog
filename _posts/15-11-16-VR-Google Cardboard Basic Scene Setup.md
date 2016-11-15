---
layout: post
title: "VR - Google VR Basic Scene Setup"
description: "Google Cardboard Basic Scene Setup"
date: 2016-11-15
tags: [design, virtual reality, googleVR]
comments: true
share: true
---
# SOFTWARE SETUP

1. Download Java SE Development Kit 8 [link](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
Install it.

2. Download Android Studio [link](https://developers.google.com/vr/unity/get-started-android)
Install using the “SDK Tools Only” option.
On some Windows systems, the launcher script does not find where the JDK is installed. If you encounter this problem, you need to set an environment variable indicating the correct location.
Select Start menu > Computer > System Properties > Advanced System Properties. Then open Advanced tab > Environment Variables and add a new system variable JAVA_HOME that points to your JDK folder, for example C:\Program Files\Java\jdk1.8.0_77.

3. Download the Google VR SDK for Unity [link](https://developers.google.com/vr/unity/)

4. Open Unity (working with the Google VR SDK for Unity requires Unity 5.2.1 or later)
Assets> Import Package> ‘GoogleVRForUnity.unitypackage’, uncheck Plugins/iOS and ‘Import’.
Under Project window we will see Assets/GogleVR and Assets/Plugin.

> NOTICE: if the Unity console write about a script error, ignore it and Switch Platform to Android

5. Unity> Build Settings> Android and Texture Compression ETC2 (GLES 3.0)

# UNITY CAMERA BASIC SETUP

1. Create a New Scene

2. Create a Plane and a Cube

3. Project> Assets> GoogleVR> Prefabs> GvrMain DRAG AND DROP in Hierarchy

4. Hierarchy> GvrMain > Head> Main Camera> Inspector> Add Component> Physics Raycaster (NOT THE Physics 2D Raycaster!!!)
The Raycaster raycasts against 3D objects in the scene. This allows messages to be sent to 3D physics objects that implement event interfaces.

5. Delete the old ‘Main Camera’

6. Project> Assets> GoogleVR> Prefabs> UI> GvrReticle, DRAG AND DROP in Hiearchy over Main Camera.

7. Press Play and rotate the camera using ALT + move the mouse without clicking.

# UNITY INPUT SETUP

1. RMB on a empty area in Hierarchy> UI> add an ‘Event System’

2. Event System> Inspector> Add Component> GazeInputModule.cs, gear icon> ‘Move Up’ the component, the correct order is:

Transform
EventSystem (Script)
GazeInputModule (Script)
Standalone InputModule (Script)

3. Cube> Inspector> assign a Green material

4. Cube> Inspector> Add Component> EventTrigger (Script)> ‘Add New Event Type’> Pointer Enter> +> in the Empty Slot DRAG Cube, No Function> MeshRenderer> Material> DRAG a Red material

5. Cube> Inspector> Add Component> EventTrigger (Script)> ‘Add New Event Type’> Pointer Exit> +> in the Empty Slot DRAG Cube, No Function> MeshRenderer> Material> DRAG a Green material

6. Play
 6.1– pointer Enter material changes to Red
 6.2– pointer Exit material changes to Green

7. The interactions detection system flow is:

 a) main Camera/Physics Raycaster + CardboardReticle send rays
 b) rays casts Cube/Box Collider
 c) Cube/Event Trigger sends data to Hierarchy/EventSystem
 d) Hierarchy/EventSystem + Gaze Input Module manages data

> If it does not work check the ‘Physics Raycaster (Script)’ attached to the Main Camera or the Box Collider of the Cube.

# CARDBOARD BUILDING SETUP

1. Google Cardboard

> Player Settings> Virtual Reality support disabled
> GvrMain> GvrViewer (Script)> VR Mode enabled -> this split the camera for Card Board only
> GvrMain> Head> GvrHead (Script)> Track position enabled -> this track position for Card Board only
> GvrMain> Head> GvrHead (Script)> Track rotation enabled -> this track rotation for Card Board only

2. Build Settings: Player settings
> Company Name: MyCompany
> Product Name: CardBoardTest
> Default orientation: Landscape Left
> Multithreaded Rendering: on
> Bundle Identifier: com.mycompany.cardboardtest
> Minimum API Level: Android 4.1 (API Level 16)
> Device Filter: ARMv7
> Android TV Compatibility: off

3. Add the corrent scene to build

4. Build and Play!

5. Assets> Plugins> Android> create a folder ‘assets’, copy here your oculus signature file, generate it using [link](https://developer.oculus.com/osig/)
