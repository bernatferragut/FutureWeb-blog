---
title: VR
permalink: /vr/
---
> VR Projects

1. Learn and understand VR fundamentals
2. Made with Unity & coded in C#
3. Made with GoogleVr SDK and for Android platform

[3.MAZE](#maze)|[2.PLANETS](#planets)|[1.DISTANCES](#distances)

# Maze

### Objectives

> Move in 3D through a Maze. Find a Key that opens the door to Finish the Experience. Movement through FPV and Waypoints.

![IMAGE](/images/P3.jpg)

### Code

> An example of Interaction design script from the 'Maze'.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Door : MonoBehaviour 
{
	// Create a boolean value called "locked" that can be checked in Update()
	public bool unlocked = false;
	public Vector3 fullyRaised ;
	public GameObject bravo;

	void Update() 
	{
		// If the door is unlocked and it is not fully raised
		// Animate the door raising up

		if (unlocked == true && fullyRaised.y <= 51.0f) // 

		{
			fullyRaised = transform.position;
			fullyRaised.y = fullyRaised.y + Time.deltaTime;
			print ("fullyRaised" + fullyRaised.y);
			transform.position = fullyRaised;
			bravo.SetActive (true);
		}
	}

	public void Unlock()
	{
		// You'll need to set "locked" to true here
		unlocked = true;
	}
}
```

![IMAGE](/images/P3b.jpg)

### Aims

1. Play with physics attched to the Main Camera
2. Move between autowalk and teleport to see the potential effects combining both at the same time
3. Inclusion and experimentation with waypoints to move between certain places where crossing is difficult
4. Apply game logic to go from place to place and taking objects to open doors
5. General Sound / and object especific inclusion
6. Simple Interaction.
7. Fun to play and really immersive because of the maze proportions
8. A positive first moving experience inside VR
9. Important feedback that gives as important clues about how to approach the next projects


# Planets

### Objectives

> Follow the planet's translations in the universe while learning the names of each one orbits around you.

![IMAGE](/images/P2.jpg)

### Code

> An example of Interaction design script from the 'Planets'.

````c#
using UnityEngine;
using System.Collections;

public class UniversalNameChanger : MonoBehaviour 
{
	// Initialize varaibles

	public string objectCollided;
	public TextMesh textMessage;

	void Start () 
	{
		textMessage = GameObject.Find("PlanetNames").GetComponent<TextMesh> ();
		textMessage.text = "Planets";
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
			textMessage.color = new Color(1.0f, 1.0f, 0.8f, 1.0f); // chnage color
		} 
		else 
		{
			textMessage.text = "Planets"; // printing to the 3D Text.TextMesh.text
			textMessage.color = new Color(0.8f, 1.0f, 0.8f, 0.5f); // change color
		}
	}
}

````

![IMAGE](/images/P2b.jpg)

### Aims

1. Insert real textures to the scene.
2. Create sort of photorealism .
3. Inclusion of camera effect LensFlare when looking at the sun.
4. We can see which planet we are looking at when gazing over through a script.
5. Great Immersion.
6. Simple Interaction.
7. You can have real feeling of the distances and proportions of the different planets.
8. More than a game is a learning experience.


# Distances

### Objectives

> Get a first 'feeling' of the 3D filed of view in VR and see which are the best distances to interact with objects.

![IMAGE](/images/P1a.jpg)

### Code

> An example of Interaction design script from the 'Distances'.

```c#
using UnityEngine;
using System.Collections;

public class cubeScript : MonoBehaviour 
{
	//CubeFunction Red
	public void myCubeFunction(){
		//Debug.Log("Hello World!");
		 gameObject.GetComponent<Renderer>().material.color = Color.red;
	}
}
```

![IMAGE](/images/P1b.jpg)

### Aims

1. Presence
2. 3D Positionnement
3. Shapes and Colors
4. Simple Interaction
5. Feedback checkslist 5 Positionnement 6 Distances 7 Sizes and Colors 8 Interaction

