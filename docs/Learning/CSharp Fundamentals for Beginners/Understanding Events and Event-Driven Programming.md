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






