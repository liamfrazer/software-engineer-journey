---
tags:
  - csharp
  - SerializedField
  - Unity
---
# Using SerializedField
* Changing a value in the inspector doesn't change the value within the script

![[Pasted image 20240113163809.png]]

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Mover : MonoBehaviour
{
    [SerializeField] float xValue = 0.00f;
    [SerializeField] float yValue = 0.00f;
    [SerializeField] float zValue = 0.00f;

    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        transform.Translate(xValue, yValue, zValue);
    }
}

```




