---
layout: post
title: "VR - Google VR Interaction part4"
description: "AutoWalk"
date: 2016-11-22
tags: [design, virtual reality, googleVR]
comments: true
share: true
---
## GvrView and AutoWalk Setup

![maze2](https://cloud.githubusercontent.com/assets/17754060/20543151/3747bc5a-b0db-11e6-9a4f-7d9e558dc318.png)

> There are several way we can achieve the AutoWalk behaviour inside the Google VR SDK.

1. **Method 1** 

> Autowalks follows the head movement and stops when it looks at the floor.

      using UnityEngine;
      using Syste.Collections;

      public class WalkController : MonoBehaviour
      {
          private bool walking = true;
          private vector3 startingPoint;

          void Start()
          {
              startingPoint = transform.position;
          }

          void Update()
          {
              if (walking)
              {
                  transform.position = transform.position + Camera.main.transform.forward * .5f * Time.deltaTime;
              }

              if (transform.position < -10f)
              {
                  Ray ray = Camera.main.ViewportPointToRay ( new vector3(.5f, .5f, 0));
                  RayCastHit hit;
              }
              if (Physics.Raycast (ray, out hit))
              {
                  if (hit.collider.name.Contains("plane"))
                  {
                      walking = false;
                  } 
                  else 
                  {
                      walking = true;
                  }
              }

          }

      }
