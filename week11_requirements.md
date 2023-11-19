## Project work 4

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

The feedback I gave to Adarsha was very positive, there were no issues with the cleanliness of his code as far as I could see. 

__Reflection__
I feel that I am still improving my clean code skills and familiarity with .NET MAUI each week and I now feel I am confident enough to go back and improve my old code, which is pleasing. 


