---
tags:
  - csharp
---
# Working with Dates and Times

```c#
using System.Text;

namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            DateTime myValue = DateTime.Now;
            // Console.WriteLine(myValue.ToString());
            // Console.WriteLine(myValue.ToShortDateString());
            // Console.WriteLine(myValue.ToShortTimeString());
            // Console.WriteLine(myValue.ToLongDateString());
            // Console.WriteLine(myValue.ToLongTimeString());

            // Console.WriteLine(myValue.AddDays(1).ToLongDateString());
            // Console.WriteLine(myValue.AddHours(3).ToLongTimeString());
            // Console.WriteLine(myValue.AddDays(-3).ToLongTimeString());

            //Console.WriteLine(myValue.Month);

            // DateTime myBirthday = new DateTime(2000, 1, 1);
            // Console.WriteLine(myBirthday.ToShortDateString());

            DateTime myBirthday = DateTime.Parse("01/01/2000");
            TimeSpan myAge = DateTime.Now.Subtract(myBirthday);
            Console.WriteLine(myAge.TotalDays);
            Console.ReadLine();
        }
    }
}
```



