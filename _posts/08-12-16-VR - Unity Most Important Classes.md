---
layout: post
title: "VR - Unity:  The Big 3 Classes"
description: "The Important Classes in Unity: 1. MonoBehaviour"
date: 2016-12-08
tags: [design, virtual reality, googleVR, unity]
comments: true
share: true
---

## Unity: Important Classes

> Important Classes:

1. MonoBehaviour
2. GameObject
3. Transform
4. // Rigigbody

These are some of the most important classes you'll be using 
when scipting with unity. They cover some of the core areas of Unity's game
scriptable systems and provide a good starting point for looking to Update
which functions and events are available.

[Unity Classes API](https://docs.unity3d.com/Manual/ScriptingImportantClasses.html)

### 1.MonoBehaviour

The base class for all new Unity scripts, the MonoBehaviour
reference provides you with a list of all the functions and 
events that are available to standard scripts attached to 
Game Objects. Start here if you’re looking for any kind of 
interaction or control over individual objects in your game.

### 2.GameObject

GameObjects are the fundamental objects in Unity that represent 
characters, props and scenery. They do not accomplish much in 
themselves but they act as containers for Components, which 
implement the real functionality.

### 3.Transform

Every Game Object has a position, rotation and scale in space 
(whether 3D or 2D), and this is represented by the Transform 
component. As well as providing this information, the transform 
component has many helpful functions which can be used to move, 
scale, rotate, reparent and manipulate objects, as well as 
converting coordinates from one space to another.

### 4.RigidBody // Extra

For most gameplay elements, the physics engine provides the 
easiest set of tools for moving objects around, detecting 
triggers and collisions, and applying forces. The Rigidbody 
class (or its 2D equivalent, Rigidbody2D) provides all the 
properties and functions you’ll need to play with velocity, 
mass, drag, force, torque, collision and more.

## 1.MonoBehaviour // Inherits from: Behaviour

### Description

MonoBehaviour is the base class from which every Unity script 
derives.

When you use C#, you must explicitly derive from MonoBehaviour. 
When you use UnityScript (a type of JavaScript), you do not have to 
explicitly derive from MonoBehaviour.

Note: There is a checkbox for disabling MonoBehaviour on the Unity Editor; 
it disables Start(), Awake(), Update(), FixedUpdate(), and OnGUI() from executing 
when unticked. If none of these functions are present in the script, the Editor does 
not display the checkbox.

### Variables

1. runInEditMode
> Allow a specific instance of a MonoBehaviour to run in edit mode (only available in the editor).

2. useGUILayout
> Disabling this lets you skip the GUI layout phase.
