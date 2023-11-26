## Project work 5

This week there were no issues left to choose from, so I improvised and saw there wasn't the ability to add or manage equipment, so I decided to create this function for the app. 

I added an SQLite table, CRUD operations, a search bar and the relevant UI.

Some examples of my code are:

```
private async void OnAddEquipmentClicked(object sender, EventArgs e)
{
	var newName = await DisplayPromptAsync("New Equipment", "Please enter the name of the equipment: ");
	var quantityInput = await DisplayPromptAsync("New Equipment", "Please enter the quantity of equipment: ");
	var newDescription = await DisplayPromptAsync("New Equipment", "Please enter the equipment description: ");

	int.TryParse(quantityInput, out int newQuantity);

	if(!string.IsNullOrEmpty(newName))
	{
		equipmentManager.AddEquipment(newName, newQuantity, newDescription);

		EquipmentList.Clear();

		foreach(var equipment in equipmentManager.GetEquipment())
			EquipmentList.Add(equipment);
	}
}
```

Here I implement the ability to add entries to the database. I believe I have followed clean code well as the method name is suitable, as are the parameters and its length. It also only deals with one action. 

I believe KISS, YAGNI, and DRY have been followed well, and that my variables follow C# standard coding conventions. 

__Feedback I recieved__

The only feedback I recieved this week was that summary comments could be used to help describe what classes are doing, however I didn't feel these were necessary as they are relatively simple ones and in my opinion the code is quite self descriptive.

__Feedback I gave__

The feedback I gave this week was for Guy and was as follows: 

 Aidan40661224 Nov 22, 2023

Nice quality of life addition to the calendar feature. Code looks good and clean, no code smells exhibited and KISS, DRY and YAGNI seem to have been followed. Only suggestion/comment is that the code comments aren't exactly necessary as the code is self describing, but that is more of a subjective choice.

I would also suggest the No_overlap function name should follow PascalCase as per C# coding convetions, and so should be No_Overlap or even OnNoOverlap potentially.

Other than that the function is clearly laid out and written, the parameters are suitable and it is of an appropriate length, while only dealing with one thing.

__Reflection__

Unfortunately I haven't managed to get my unit tests working with the project as I haven't had as much time as I would like to dedicate to this due to work and balancing work for other modules.

I think overall at this stage though I am much better at naturally adhering to clean code rules and it is becoming second nature. 

This also applies to when I look at other people's code for reviews, I feel I am able to recognize fairly quickly any naming conventions that are violated, and detecting things like redundant code, or code that isn't needed.

I am pleased over the weeks I have managed to gradually avoid making mistakes, especially repeating some mistakes in earlier weeks. 

