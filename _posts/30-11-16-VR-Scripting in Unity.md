---
layout: post
title: "VR - Scripting in Unity"
description: "C# Snippet Compilation of Unity scripting basics"
date: 2016-11-30
tags: [design, code]
comments: true
share: true
---

## Scripting Basics Snippets Guide in 'C#' ##

> **01. Scripts as Behaviours Components**

```c#
using UnityEngine;
using System.Collections;

public class ExampleBehaviourScript : MonoBehaviour
{
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.R))
        {
            GetComponent<Renderer>().material.color = Color.red;
        }
        if (Input.GetKeyDown(KeyCode.G))
        {
            GetComponent<Renderer>().material.color = Color.green;
        }
        if (Input.GetKeyDown(KeyCode.B))
        {
            GetComponent<Renderer>().material.color = Color.blue;
        }
    }
}
```
> **02. Variables and Functions**

```c#
using UnityEngine;
using System.Collections;

public class VariablesAndFunctions : MonoBehaviour
{
    int myInt = 5;

    void Start()
    {
       myInt = MultiplyByTwo(myInt);
       print(myInt);
    }

    int MultiplyByTwo(int number)
    {
        int res;
        res = number * 2;
        return res;
    }
}
```

> **03. Conventions and Syntax**

```c#
using UnityEngine;
using System.Collections;

public class ConventionsAndSyntax : MonoBehaviour
{
    void Start()
    {
        print(transform.position.x);

        if (transform.position.y <= 5f)
        {
            print("I'm about to hit the ground!");
        }
    }
}
```

> **04. IF Statements**

```c#
using UnityEngine;
using System.Collections;

public class IfStatements : MonoBehaviour
{
    float coffeTemperature = 85.0 f;
    float hotLimitTemperature = 70.0 f;
    float coldLimitTemperature = 40.0 f;

    void Update()
    {
        if(Input.GetKeyDown(KeyCode.Space))
            TemperatureTest();

        coffeTemperature -= Time.deltaTime * 5f;
    }

    TemperatureTest()
    {
        if(coffeTemperature > hotLimitTemperature)
        {
            print("Coffee is too hot!");
        }
         if(coffeTemperature < coldLimitTemperature)
        {
            print("Coffee is too cold");
        }
         else
        {
            print("just right!");
        }
    }
}
```

> **05a. For Loop**

```c#
using UnityEngine;
using System.Collections;

public class ForLoop : MonoBehaviour
{
    int numEntities = 3;

    void Start()
    {
        for (int i=0; i<numEntities; i++)
        {
            print("Creating number: " + i);
        }
    }
}
```

> **05b. While Loop**

```c#
using UnityEngine;
using System.Collections;

public class While : MonoBehaviour
{
    int cupInTheSink = 4;

    void Start()
    {
        while(cupInTheSink > 0) 
        {
            print("I've washed a cup!");
            cupInTheSink--;
        }
    }
}
```

> **05c. DoWhile Loop**

```c#
using UnityEngine;
using System.Collections;

public class DoWhile : MonoBehaviour // it will execute only the first time
{
    void Start()
    {
        bool shouldContinue = false;

        do{
            print("Hello World!");
        }
        while( shouldContinue == true);
    }
}
```

> **05d. ForEach Loop**

```c#
using UnityEngine;
using System.Collections;

public class Foreach : MonoBehaviour // Foreach in
{
    void Start()
    {
        string[] strings = new string[3];

        string[0] = "First string";
        string[1] = "Second string";
        string[2] = "Third string";

        Foreach(string item in string)
        {
            print("item");
        }
    }
}
```

> **06. ScopeAndAccessModifiers**

```c#
using UnityEngine;
using System.Collections;

public class ScopeAndAccessModifiers : MonoBehaviour 
{
    public int alpha = 5;

    private int beta = 0;
    private int gamma = 5;

    private AnotherClass myOtherClass();

    void Start ()
    {
        alpha = 29;

        myOtherClass = new AnotherClass();
        myOtherClass.FruitMachine(alpha, myOtherClass.apples);
    }

    void Example (int pens, int crayons)
    {
        int answer;
        answer = pens * crayons * alpha;
        print(answer);
    }

    void Update()
    {
        print("Alpha is set to: " + alpha);
    }
}

// AnotherClass

using UnityEngine;
using System.Collections;

public class AnotherClass
{
    public int apples;
    public int bananas;
    
    
    private int stapler;
    private int sellotape;
    
    
    public void FruitMachine (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Fruit total: " + answer);
    }
    
    
    private void OfficeSort (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Office Supplies total: " + answer);
    }
}
```

> **07. AwakeAndStart**

```c#
using UnityEngine;
using System.Collections;

public class AwakeAndStart : MonoBehaviour
{
    void Awake()
    {
        print("Awake called");
    }
    
    void Start()
    {
        Debug.Log("Start called");
    }
}
```

> **08. UpdateAndFixedUpdate**

```c#
using UnityEngine;
using System.Collections;

public class UpdateAndFixedUpdate : MonoBehaviour
{
    void FixedUpdate() // Called every pshysics Step
    {
        Debug.Log("FixedUpdate time: + Time.deltaTime");
    }

    void Update() // Called update frame
    {
        Debug.Log("Update time: + Time.deltaTime");
    }
}
```

> **09.a Vector3.Angle**

```c#
using UnityEngine;
public class AngleExample : MonoBehaviour
{
	public Transform     target;

	// prints "close" if the z-axis of this transform looks
	// almost towards the target

	void Update ()
	{
		Vector3 targetDir = target.position - transform.position;
		float angle = Vector3.Angle( targetDir, transform.forward );

		if( angle < 5.0f )
			print( "close" );
	}
}
```

> **09.b Vector3.Cross**

```c#
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour 
{
    Vector3 GetNormal(Vector3 a, Vector3 b, Vector3 c) {
        Vector3 side1 = b - a;
        Vector3 side2 = c - a;
        return Vector3.Cross(side1, side2).normalized;
    }
}
```

> **09.c Vector3.Distance**

```c#
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour 
{
    public Transform other;
    void Example() {
        if (other) {
            float dist = Vector3.Distance(other.position, transform.position);
            print("Distance to other: " + dist);
        }
    }
}
```

> **09.d Vector3.Lerp**

```c#
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour 
{
    public Transform startMarker;
    public Transform endMarker;
    public float speed = 1.0F;
    private float startTime;
    private float journeyLength;
    void Start() {
        startTime = Time.time;
        journeyLength = Vector3.Distance(startMarker.position, endMarker.position);
    }
    void Update() {
        float distCovered = (Time.time - startTime) * speed;
        float fracJourney = distCovered / journeyLength;
        transform.position = Vector3.Lerp(startMarker.position, endMarker.position, fracJourney);
    }
}
```

> **10 EnableComponents**

```c#
using UnityEngine;
using System.Collections;

public class EnableComponents : MonoBehaviour 
{
    private Light myLight;

    void Start()
    {
        myLight = GetComponent<Light>;
    }

    void Update()
    {
        if(Input.GetKeyDown(KeyCode.Space))
        {
            myLight.enabled = !myLight.enabled; // switch
        }
    }
}
```

> **11. ActiveObjects**

```c#
using UnityEngine;
using System.Collections;

public class ActiveObjects : MonoBehaviour 
{
    void Start()
    {
        gameObject.SetActive(false);
    }
}

using UnityEngine;
using System.Collections;

public class CheckState : MonoBehaviour 
{
    public GameObject myObject;
    
    void Start()
    {
        Debug.Log("Active Self: " + myObject.activeSelf);
        Debug.Log("Active in Hierarchy" + myObject.activeInHierarchy);
    }
}
```
> **12. TransformFunctions**

```c#
using UnityEngine;
using System.Collections;

public class TransformFunctions : MonoBehaviour 
{
    public float moveSpeed = 10f;
    public float turnSpeed = 50f;

    void Update()
    {
        if(Input.GetKey(KeyCode.UpArrow))
            transform.Translate(Vector3.forward * moveSpeed * Time.deltaTime);

        if(Input.GetKey(KeyCode.DownArrow))
            transform.Translate(Vector3.down * moveSpeed * Time.deltaTime);

        if(Input.GetKey(KeyCode.LeftArrow))
            transform.Rotate(Vector3.up * turnSpeed * Time.deltaTime);

        if(Input.GetKey(KeyCode.RightArrow))
            transform.Rotate(Vector3.up * turnSpeed * Time.deltaTime);      
    }
}
```
> **13. CameraLookAt**

```c#
using UnityEngine;
using System.Collections;

public class CameraLookAt : MonoBehaviour 
{
    public Transform target;

    void Uppdate()
    {
        transform.LookAt(target);
    }
}
```
> **14. LinearInterpolation**

```c#
using UnityEngine;
using System.Collections;

public class LinearInterpolation : MonoBehaviour 
{
    void Uppdate()
    {
        // interpolate between 3 and 5 for 50%
        float result = Mathf.Lerp(3f, 5f, 0.5f);

        Vector3 from = new Vector3(1f, 2f, 3f);
        Vector3 to = new Vector3(5f, 6f, 7f);
    }

    void Uppdate()
    {
        Vector3 from = new Vector3(1f, 2f, 3f);
        Vector3 to = new Vector3(5f, 6f, 7f);

        //Here the result = (4,5,6) > the 75% between points
        Vector3 result = Vector3.Lerp(from, to, 0.75f);
    }

        void Uppdate()
    {
        // from 0f tp 8f by 0.5f - frame depenent ( every frame goes 0.5 closer)
        light.intensity = Mathf.Lerp(light.intesity, 8f, 0.5f);
    }

     void Uppdate()
    {
        // from 0f tp 8f by 0.5f - frame indepenent ( every second goes 0.5 closer)
        light.intensity = Mathf.Lerp(light.intesity, 8f, 0.5f * Time.deltaTime);
    }
```

> **15. Destroy**

```c#
using UnityEngine;
using System.Collections;

public class DestroyBasic : MonoBehaviour 
{
    void Update()
    {
        if(Input.GetKey(KeyCode.Space))
        {
            Destroy(gameObject);
        }
    }
}

public class DestroyOther : MonoBehaviour 
{
    void Update()
    {
        if(Input.GetKey(KeyCode.Space))
        {
            Destroy(other);
        }
    }
}

public class DestroyComponent : MonoBehaviour 
{
    void Update()
    {
        if(Input.GetKey(KeyCode.Space))
        {
            Destroy(GetComponent<MeshRenderer>());
        }
    }
}
```

> **16. KeyInput**

```c#
using UnityEngine;
using System.Collections;

public class KeyInput : MonoBehaviour 
{
    public GUITexture graphic;
    public Texture2D standard;
    public Texture2D downgfx;
    public Texture2D upgfx;
    public Texture2D heldgfx;

    void Start()
    {
            graphic.texture = standard;
    }

    void Update()
    {
        bool down = Input.GetKeyDown(KeyCode.Space);
        bool held = Input.GetKey(KeyCode.Space);
        bool up = Input.GetKeyUp(KeyCode.Space);

        if(down)
        {
            graphic.texture = downgfx;
        }
        else if(held)
        {
            graphic.texture = heldgfx
        }
        else if(up)
        {
            graphic.texture = upgfx
        }
        else
        {
            green.texture = standard
        }

        guiText.text = " " + down + "\n" + up;
    }
}


// BUTTON INPUT

public class ButtonInput : MonoBehaviour
{
    public GUITexture graphic;
    public Texture2D standard;
    public Texture2D downgfx;
    public Texture2D upgfx;
    public Texture2D heldgfx;
    
    void Start()
    {
        graphic.texture = standard;
    }
    
    void Update ()
    {
        bool down = Input.GetButtonDown("Jump");
        bool held = Input.GetButton("Jump");
        bool up = Input.GetButtonUp("Jump");
        
        if(down)
        {
            graphic.texture = downgfx;
        }
        else if(held)
        {
            graphic.texture = heldgfx;
        }
        else if(up)
        {
            graphic.texture = upgfx;
        }
        else
        {
            graphic.texture = standard;
        }
    
        guiText.text = " " + down + "\n " + held + "\n " + up;
    }
}
```

> **17. GetAxis** // mainly dor joysticks

```ruby
using UnityEngine;
using System.Collections;

public class AxisSimple : MonoBehaviour
{
    public float range;
    public guiText textOutput;

    void Update()
    {
        float h = Input.GetAxis("Horizontal");
        float xPos = h * range;

        transform.position = new Vector3 (xPos, 2f, 0);
        textOutput.text = "Value Returned: " + h.ToString("F2");
    }
}

using UnityEngine;
using System.Collections;

public class AxisRawExample : MonoBehaviour
{
    public float range;
    public guiText textOutput;

    void Update()
    {
        float h = Input.GetRaw("Horizontal");
        float xPos = h * range;

        transform.position = new Vector3 (xPos, 2f, 0);
        textOutput.text = "Value Returned: " + h.ToString("F2");
    }
}

```
