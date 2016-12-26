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
> **05. Inheritance**

```C#
using UnityEngine;
using System.Collections;

//This is a base class which is
//also known as the parent class
public class Fruit
{
    public string color;

    //This is the first constructor for the Fruit class
    //ans is not inherited by any derived classes.
    public Fruit()
    {
        color = "orange";
        Debug.Log("1st Fruit Constructor Called");
    }

    //This is a second constructor for the fruit class
    //and is not inherited by any derived classes.
    public Fruit(string newColor)
    {
        color = newColor;
        Debug.Log("2nd Fruit Constructor called");
    }

    public void Chop()
    {
        Debug.Log("The" + color + "fruit has been chopped");
    }

    public void SayHello()
    {
        Debug.Log("Hello, I am a fruit");
    }
}

using UnityEngine;
using System.Collections;

//This is the derived class which is
//also known as the Child class.
public class Apple : Fruit
{
    //This is the first constructor for the Apple class.
    //It calls the parent constructor immediately, even
    //before it runs.
    public Apple()
    {
        //Notice how Apple has access to the public variable
        //color, which is a part of the Fruit Class.
        color = "red";
        Debug.Log("first Apple constructor called);
    }


    //This is the second constructor for the Apple class.
    //It specifies which parent constructor will be called
    //using the "base" keyword.
    public Appl(string newColor) : base(newColor)
    {
        //Notice how this constructor does not set the color
        //since the base constructor sets the coloe that 
        //is passed as an arguments.
        Debug.Log("2nd Apple Constructor Called");
    }
}

using UnityEngine;
using System.Collections;

public class FruitSalad : MonoBehaviour
{
    void Start()
    {
        //Let's illustrate inheritance with the
        //default constructors.
        Debug.Log("Creating a Fruit");
        Fruit myFruit = new Fruit();
        Debug.Log("Creating the Apple");
        Apple myApple = new Apple();

        //Call the methods on the Fruit class.
        myFruit.SayHello();
        myFruit.Chop();

        //Now let's illustrate inheritance with the 
        //constructors that read in a string.
        Debug.Log("Creating the fruit");
        myFruit = new Fruit("yellow");
        Debug.Log("Creating the apple");
        myApple = new Apple("green");
        
        //Call the methods of the Fruit class.
        myFruit.SayHello();
        myFruit.Chop();

        //Call the methods of theh Apple class.
        //Notice how class Apple has access to all
        //of the public methods of class Fruit.
        myApple.SayHello();
        myApple.Chop();

        //Call the methods of the Apple class.
        //Notice how ckass Apple has access to all
        //of the public methods of the class Fruit.
        myApple.SayHello();
        myApple.Chop();
    }
}
```

> **06. Polymorphism**

```C#
using UnityEngine;
using System.Collections;

public class Fruit 
{
    public Fruit()
    {
        Debug.Log("1st Fruit Constructor Called");
    }
    
    public void Chop()
    {
        Debug.Log("The fruit has been chopped.");     
    }
    
    public void SayHello()
    {
        Debug.Log("Hello, I am a fruit.");
    }
}

using UnityEngine;
using System.Collections;

public class Apple : Fruit 
{
    public Apple()
    {
        Debug.Log("1st Apple Constructor Called");
    }
    
    //Apple has its own version of Chop() and SayHello(). 
    //When running the scripts, notice when Fruit's version
    //of these methods are called and when Apple's version
    //of these methods are called.
    //In this example, the "new" keyword is used to supress
    //warnings from Unity while not overriding the methods
    //in the Apple class.
    public new void Chop()
    {
        Debug.Log("The apple has been chopped.");     
    }
    
    public new void SayHello()
    {
        Debug.Log("Hello, I am an apple.");
    }
}

using UnityEngine;
using System.Collections;

public class FruitSalad : MonoBehaviour
{
    void Start () 
    {
        //Notice here how the variable "myFruit" is of type
        //Fruit but is being assigned a reference to an Apple. This
        //works because of Polymorphism. Since an Apple is a Fruit,
        //this works just fine. While the Apple reference is stored
        //in a Fruit variable, it can only be used like a Fruit
        Fruit myFruit = new Apple();

        myFruit.SayHello();
        myFruit.Chop();
        
        //This is called downcasting. The variable "myFruit" which is 
        //of type Fruit, actually contains a reference to an Apple. Therefore,
        //it can safely be turned back into an Apple variable. This allows
        //it to be used like an Apple, where before it could only be used
        //like a Fruit.
        Apple myApple = (Apple)myFruit;
        
        myApple.SayHello();
        myApple.Chop(); 
    }
}
```
