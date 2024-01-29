---
tags:
  - csharp
---
# Obstacle hitting bug
* When we push a particular key, we're forcing the rotation
* When hitting another object in the world, the physics system takes over and causes conflicts


```c#
    private void ApplyRotation(float rotationThisFrame)
    {
        rb.freezeRotation = true; // Freezing rotation so we can manually rotate
        transform.Rotate(Vector3.forward * rotationThisFrame * Time.deltaTime);
        rb.freezeRotation = false; // Unfreezing rotation so the physics system can take over
    }
```





