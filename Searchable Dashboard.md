Can be done without customization, but requires a new query each search.
Note: you need [menu maintenance.](https://www.youtube.com/watch?v=AobOja72Mqg) to deploy customizations. 
Notes based on [this video](https://www.youtube.com/watch?v=YsfRCq0Baek).


With Customization permissions enabled in your environment...
Create a dashboard.
1. Add a grid and a tracker
2. Deploy the dashboard
3. Enter Customization developer mode
4. Open the dashboard
5. Tools > Customize
6. In the "Customization Tools Dialog", Tools > ToolBox
7. Add a Label & a search bar

Now the fun...
The Event Wizard allows you create evnets triggered by interface elements.

8. Choose control type: TextBox
9. Choose the name of your text box
10. Choose an event, in this case "TextChanged"
11. Click the arrow ▶ to generate the event code
12. In the bottom left, click "Update all Event Code" to add the code snippet
13. Navigate to "Script Editor" tab to verify the snippet has been added.

Write the code to be fired within this snippet.
To use objects from within the Dashboard, go to Tools > Object Explorer.
Select the Data Objects tab. The tableName/dataview will contain code references to the data in the grid.

Combination SQL & C# search.
% is SQL wildcard
{0} is a C# variable used with the String.Format() method

```C#
// This code block is executed every time text changes in the textbox
// get reference to the dashboard/view
var partsEdv = (EpiDataView)(oTrans.EpiDataViews["V_ah_part_usage_1View"]);
// create SQL query based on searchbar text
String filter = String.Format("Part_PartNum like '%{0}%'", SearchBarPartUsage.Text);
// run the SQL statement
partsEdv.dataView.RowFilter = filter;
```

F5 to compile/test (optional I think).
Save.

To deploy these kinds of customizations to dashboards you need [menu maintenance.](https://www.youtube.com/watch?v=AobOja72Mqg).

