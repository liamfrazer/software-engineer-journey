---
tags:
  - csharp
---
# Understanding Data Types and Variables

* We have to declare the variables (buckets) and then label them to ensure we can access them.

```c#
            int x;
            int y;
```
* Assigning integer values into the variables `x` and `y`

```c#
            int x;
            int y;

            x = 7;
            y = x + 3;
```
* Using the `=` assignment operator, assigning a value into the Y variable

```c#
Console.WriteLine("What is your name?");
            Console.WriteLine("Type your first name: ");
            string myFirstName;

            myFirstName = Console.ReadLine();

            string myLastName;
            Console.Write("Type your last name: ");
            myLastName = Console.ReadLine();

            Console.WriteLine("Hello, " + myFirstName + " " + myLastName + "!"); // Hello, firstName secondName!
```





