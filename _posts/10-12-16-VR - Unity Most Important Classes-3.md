---
layout: post
title: "VR - Unity:  The Big 3 Classes"
description: "The Important Classes in Unity: 3. Transform"
date: 2016-12-10
tags: [design, virtual reality, googleVR, unity]
comments: true
share: true
---

## 3.Transform 

### Description

Position, rotation and scale of an object.

Every object in a scene has a Transform. 
It's used to store and manipulate the position, rotation and scale of the object. 
Every Transform can have a parent, which allows you to apply position, 
rotation and scale hierarchically. 
This is the hierarchy seen in the Hierarchy pane. 
They also support enumerators so you can loop through children using:

```ruby
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour {
    void Example() {
        foreach (Transform child in transform) {
            child.position += Vector3.up * 10.0F;
        }
    }
}
```
### Variables

1.childCount

> The number of children the Transform has.

2.eulerAngles

> The rotation as Euler angles in degrees.

3.forward	

> The blue axis of the transform in world space.

4.hasChanged	

> Has the transform changed since the last time the flag was set to 'false'?

5.localEulerAngles	

> The rotation as Euler angles in degrees relative to the parent transform's rotation.

6.localPosition	

> Position of the transform relative to the parent transform.

7.localRotation	

> The rotation of the transform relative to the parent transform's rotation.

8.localScale	

> The scale of the transform relative to the parent.

9.localToWorldMatrix	

> Matrix that transforms a point from local space into world space (Read Only).

10.lossyScale	

> The global scale of the object (Read Only).

11.parent	

> The parent of the transform.

12.position	

> The position of the transform in world space.

13.right	

> The red axis of the transform in world space.

14.root	

> Returns the topmost transform in the hierarchy.

15.rotation	

> The rotation of the transform in world space stored as a Quaternion.

16.up	

> The green axis of the transform in world space.

17.worldToLocalMatrix	

> Matrix that transforms a point from world space into local space (Read Only).

