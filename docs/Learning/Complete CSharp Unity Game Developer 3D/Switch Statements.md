---
tags:
  - csharp
  - Unity
  - Switch
---
# Switch Statements


* Switch statements are a conditional like if/else statements
* Switch statements allow us to compare a single variable to a series of constants

```c#
using UnityEngine;

public class CollisionHandler : MonoBehaviour
{
    private void OnCollisionEnter(Collision collision)
    {
        switch (collision.gameObject.tag)
        {
            case "Friendly":
                Debug.Log("Friendly collision");
                break;
            case "Finish":
                Debug.Log("Finish collision");
                break;
            case "Fuel":
                Debug.Log("Fuel collision");
                break;
            default:
                Debug.Log("Enemy collision");
                break;
        }
    }
}
```

![[Pasted image 20240129182257.png]]




