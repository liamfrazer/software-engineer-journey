---
tags:
  - csharp
---
# Gracefully Handling Exceptions
* We should be pessimistic regarding everything that we cannot control
* Anything that we can't control directly should be treated with suspicion and code should always be created defensively

![[Pasted image 20240107175412.png]]
```c#
using System.Collections;

namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            string content = File.ReadAllText(@"C:\dev\tex.txt");
            Console.WriteLine(content);
            Console.ReadLine();
        }
    }
}
```

```c#
{
    try
    {
        string content = File.ReadAllText(@"C:\dev\tex.txt");
        Console.WriteLine(content);
    }
    catch (Exception ex)
    {
        Console.WriteLine("There was a problem!");
        Console.WriteLine(ex.Message);
    }
    Console.ReadLine();
}
```
```console
There was a problem!
Could not find file 'C:\dev\tex.txt'.
```

![[Pasted image 20240107175952.png]]
* In our example, we can use a `try/catch` statement to work from the most specific cases with the more specific errors, down to a general `Exception` case to ensure it's still captured.










