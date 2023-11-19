## Project work 4

Week 10 is the third and last week in a series in which the goal is to improve your personal software engineering practice. Your portfolio entry has the same general content as last week's, including:

    A descriptive summary of the issue that you worked on.
    Snippets from your code with commentary showing how you have used good software design practice.
    A descriptive summary of the test code that you have written.
    A reflective summary of any changes that were requested during the code review along with your fixes.
    A descriptive summary of any issues you found with the code that you were asked to review.
    A general reflective section that identifies, for example,
        New things you have realised this week
        Common problems that can arise in a team development situation
        How your practice compares to other people's
        etc.

Be sure to include links to the original items in the team's GitHub repository.

In the reflective sections this week, you should highlight ways that you persona practice has improved as before. It would also be good to reflect on any improvements that have been made to the agreed team workflow and related procedures. Are things working better than they were? What further improvements could be made in the future?

This week I worked on improving my code from previous weeks as I had some outstanding code review changes to be completed. 

In week 9 I added the ability for accomodation status' to be viewed and added to a database, however the capacities were passed as strings. Here is how I improved that code by passing them as integers:

```
private async void OnAccomodationNameModified(object sender, EventArgs e)
{
    var button = sender as Button;
    var selectedAccomodation = button?.CommandParameter as Accomodation;

    if (selectedAccomodation != null)
    {
        var newName = await DisplayPromptAsync("Update accomodation", "Please enter a new name for the accomodation", initialValue: selectedAccomodation.name);
        var maxCapInput = await DisplayPromptAsync("New Accomodation", "Please enter the maximum capacity of the accomodation: ");
        var currCapInput = await DisplayPromptAsync("New Accomodation", "Please enter the current capacity of the accomodation: ");
        int.TryParse(maxCapInput, out int maxCap);
        int.TryParse(currCapInput, out int currCap);

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

I believe this code still follows clean code principles as the method is suitably long, deals with one thing, is named appropriately and has the correct parameters. The variables themselves are also named clearly, and the code is self documenting. It follows KISS, YAGNI and DRY.

__Feedback I recieved__

Findaadi commented Nov 19, 2023

The coderequest change has been fulfilled, has used appropriate data types in this change as requested. approved.

This is the feedback I recieved from Adarsha after changing the variable types for the capacity variables, I am happy with this feedback as the branch can now be merged and the code is better.

__Feedback I gave__

__Reflection__

