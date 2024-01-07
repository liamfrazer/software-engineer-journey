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


