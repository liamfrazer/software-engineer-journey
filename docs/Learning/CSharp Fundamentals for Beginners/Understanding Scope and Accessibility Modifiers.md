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

```c#
using System.Text;
using System.Xml.Schema;

namespace Program
{
    class Program
    {

        private static string k = "";
        static void Main(string[] args)
        {
            string j = "";
            for (int i = 0; i < 10; i++)
            {
                j = i.ToString();
                k = i.ToString();
                Console.WriteLine(i);
            }
            // Console.WriteLine(i);
            Console.WriteLine("Outside of the for: " + j);
            Console.WriteLine("Outside of the for: " + k);

            HelperMethod();
            Console.ReadLine();

        }

        static void HelperMethod()
        {
            Console.WriteLine("Value of k from the HelperMethod(): " + k);
        }
    }
}



```
* K is being defined at the class level, making it a sibling to `static void Main` and `static void HelperMethod()`

```c#
			for (int i = 0; i < 10; i++)
            {
                j = i.ToString();
                k = i.ToString();
                Console.WriteLine(i);

                if (i == 9)
                {
                    string l = i.ToString();
                }

                Console.WriteLine(l);
            }
```
* `l` is not accessible as it was being declared within the `for loop` statement above

* private and public are related to encapsulation
* private means that a method can be called by any other method within the same class
* A public method is then called outside of the given class
* Private methods are only called within side the clas

```c#
class Car
{
    public void DoSomething()
    {
        Console.WriteLine(helperMethod());
    }

    private string helperMethod()
    {
        return "Hello World";
    }
}
```
![[Pasted image 20240107124703.png]]
* The consumer of the `Car` cla



