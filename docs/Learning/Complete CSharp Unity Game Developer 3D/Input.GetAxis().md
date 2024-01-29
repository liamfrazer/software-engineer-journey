---
tags:
  - csharp
  - Unity
---
# Input.GetAxis()

![[Pasted image 20240113164821.png]]
![[Pasted image 20240113164849.png]]
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Mover : MonoBehaviour
{

    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        float xValue = Input.GetAxis("Horizontal");
        float zValue = Input.GetAxis("Vertical");
        transform.Translate(xValue, 0, zValue);
    }
}

```


