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

Some examples of my code are:

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
private void ViewTeamMembersClicked(object sender, EventArgs e)
{
    Shell.Current.GoToAsync(nameof(TeamMemberList));
}
```
This function again is simple, as it only does one thing. The function name is a verb, and there are a small number of parameters. 

Both of these snippets also don't repeat themselves, and don't include any code that isn't needed. This helps keep it readable, efficient, and expandable.
