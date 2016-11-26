---
layout: post
title: "VR - Google VR Interaction part6"
description: "OnGaze - Attach / Release Objects"
date: 2016-11-26
tags: [design, virtual reality, googleVR]
comments: true
share: true
---

## OnGaze - Attach / Release Objects

![screen shot 2016-11-26 at 9 49 49 am](https://cloud.githubusercontent.com/assets/17754060/20641842/3a7ee854-b3d7-11e6-84eb-c162c507b70f.png)

> One of the interesting things we can do when Gazing Objects is Attaching them to the Head Object. This simple action 
will allow us to translate or move objects! When depositing them we can do it smoothly or 'throw' them to the outer space affecting other objects through the laws of physics. ( we can invent the physics too )

1. **HEAD ROTATION**
2. **GAZE**

> We achieve

1. ATTACH OBJECT TO THE HEAD
2. MOVE OBJECTS
5. RELEASE OBJECTS SMOOTHLY OR AS PROJECTILES

> Here the code to achieve it:

    // Attach / Detach an Object to the HEAD Object 

    using UnityEngine;
    using System.Collections;

    public class Attach : MonoBehaviour
    {
      public GvrHead GV; // We create a public var that will allocate the GvrHead
      Transform Head;  // 
      bool secondClick;
      Rigidbody RB;

      [Range ( 1, 50)]
      public float speed;

      void Start()
      {
        Head = GV.transform.GetChild (0); // Here we get the camera transform ( The Child's Head )
        RB = GetComponent <Rigidbody>();
      }

      //Attach
      public void GetObject()
      {
        if (secondClick == false) 
        {
          transform.parent = Head; // // Here we pass the cube's parent transform to the Camera one 
          secondClick = true;
        }
        else 
        {
          transform.parent = null;
          secondClick = false;
          RB.velocity = Head.forward * speed;
        }
      }

    }


