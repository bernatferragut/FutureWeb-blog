---
layout: post
title: "VR-Interaction-Part4"
description: "AutoWalk"
date: 2016-11-22
tags: [design, virtual reality, googleVR]
comments: true
share: true
---
## GvrView and AutoWalk Setup

![interaction](https://cloud.githubusercontent.com/assets/17754060/20390726/822801fa-aca6-11e6-94d4-781800a38f9b.jpg)

> There are several way we can achieve the AutoWalk behaviour inside the Google VR SDK.

1. **Method 1**

      // AutoWalk any direction your head is heading
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
                      walking = true;x
                  }
              }

          }

      }
