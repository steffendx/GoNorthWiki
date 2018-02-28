Kortisto is the npc planning module of GoNorth. You can access it from the Kortisto tile on the home page or the navigation on the top.  
Kortisto allows you to build your own templates with different fields. This way you can build a template for humans for example which has a health value, strength but also a background text box to provide more details for this npc. A monster template on the other hand might include a health and strength field but not a background text box since its just an enemy.  
Please note: While a user edits a npc or template this npc or template will be readonly for other users to prevent them from overwriting each others changes.

## Npc List
You will see a list of npcs and categories after navigating to Kortisto.  
By using the search box you can search for npcs. This will search in the name and the tags assigned to a npc.

By clicking on create category you can create a new category for npcs. You can think of categories as folders in the file system. This way you can organize your different npcs.  
Each category can be renamed using the pencil icon on the top right of the tile. You can also delete a category by pressing the trash bin icon. Please note: You can only delete empty categories.

By clicking on the create npc button you can choose a template and create a new npc based on this template. If no templates are shown there you will have to create a new template first by clicking on the manage template link in the drop down list.

## Manage Templates
On the manage templates page you see all templates that currently exist. By pressing Create template the template form will open and you can create a new template. By clicking on an existing template you can edit the existing template.

## Npc Form
By clicking on an existing template, existing npc, creating a new npc or creating a new template you will be redirected to the npc form.

### Buttons
At the top of the form you will find several buttons:
 * **Save**: Will save the current npc or template
 * **Save & distribute fields to npcs**: This button is only available if you are working on a template. By pressing this button the template will be saved and all new fields will be distributed to all npcs based on this template. Please note: If you delete a field from a npc and distribute the fields of the template this field will be added again.
 * **Add field**: This drop down list allows you to add a new field to the current npc or template. You can choose between a single line text field, multi line text field and a number field. After selecting a field type you must provide a name of the field and add it to the npc or template.
 * **Mark as implemented**: This button will only be available if the current user is an implementation status tracker and working on a npc. If the current npc is not implemented you can click on this button to see the changes to the npc and flag it as implemented. If the current npc is already implemented this button will be labeled with implemented and be disabled.
 * **Dialog**: This button is only available if you are working on a npc and have the Tale role. By clicking this button you will switch to the [dialog of the npc](/steffendx/GoNorth/wiki/Tale).
 * **Mark as player**: This button will only be available if the current user is a Kortisto Player Manager and working on a npc. This button allows the user to flag an npc as the player npc. This is important in quests and dialogs to be able to select player values in actions and conditions.
 * **Delete**: Allows the user to delete the npc or template.

### Image
On the left side the picture of the current npc will be displayed. If no picture is uploaded a placeholder icon will be displayed. You can add a picture to the npc or template by clicking on the picture or simply dropping an image on the icon. Please note: You can only add an image to a npc or template after saving the current form.

### Field list
In the main part of the form you will see the name of the npc and the list of fields of the npc. Here you can change the values of the fields. Additionally you can use one of the following buttons on the right of the name of the field:
 * **Arrows**: By clicking on the arrows you can rearrange the fields
 * **Door with arrow**: By clicking this icon you can change the script settings of the field.  
 Please note: Currently this has no effect since script exporting is not yet implemented. I've implemented this to allow users to already set these values when creating quests to be ready for exporting.  
 This is not available for multi line text fields since they will not be exported to a script any way.  
 In the dialog you can set the following values:
   * **Additional script names**: You can provide additional names for script exporting here. This allows you to export the field to the script multiple times with different names. This way you can export CurrentHealth as MaxHealth as well for example.
   * **Dont export to script**: Dont export the selected field to the script.
 * **Pencil**: You can rename the field by clicking this icon.
 * **Trash bin**: You can delete the field by clicking this icon.

### Inventory
By clicking the Add item button you can add a new item to the inventory of the current npc or template. You will have to create the item in Styr for this.  
Below you will see a table with all the items that are currently in the inventory of the npc. In this table you will be able to set the quantity of items in the inventory as well as flagging the item as equipped (for weapons, and armor etc.).  
On the most right you will be able to click the trash bin icon to delete the item from the inventory.

### Tags
In the tag box you can assign tags to the current template or npc. These tags are used in the npc search (either in the npc list page or when choosing a npc in the object select dialog).

### Reference Display
If you have a npc open and not a template you can see a list of references where the current npc is used. This will show you the quests, wiki pages, maps and dialogs in which the npc is used.