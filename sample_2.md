## Cumulative Verse Song

**Project description:** For this excercise we focus on repetition in programming and what that means for certain songs that we can relate to. I've decided to do 12 days Christmas for this exercise. 

### 1. Program.cs 

```javascript
namespace CumulativeVerseSong;
class Program
{
    static void Main(string[] args)
    {
        
        string[] verses = { "First Day", "Second Day", "Third Day", "Fourth Day", "Fifth Day", "Sixth Day", "Seventh Day", "Eighth", "Ninth Day", "Tenth Day", "Eleventh Day", "Twelth Day" };

        string[] gifts = {"Partridge in a pear tree" , "Two Turtle Doves" , "Three French Hens", "Four Calling Birds", "Five golden rings", "Six Geese Laying" , "Seven Swans a Swimming" , "Eight Maids a milking" , "Nine Ladies dancing", "Ten Lords a leaping", "Eleven pipers piping" , "Twelve drummers drumming"};

        for (int i = 0; i < 12; i++)

        {
            Console.WriteLine($"On the {verses[i]} of Christmas my True Love gave to me a");


            int num = i;
            while (num >= 0)
            {
                Console.WriteLine($" {gifts[num]} ");
                num = num - 1;
            }
        }
        Console.ReadKey();
    }
}

```
For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
