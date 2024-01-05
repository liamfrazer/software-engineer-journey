---
tags:
  - csharp
  - if
---
# The IF Decision Statement

* Making a decision to execute a code, based on some condition
* This could be input, state data, but we're going to make a decision depending on a certain state

```c#
namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Liam's Big Giveaway");
            Console.Write("Choose a Door: 1, 2 or 3: ");
            string userValue = Console.ReadLine();

            if (userValue == "1")
            {
                string message = "You won a new car!";
                Console.WriteLine(message);
            }

            Console.ReadLine();
        }
    }
}
```

* `=` is a single assignment operator
* `==` is an evaluation to create a Boolean value of true or false
* If the value is false in an IF statement, this will move automatically to code next code block.

```c#
namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Liam's Big Giveaway");
            Console.Write("Choose a Door: 1, 2 or 3: ");
            string userValue = Console.ReadLine();

            if (userValue == "1")
            {
                string message = "You won a new car!";
                Console.WriteLine(message);
            }
            else if (userValue == "2")
            {
                string message = "You won a new boat!";
                Console.WriteLine(message);
            }
            else if (userValue == "3")
            {
                string message = "You won a new cat!";
                Console.WriteLine(message);
            }

            Console.ReadLine();
        }
    }
}
```
* If any of the values are true, that code block will be ran
* For example, if the second `else if` statement is true, the other codeblock is not ran

* An `else` statement at the end of the construct can be used as a safety catch to catch any other case possible.

* In the above code, there are plenty of examples of DRY examples (don't repeat yourself)
* Defining a variable within an inner scope, means that specific variable will not be accessible outside of that scope.
```c#
            else
            {
                string message = "Sorry, we didn't understand.";
            }
            Console.WriteLine(message);
            Console.ReadLine();
```
* Moving `message` outside of the last `else` statement will cause an error if `message` does not exist as a variable in the outer scope.
* A cleaner example of the code 

