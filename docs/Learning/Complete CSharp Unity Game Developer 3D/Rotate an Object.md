---
tags:
  - csharp
---
# Rotate an Object

![[Pasted image 20240123205021.png]]

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Spinner : MonoBehaviour
{

    [SerializeField] float rotationSpeed = 100f;
    Transform spinner;

    // Update is called once per frame
    void Update()
    {
        spinner = GetComponent<Transform>();
        spinner.Rotate(0, Time.deltaTime * rotationSpeed, 0);
    }
}
```


