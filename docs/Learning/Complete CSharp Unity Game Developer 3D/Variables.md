---
tags:
  - csharp
---
# Variables

* Variables are like boxes
* Variables help us store, manipulate and refer to information
* Each variable has a name
* Each variable contains data
* Each variable is of a particular type

```c#
int hitPoints = 20;
float speed = 3.8f;
bool isAlive = true;
string myName = "Rick";
```


```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Mover : MonoBehaviour
{
    float xValue = 0.01f;
    float yValue = 0.00f;
    float zValue = 0.00f;

    // Start is called before the first frame update
    void Start()
    {
        transform.Translate(xValue, yValue, zValue);
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}

```





