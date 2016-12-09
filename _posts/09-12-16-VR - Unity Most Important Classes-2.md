---
layout: post
title: "VR - Unity:  The Big 3 Classes"
description: "The Important Classes in Unity: 2. GameObjects"
date: 2016-12-09
tags: [design, virtual reality, googleVR, unity]
comments: true
share: true
---

## 2.Transform 

### Description

GameObjects are the fundamental objects in Unity that represent characters, 
props and scenery. They do not accomplish much in themselves but they act as 
containers for Components, which implement the real functionality.


### Variables

1.activeInHierarchy

> Is the GameObject active in the scene?

2.activeSelf	

> The local active state of this GameObject. (Read Only)

3.isStatic	

> Editor only API that specifies if a game object is static.

4.layer	

> The layer the game object is in. A layer is in the range [0...31].

5.scene	

> Scene that the GameObject is part of.

6.tag	

> The tag of this game object.

7.transform	

> The Transform attached to this GameObject. (null if there is none attached).


### Constructors

1.GameObject	

> Creates a new game object, named name.


### Public Functions

1.AddComponent	

> Adds a component class named className to the game object.

2.BroadcastMessage	

> Calls the method named methodName on every MonoBehaviour in this game object or any of its children.

3.CompareTag	

> Is this game object tagged with tag ?

4.GetComponent	

> Returns the component of Type type if the game object has one attached, null if it doesn't.

5.GetComponentInChildren	

> Returns the component of Type type in the GameObject or any of its children using depth first search.

6.GetComponentInParent	

> Returns the component of Type type in the GameObject or any of its parents.

7.GetComponents	

> Returns all components of Type type in the GameObject.

8.GetComponentsInChildren	

> Returns all components of Type type in the GameObject or any of its children.

9.GetComponentsInParent	

> Returns all components of Type type in the GameObject or any of its parents.

10.SendMessage	

> Calls the method named methodName on every MonoBehaviour in this game object.

11.SendMessageUpwards	

> Calls the method named methodName on every MonoBehaviour in this game object and on every ancestor of the behaviour.

12.SetActive	

> Activates/Deactivates the GameObject.


### Static Functions

1.CreatePrimitive	

> Creates a game object with a primitive mesh renderer and appropriate collider.

2.Find	

> Finds a game object by name and returns it.

3.FindGameObjectsWithTag	

> Returns a list of active GameObjects tagged tag. Returns empty array if no GameObject was found.

4.FindWithTag	

> Returns one active GameObject tagged tag. Returns null if no GameObject was found.

### Inherited members
#### Variables

1.hideFlags	

> Should the object be hidden, saved with the scene or modifiable by the user?

2.name	

> The name of the object.

### Public Functions

1.GetInstanceID	

> Returns the instance id of the object.

2.ToString	

> Returns the name of the game object.


