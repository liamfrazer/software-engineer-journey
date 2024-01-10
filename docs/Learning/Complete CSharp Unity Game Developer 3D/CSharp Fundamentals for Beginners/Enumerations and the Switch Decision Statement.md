---
tags:
  - csharp
---
# Enumerations and the Switch Decision Statement
* You want to limit and constrain the data with Enums or Enumerations
* We may want to constrain the possible status to a certain limit, if we're looking to keep track of them

![[Pasted image 20240107172916.png]]
![[Pasted image 20240107173154.png]]

```c#
 private static void PrintAssesment(List<Todo> todos)
 {
     foreach (var todo in todos)
     {
         switch (todo.Status)
         {
             case Status.NotStarted:
                 Console.ForegroundColor = ConsoleColor.DarkRed;
                 break;

             case Status.InProgress:
                 Console.ForegroundColor = ConsoleColor.Yellow;
                 break;

             case Status.OnHold:
                 Console.ForegroundColor = ConsoleColor.Red;
                 break;

             case Status.Completed:
                 Console.ForegroundColor = ConsoleColor.Green;
                 break;

             case Status.Deleted:
                 Console.ForegroundColor = ConsoleColor.DarkRed;
                 break;
             default:
                 break;
         }
         Console.WriteLine(todo.Description);
     }
 }
```
```console
Buy milk
Buy bread
Buy cheese
Buy eggs
```


```c#


using System.Collections;

namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            List<Todo> todos = new List<Todo>()
            {
                new Todo { Description = "Buy milk", EstimatedHours = 1, Status = Status.InProgress },
                new Todo { Description = "Buy bread", EstimatedHours = 2, Status = Status.Completed },
                new Todo { Description = "Buy cheese", EstimatedHours = 3, Status = Status.NotStarted },
                new Todo { Description = "Buy eggs", EstimatedHours = 4, Status = Status.OnHold }

            };

            PrintAssesment(todos);
            Console.ReadLine();
        }

        private static void PrintAssesment(List<Todo> todos)
        {
            foreach (var todo in todos)
            {
                switch (todo.Status)
                {
                    case Status.NotStarted:
                        Console.ForegroundColor = ConsoleColor.DarkRed;
                        break;

                    case Status.InProgress:
                        Console.ForegroundColor = ConsoleColor.Yellow;
                        break;

                    case Status.OnHold:
                        Console.ForegroundColor = ConsoleColor.Red;
                        break;

                    case Status.Completed:
                        Console.ForegroundColor = ConsoleColor.Green;
                        break;

                    case Status.Deleted:
                        Console.ForegroundColor = ConsoleColor.DarkRed;
                        break;
                    default:
                        break;
                }
                Console.WriteLine(todo.Description);
            }
        }
    }
    class Todo
    {
        public string Description { get; set; }
        public int EstimatedHours { get; set; }
        public Status Status { get; set; }
    }

    enum Status
    {
        NotStarted,
        InProgress,
        OnHold,
        Completed,
        Deleted
    }
}



```













