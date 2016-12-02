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

```ruby
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

```ruby
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

```ruby
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

```ruby
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

```ruby
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

```ruby
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

```ruby
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

```ruby
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
