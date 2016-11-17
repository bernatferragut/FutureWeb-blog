---
layout: post
title: "VR - Google VR Interaction part2"
description: "Head Rotation and Gaze"
date: 2016-11-17
tags: [design, virtual reality, googleVR]
comments: true
share: true
---

### THE CENTER OF VR INTERACTION

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

## GAZE INPUT

> When using Gaze we mean the IGvrGazeResponder System which incorporates the following functions:

1. OnGazeEnter()
2. OnGazeExit()
3. OnGazeTrigger()

Here as an example the code to change the color of a cube on Enter/Exit and Playing an animation on Tigger"

'''

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
  
'''
