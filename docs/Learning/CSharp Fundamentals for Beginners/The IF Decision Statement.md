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

* If there is only one line of code underneath an IF statement, the code blocks are not required

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
            string message;

            if (userValue == "1")
                message = "You won a new car!";
            else if (userValue == "2")
                message = "You won a new boat!";
            else if (userValue == "3")
                message = "You won a new cat!";
            else
                message = "Sorry, we didn't understand.";

            Console.WriteLine(message);
            Console.ReadLine();
        }
    }
}
```

* Two line of code will cause the second line to be "outside" of the hidden code block

```c#
            {
                message = "Sorry, we didn't understand.";
                message += "You lose.";
            }
```
* The assignment and concat operator can be combined into one

```c#
string message = (userValue == "1") ? "Boat" : "strand of hair";
```
* Similar to a Ternary operator, if the evaluation is TRUE, we would take the value from after the ?
* If the evaluation is FALSE, we would take the value after the :
* This is only usable when there are two valuations. Like an IF ELSE statement

```c#
 Console.WriteLine("You won a {0}, therefor you won a {1}.", userValue, message);
```
* Replacement values can be used like `{0}` to then input a value into.
* The first item in the list will be element 0, replaced by the list of input parameters after the literal string.













