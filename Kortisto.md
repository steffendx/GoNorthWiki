Kortisto is the npc planning module of GoNorth. You can access it from the Kortisto tile on the home page or the navigation on the top.  
Kortisto allows you to build your own templates with different fields. This way you can build a template for humans for example which has a health value, strength but also a background text box to provide more details for this npc. A monster template on the other hand might include a health and strength field but not a background text box since its just an enemy.  
Please note: While a user edits an npc or template this npc or template will be readonly for other users to prevent them from overwriting each others changes.

## Npc List
You will see a list of npcs and categories after navigating to Kortisto.  
By using the search box you can search for npcs. This will search in the name and the tags assigned to an npc.

By clicking on create category you can create a new category for npcs. You can think of categories as folders in the file system. This way you can organize your different npcs.  
A category can be given a name, a description and an image. The description will be shown on mouse hover over the image or icon of the category.  
Each category can be edited using the pencil icon on the top right of the tile. You can also delete a category by pressing the trash bin icon. Please note: You can only delete empty categories.

By clicking on the create npc button you can choose a template and create a new npc based on this template. If no templates are shown there you will have to create a new template first by clicking on the manage template link in the drop down list.

### Moving Npcs or folders to other categories
If you want to move an npc or folder to a different category you can drag that object onto a different existing folder and drop it there. Afterwards the dragged object will be moved into that category.  
To move an object up a level, a small grey area with a fitting icon will be diplayed while dragging an object. If you drop that object in this area, the object will be moved one level up.  
Using drag and drop you can quickly move objects one level up or down.  

Alternatively you can press the rectangle with an arrow icon at the top right of each tile. This will open a new dialog where you can choose the target category to which the object should be moved.  
You will not be able to move a category to one of its child categories.  
This is useful if you want to move one object over multiple levels.

## Manage Templates
On the manage templates page you see all templates that currently exist. By pressing Create template the template form will open and you can create a new template. By clicking on an existing template you can edit the existing template.

## Npc Form
By clicking on an existing template, existing npc, creating a new npc or creating a new template you will be redirected to the npc form.

### Buttons
At the top of the form you will find several buttons:
 * **Save**: Will save the current npc or template
 * **Save & distribute fields to npcs**: This button is only available if you are working on a template. By pressing this button the template will be saved and all new fields will be distributed to all npcs based on this template. Please note: If you delete a field from an npc and distribute the fields of the template this field will be added again.
 * **Add field**: This drop down list allows you to add a new field to the current npc or template. You can choose between a single line text field, multi line text field and, a number field, a dropdown field and a field group. After selecting a field type you must provide a name of the field and add it to the npc or template.
 * **Mark as implemented**: This button will only be available if the current user is an implementation status tracker and working on an npc. If the current npc is not implemented you can click on this button to see the changes to the npc and flag it as implemented. If the current npc is already implemented this button will be labeled with implemented and be disabled.
 * **Export Template**: Allows you to customize the export template of the current object. See [Export Templates](/steffendx/GoNorth/wiki/ExportTemplates) for more details.
 * **Export**: This button will give you a dropdown list with additional functionality, all part of exporting the npc:
    * **Script**: This will export the npc as a script based on the existing [Export Templates](/steffendx/GoNorth/wiki/ExportTemplates)
    * **JSON**: This will export the npc as a JSON file
    * **Language File**: This will export the used language keys and their value as a language file based on the existing language file template
    * **Export snippets**: This will open a dialog that allows you to customize the export snippets of the npc. See [Export Snippets](/steffendx/GoNorth/wiki/Export-Snippets) for more details.
    * **Regenerate Language Keys**: This will refresh all language keys. You can find more details on the [Export](/steffendx/GoNorth/wiki/Export) page.
 * **Dialog**: This button is only available if you are working on an npc and have the Tale role. By clicking this button you will switch to the [dialog of the npc](/steffendx/GoNorth/wiki/Tale).
 * **Name generator**: This button is only available if you are working on a template. By clicking this button you will be able to setup the name generator template. In the dialog you can enter the template by using different placeholders and test the generated names. You can find more information about the algorithm [here](http://rinkworks.com/namegen/instr.shtml) and [here](http://rinkworks.com/namegen/reference.shtml).
 * **Generate name**: This button is only available if you are working on an npc. By clicking this button a name for the npc will be generated based on the name generator template of the npc template on which the npc is based. If no name generator template was specified in the npc template this button will be disabled.
 * **Mark as player**: This button will only be available if the current user is a Kortisto Player Manager and working on an npc. This button allows the user to flag an npc as the player npc. This is important in quests and dialogs to be able to select player values in actions and conditions.
 * **Delete**: Allows the user to delete the npc or template.

### Image
On the left side the picture of the current npc will be displayed. If no picture is uploaded a placeholder icon will be displayed. You can add a picture to the npc or template by clicking on the picture or simply dropping an image on the icon. Please note: You can only add an image to an npc or template after saving the current form.

### Field list
In the main part of the form you will see the name of the npc and the list of fields of the npc. Here you can change the values of the fields. Additionally you can use one of the following buttons on the right of the name of the field:
 * **Arrows**: By clicking and dragging the arrows you can rearrange the fields
 * **Door with arrow**: By clicking this icon you can change the script settings of the field.  
 Please note: Currently this has no effect since script exporting is not yet implemented. I've implemented this to allow users to already set these values when creating quests to be ready for exporting.  
 This is not available for multi line text fields and field groups since they will not be exported to a script any way.  
 In the dialog you can set the following values:
   * **Additional script names**: You can provide additional names for script exporting here. This allows you to export the field to the script multiple times with different names. This way you can export CurrentHealth as MaxHealth as well for example.
   * **Dont export to script**: Dont export the selected field to the script.
 * **Pencil**: You can rename the field by clicking this icon and edit the available options for an option field.
 * **Trash bin**: You can delete the field by clicking this icon.

### Inventory
By clicking the Add item button you can add a new item to the inventory of the current npc or template. You will have to create the item in Styr for this.  
Below you will see a table with all the items that are currently in the inventory of the npc. In this table you will be able to set the quantity of items in the inventory as well as flagging the item as equipped (for weapons, and armor etc.).  
On the most right you will be able to click the trash bin icon to delete the item from the inventory.

### Skills
By clicking the Add skill button you can add a new skill the npc can cast. You will have to create the skill in Evne for this.  
Below you will see a table with all the skills that the npc can cast.  
On the most right you will be able click the trash bin icon to delete the skill.

### Daily routines
In this section you can define the daily routine of the npc, as well as displaying it.  

In the table of this section you will see all daily routine events that were already created for this npc. This table will be sorted using the time of the events. To get a clearer view of the default daily routine you can hide disabled events using the "Hide disabled events" button.  
If an event has a script associated to it, you can click on the name of the script to edit it.  
On the right of each event you will find the following buttons:
 * **Pencil**: Allows you to edit the time of the event and change if it is disabled by default or not.
 * **Trash bin**: You can delete the event using this icon.

Using the new movement target button you will be redirected to Karta where you can place the different movement targets of the npc during the day. You can find more details on this in the [Karta wiki page](/steffendx/GoNorth/wiki/Karta#npc-daily-routine).  
By pressing the New script event button, a dialog will open that allows you to specify the time of day at which this event triggers. You can specify an earliest and latest time to give the daily routine of the npc a bit more varity. If your project is not using a 24 hour day, you can change this in the [Project Config](/steffendx/GoNorth/wiki/Project-Config). Here you can also select if this event is activated by default or not (you can activate the daily routine later on using an "enable daily routine event" action in a node system for example.)  
After pressing next you will have to choose if you want to add a node system script or a code script. **Please note:** This can not be changed later on.  

#### Node system
If you choose to create a node system as script you can use condition and action nodes to specify the action that should be run. You can find more details on building a script using a node system in the [Tale](/steffendx/GoNorth/wiki/Tale) wiki page.  
You will also have to specify a name for better usability.

#### Code sript
If you create a code script an editor will open where you can enter an arbitrary script that should be run. This gives you maximal flexibility, but will require coding skills and might be harder to maintain later on because you can not simply change a template.  
You will also have to specify a name for better usability.

### Tags
In the tag box you can assign tags to the current template or npc. These tags are used in the npc search (either in the npc list page or when choosing an npc in the object select dialog).

### Reference Display
If you have an npc open and not a template you can see a list of references where the current npc is used. This will show you the quests, wiki pages, maps and dialogs in which the npc is used.

## Bulk Import / Export values and objects
### Export objects / values
To help you balance, analyze or transfer your Npc values GoNorth offers a function to bulk export or import Npcs. To use this you have to navigate to the Npc List and select "Export field values".  
This will open a new dialog which allows you to select a template for which you want to export the objects and the fields you want to export. Once you confirm this selection you will be provided with a CSV-File containing the objects you have just selected. **Please note:** Only the objects inside the current folder or below are exported. If you want to export all objects you have to navigate to the root level.

### Import objects / values
Next to the "Export field values" button you will find an "Import field values" button. This allows you to import a previously exported CSV-File. You can update the values inside the CSV-File to bulk update a list of Npcs to improve balancing or simply update a lot of fields. Just make sure to not change the Id column since this is required to match the Npc which must be updated.  
To import a CSV-File you have to hit the "Import field values" button and then drag the CSV-File into the offered dropzone. Once you drop the file GoNorth will analyze its content and present you with a preview of objects that will be updated or created. You can deselect a line if you are not happy with the changes, this line will be ignored. After making sure all the values are correct you can hit the import button and the values will be imported for real.  
Once the import process is finished the results will be displayed with each row indicating success, error or no change. You can also export the results into a CSV file to save for later use and reference.

If you open the import field values dialog you can also show a list of previous imports in order to check the history of figure out the source of a bulk import.