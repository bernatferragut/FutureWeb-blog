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

### Static Functions

1. print	
>Logs message to the Unity Console (identical to Debug.Log).

### Messages

1. Awake	
> Awake is called when the script instance is being loaded.
2. FixedUpdate	
> This function is called every fixed framerate frame, if the MonoBehaviour is enabled.
3. LateUpdate	
> LateUpdate is called every frame, if the Behaviour is enabled.
4. OnAnimatorIK	
> Callback for setting up animation IK (inverse kinematics).
5. OnAnimatorMove	
> Callback for processing animation movements for modifying root motion.
6. OnApplicationFocus	
> Sent to all game objects when the player gets or loses focus.
7. OnApplicationPause	
> Sent to all game objects when the player pauses.
8. OnApplicationQuit	
> Sent to all game objects before the application is quit.
9. OnAudioFilterRead	
> If OnAudioFilterRead is implemented, Unity will insert a custom filter into the audio DSP chain.
10. OnBecameInvisible	
> OnBecameInvisible is called when the renderer is no longer visible by any camera.
11. OnBecameVisible	
> OnBecameVisible is called when the renderer became visible by any camera.
12. **OnCollisionEnter**
> OnCollisionEnter is called when this collider/rigidbody has begun touching another rigidbody/collider.
13. OnCollisionEnter2D	
> Sent when an incoming collider makes contact with this object's collider (2D physics only).
14. OnCollisionExit	
> OnCollisionExit is called when this collider/rigidbody has stopped touching another rigidbody/collider.
15 OnCollisionExit2D	
> Sent when a collider on another object stops touching this object's collider (2D physics only).
16. OnCollisionStay	
>OnCollisionStay is called once per frame for every collider/rigidbody that is touching rigidbody/collider.
17. OnCollisionStay2D	
> Sent each frame where a collider on another object is touching this object's collider (2D physics only).
18. OnConnectedToServer	
> Called on the client when you have successfully connected to a server.
19. OnControllerColliderHit	
> OnControllerColliderHit is called when the controller hits a collider while performing a Move.
20. OnDestroy	
> This function is called when the MonoBehaviour will be destroyed.
21. OnDisable	
This function is called when the behaviour becomes disabled () or inactive.
22. OnDisconnectedFromServer	
> Called on the client when the connection was lost or you disconnected from the server.
23. OnDrawGizmos	
> Implement OnDrawGizmos if you want to draw gizmos that are also pickable and always drawn.
24. OnDrawGizmosSelected	
> Implement this OnDrawGizmosSelected if you want to draw gizmos only if the object is selected.
25. OnEnable	
> This function is called when the object becomes enabled and active.
26. OnFailedToConnect	
> Called on the client when a connection attempt fails for some reason.
27. OnFailedToConnectToMasterServer	
> Called on clients or servers when there is a problem connecting to the MasterServer.
28. OnGUI	
> OnGUI is called for rendering and handling GUI events.
29. OnJointBreak	
> Called when a joint attached to the same game object broke.
30. OnLevelWasLoaded	
> This function is called after a new level was loaded.
31. OnMasterServerEvent	
> Called on clients or servers when reporting events from the MasterServer.
32. OnMouseDown	
> OnMouseDown is called when the user has pressed the mouse button while over the GUIElement or Collider.
33. OnMouseDrag	
> OnMouseDrag is called when the user has clicked on a GUIElement or Collider and is still holding down the mouse.
34. OnMouseEnter	
> Called when the mouse enters the GUIElement or Collider.
35. OnMouseExit	
> Called when the mouse is not any longer over the GUIElement or Collider.
36. OnMouseOver	
> Called every frame while the mouse is over the GUIElement or Collider.
37. OnMouseUp	
> OnMouseUp is called when the user has released the mouse button.
38. OnMouseUpAsButton	
> OnMouseUpAsButton is only called when the mouse is released over the same GUIElement or Collider as it was pressed.
39. OnNetworkInstantiate	
> Called on objects which have been network instantiated with Network.Instantiate.
40. OnParticleCollision	
> OnParticleCollision is called when a particle hits a collider.
41. OnPlayerConnected	
> Called on the server whenever a new player has successfully connected.
42. OnPlayerDisconnected	
> Called on the server whenever a player disconnected from the server.
43. OnPostRender	
> OnPostRender is called after a camera finished rendering the scene.
44. OnPreCull	
> OnPreCull is called before a camera culls the scene.
45. OnPreRender	
> OnPreRender is called before a camera starts rendering the scene.
46. OnRenderImage	
> OnRenderImage is called after all rendering is complete to render image.
47. OnRenderObject	
> OnRenderObject is called after camera has rendered the scene.
48. OnSerializeNetworkView	
> Used to customize synchronization of variables in a script watched by a network view.
49. OnServerInitialized	
> Called on the server whenever a Network.InitializeServer was invoked and has completed.
50. OnTransformChildrenChanged	
> This function is called when the list of children of the transform of the GameObject has changed.
51. OnTransformParentChanged	
> This function is called when the parent property of the transform of the GameObject has changed.
52. OnTriggerEnter	
> OnTriggerEnter is called when the Collider other enters the trigger.
53. OnTriggerEnter2D	
> Sent when another object enters a trigger collider attached to this object (2D physics only).
54. OnTriggerExit	
> OnTriggerExit is called when the Collider other has stopped touching the trigger.
55. OnTriggerExit2D	
> Sent when another object leaves a trigger collider attached to this object (2D physics only).
56. OnTriggerStay	
> OnTriggerStay is called once per frame for every Collider other that is touching the trigger.
57. OnTriggerStay2D	
> Sent each frame where another object is within a trigger collider attached to this object (2D physics only).
58. OnValidate	
> This function is called when the script is loaded or a value is changed in the inspector (Called in the editor only).
59. OnWillRenderObject	
> OnWillRenderObject is called once for each camera if the object is visible.
60. Reset	
> Reset to default values.
61. Start	
> Start is called on the frame when a script is enabled just before any of the Update methods is called the first time.
62. Update	
> Update is called every frame, if the MonoBehaviour is enabled.

### Variables

1. enabled	

> Enabled Behaviours are Updated, disabled Behaviours are not.

2. isActiveAndEnabled	

> Has the Behaviour had enabled called.

3. gameObject	

> The game object this component is attached to. A component is always attached to a game object.
tag	The tag of this game object.

4.transform	

> The Transform attached to this GameObject (null if there is none attached).

5. hideFlags	

> Should the object be hidden, saved with the scene or modifiable by the user?


6. name	

> The name of the object.
