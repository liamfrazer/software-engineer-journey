---
tags:
  - csharp
---
# Working with Collections

* There was no way of limiting the data stored with an ArrayList collection
* The ArrayList is not strongly typed, which could cause bugs like the example below
* We allowed our Collection to store an item, other than a car

```c#
    class Program
    {
        static void Main(string[] args)
        {
            Car carOne = new Car();
            carOne.Make = "Toyota";
            carOne.Model = "Camry";

            Car carTwo = new Car();
            carTwo.Make = "Nissan";
            carTwo.Model = "Altima";

            Book bookOne = new Book();
            bookOne.Author = "Jane Doe";
            bookOne.Title = "The Great Gatsby";
            bookOne.ISBN = "0-000-00000-0";

            // ArrayLists are dynamically sized
            // Support features like sorting, adding, and removing
            ArrayList arrayList = new ArrayList();
            arrayList.Add(carOne);
            arrayList.Add(carTwo);
            arrayList.Add(bookOne);

            foreach (Car car in arrayList)
            {
                Console.WriteLine(car.Make);
            }

            Console.ReadLine();
        }
    }
```
![[Pasted image 20240107155627.png]]
![[Pasted image 20240107155634.png]]

* C# introduced Generic Collections, that requires myself to make it specific by providing the data type within that collection

```c#
            // List<T>
            List<Car> myList = new List<Car>();
            myList.Add(carOne);
            myList.Add(carTwo);
            myList.Add(bookOne);
```
![[Pasted image 20240107155940.png]]

* Dictionaries contains a key and a definition next to it
* Neither Make or Model would be appropriate as Dictionary keys, as there could be duplicates and will be duplicates of the same value, instead we can add an additional VIN

```c#
Dictionary<string, Car> myDictionary = new Dictionary<string, Car>();

myDictionary.Add(carOne.VIN, carOne);
myDictionary.Add(carTwo.VIN, carTwo);

Console.WriteLine(myDictionary["1"].Make); // Toyota
```

* Initialising a Dictionary at it's creation point with object initialization
* We've created a new variable called `car`, we've created a new instance of the `Car` class within the computer's memory, and then we've populated the Car object at the moment of creation
```c#
            Car car1 = new Car() {Make = "Toyota", Model = "Camry", VIN = "1" };
            Car car2 = new Car() { Make = "Nissan", Model = "Altima", VIN = "2" };
```








