---
tags:
  - csharp
---
# For Iteration Statement
```c#
namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            for (int i = 0; i < 10; i++)
            {
                Console.WriteLine(i);
            }
            Console.ReadLine();
        }
    }
}
```

* Begin by declaring variable `i`
* As long as `i` is less than 10, we will continue to loop through the iteration
* Each time we loop through, we increase the value of `i` by 1

```c#
namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            for (int i = 0; i < 10; i++)
            {
                Console.WriteLine(i);
                if (i == 7)
                {
                    Console.WriteLine("Found seven!");
                    break;
                }
            }
            Console.ReadLine();
        }
    }
}
```
* Within the loop iteration, we're checking for the value of `i`
* Once the value is true, we evaluate the additional code block
* Once that codeblock is evaluated, we then `break` out  of the code.

## Debugging

![[Pasted image 20240106100718.png]]


