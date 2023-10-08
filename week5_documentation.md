# Documentation

This section is related to your work on clean code and documentation in week 5.

First, choose six rules of clean code and explain them. For each one,

* Summarise the rule in your own words.
* Provide an example from the code that you wrote in week 2 and then refined in week 4.
* Explain how your code implements the rule. 

Second, copy the doxygen comments from your code into your portfolio and provide some 
descriptive commentary on their purpose and structure. Use screenshots showing the HTML 
content that is generated from your code to illustrate your explanation.

Finally, highlight three examples from your code where you have eliminated the need
for comments by adhering to the principles of clean code.
 
This week in our lecture we learned more about the importance of software design and documentation, and some tools and methods on how to create good documentation. One of these tools is Doxygen which we have been tasked with using to create documentation for our project.

__PART ONE__

First however, I will explain some rules of clean code and provide examples of them from my code.

1. _Standard C# naming conventions:_ This rule allows anyone who may need to read, review or edit your code to easily distinguish between variables, methods, classes etc by using camelCasing or PascalCasing in the correct places, for example. It also helps make your code easy to understand by giving variables and methods suitable names. For example variables should be nouns that fully describe what they represent, and methods should be verbs that do the same.

``` EquipmentTypeDataBase database; ``` 

This name clearly shows the variable represents the database for the equipment types that are entered and follows camelCasing.

```async void OnSaveClicked(object sender, EventArgs e)
{
    if (string.IsNullOrWhiteSpace(Item.Name))
    {
        await DisplayAlert("Name required", "Please enter Equipment Type.", "Okay");
        return;
    }

    await database.SaveItemAsync(Item);
    await Shell.Current.GoToAsync("..");
}
```
This method name shows it handles what happens when 'Save' is clicked by the user and follows PascalCasing.

2. _Keep it simple stupid:_ This rule again helps to improve the readability of your code not only for others, but also for yourself if you ever have to return to it. By reducing complexity as much as possible you inherently make your code easier to understand and revisit if required.

```
public class EquipmentType
{
    [PrimaryKey, AutoIncrement]
    public int ID { get; set; }
    public string Name { get; set; }
}
```
This class is very simple and explains itself well. 

3. _The next rule(s) I would like to discuss are in relation to functions/methods._ As previously mentioned, functions should have names that are verbs, should be short and should also do only one thing. This helps to keep them simple and readable, and allows you or others to understand what your code does. It also allows for easier debugging as you can pinpoint where an error is coming from more easily if each function only does one thing.  

```
async void OnDeleteClicked(object sender, EventArgs e)
{
    if (Item.ID == 0)
        return;
    await database.DeleteItemAsync(Item);
    await Shell.Current.GoToAsync("..");
}
```
This function has a verb name and clearly shows that if the delete button is clicked by the user, the item is deleted from the database.

4. _Comments:_ The clean code approach says that comments shouldn't be necessary as code should be self describing, and if it isn't, the code may be too complex. There are however times where it is difficult to make code any simpler, and in these instances a comment to describe the code is okay. However comments should be used sparingly and shouldn't be used if they are stating the obvious.

```
public const SQLite.SQLiteOpenFlags Flags =
    // open the database in read/write mode
    SQLite.SQLiteOpenFlags.ReadWrite |
    // create the database if it doesn't exist
    SQLite.SQLiteOpenFlags.Create |
    // enable multi-threaded database access
    SQLite.SQLiteOpenFlags.SharedCache;
``` 
Here the code may not necessarily be obvious to someone who hasn't used SQLite before, such as a lot of our team. Therefore some brief comments descriptions are okay. 

5. _Single Responsibility Principle:_ This rule states that classes should also only perform a single responsibility, not just functions.

```
public class EquipmentType
{
    [PrimaryKey, AutoIncrement]
    public int ID { get; set; }
    public string Name { get; set; }
}
```
Despite already being used I believe this to be a good example of the single responsibility principle as this class only allows the creation of the parameters of the equipment types that will be entered. 

6. _Open/Closed principle:_ This rule states that your code should not need to be modified to be expanded upon. This is useful as it allows for future expansion of a project if required and makes doing so as easy as possible.
```
public class EquipmentType
{
    [PrimaryKey, AutoIncrement]
    public int ID { get; set; }
    public string Name { get; set; }
}
```
This code can easily be expanded upon if there was a need to add more parameters to the equipment type class.

__PART TWO__

Here are some examples of my Doxygen comments along with explanations

Constant.cs

/// <summary>
/// This class allows for CRUD operations to be carried out
/// </summary>

<figure>  
  <img src="https://github.com/Aidan40661224/Portfolio_Aidan/blob/main/images/Doxygen%20example.PNG">  
</figure>

I have added this comment so anyone viewing the documentation can clearly see that the purpose of this class is to allow create, read, update and delete database entries.

__PART THREE__

```
public async Task<List<EquipmentType>> GetItemsAsync()
{
    await Init();
    return await Database.Table<EquipmentType>().ToListAsync();
}
```
```
public async Task<int> SaveItemAsync(EquipmentType item)
{
    await Init();
    if (item.ID != 0)
    {
        return await Database.UpdateAsync(item);
    }
    else
    {
        return await Database.InsertAsync(item);
    }
}
```
```
public async Task<int> DeleteItemAsync(EquipmentType item)
{
    await Init();
    return await Database.DeleteAsync(item);
}
```

These code examples all adhere to clean code and therefore do not require comments in my opinion as the functions are named suitably, they all carry out one task, and are kept short and simple.
