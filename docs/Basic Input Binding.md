---
tags:
  - csharp
---
# Basic Input Binding
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Movement : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        ProcessThrust();
        ProcessRotation();
    }

    private void ProcessThrust()
    {
        if (Input.GetKey(KeyCode.Space))
        {
            Debug.Log("Space Key - Thrust");
        }

    }

    private void ProcessRotation()
    {
        if (Input.GetKey(KeyCode.A))
        {
            Debug.Log("A - Rotate Left");
        }
        else if (Input.GetKey(KeyCode.D))
        {
            Debug.Log("D - Rotate Right");
        }
    }
}

```


