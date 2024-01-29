---
tags:
  - csharp
  - Unity
---
# Introduction to Method

```c#
void CleanYourRoom()
{
	Things to do;
}
```

* `void` is the return value - void = return nothing
* `CleanYourRoom` is the function name
* `()` is the parameter - () = nothing required

* We can ask for some information to be RETURNED
* We can specify parameters, which are requirements for the function to run

* Parameter is the argument we would be passing into it
* The return is data we're returning from the function

```c#
bool CleanYourRoom(int time)
{
	Things To Do;
	Dealine = time;
	return false;
}
```


* Start() and Update() are called by Unity's internal logic which is taking care of calling them for us at the right time
* Start() and Update() are referred to as callbacks

```c#
	void Start()
   {
       PrintInstructions();
   }
    
    void PrintInstructions()
    {
        Debug.Log("Welcome to the game");
        Debug.Log("Move with WASD or arrow keys");
        Debug.Log("Don't hit the walls");
    }
```

![[Pasted image 20240122201139.png]]





