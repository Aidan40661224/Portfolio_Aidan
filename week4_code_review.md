This week in our lecture we learned about what makes good quality code versus poor quality, such as whether any code smells are exhibited, or whether general coding principles such as KISS or YAGNI have been followed. This was then followed with being taught about code reviews and why they are important, before going on to practice our own in the practical.

The code I would like to discuss in my portfolio is as follows:

```
public class Character 
{
    public int Level { get; private set; }
    public List<SpecialAbilities> Abilities { get; private set; }

    public void LevelUp() 
    {
        Level++;
    }
}
```

I have chosen to discuss this code despite gaining full marks in the practice form because it shows a good example of the YAGNI (You aren't gonna need it) principle being violated by the ``` public List<SpecialAbilities> Abilities { get; private set; } ```
This goes against the YAGNI principle as this code is creating a list pre-emptively as it is not currently necessary. In a small situaton like this it may not present too much of an issue, however as projects scale unecessary code can open the door for potential bugs and errors, as well as making it harder to efficiently debug and review code. It can also cause unecessary bloat to the application. 

Despite losing a mark for selecting it, I also believe ``` public int Level { get; private set; } ``` violates standard C# coding conventions which state that variables should be named using camelCasing, but as you can see the 'Level' variable here is named with a capital 'L', which is not camelCase.

Having completed my code review I edited the code:

```
public class Character 
{
    public int level { get; private set; }

    public void LevelUp() 
    {
        Level++;
    }
}
```

I believe my solution is better than the original as the variable is named using camelCasing as per the standard C# coding conventions. This helps to make it clear to anyone who may need to read or expand upon this code in the future that this is a variable, and not class or a method. I have also removed the unecessary code which could be used to create a list. As I mentioned previously this code doesn't need to be there in the current iteration of this code as it isn't actually being used for anything. If in the future it is decided to add special abilities to this character class, the code can be implemented again. 

Having made these changes I feel the code for this class is now easier to read and more efficient for anyone who may need to review it for any reason.
