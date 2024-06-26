## Recursion Exercise

**Project description:** I've chosen this exercise to add since it was interesting learning about how to manage computer mathematics. I feel like it was a good challenge for learning programming. 

### 1. Program.cs 

```javascript
using System;
namespace Recursion
{
	public class Pot
    { //private means that only members of this class
        //can access (read or change) these variables
        private int diameter = 9;
        private int minimumDiameter = 1;
        private string measurementSystem = "inches";
        private int step = 1;

        //Constructor
        //When an instance is made, the statements in this method
        //will run first, and only once
        public Pot()
        {
            Console.WriteLine("Steps to draw a Dogon-like pot:");
            DrawPot();
        }

        private void DrawPot()
        {
            //if-then conditional statement
            if (diameter <= minimumDiameter)
            {
                Console.WriteLine($"{step}. Draw the lid");
            }
            else
            {
                Console.WriteLine($"{step}. Draw a circle that is {diameter} {measurementSystem} in size");

                diameter = diameter * 2 / 3;

                step = step + 1;

                DrawPot();

            }
        }

    }
}
```
For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
