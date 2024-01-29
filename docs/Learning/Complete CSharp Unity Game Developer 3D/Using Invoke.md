---
tags:
  - csharp
  - Unity
  - Invoke
---
# Using Invoke

* Using Invoke() allows us to call a method so it executes after a delay of x seconds
* Invoke("MethodName", delayInSeconds);

```c#
using UnityEngine;
using UnityEngine.SceneManagement;

public class CollisionHandler : MonoBehaviour


{

    [SerializeField] float levelLoadDelay = 2f;

    private void OnCollisionEnter(Collision collision)
    {
        switch (collision.gameObject.tag)
        {
            case "Friendly":
                Debug.Log("Friendly collision");
                break;
            case "Finish":
                StartSuccessSequence();
                break;
            default:
                StartCrashSequence();
                break;
        }
    }

    void StartSuccessSequence()
    {
        // ToDo - Add particle effects
        // ToDo - Add sound effects
        GetComponent<Movement>().enabled = false;
        Invoke("LoadNextLevel", levelLoadDelay);
    }

    void StartCrashSequence()
    {
        // ToDo - Add particle effects
        // ToDo - Add sound effects
        GetComponent<Movement>().enabled = false;
        Invoke("ReloadLevel", levelLoadDelay);
    }

    void LoadNextLevel()
    {
        int currentSceneIndex = SceneManager.GetActiveScene().buildIndex;
        int nextSceneIndex = currentSceneIndex + 1;
        if (nextSceneIndex == SceneManager.sceneCountInBuildSettings)
        {
            nextSceneIndex = 0;
        }
            SceneManager.LoadScene(nextSceneIndex);
    }

    void ReloadLevel()
    {
        int currentSceneIndex = SceneManager.GetActiveScene().buildIndex;
        SceneManager.LoadScene(currentSceneIndex);
    }
}

```




