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
