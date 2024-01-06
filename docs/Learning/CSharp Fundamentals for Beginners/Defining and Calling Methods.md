---
tags:
  - csharp
---
# Defining and Calling Methods
* A method is a block of code, we can then call it by it's name to invoke that code defined within it's codeblock

```c#
        static void Main(string[] args)
        {
            HelloWorld();
        }

        private static void HelloWorld()
        {
            Console.WriteLine("Hello world!");
        }
```
* Simplest example of show how to create and call a method

```c#
namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("The Name Game");

            Console.Write("What's your first name? ");
            string firstName = Console.ReadLine();

            Console.Write("What's your last name? ");
            string lastName = Console.ReadLine();

            Console.Write("What city were you born in? ");
            string city = Console.ReadLine();

            char[] firstNameArray = firstName.ToCharArray();
            Array.Reverse(firstNameArray);

            char[] lastNameArray = lastName.ToCharArray();
            Array.Reverse(lastNameArray);

            char[] cityArray = city.ToCharArray();
            Array.Reverse(cityArray);

            string result = "";

            foreach (char item in firstNameArray)
            {
                result += item;
            }

            result += " ";

            foreach (char item in lastNameArray)
            {
                result += item;
            }

            result += " ";

            foreach (char item in cityArray)
            {
                result += item;
            }

            Console.WriteLine(result);


        }
    }
}
```
* Example of code with multiple points of repetition that can be replaced with methods/functions

* To create an input parameter to a method, it requires a datatype and a name
* This allows code outside of the method to pass through a variable to then be used inside the method

* The void keyword means that we're not bothered about the return of the method
* If this was changed to `string` for example, we're asking the Method to return back a string

* `String.Format` will create a new string


* Overloaded versions of methods
* 

