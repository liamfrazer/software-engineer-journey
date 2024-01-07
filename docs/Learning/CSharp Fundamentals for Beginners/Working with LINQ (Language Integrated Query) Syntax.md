---
tags:
  - csharp
  - LINQ
---
# Working with LINQ (Language Integrated Query) Syntax

```c#
            List<Car> myCars = new List<Car>()
            {
                new Car() {VIN="A1", Make="BMW", Model="550i", Year=2016, StickerPrice=55000.00 },
                new Car() {VIN="B2", Make="Toyota", Model="4Runner", Year=2016, StickerPrice=35000.00 },
                new Car() {VIN="C3", Make="BMW", Model="745li", Year=2020, StickerPrice=25000.00 },
                new Car() {VIN="D4", Make="Ford", Model="Escape", Year=2018, StickerPrice=32000.00 },
                new Car() {VIN="E5", Make="Nissan", Model="Rogue", Year=2015, StickerPrice=38000.00 }
            };
```




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
* var does not mean the same as JavaScript
* In C#, this tells the complier to figure out what the type is at point of compile

```c#
            var orderedCars = from car in myCars
                              orderby car.Year descending   
                              select car;



            foreach (var car in orderedCars)
            {
                Console.WriteLine("{0} {1} {2} {3}",car.Year, car.Make, car.Model, car.VIN);
            }   
```
```console
2020 BMW 745li C3
2018 Ford Escape D4
2016 BMW 550i A1
2016 Toyota 4Runner B2
2015 Nissan Rogue E5
```

```c#
var orderedCars = myCars.OrderByDescending(p => p.Year);
```
```console
2020 BMW 745li C3
2018 Ford Escape D4
2016 BMW 550i A1
2016 Toyota 4Runner B2
2015 Nissan Rogue E5
```

```c#
            var firstBMW = myCars.First(p => p.Make == "BMW");
            Console.WriteLine(firstBMW.VIN);
```
```console
A1
```

```c#
            var firstBMW = myCars.OrderByDescending(p => p.Year).First(p => p.Make == "BMW");
            Console.WriteLine(firstBMW.VIN);
```
```console
C3
```

```c#
Console.WriteLine(myCars.TrueForAll(p => p.Year > 2012)); // True
```
```c#
Console.WriteLine(myCars.TrueForAll(p => p.Year > 2020)); // False
```
```c#
myCars.ForEach(i => Console.WriteLine("{0} {1}",i.Make, i.Model));
```
```console
BMW 550i
Toyota 4Runner
BMW 745li
Ford Escape
Nissan Rogue
```


```c#
myCars.ForEach(i => Console.WriteLine("{0} {1} {2:C}",i.Make, i.Model, i.StickerPrice));
```
```console
BMW 550i £55,000.00
Toyota 4Runner £35,000.00
BMW 745li £25,000.00
Ford Escape £32,000.00
Nissan Rogue £38,000.00
```

```c#
            myCars.ForEach(i => i.StickerPrice -= 3000);
            myCars.ForEach(i => Console.WriteLine("{0} {1} {2:C}",i.Make, i.Model, i.StickerPrice));
```
```console
BMW 550i £52,000.00
Toyota 4Runner £32,000.00
BMW 745li £22,000.00
Ford Escape £29,000.00
Nissan Rogue £35,000.00
```
















































