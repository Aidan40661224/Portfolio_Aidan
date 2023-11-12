# Project work 3

This week I worked on adding the ability for a deputy team leader to be able to view the status of sub teams so they can identify and resolve issues as they occur. 

I feel I have followed clean code well and have improved on the first two weeks, as my feedback hasn't contained comments about any of the clean code principles I hadn't followed in previous weeks that was identified in the reviews.

Some examples of my code from this week are:

```
private async void OnAddSubTeamStatusClicked(object sender, EventArgs e)
{code 
	var newStatus = new SubTeamStatus();
	newStatus.subTeamName = await DisplayPromptAsync("New Sub Team Status", "Please enter the Sub Team's name");
    newStatus.status = await DisplayPromptAsync("New Sub Team Status", "Please enter the Sub Team's status");
    newStatus.issue = await DisplayPromptAsync("New Sub Team Status", "Please describe the issue");
    newStatus.resolution = await DisplayPromptAsync("New Sub Team Status", "Please describe your resolution");

	if (!string.IsNullOrWhiteSpace(newStatus.subTeamName) && !string.IsNullOrWhiteSpace(newStatus.status) &&
		!string.IsNullOrWhiteSpace(newStatus.issue) && !string.IsNullOrWhiteSpace(newStatus.resolution))
	{
		subTeamStatusManager.AddSubTeamStatus(newStatus);
		SubTeamStatusList.Add(newStatus);
	}
}
```

Here you can see this method only does one thing, which is add new data to my SQLite table. It it suitably named, with an appropriate length and number of parameters. The code is self describing, and I believe the variables have been appropriately named.

__Feedback I recieved__

The feedback I received was generally positive about my code, and they were happy that my code was clean. The only suggestion they gave me was to indent some code in one of my methods, however I didn't feel it was necessary and didn't particularly improve the readability of the code.

__Feedback I gave__

I was happy with Guy's code and felt that he followed the clean code principles well. KISS, DRY and YAGNI had all been applied well.

__Reflection__

Over all this week I feel I have made positive progress in writing clean code. I was happy with the feedback I recieved and look forward to continuing to implement these principles in the future weeks. I feel giving feedback is becoming harder though, as my peers are also getting better at applying clean code, so there is less to talk about and give feedback on.

I still haven't been able to implement unit testing successfully and im not aware of any team mates who have. This is frustrating as it means we can't practice what we learned earlier in the course. 
