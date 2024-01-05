---
tags:
  - csharp
---
# Operators, Expressions and Statements


* `;` is used to show a complete line of code
* Statements are typically one line of code
* A statement is made up of 1 or more expressions
* Expressions are made up of 1 or more operators/operands

* Each line of code is a statement
* Each statement is made up of 1 or more expressions

* Operands are things like objects, classes and variables, these are the subject of the statement of code
* Operators are tools that act on the operand to perform an action

* An expressions is made up of operands and operators
* You use expressions to form statements, which are how instructions are expressed to the compiler/dotnet runtime

```c#
namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            // Variable declaration
            int x, y, a, b;

            // Assignment operator
            x = 3;
            y = 2;
            a = 1;
            b = 0;

            // Addition operator
            x = 3 + 4;

            // Subtraction operator
            x = 4 - 3;

            // Multiplication operator
            x = 10 * 5;

            // Division operator
            x = 10 / 5;

            // Order of operations using parenthesis
            x = (x + y) * (a - b);

            // Equality operator
            if (x == y)
            {
            }

            // Greater than operator
            if (x > y)
            {
            }

            // Less than operator
            if (x < y)
            {
            }

            // Greater or equal to operator
            if (x >= y)
            {
            }

            // Conditional AND operator
            if ((x > y) && (a > b))
            {
            }

            // Conditional OR operator
            if ((x > y) || (a > b))
            {
            }

            // In-line Conditional Operator
            string message = (x == 1) ? "Car" : "Boat";

            // Member access and Method invocation
            Console.WriteLine("Hi");
        }
    }
}
```


