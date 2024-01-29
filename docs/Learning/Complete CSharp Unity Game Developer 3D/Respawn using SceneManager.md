---
tags:
  - csharp
  - Unity
  - SceneManager
---
# SceneManager

![[Pasted image 20240129182608.png]]

```c#
using UnityEngine;
using UnityEngine.SceneManagement;

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
                ReloadLevel();
                break;
            case "Fuel":
                Debug.Log("Fuel collision");
                break;
            default:
                ReloadLevel();
                break;
        }
    }

    void ReloadLevel()
    {
        int currentSceneIndex = SceneManager.GetActiveScene().buildIndex;
        SceneManager.LoadScene(currentSceneIndex);
    }
}
```


