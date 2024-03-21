## Casino Catchers!

**Project description:** For our Midterm Projects, we were able to work on pick and choose games. For mine, I chose a story about twin siblings in Harlem Renaissance New York who help hack casinos for money. They ask the player if they'd like to join. You enter your name and head with them on a journey to the next casino where you play Slots, Black Jack, and hopefully win some money!

### 1. Program.cs 

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

```javascript
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace AdventureGame;

class Program
{
    static void Main(string[] args)
    {
        Game game = new Game();
    }

}

```

### 2. Game.cs

```javascript
using System;
namespace AdventureGame
{
	public class Game
	{
		public Game()
		{
            Start();
		}
        public Player currentPlayer = new Player();
        public Casino1 casino = new Casino1();
        private string gameDecision;

        public void Start()
        {
            Console.WriteLine(@"
  /$$$$$$                      /$$                            /$$$$$$              /$$               /$$                                     /$$
 /$$__  $$                    |__/                           /$$__  $$            | $$              | $$                                    | $$
| $$  \__/  /$$$$$$   /$$$$$$$ /$$ /$$$$$$$   /$$$$$$       | $$  \__/  /$$$$$$  /$$$$$$    /$$$$$$$| $$$$$$$   /$$$$$$   /$$$$$$   /$$$$$$$| $$
| $$       |____  $$ /$$_____/| $$| $$__  $$ /$$__  $$      | $$       |____  $$|_  $$_/   /$$_____/| $$__  $$ /$$__  $$ /$$__  $$ /$$_____/| $$
| $$        /$$$$$$$|  $$$$$$ | $$| $$  \ $$| $$  \ $$      | $$        /$$$$$$$  | $$    | $$      | $$  \ $$| $$$$$$$$| $$  \__/|  $$$$$$ |__/
| $$    $$ /$$__  $$ \____  $$| $$| $$  | $$| $$  | $$      | $$    $$ /$$__  $$  | $$ /$$| $$      | $$  | $$| $$_____/| $$       \____  $$    
|  $$$$$$/|  $$$$$$$ /$$$$$$$/| $$| $$  | $$|  $$$$$$/      |  $$$$$$/|  $$$$$$$  |  $$$$/|  $$$$$$$| $$  | $$|  $$$$$$$| $$       /$$$$$$$/ /$$
 \______/  \_______/|_______/ |__/|__/  |__/ \______/        \______/  \_______/   \___/   \_______/|__/  |__/ \_______/|__/      |_______/ |__/
                                                                                                                                                ");
            Console.WriteLine("Name:");
            currentPlayer.name = Console.ReadLine();

            Console.WriteLine($"Welcome {currentPlayer.name}!");
            Console.WriteLine("You're sitting at the bar in Hellfire's Casino when two siblings approach you. They look familiar...");
            Console.WriteLine("They introduce themselves as Loretta and Gerald.");
            Console.WriteLine("They ask if you want to go with them to go gamble.");

            Decision();
        }

        public void Decision()
        {
            Console.WriteLine("Will you join them?");
            Console.WriteLine("y for Yes and n for No:");

            Console.Write("< ");
            string gameDecision = Console.ReadLine();

            if (gameDecision == "y")
            {
                Console.WriteLine("You get up and head to the next casino with them!");
                Console.WriteLine("Press any key to Continue...");
                Console.ReadKey();
                Console.Clear();
                casino.Intro();
                currentPlayer.wallet = currentPlayer.wallet + casino.Earnings;
                Ending();

            }
            else if (gameDecision == "n")
            {
                Console.WriteLine("You decide to stay back this time.");
                Console.WriteLine("The End.");
                Console.WriteLine("Press any key to close the game...");
                Console.ReadKey();
                Console.Clear();

            }
            else
            {
                Console.WriteLine("Only y or n is allowed...");
                Decision();
            }
        }

        public void Ending()
        {
            if (currentPlayer.wallet > 0)
            {
                Console.WriteLine("Looks like you're walking out with some money!");
                Console.WriteLine($"You've made ${currentPlayer.wallet}");
                Console.WriteLine("Press any key to close the game...");
                Console.ReadKey();
               

            }
            else if (currentPlayer.wallet < 0)
            {
                Console.WriteLine("Looks like no eating for a couple of nights...");
                Console.WriteLine($"You've made ${currentPlayer.wallet}");
                Console.WriteLine("Press any key to close the game...");
                Console.ReadKey();
              


            }
        }

    }
}


```

### 3. Player.cs

```javascript
using System;
namespace AdventureGame
{
	public class Player
	{
		public string name;
		public int wallet= 0;
		public int health= 10;
	}
}

```
**### 4. Casino1.cs**

```javascript
using System;
namespace AdventureGame
{
	public class Casino1
	{
		public int Earnings = 0;
		public Casino1()
		{
		}

        public void Intro()
		{
			Console.WriteLine("You walk with the siblings down the street to the next Casino.");

			Console.WriteLine("You walk in. Would you like to play Black Jack, or Slots?");
			Console.WriteLine("b for Black Jack, s for slots");

			string choice1 = Console.ReadLine();

			if (choice1 == "b")
			{
				Console.WriteLine("You walk over to the Black Jack Table");
				BlackJack();
			}
			else if(choice1 == "s")
			{
				Slots();
			}
			else
			{
				Console.WriteLine("only b or s is allowed...");
				Intro();
			}
		}
		public void BlackJack()
		{
			Console.WriteLine("You sit down at the table, You are dealt some cards.");
			Console.WriteLine("Your 3 options are:\n1.Look at oponents cards\n2.Play regularly\n3.Look at dealer's cards");

			string cheat1 = Console.ReadLine();
            if (cheat1 == "1")
            {
                Console.WriteLine("You look over, but their hand offers no help...");
				Console.WriteLine("You lose $500");

				Earnings = Earnings - 500;

                Console.WriteLine("Press any key to Continue...");
                Console.ReadKey();
                Console.Clear();

                Slots2();


            }
            else if (cheat1 == "2")
            {
                Console.WriteLine("You decide not to cheat...");
				Console.WriteLine("You make $20");

                Earnings = Earnings + 20;

                Console.WriteLine("Press any key to Continue...");
                Console.ReadKey();
                Console.Clear();

                Slots2();


            }
            else if (cheat1 == "3")
            {
				Console.WriteLine("You look at the dealer, you catch him giving you the card you need...");
				Console.WriteLine("You make $6000!");

                Earnings = Earnings + 6000;

                Console.WriteLine("Press any key to Continue...");
                Console.ReadKey();
                Console.Clear();
                Slots2();


            }

            else
            {
                Console.WriteLine("only 1, 2, 3 are allowed...");
                BlackJack();
            }

            void Slots2()
			{
                Console.WriteLine("Do you want to try Slots?");
                Console.WriteLine("y for yes, n for no");

                string slots = Console.ReadLine();
                if (slots == "y")
                {
                    Console.WriteLine("You get up and head to the next casino with them");
                    Console.WriteLine("Press any key to Continue...");
                    Console.ReadKey();
                    Console.Clear();
                    Slots();
                }
                else if (slots == "n")
                {
                    Console.WriteLine("You Decide it's time to go home.");
                    Console.WriteLine("Press any key to Continue...");
                    Console.ReadKey();
                    Console.Clear();


                }
                else
                {
                    Console.WriteLine("only y or n is allowed...");
                    Slots2();
                }
            }


			


        }
        public void Slots()
		{
            Console.WriteLine("You walk over to the Slot Machines and take a seat.");
            Console.WriteLine("You try copying what Loretta and Gerald do.");

            Console.WriteLine("Your 3 options are:\n1.Try pausing the Machine\n2.Press the side button\n3.Play regularly");


            string cheat2 = Console.ReadLine();
            if (cheat2 == "1")
            {
                Console.WriteLine("You try to pause the machine, but it gets faster...");
                Console.WriteLine("You lose $2000");

                Earnings = Earnings - 2000;

                Console.WriteLine("Press any key to Continue...");
                Console.ReadKey();
                Console.Clear();

                BlackJack2();



            }
            else if (cheat2 == "2")
            {
                Console.WriteLine("You press the side button a couple times. It stops on the Jackpot!");
                Console.WriteLine("You make $300");

                Earnings = Earnings + 300;

                Console.WriteLine("Press any key to Continue...");
                Console.ReadKey();
                Console.Clear();

                BlackJack2();


            }
            else if (cheat2 == "3")
            {
                Console.WriteLine("You play without cheating");
                Console.WriteLine("You lose $200...");

                Earnings = Earnings - 200;

                Console.WriteLine("Press any key to Continue...");
                Console.ReadKey();
                Console.Clear();

                BlackJack2();


            }

            else
            {
                Console.WriteLine("only 1, 2, 3 is allowed...");
                Slots();
            }

            void BlackJack2()
            {
             Console.WriteLine("Do you want to try Black Jack?");
             Console.WriteLine("y for yes, n for no");

             string slots = Console.ReadLine();
             if (slots == "y")
                    {
                        Console.WriteLine("You head over to the Black Jack Table.");
                        Console.WriteLine("Press any key to Continue...");
                        Console.ReadKey();
                        Console.Clear();
                        BlackJack();
                    }
                    else if (slots == "n")
                    {
                        Console.WriteLine("You decide it's time to go home.");
                        Console.WriteLine("Press any key to Continue...");
                        Console.ReadKey();
                        Console.Clear();


                }
                else
                    {
                        Console.WriteLine("only y or n is allowed...");
                        BlackJack2();
                    }
              


            }
        }
    }
}

```
For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
