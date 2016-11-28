---
layout: post
title: "VR - The Singleton Pattern"
description: "Good habits programming in C#"
date: 2016-11-28
tags: [virtual reality, googleVR, programming]
comments: true
share: true
---
## THE SINGLETON PATTERN

![interaction](https://cloud.githubusercontent.com/assets/17754060/20390726/822801fa-aca6-11e6-94d4-781800a38f9b.jpg)

### Context

> If You are building an application in C#. You need a class that has only one instance, 
and you need to provide a global point of access to the instance. The Singleton Pattern is the way to go.

1. EASIEST PATTERN TO LEARN
4. PROVIDES ONE INSTANCE THAT HANDLES THE LOGIC
5. EASY TO IMPLEMENT AND MANTAIN

### Implementation Strategy in C# (.Net Framework)

> Even though Singleton is a comparatively simple pattern, there are various tradeoffs and options, 
depending upon the implementation. 

The following implementation of the Singleton design pattern follows the solution presented in Design Patterns: Elements of Reusable Object-Oriented Software [Gamma95] but modifies it to take advantage of language features available in C#, such as properties:
 

    using System;

    public class Singleton
    {
       private static Singleton instance;

       private Singleton() {}

       public static Singleton Instance
       {
          get 
          {
             if (instance == null)
             {
                instance = new Singleton();
             }
             return instance;
          }
       }
    }
 
### This implementation has two main advantages:

Because the instance is created inside the Instance property method, the class can exercise additional functionality (for example, instantiating a subclass), even though it may introduce unwelcome dependencies.

The instantiation is not performed until an object asks for an instance; this approach is referred to as lazy instantiation. Lazy instantiation avoids instantiating unnecessary singletons when the application starts.

The main disadvantage of this implementation, however, is that it is not safe for multithreaded environments. If separate threads of execution enter the Instance property method at the same time, more that one instance of the Singleton object may be created.

### Implementation Strategy inside Unity

> Even though Singleton is a comparatively simple pattern, there are various tradeoffs and options, 
depending upon the implementation. 

The following implementation of the Singleton design pattern follows the solution implemented by 'Pygment Tyrant' on his Youtube Channel:

    using UnityEngine;
    using System.Collections;

    public class Singleton : MonoBehaviour 
    {
    
    private int _currentScore;
    // Here we declare the one and only instance possible called the singleton
    
    public static MainGameManager instance;

    void Awake()
    {	
     instance.this; // Here we create the one and only instance possible called the singleton
    }

      public adjustScore( int num)
      
    {
     _currentScore = _currentScore + num;
    }

    void OnGUI()
    {
      GUI.Label (new Rect (10, 100, 100, 100), "Score = " + _currentScore);
    }
    }

### This implementation advantages inside Unity:

Because Unity forks inside a 'Component Oriented Forklflow', using the Singleton Pattern is very useful:

1. It concentrates the main logic of the Game
2. It avoids dispersing the main logic in tiny pieces
3. Increases performance
4. Facilitates to understand how the Game works


