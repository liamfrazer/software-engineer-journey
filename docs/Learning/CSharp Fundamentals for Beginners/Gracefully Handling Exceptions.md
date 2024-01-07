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


