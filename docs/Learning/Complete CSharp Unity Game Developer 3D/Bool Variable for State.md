---
tags:
  - csharp
  - Unity
  - state
---
# Bool Variable for State

```c#
    bool isTransitioning;
```

```c#
    private void OnCollisionEnter(Collision collision)
    {
        if (isTransitioning) { return; }

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
```

```c#
    void StartSuccessSequence()
    {
        isTransitioning = true;
        audioSource.Stop();
        // ToDo - Add particle effects
        audioSource.PlayOneShot(onSuccess);
        GetComponent<Movement>().enabled = false;
        Invoke("LoadNextLevel", levelLoadDelay);
    }
```

* As we're resetting the scene on each sequence, we do not have to worry about resetting the isTransitioning to false as first initially set, if we weren't resetting the scene we would have to set this back to false.











