---
tags:
  - csharp
---
# Understanding Namespaces and Working with the .NET Class Library

* Every DotNet applications accesses the same cache of DotNet assembly files and the DotNet Framework is required to be installed on the machine
* namespaces are like `last names` for our classes, 
* The `using` statement at the top of the file allows us to swap `System.Console.WriteLine()` to `Console.WriteLine` instead. 

```c#
using System.IO;

namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            string text = "Sample Text";
            File.WriteAllText(@"C:\dev\text.txt", text);
        }
    }
}
```
```console
// text.txt
Sample Text
```

```c#
using System.IO;
using System.Net;
using static System.Net.Mime.MediaTypeNames;

namespace Program
{
    class Program
    {
        static void Main(string[] args)
        { 
            WebClient client = new WebClient();
            string reply = client.DownloadString("https://msdn.microsoft.com");
            File.WriteAllText(@"C:\dev\text.txt", reply);

            Console.WriteLine(reply);
            Console.ReadLine();
        }
    }
}
```
![[Pasted image 20240107133249.png]]





