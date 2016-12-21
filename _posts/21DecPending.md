---
Not yet Set
---

## Intermediate Gameplay Scripting Guide in Csharp#

> **01. Properties**

```C#
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







