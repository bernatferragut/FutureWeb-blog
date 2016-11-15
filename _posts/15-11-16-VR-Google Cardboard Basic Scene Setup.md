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

> **D-START USER SETTING AND ENVIRONMENT DESIGN**

  * START USER SETTING AND ENVIRONMENT DESIGN
  * WE INTRODUCE ENVIRONMENT DESIGN
  * WE INTRODUCE 3D MODELLING - DISCOVERY POSTERS - VISUAL DESIGN
  * ELEGANT FLATTENING WINDOW WHEN 3D NOT NEEDED - INCREASE PARALLAX WHEN NEEDED
  * TRANSITIONS + INTERACTIVITY + 3D MODELS
  * MOTION DESIGN
  * LIGHTING + MATERIALS
  * SOUND DESIGN

> **VR FIRST PROCESS WORKFLOW**
