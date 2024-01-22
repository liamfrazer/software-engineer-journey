---
tags:
  - csharp
---
# Using GetComponent

![[Pasted image 20240122202542.png]]

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectHit : MonoBehaviour
{
    private void OnCollisionEnter(Collision collision)
    {
        Debug.Log(collision.gameObject.name + " bumped into a wall.");
        GetComponent<MeshRenderer>().material.color = Color.red; // <--- Change the color of the cube>
    }
}

```




