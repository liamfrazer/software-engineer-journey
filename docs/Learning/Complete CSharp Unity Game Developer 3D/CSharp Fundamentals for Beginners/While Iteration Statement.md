---
tags:
  - csharp
---
# While Iteration Statement
* The `while` statement in this scenario is allowing us to check for a condition
* `while` the evaluation is true, we're able to recall the `MainMenu()` method
* `while` the evaluation is false, we're able to break out of the while statement

* The `do while` statement allows us to run the `do` part of the statement atleast one time

```c#
namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            bool displayMenu = true;

            while (displayMenu)
            {
                displayMenu = MainMenu();
            }
        }

        private static bool MainMenu()
        {
            Console.Clear();
            Console.WriteLine("Choose an option:");
            Console.WriteLine("1) Print Numbers");
            Console.WriteLine("2) Guessing Game");
            Console.WriteLine("3) Exit");
            string result = Console.ReadLine();

            if (result == "1")
            {
                PrintNumbers();
                return true;
            }
            else if (result == "2")
            {
                GuessingGame();
                return true;
            }
            else if (result == "3")
            {
                return false;
            }
            else
            {
                return true;
            }
        }

        private static void PrintNumbers()
        {
            Console.Clear();
            Console.WriteLine("Print Numbers");
            Console.Write("Type a number: ");
            int result = int.Parse(Console.ReadLine());
            int counter = 1;
            while (counter < result + 1) 
            {
                Console.Write(counter);
                Console.Write("-");
                counter++;
            }
            Console.ReadLine();
        }

        private static void GuessingGame()
        {
            Console.Clear();
            Console.WriteLine("Guessing Game");

            Random myRandom = new Random();
            int randomNumber = myRandom.Next(1, 11);

            int guessCount = 0;
            bool incorrect = true;

            do
            {
                Console.WriteLine("Guess a number between 1 and 10: ");
                string result = Console.ReadLine();
                guessCount++;
                if (result == randomNumber.ToString())
                    incorrect = false;
                else
                    Console.WriteLine("Wrong");

            } while (incorrect);
                Console.WriteLine("Correct! It took you {0} guesses.", guessCount);


            Console.ReadLine();
        }
    }
}
```


