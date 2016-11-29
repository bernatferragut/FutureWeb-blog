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

![raycast](https://cloud.githubusercontent.com/assets/17754060/20708944/cbe4bde0-b608-11e6-998e-a75763118da7.png)

# Physics.Raycast

### Description 1

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

### Notes

If you move Colliders from scripting or by animation, you need to allow at least one FixedUpdate to be executed so that the physics library can update before a Raycast will hit the Collider at its new position.

### Parameters

**Origin**:                       The starting point of the ray in world coordinates. 

**Direction**:                    The direction of the ray. 

**HitInfo**:                      If true is returned, hitInfo will contain more information about where the collider was hit (See Also: RaycastHit).

**MaxDistance**:                  The max distance the ray should check for collisions.  

**LayerMask**:                    A Layer mask that is used to selectively ignore colliders when casting a ray. 

**QueryTriggerInteraction**:      Specifies whether this query should hit Triggers. 


### Returns

> bool True when the ray intersects any collider, otherwise false.

### Description 2

Casts a ray against all colliders in the scene and returns detailed information on what was hit.

This example reports the distance between the current object and the reported Collider:

      using UnityEngine;

      public class RaycastExample : MonoBehaviour
      {
          public Missile missile;

          void FixedUpdate()
          {
              RaycastHit hit;

              if (Physics.Raycast(transform.position, -Vector3.up, out hit))
                  print("Found an object - distance: " + hit.distance);
          }
      }

### Description 3

Same as above using ray.origin and ray.direction instead of origin and direction.

This example draws a line along the length of the Ray whenever a collision is detected:

      using UnityEngine;

      public class ExampleClass : MonoBehaviour 
      {
          void Update() 
          {
              Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
              RaycastHit hit;

              if (Physics.Raycast(ray, out hit, 100)) 
                  Debug.DrawLine(ray.origin, hit.point);
          }
      }

### Description 4

In this case, the when the ray hits an object, we take the name of the collided object and make it appear 
in a 3D TextMesh for Visual representation. ( This example is made by myself for the Planets .apk VR game )

      using UnityEngine;
      using System.Collections;

      public class RayCasting2 : MonoBehaviour {

            // Initialize varaibles

            public string objectCollided;
            public TextMesh textMessage;

            void Start () 
            {
                  textMessage = GameObject.Find("TextPanel").GetComponent<TextMesh> ();
                  textMessage.text = "nothing";
            }

            // We RayCast

            public void FixedUpdate() 
            {
                  RaycastHit hit; // the one who stores hit info - very important !!!
                  Vector3 origin = transform.position;
                  Vector3 direction = transform.TransformDirection(Vector3.forward);
                  Ray myRay = new Ray (origin, direction);

                  //If we collide we announce the object collided to the Console and to a 3DText

                  if (Physics.Raycast (myRay, out hit, 100f)) 
                  {
                        objectCollided = hit.collider.gameObject.name;

                        print (objectCollided); // == Debug.Log in Console

                        textMessage.text = objectCollided; // printing to the 3D Text.TextMesh.text
                  } 
                  else 
                  {
                        textMessage.text = "nothing"; // printing to the 3D Text.TextMesh.text
                  }
            }

      }
