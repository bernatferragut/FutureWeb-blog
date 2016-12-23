---
layout: post
title: "VR - Scripting in Unity-2"
description: "Intermediate C# Scripting in Unity"
date: 2016-12-22
tags: [virtual reality, unity]
comments: true
share: true
---

## Intermediate Gameplay Scripting Guide in Csharp#

> **01. Properties**

```c#
using UnityEngine;
using System.Collections;

public class Player : MonoBehaviour
{
    //Member variables can be referred to as fields.
    //By Getting or Setting you can make them visible or invisble
    public int Experience;
    {
        get
        {
            //Some other code
            return experience
        }
        set
        {
            //Some other code
            experience = value;
        }
    }

    //Level is property that converts experience
    //points into the level of a player automatically
    public int Level
    {
        get
        {
            return experience/1000;
        }
        set
        {
            experience = value * 1000;
        }
    }
    //This is an example of an autoimplemented property
    public int Health{ get; set;};
}

public class Game : MonoBehaviour
{
    void Start()
    {
        Player mPlayer = new Player();

        //Properties can be used just like variables
        mPlayer.Experience = 5;
        int x = mPlayer.Experience;
    }
}

```

> **02. TernaryOperator**

```c#
using UnityEngine;
using System.Collections;

public class TernaryOperator : MonoBehaviour
{
    void Start()
    {
        int health = 10;
        string message;

        //TernaryOperator choose message based on health
        //Similar to IF statements
        message = health>0 ?; "Players is alive" : "Playes is moonkied";
    }
}
```
 > **03. Statics**

```c#
using UnityEngine;
using System.Collections;

public class Enemy
{
   //Static variables are shared across all instances of a class
   public static int enemmyCount = 0;

   public Enemy()
   {
       //Increment the static variable to know how many
       //objects of this class have been created
       enemmyCount++;
   }
}

public class 
{
   public class Game
   {
       void Start()
       {
           Enemy enemy1 = new Enemy();
           Enemy enemy2 = new Enemy();
           Enemy enemy3 = new Enemy();

           //You can access a static varaible by using
           //the class and the dot operator
           int x = Enemy.enemyCount;
       }
   }
}

public class Player : MonoBehaviour
{
   //Static variables are shared across all instances
   //of a class.
   public static int playerCount = 0;

   void Start()
   {
       //Increment the static variable to know how many
       //objects of this class have been created.
       playerCount++;
   }
}

public class PlayerManager : MonoBehaviour
{
   void Start()
   {
       //You can access a static variable using the class
       //name and the dot operator.
       int x = Player.playerCount;
   }
}

public static class Utilities
{
   //A static method can be invoked without an objects
   //of a class. Note that static methods cannot access
   //non-static member variables.
   public static int(int num1, int num2)
   {
       return num1 + num2;
   }
}

public class  UtilitiesExample : MonoBehaviour
{
   void Start()
   {
       //You can access a static method by using the class name
       //and the dot operator.
       int x = Utilities.Add(5,6);
   }
}
```
> **03. MethodOverloading**

```c#
using UnityEngine;
using System.Collections;

public class SomeClass
{
    //The first Add method has a signature of
    //"Add(int, int). This signature must be unique.
    public int Add(int num1, int num2)
    {
        return num1 + num2;
    }

    //The second Add method has a signature of
    //"Add(string, string)". Again, this must be unique.
    public string Add(string str1, string str2)
    {
        return str1+str2;
    }
}

public class SomeOtherClass : MonoBehaviour
{
    void Start()
    {
        SomeClass myClass = new SomeClass();//Instantition

        //The specific Add method called will depend on
        //the arguments passed in.
        myClass.Add(1,2);
        myClass.Add("Hello", "Bern");
    }
}
```
> **04. Generics**

```c#
using UnityEngine;
using System.Collections;

public class SomeClass
{
   //Here is a generic method. Notice the generic
   //type"T". This 'T' will be replaced at runtime
   //with an actual type.
   public T GenericMethod<T>(T param)
   {
       return param;
   }
}


using UnityEngine;
using System.Collections;

public class SomeOtherClass : MonoBehaviour 
{
    void Start () 
    {
        SomeClass myClass = new SomeClass();
        
        //In order to use this method you must
        //tell the method what type to replace
        //'T' with.
        myClass.GenericMethod<int>(5);
    }
}

using UnityEngine;
using System.Collections;

//Here is a generic class. Notice the generic type 'T'.
//'T' will be replaced with an actual type, as will also 
//instances of the type 'T' used in the class.
public class GenericClass <T>
{
    T item;
    
    public void UpdateItem(T newItem)
    {
        item = newItem;
    }
}
using UnityEngine;
using System.Collections;

public class GenericClassExample : MonoBehaviour 
{
    void Start () 
    {       
        //In order to create an object of a generic class, you must
        //specify the type you want the class to have.
        GenericClass<int> myClass = new GenericClass<int>();
        
        myClass.UpdateItem(5);
    }
}
```
