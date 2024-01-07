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

```








