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

1. activeInHierarchy

> Is the GameObject active in the scene?

2. activeSelf	

> The local active state of this GameObject. (Read Only)

3. isStatic	

> Editor only API that specifies if a game object is static.

4. layer	

> The layer the game object is in. A layer is in the range [0...31].

5. scene	

> Scene that the GameObject is part of.

6. tag	

> The tag of this game object.

7. transform	

> The Transform attached to this GameObject. (null if there is none attached).
