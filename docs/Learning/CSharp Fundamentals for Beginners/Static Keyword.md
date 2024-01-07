---
tags:
  - csharp
---
# Static Keyword

* Static methods will be available to you, without having to create an instance of the class
```c#
        static void Main(string[] args)
        {
            Car myCar = new Car();

            Car.MyMethod();
```
```c#
class Car
{
    public string Make { get; set; }
    public string Model { get; set; }
    public int Year { get; set; }
    public string Color { get; set; }
    
    
    public Car()
    {
        // You could load from a configuration file, such as a database.
        Make = "Nissan";
    }

    public Car(string make, string model, int year, string color)
    {
        Make = make;
        Model = model;
        Year = year;
        Color = color;
    }
    
    public static void MyMethod()
    {
        Console.WriteLine("Called the static MyMethod");
    }
}
```
```console
Called the static MyMethod
```

* There is a di




