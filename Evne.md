Evne is the skill planning module of GoNorth. You can access it from the Evne tile on the home page or the navigation on the top.  
Evne allows you to build your own templates with different fields. This way you can build a template for attack skills which have a damage type and damage value while a healing template has an amount of health healed by it.  
Please note: While a user edits a skill or template this skill or template will be readonly for other users to prevent them from overwriting each others changes.

## Skill List
You will see a list of skills and categories after navigating to Evne.  
By using the search box you can search for skills. This will search in the name and the tags assigned to a skill.

By clicking on create category you can create a new category for skills. You can think of categories as folders in the file system. This way you can organize your different skills.  
A category can be given a name, a description and an image. The description will be shown on mouse hover over the image or icon of the category.  
Each category can be edited using the pencil icon on the top right of the tile. You can also delete a category by pressing the trash bin icon. Please note: You can only delete empty categories.

By clicking on the create skill button you can choose a template and create a new skill based on this template. If no templates are shown there you will have to create a new template first by clicking on the manage template link in the drop down list.

### Moving Skills or folders to other categories
If you want to move a skill or folder to a different category you can drag that object onto a different existing folder and drop it there. Afterwards the dragged object will be moved into that category.  
To move an object up a level, a small grey area with a fitting icon will be diplayed while dragging an object. If you drop that object in this area, the object will be moved one level up.  
Using drag and drop you can quickly move objects one level up or down.  

Alternatively you can press the rectangle with an arrow icon at the top right of each tile. This will open a new dialog where you can choose the target category to which the object should be moved.  
You will not be able to move a category to one of its child categories.  
This is useful if you want to move one object over multiple levels.

## Manage Templates
On the manage templates page you see all templates that currently exist. By pressing Create template the template form will open and you can create a new template. By clicking on an existing template you can edit the existing template.

## Skill Form
By clicking on an existing template, existing skill, creating a new skill or creating a new template you will be redirected to the skill form.

### Buttons
At the top of the form you will find several buttons:
 * **Save**: Will save the current skill or template
 * **Save & distribute fields to skills**: This button is only available if you are working on a template. By pressing this button the template will be saved and all new fields will be distributed to all skills based on this template. Please note: If you delete a field from a skill and distribute the fields of the template this field will be added again.
 * **Add field**: This drop down list allows you to add a new field to the current skill or template. You can choose between a single line text field, multi line text field and, a number field, a dropdown field and a field group. After selecting a field type you must provide a name of the field and add it to the skill or template.
 * **Mark as implemented**: This button will only be available if the current user is an implementation status tracker and working on a skill. If the current skill is not implemented you can click on this button to see the changes to the skill and flag it as implemented. If the current skill is already implemented this button will be labeled with implemented and be disabled.
 * **Export Template**: Allows you to customize the export template of the current object. See [Export Templates](/steffendx/GoNorth/wiki/ExportTemplates) for more details.
 * **Export**: This button will give you a dropdown list with additional functionality, all part of exporting the skill:
    * **Script**: This will export the skill as a script based on the existing [Export Templates](/steffendx/GoNorth/wiki/ExportTemplates)
    * **JSON**: This will export the skill as a JSON file
    * **Language File**: This will export the used language keys and their value as a language file based on the existing language file template
    * **Export snippets**: This will open a dialog that allows you to customize the export snippets of the skill. See [Export Snippets](/steffendx/GoNorth/wiki/Export-Snippets) for more details.
    * **Regenerate Language Keys**: This will refresh all language keys. You can find more details on the [Export](/steffendx/GoNorth/wiki/Export) page.
 * **Delete**: Allows the user to delete the skill or template.

### Image
On the left side the picture of the current skill will be displayed. If no picture is uploaded a placeholder icon will be displayed. You can add a picture to the skill or template by clicking on the picture or simply dropping an image on the icon. Please note: You can only add an image to a skill or template after saving the current form.

### Field list
In the main part of the form you will see the name of the skill and the list of fields of the skill. Here you can change the values of the fields. Additionally you can use one of the following buttons on the right of the name of the field:
 * **Arrows**: By clicking and dragging the arrows you can rearrange the fields
 * **Door with arrow**: By clicking this icon you can change the script settings of the field.  
 Please note: Currently this has no effect since script exporting is not yet implemented. I've implemented this to allow users to already set these values when creating quests to be ready for exporting.  
 This is not available for multi line text fields and field groups since they will not be exported to a script any way.  
 In the dialog you can set the following values:
   * **Additional script names**: You can provide additional names for script exporting here. This allows you to export the field to the script multiple times with different names. This way you can export CurrentHealLeft as MaxHeal as well for example.
   * **Dont export to script**: Dont export the selected field to the script.
 * **Pencil**: You can rename the field by clicking this icon and edit the available options for an option field.
 * **Trash bin**: You can delete the field by clicking this icon.

### Skill flow
After the main fields of the skill you can find a node graph system which helps you to describe the flow of the skill. As an example this can be used for a fireball to display: Player channels skill -> Fireball is launched -> Target Npc takes damage -> Target Npc is burning.  
The following nodes can be dragged into the node graph system:
 * **Text**: A text node can be used to describe a step in the skill flow.
 * **Condition**: A condition to branch the skill. By pressing the "+" at the top next to the "x" you can add a new condition. By pressing on the condition text you can edit the condition, see condition dialog below. Next to each condition you find the following icons:
    * **Arrows**: Using the arrows you can rearrange the the different conditions
    * **Trash bin**: By clicking this icon you can delete the condition
* **Action**: An action to trigger. The following actions are available:
    * **Change skill value**: Change a value of the skill
    * **Change player value**: Change a value of the player
    * **Change player state**: Allows you to change the state of the player. If you are using a state machine for npcs you can use this as a state in the state machine, if not you can use this to specify if the player is confused for example.
    *  **Change target npc state**: Allows you to change the state of the target npc of the skill. If you are using a state machine for npcs you can use this as a state in the state machine, if not you can use this to specify if the npc is angry for example.
    * **Wait**: Allows you to specify an amount of time to wait. The time can be specified in real time or game time.

### Condition dialog
When editing a condition the condition dialog will open. At the top of the condition dialog you will find the following buttons:
 * **Add condition**: Adds a new condition. By default all conditions on the root level are grouped with and "And" operator
 * **And**: Group the selected conditions with an "And" operator
 * **Or**: Group the selected conditions with an "Or" operator

Below you find a list of conditions. You can select a type of condition from the drop down list. The following conditions are available:
 * **Check skill value**: Check a value of the skill.
 * **Check player value**: Check a value of the player.
 * **Check pick quest value**: Allows you to pick a quest and check a value of this quest
 * **Check quest state**: Allows you to pick a quest and check the state of the quest
 * **Check npc alive state**: Allows you to pick an npc and check if the npc is alive or dead
 * **Check game time**: Allows you check if the current game time is before or after a specified time. If your project is not using a 24 hour day, you can change this in the [Project Config](/steffendx/GoNorth/wiki/Project-Config).
 * **Check random value**: Allows you to compare a random value to a certain value using different operators. This can be used if you want to add some varity in a skill.

On the right of each condition you will find the following icons:
 * **Arrows**: Allows you to rearrange the conditions
 * **Move indicator**: Allows you to drag the condition into a different condition group
 * **Trash bin**: Allows you to delete the condition. If you click this for a group the conditions will stay and just the grouping will be removed

At the bottom you can press confirm to confirm the condition and cancel to cancel the editing of the condition.

### Tags
In the tag box you can assign tags to the current template or skill. These tags are used in the skill search (either in the skill list page or when choosing an skill in the object select dialog).

### Reference Display
If you have an skill open and not a template you can see a list of references where the current skill is used. This will show you the quests, wiki pages, dialogs and npcs which can use the skill.

## Bulk Import / Export values and objects
### Export objects / values
To help you balance, analyze or transfer your skill values GoNorth offers a function to bulk export or import skills. To use this you have to navigate to the skill List and select "Export field values".  
This will open a new dialog which allows you to select a template for which you want to export the objects and the fields you want to export. Once you confirm this selection you will be provided with a CSV-File containing the objects you have just selected. **Please note:** Only the objects inside the current folder or below are exported. If you want to export all objects you have to navigate to the root level.

### Import objects / values
Next to the "Export field values" button you will find an "Import field values" button. This allows you to import a previously exported CSV-File. You can update the values inside the CSV-File to bulk update a list of skills to improve balancing or simply update a lot of fields. Just make sure to not change the Id column since this is required to match the skill which must be updated.  
To import a CSV-File you have to hit the "Import field values" button and then drag the CSV-File into the offered dropzone. Once you drop the file GoNorth will analyze its content and present you with a preview of objects that will be updated or created. You can deselect a line if you are not happy with the changes, this line will be ignored. After making sure all the values are correct you can hit the import button and the values will be imported for real.  
Once the import process is finished the results will be displayed with each row indicating success, error or no change. You can also export the results into a CSV file to save for later use and reference.

If you open the import field values dialog you can also show a list of previous imports in order to check the history of figure out the source of a bulk imp