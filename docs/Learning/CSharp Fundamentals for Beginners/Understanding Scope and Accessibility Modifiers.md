---
tags:
  - csharp
---
# Understanding Scope and Accessibility Modifiers

* When you declare a variable within a block of code, that variable is only live in the duration of that codeblock, or within any of the codeblocks within the codeblock where it was declared
* When the codeblock is finished executing, the variable is no longer accessible

![[Pasted image 20240107123516.png]]
```c#
using System.Text;
using System.Xml.Schema;

namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            string j = "";
            for (int i = 0; i < 10; i++)
            {
                j = i.ToString();
                Console.WriteLine(i);
            }
            // Console.WriteLine(i);
            Console.WriteLine("Outside of the for: " + j);
            Console.ReadLine();

        }
    }
}



```


* A private field is available to all members of the class

