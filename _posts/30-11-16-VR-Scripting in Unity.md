---
layout: post
title: "VR - Scripting in Unity"
description: "C# Snippet Compilation of Unity scripting basics"
date: 2016-11-30
tags: [design, code]
comments: true
share: true
---

## Scripting Basics Snippets Guide in C#

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
