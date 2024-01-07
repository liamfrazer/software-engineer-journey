---
tags:
  - csharp
---
# Understanding Classes

* A class is a container for related methods
* The class is the blueprint, the object is created as a result of the blueprint
```c#
Car myCar = new Car();
```
* Declaring a new car in memory, then creating a new instance of the Car class
* Each time we initialise a class, we would have an object that is separate to all the other Classes within the computer's memory
* A Class is like a Cookie Cutter, it gives the shape to the object, but not the actual object itself

* The `new` keyword uses the blueprint, in order to create a new instance of Car
* Car describes the class/the blueprint, we want to work with one instance which we've set in memory as `myCar`

```c#
private static decimal DetermineMarketValue(Car car)
```
* The uppercase Car corresponds to the name of the Class, the lowercase car is responding to the object, this is an input parameter

* In our scenario, it would make more sense for the DetermineMarketValue method to be a part of the `Car` class, as the class has full access to all the variables/values required for the method to function
* In our example, we could write a small function that determines the value of the car depending on the year of the car

```c#
class Car
{
    public string Make { get; set; }
    public string Model { get; set; }
    public int Year { get; set; }
    public string Color { get; set; }
    
    public decimal DetermineMarketValue()
    {
        decimal carValue;
        if (Year > 1990)
            carValue = 10000;
        else
            carValue = 2000;

        return carValue;
    }
}
```

```c#
using System.Text;

namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            Car myCar = new Car();
            myCar.Make = "Ford";
            myCar.Model = "Mustang";
            myCar.Year = 1964;
            myCar.Color = "Red";

            Console.WriteLine("{0} {1} {2} {3}",
                myCar.Make,
                myCar.Model,
                myCar.Year,
                myCar.Color);

            Console.WriteLine("{0:C}", myCar.DetermineMarketValue());

            Console.ReadLine();
        }
    }
  

    class Car
    {
        public string Make { get; set; }
        public string Model { get; set; }
        public int Year { get; set; }
        public string Color { get; set; }
        
        public decimal DetermineMarketValue()
        {
            decimal carValue;
            if (Year > 1990)
                carValue = 10000;
            else
                carValue = 2000;

            return carValue;
        }
    }
}
```
```console
Ford Mustang 1964 Red
£2,000.00
```










