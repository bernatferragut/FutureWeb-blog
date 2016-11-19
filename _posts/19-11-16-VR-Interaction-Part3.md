---
layout: post
title: "VR - Google VR Interaction part3"
description: "GAZE + TIMER"
date: 2016-11-19
tags: [design, virtual reality, googleVR]
comments: true
share: true
---

## GAZE + DELAY (seconds)

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

> Altough a very simple method to use, the potential for it is hughe:

1. You do not need a 'controller'
2. It's very intuitive
3. Once understood you can do more things than imagined.
4. Still open to experimentation
