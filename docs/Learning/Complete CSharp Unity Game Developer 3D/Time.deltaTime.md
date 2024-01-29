---
tags:
  - csharp
  - deltaTime
  - Unity
---
# Time.deltaTime

![[Pasted image 20240113165926.png]]
* Depending on CPU speed, this changes how quick the `Update()` class runs
* Using `Time.deltaTime`, Unity can tell us how long each frame took to execute
* When we multiply something by `Time.deltaTime`, it makes our game "frame rate independent"
* The game will behave the same on any PC


```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Mover : MonoBehaviour
{

    [SerializeField] float moveSpeed = 10f;

    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        float xValue = Input.GetAxis("Horizontal") * Time.deltaTime * moveSpeed;
        float zValue = Input.GetAxis("Vertical") * Time.deltaTime * moveSpeed;
        transform.Translate(xValue, 0, zValue);
    }
}

```







