---
tags:
  - csharp
---
# Understanding Arrays
```c#
int[] numbers = new int[5];
```
* Declaring an array of integers collected under the value `numbers`

```c#
            numbers[0] = 4;
            numbers[1] = 8;
            numbers[2] = 15;
            numbers[3] = 16;
            numbers[4] = 23;
```
* Accessing the elements of the array and then assigning a value to each

```c#
Console.WriteLine(numbers[2]);
```
* Accessing the assigned value of the 3rd element of the array

```c#
Console.WriteLine(numbers.Length);
```
* Accessing the length of the array by using the `length` property

```c#
        {
            int[] numbers = new int[] { 4, 8, 15, 16, 23, 42 };
        }
```
* Assigning the values of the array at runtime, while also allowing the complier to work out how many values are within the array

```c#
{
    string[] names = new string[] { "Liam", "Frazer", "Michael", "David" };

    for (int i = 0; i < names.Length; i++)
    {
        Console.WriteLine(names[i]);
    }
}
```
* Iterating through each value within the array, using a `for` loop

```c#
        {
            string[] names = new string[] { "Liam", "Frazer", "Michael", "David" };
            
            foreach (string name in names)
            {
                Console.WriteLine(name);
            }
        }
```
* Using a `foreach` loop to iterate through the array

```c#
{
    string quote = "You can get what you want out of life" + 
        " if you help enough other people get what they want";

    char[] charArray = quote.ToCharArray();

    Array.Reverse(charArray);

    foreach (char c in charArray)
    {
        Console.Write(c);
    }
    Console.ReadLine();
}
```
* Reversing a string by using the `toCharArray()` method, the `Array.Reverse` method and the `foreach` iteration loop.

















