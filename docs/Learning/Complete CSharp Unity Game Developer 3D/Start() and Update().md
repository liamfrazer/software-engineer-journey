---
tags:
  - csharp
  - Unity
---
# Start() and Update()
* Anything within Start() when the script first comes to life and will only be completed once
* Update() controls a script that will be ran each for each frame in the game

* `transform` is accessing the transform of the game object we're currently on
* `Translate` is a built in Unity method 

```c#
    void Start()
    {
        transform.Translate(1, 0, 0);
    }
```

* Moving this to update would run the script above would run on every frame

