---
tags:
  - csharp
---
# Understanding Events and Event-Driven Programming

* Events allow responses by handling those key moments within the application's lifecycle
* We can write code to respond to events being raised

```c#
static void Main(string[] args)
{
    System.Timers.Timer timer = new System.Timers.Timer(2000);

    timer.Elapsed += Timer_Elapsed;

    timer.Start();

    Console.ReadLine();

}

private static void Timer_Elapsed(object? sender, System.Timers.ElapsedEventArgs e)
{
    Console.WriteLine("Elapsed: {0:HH:mm:ss.fff}", e.SignalTime);
}
```
```console
Elapsed: 18:22:41.196
Elapsed: 18:22:43.193
Elapsed: 18:22:45.193
Elapsed: 18:22:47.193
Elapsed: 18:22:49.191
Elapsed: 18:22:51.191
```

```c#

namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            System.Timers.Timer timer = new System.Timers.Timer(2000);

            timer.Elapsed += Timer_Elapsed;
            timer.Elapsed += Timer_Elapsed1;

            timer.Start();

            Console.WriteLine("Press enter to remove the red event.");
            Console.ReadLine();

            timer.Elapsed -= Timer_Elapsed1;

            Console.ReadLine();

        }

        private static void Timer_Elapsed1(object? sender, System.Timers.ElapsedEventArgs e)
        {
            Console.ForegroundColor = ConsoleColor.Red;
            Console.WriteLine("Elapsed: {0:HH:mm:ss.fff}", e.SignalTime);
        }

        private static void Timer_Elapsed(object? sender, System.Timers.ElapsedEventArgs e)
        {
            Console.ForegroundColor = ConsoleColor.White;
            Console.WriteLine("Elapsed: {0:HH:mm:ss.fff}", e.SignalTime);
        }
    }
}
```

![[Pasted image 20240107183703.png]]







