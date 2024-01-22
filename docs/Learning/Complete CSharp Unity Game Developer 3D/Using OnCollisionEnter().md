---
tags:
  - csharp
  - OnCollisionEnter
---
# Using OnCollisionEnter()
```c#
    private void OnCollisionEnter(Collision collision)
    {
        Debug.Log("I collided with " + collision.gameObject.name);
    }
```


* Collision is the type of variable that `collision will be`
* When a player bumps into the wall, we're calling OnCollisionEnter and asking for the information of who collided with me

![[Pasted image 20240122202320.png]]

