# Project work 1

In week 8, you are exercising all the principles and techniques that have been discussed 
in the module so far. Your portfolio entry should demonstrate your ability to integrate 
the various dimensions of software engineering into your practice. It should include 

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

This week my issue was to add the ability for an UNDAC Deputy Team Leader to maintain a list of team members so they can be contacted immediately. To complete this task the all team members must be listed, details of a particular team member must be viewed, the list must be filtered by full text search, skill, assignment etc, and the filters must be able to be cleared.

As I am not particularly confident implementing these features in .Net Maui I haven't been able to complete all of them, however I will continue working on them and try to implement them all.

__Some examples of my code are:__

```
namespace UNDAC_App.Models
{
    public class TeamMember
    {
        public string name { get; set; }
        public string email { get; set; }
        public int phone { get; set; }

    }
}
```
This class creates a team member to be added to the list. This class is simple, it only does one thing (initialize the object), and can easily be expanded upon in the future if more information needs to be added for team members, such as addresses or skills.

```
void SearchBar_TextChanged(object sender, TextChangedEventArgs e)
{
	var searchTerm = e.NewTextValue;

	if (string.IsNullOrEmpty(searchTerm))
		searchTerm = string.Empty;

	searchTerm = searchTerm.ToLowerInvariant(); // allows search to not be case sensitive

	var filteredItems = TeamMembers.Where(value => value.Contains(searchTerm)).ToList();

	foreach (var value in TeamMembers)
	{
		if (!filteredItems.Contains(value))
			TeamMembers.Remove(value);
		else if (!TeamMembers.Contains(value))
			TeamMembers.Add(value);
	}
}
```
In my opinion this snippet also follows clean code principles as it only handles one thing, searching the list. DRY and YAGNI principles have also been followed as there is no repetition of code, and there is no redundant code. 
I have also followed the correct naming conventions for the method name being descriptive and a verb. There are also as few parameters as possible. Within the method any temporary variables which are declared are suitably named, and follow camelCasing. I have added a comment, but I feel this is okay as someone who hasn't used .NET MAUI before may not realise what ToLowerInvariant() does/means.

__My test code__

```
public class Test_ObservableCollection_DisplaysCorrectData
{
    public ObservableCollection<TeamMember> expected { get; set; }
    [Fact]    
    public void Test_ListDisplaysCorrect()
    {
        expected = new ObservableCollection<TeamMember>
        {
            new TeamMember{name = "John Doe", skill = "Skill 1", currentAssignment = "assignment 1"},
            new TeamMember{name = "Jane Doe", skill = "Skill 2", currentAssignment = "assignment 2"},
            new TeamMember{name = "Bob Smith", skill = "Skill 3", currentAssignment = "assignment 3"}
        };
        TeamMemberList teamMemberList = new TeamMemberList();
        Assert.Equal(expected, teamMemberList);
    }
}
```

Unfortunately due to an error in my .xaml.cs file which I haven't been able to resolve, I haven't been able to test this function. Please note that as I am still new to writing unit tests so I am unsure if what I have currently written will work. The idea of the code I have written is that the test creates a list of team members which can be altered for testing purposes and then compares if it is equal to the list of team members created in the .xaml.cs file. If the lists contain equal data the test will pass. 

__My code review feedback__



__Feedback I gave__

I carried out a code review for findingaadi (Adarsha) who was working on issue #64. I made sure to carefully read through the changes in all files, marking them as viewed and adding any relevant comments regarding the cleanliness of the code. Generally the code itself I felt followed clean code principles and there weren't any changes required. I provided some feedback in each file as a comment, advising that I felt he followed the DRY, YAGNI, KISS principles, his variables were named well and there wasn't any redundant code I could see. 

I gave one suggestion of moving a class into a seperate file under the 'Models' folder, however I felt that this wasn't totally necessary as it didnt contravene any clean code rules that I am aware of. 


# Reflection

I struggled a bit with this weeks task as I am still learning .NET MAUI. However I sought help of my team mates who were able to help me, for example I had issues getting my observable collection to display in app until a team mate helped to explain I was trying to bind the wrong attribute in the .xaml file for my issue.

I have almost successfully implemented the search filter, however I am stuck with one error that I haven't been able so solve. I will seek assistance with this error in the practical and hopefully fix it as soon as possible to fully complete my issue.

Ontop of this I haven't been able to test if my search bar works yet as the app can't run due to the error. Once the above mentioned error is resolved, I will be sure to run my unit test and ensure the feature works as desired.

I was already well aware of the necessity of good naming practices while coding, however this week has really hammered this home again as there were a few times I was finding myself getting confused about which variables to use where between the .xaml and .xaml.cs files, ontop of learning the syntax of C# in the .NET MAUI environment. I had to rename a couple of variables, for example: My .NET MAUI content page files are named TeamMemberList, my class for initializing the list is called TeamMember, and the name of the list (observable collection) itself is TeamMembersCollection, however initially they were all named teamMember, TeamMembersList and TeamMemberList which was much more confusing.

I think common problems that can arise in team situations, especially with peers in education is being scared or embarassed to ask for help which can be a hard thing to overcome as you don't want to feel potentially looked down on. However this is (in my opinion) one of the most useful skills to try and learn in any walk of life, but especially in software engineering. It is much better to bite the bullet and ask for help which can potentially save you and your team lots of time, and prevent any major bugs or errors before they can occur. 

