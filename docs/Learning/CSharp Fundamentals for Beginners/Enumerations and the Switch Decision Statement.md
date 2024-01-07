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
 switch (todo.Status)
 {
     case Status.Completed:

         break;
     case Status.Deleted:

         break;
     default:
         break;
 }
```





