# Project work 2

In week 9, you are continuing with the team project. Your portfolio entry should 
demonstrate how your software engineering practice is improving. It should include
much the same content as last week's:

* A descriptive summary of the issue that you worked on.
* Snippets from your code with commentary showing how you have used good software design 
  practice.
* A descriptive summary of the test code that you have written.
* A reflective summary of any changes that were requested during the code review along 
  with your fixes.
* A descriptive summary of any issues you found with the code that you were asked to review.
* A general reflective section that identifies, for example,
  * New things you have realised this week
  * Common problems that can arise in a team development situation
  * How your practice compares to other people's
  * etc.

Be sure to include links to the original items in the team's GitHub repository.

In the reflective sections, try to identify things that you have done better this week. 
This could include, for example,

* Better application of the principles of clean code.
* Avoiding the repetition of previous mistakes.
* More comprehensive test coverage.
* Adoption of a more systematic personal workflow.
* Improved identification of problems in other people's code.
* etc.

This week I worked on adding the ability to view accomodation status' and incorporating a map for viewing them. Unfortunately I was unable to implement the map, partly down to being away for 3 days for a wedding in England. However I fixed the issue from last week and restructured it to include a SQLite table instead of just a list. I will continue working on the map during the next week. 

```
private async void OnAccomodationNameModified(object sender, EventArgs e)
{
    var button = sender as Button;
    var selectedAccomodation = button?.CommandParameter as Accomodation;

    if (selectedAccomodation != null)
    {
        var newName = await DisplayPromptAsync("Update accomodation", "Please enter a new name for the accomodation", initialValue: selectedAccomodation.name);
        var maxCap = await DisplayPromptAsync("New Accomodation", "Please enter the maximum capacity of the accomodation: ", keyboard: Keyboard.Numeric);
        var currCap = await DisplayPromptAsync("New Accomodation", "Please enter the current capacity of the accomodation: ", keyboard: Keyboard.Numeric);

        if (!string.IsNullOrWhiteSpace(newName))
        {
            accomodationManager.UpdateAccomodation(selectedAccomodation.Id, newName, maxCap, currCap);

            AccomodationStatusList.Clear();
            foreach (var accomodation in accomodationManager.GetAccomodation())
            {
                AccomodationStatusList.Add(accomodation);
            }
        }
    }
}
```
I feel this is a good example of clean code as itis simple, self describing code. The method isn't too long, is appropriately named without too many parameters, and only does one thing. 

The code review I received was generally positive about the code I wrote and was happy with clean code being followed. However one change was requested as it seemed there was some repetition of code over two methods:

"Code is functional and works well.
For feedback, there some code that are duplicated. here the code contains repetitive lofic to update the "AccomodationStatusList" in the methods "OnAddAccomodationClicked", "OnAccomodationNameModified" and "OnAccomodationStatusList". Each of these code contain the same code block to clear and repopulate the AccomodationStatusList. To improve maintainability, a separate method can be created that is responsible for updating the AccomodationStatusList method."

I changed my code by removing OnAccomodationClicked, renaming OnAccomodationNameModified to OnAccomodationModified, and using that one method for when users want to edit any entries.

For the code review I performed, overall I was happy with Adarsha's code and didn't detect the need for any changes in regards to clean code as it seemed to follow DRY, KISS and YAGNI, and everything was named appropriately. The only issue seemed to be an issue which has happened for other team members where the csproj.user file has duplicated and the code has been cut and pasted into the new version for some reason.

## Reflection

I think we are continuing to improve as as team, and myself personally. I think i have become more comfortable with SQLite and felt confident going back to last weeks isuse and improving it by turning the list into an SQLite table. I am disappointed in myself for having had some redundant code this week and will look to review my own code and methods better next week to prevent this from happening.

As a team we made more of an emphasis of trying to get our issues ready for review by Friday to give us a day or two to try and implement any fixes before updating our portfolios. Despite being away for a wedding, my code was reviewed on the Thursday and allowed me time to reflect on the feedback before implementing it when I got the chance.
