---
tags:
  - csharp
---
# if Statements

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Dropper : MonoBehaviour

{
    [SerializeField] float timeElapsed = 5f;


    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Time.time > timeElapsed)
        {
            Debug.Log(timeElapsed + " seconds have passed");
        }
    }
}

```




