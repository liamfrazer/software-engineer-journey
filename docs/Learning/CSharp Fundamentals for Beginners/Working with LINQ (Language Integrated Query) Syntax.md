---
tags:
  - csharp
  - LINQ
---
# Working with LINQ (Language Integrated Query) Syntax

* Language Integrated Query - Query Syntax
```c#
            var bmws = from car in myCars
                       where car.Make == "BMW"
                       && car.Year == 2016
                       select car;
```
```console
BMW 550i A1
```

* Language Integrated Query - Method Syntax
```c#
var bmws = myCars.Where(p => p.Make == "BMW" && p.Year == 2016);
```
```console
BMW 550i A1
```
* Above is similar to a mini method that returns any true values into the `var` `bmws`
* 









