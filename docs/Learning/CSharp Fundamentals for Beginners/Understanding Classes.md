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

* We're storing values in that bucket, use the reference `myCar` as a handle to that bucket
* Once that handle is dropped, the bucket will no longer be accessible.
* The DotNet framework monitors the memory that it manages, looking for objects that no longer have any handles, the reference count will go to 0, meaning that this is part of the garbage collection

* C++ is an unmanaged memory where I may have to memory manage by myself, whereas C# has a garbage selection is managed

```c#
        static void Main(string[] args)
        {
            Car myCar = new Car();

            myCar.Make = "Ford";
            myCar.Model = "Mustang";
            myCar.Year = 1969;
            myCar.Color = "Red";

            Car myOtherCar;
            myOtherCar = myCar;

            Console.WriteLine("{0} {1} {2} {3}",
                myOtherCar.Make,
                myOtherCar.Model,
                myOtherCar.Year,
                myOtherCar.Color);

            myOtherCar.Model = "Bronco";

            Console.WriteLine("{0} {1} {2} {3}",
                myCar.Make,
                myCar.Model,
                myCar.Year,
                myCar.Color);

            Console.ReadLine();
        }
```
```console
Ford Mustang 1969 Red
For Bronco 1969 Red
```
* While we're reference `myCar` in the second WriteLine, while both `mycar` and `myOtherCar` would appear to be different, they've both pointed to the same point in memory, meaning that changes to the `myOtherCar` variable will have an impact on the original `myCar` variable

* Once we exit outside of the main method, the myCar variable would go out of scope
* The same if we defined a variable within a different method and set a variable within the Method's scope

![[Pasted image 20240107113948.png]]



* We're calling a `constructor` method whenever we're creating a new instant of a class
* They're typically used to put the new object into a valid state

* The `.this` keyword is optional, it refers to this instance of the object and helps clarify where the variable is associated to.

* To put any new instance of an object into a valid state







