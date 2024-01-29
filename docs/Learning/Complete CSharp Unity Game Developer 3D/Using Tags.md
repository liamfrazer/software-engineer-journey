---
tags:
  - csharp
  - Tags
  - Unity
---
# Using Tags

![[Pasted image 20240123201854.png]]
![[Pasted image 20240123202236.png]]

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Scorer: MonoBehaviour
{
    int score = 0;
    private void OnCollisionEnter(Collision collision)
    {
        if (collision.gameObject.tag != "Hit")
        {
        score++;
        Debug.Log("Obstacle Hits: " + score);
        }
    }
}

```

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectHit : MonoBehaviour
{
    private void OnCollisionEnter(Collision collision)
    {
        if (collision.gameObject.tag == "Player")
        {
            // Debug.Log(collision.gameObject.name + " bumped into a wall.");
            GetComponent<MeshRenderer>().material.color = Color.red; // <--- Change the color of the cube>
            gameObject.tag = "Hit";
        }
    }
}

```






