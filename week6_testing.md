# Testing

This week we learned about the importance of unit testing, and how to carry these out. Unit testing is a common and useful practice used to test individual components (or methods) of code, rather than testing the entire application/class etc. Our practical for the week was to battle against other teams by completing some code provided in a template, and by writing unit tests for others.

The code I was testing was the CheckLetterInWord() method of a Hangman game. The purpose of this method is to check if the letter provided by the player was included in the word they are trying to guess. If the letter __is__ included, the method should return __true__. However if the letter __is not included__, the method should return __false__.

Since I had never done unit testing before, I paired up with Guy who was in the same position as me. This allowed us to support each other through the process of learning and implementing our unit tests.

```
namespace Test_CheckLetterInWord
{
    public class UnitTest
    {
        [Fact]
        public void Test_CheckLetterInWord_False()

        {
            // This unit test tests whether the CheckLetterInWord() method returns false if the answer given by the player isn't 
            // included in the word

            string gameType = "Easy";
            string word = "toe";
            char answer = 'a';
            bool expected = false;
            GamePage gamePage = new GamePage(gameType);
            Assert.Equal(expected, gamePage.CheckLetterInWord(word, answer));            
        }
    }
}
```
The purpose of this particular unit test is to check that the method returns __false__ if the answer isn't included in the word. 

This code takes the answer provided by the player (variable 'answer') and the word (variable 'word') and enters them into the CheckLetterInWord() function. It then takes the returned value of this function and compares whether it is equal to the expected outcome (variable 'expected') which is set to false. 

When the test is run in this setup it passes, however if you change the answer to a letter that is in the word, it fails the test. This shows that the test works as intended. 

```
[Fact]
public void Test_CheckLetterInWord_True()
{
    // This unit test tests whether the CheckLetterInWord() method returns true if the answer given by the player is 
    // included in the word

    string gameType = "Easy";
    string word = "toe";
    char answer = 'o';
    bool expected = true;
    GamePage gamePage = new GamePage(gameType);
    Assert.Equal(expected, gamePage.CheckLetterInWord(word, answer));
}
```

This unit test works in the same way as the first one I discussed, but it tests to check that if the letter provided by the player is included in the word they are guessing, that the function returns true.

# Reflection
Having not done unit testing before this was a fairly new concept for me to implement, although the theory of how they are done was what I expected. Unfortunately I haven't been able to link the word variable to the wordList.txt file provided, however I tested my unit tests with multiple combinations of words and answers so I am confident it has been implemented correctly. I believe that the tests we wrote both passed in the final result, which I am pleased at, however our overall team score is disappointing. I am interested to receive some more feedback regarding the tests I wrote.
