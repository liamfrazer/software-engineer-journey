---
tags:
  - csharp
---
# Caching a Reference

* Caching is a technique of storing frequently used data/information in memory, so that it can easily be accessed when needed.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Dropper : MonoBehaviour

{
    MeshRenderer renderer;
    Rigidbody rigidbody;

    [SerializeField] float timeElapsed = 5f;


    // Start is called before the first frame update
    void Start()
    {
        renderer = GetComponent<MeshRenderer>();
        rigidbody = GetComponent<Rigidbody>();

        renderer.enabled = false;
        rigidbody.useGravity = false;
    }

    // Update is called once per frame
    void Update()
    {
        if (Time.time > timeElapsed)
        {
            renderer.enabled = true;
            rigidbody.useGravity = true;
        }
    }
}

```


