---
layout: post
title: "VR - Google VR Interaction part2"
description: "Head Rotation and Gaze"
date: 2016-11-17
tags: [design, virtual reality, googleVR]
comments: true
share: true
---

## THE CENTER OF VR INTERACTION

![interaction](https://cloud.githubusercontent.com/assets/17754060/20390726/822801fa-aca6-11e6-94d4-781800a38f9b.jpg)

> If we try to achieve de Maximum interaction with the Minimum Input 2 are the main subjects of Study:

1. **HEAD ROTATION**
2. **GAZE**

> We will add the follwing to complete the Minimum Interaction with Google VR

3. GAZE + TIMER
4. TELETRANSPORT
5. AUTOWALK

> These Inputs achieve the following objectives:

A. They are relatively easy to program
B. They are available
C. They work on MOBILE and rea CHEAP
D. Because they are so basic there is still a lot to experiment and study about

### GAZE INPUT

> When using Gaze we mean the IGvrGazeResponder System which incorporates the following functions:

1. OnGazeEnter()
2. OnGazeExit()
3. OnGazeTrigger()

Here as an example the code to change the color of a cube on Enter/Exit and Playing an animation on Tigger"


	public class MovingBolido : MonoBehaviour {

		// Use this for initialization
		void Start () {}

		// Update is called once per frame
		void Update () {}

		// My Functions
		public void OnGazeEnter() {
			//Debug.Log ("Gaze Enter");
			this.GetComponent<Renderer>().material.color = Color.blue;
		}

		public void OnGazeExit() {
			//Debug.Log ("Gaze Exit");
			this.GetComponent<Renderer>().material.color = Color.red;

		}

		public void OnGazeTrigger() {
			/*Animator anim = GetComponent<Animator>();
			anim.Play("Clip1", -1, 0.0f);*/

			this.GetComponent<Animator>().Play("Clip1", -1, 0.0f);

		} 

	}

### GAZE + DELAY (seconds)

> We will have to create 3 different scripts to achieve the results we want

1. GvrReticle > We will add to variables and affect two different functions
2. TimedInputHandler > We will add a new event
3. TimedInputObject > We will fire this event to the object our choice

### GvrReticle Script

	using UnityEngine;
	using UnityEngine.EventSystems;	

	// >>TIMED INPUT<<
	private float gazeStartTime;
	private GameObject gazedAt;

	void Start () {
		CreateReticleVertices();

		materialComp = gameObject.GetComponent<Renderer>().material;

		// >>TIMED INPUT<<
		gazeStartTime = -1;
		gazedAt = null;
  	}

	public void OnGazeStart(Camera camera, GameObject targetObject, Vector3 intersectionPosition,bool isInteractive) {
		SetGazeTarget(intersectionPosition, isInteractive);

		// >>TIMED INPUT<<
		gazedAt = targetObj;
		gazeStartTime = Time.time;
    	}

	public void OnGazeStay(Camera camera, GameObject targetObject, Vector3 intersectionPosition,bool isInteractive) {
		SetGazeTarget (intersectionPosition, isInteractive);

		// >>TIMED INPUT<<
		if (gazedAt != null && gazeStartTime > 0f) {
			if (Time.time - gazeStartTime > 3.0f && ExecuteEvents.CanHandleEvent <TimedInputHandler> (gazedAt)) 			{
				gazeStartTime = -1f;
				ExecuteEvents.Execute (gazedAt, null, (TimedInputHandler handler, BaseEventData data) => 	handler.HandleTimedInput ());
			}
		}
	}

### Timed Input Handler

	using UnityEngine;
	using System.Collections;
	using UnityEngine.EventSystems;

	public interface TimedInputHandler : IEventSystemHandler {
		// >>TIMED INPUT<<
		void HandleTimedInput();
	}

### Timed Input Object

	using UnityEngine;
	using System.Collections;

	public class TimedInputObject : MonoBehaviour, TimedInputHandler {

		// Use this for initialization
		void Start () {
			GetComponent<Renderer> ().material.color = Color.black;
		}
		
		// Update is called once per frame
		void Update () {}

		// We inherit from the Interface
		public void HandleTimedInput(){
			GetComponent<Renderer> ().material.color = Color.red;
		}

	}
