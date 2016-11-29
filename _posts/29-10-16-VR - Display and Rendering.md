---
layout: post
title: "VR - Display and Rendering"
description: "VR Illinois University Class"
date: 2016-10-29
tags: [VR, Engineering]
comments: true
share: true
---
# Raycasting in Unity: The Key to any sort of Interaction

> When facing interaction everythig boills down to one thing: Colliding with something so the interaction can start happening.

Therefore the need to understand in depth how raycasting works in Unity.

# Physics.Raycast

### Description

> Casts a ray, from point origin, in direction direction, of length maxDistance, against all colliders in the scene.

You may optionally provide a LayerMask, to filter out any Colliders you aren't interested in generating collisions with. 

Specifying queryTriggerInteraction allows you to control whether or not Trigger colliders generate a hit, or whether to use the global Physics.queriesHitTriggers setting.

This example creates a simple Raycast, projecting forwards from the position of the object's current position, extending for 10 units.

      using UnityEngine;

      public class ExampleClass : MonoBehaviour 
      {
          void FixedUpdate() 
          {
              Vector3 fwd = transform.TransformDirection(Vector3.forward);

              if (Physics.Raycast(transform.position, fwd, 10)) 
                  print("There is something in front of the object!");
          }
      }

