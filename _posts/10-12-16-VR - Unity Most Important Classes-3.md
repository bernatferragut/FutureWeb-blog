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

### Public Functions

1.DetachChildren

> Unparents all children.

2.Find	

> Finds a child by name and returns it.

3.GetChild	

> Returns a transform child by index.

4.GetSiblingIndex	

> Gets the sibling index.

5.InverseTransformDirection	

> Transforms a direction from world space to local space. The opposite of Transform.TransformDirection.

6.InverseTransformPoint	

> Transforms position from world space to local space.

7.InverseTransformVector	

> Transforms a vector from world space to local space. The opposite of Transform.TransformVector.

8.IsChildOf	

> Is this transform a child of parent?

9.LookAt	

> Rotates the transform so the forward vector points at /target/'s current position.

10.Rotate	

> Applies a rotation of eulerAngles.z degrees around the z axis, eulerAngles.x degrees around the x axis, and eulerAngles.y degrees around the y axis (in that order).

11.RotateAround	

> Rotates the transform about axis passing through point in world coordinates by angle degrees.

12.SetAsFirstSibling	

> Move the transform to the start of the local transform list.

13.SetAsLastSibling	

> Move the transform to the end of the local transform list.

14.SetParent	

> Set the parent of the transform.

15.SetSiblingIndex	

> Sets the sibling index.

16.TransformDirection	

> Transforms direction from local space to world space.

17.TransformPoint	

> Transforms position from local space to world space.

18.TransformVector	

> Transforms vector from local space to world space.

19.Translate	

> Moves the transform in the direction and distance of translation.
