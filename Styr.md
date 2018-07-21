Styr is the item planning module of GoNorth. You can access it from the Styr tile on the home page or the navigation on the top.  
Styr allows you to build your own templates with different fields. This way you can build a template for weapons which have a weapon type and damage value while a potion template has an amount of health healed by it.  
Please note: While a user edits an item or template this item or template will be readonly for other users to prevent them from overwriting each others changes.

## Item List
You will see a list of items and categories after navigating to Styr.  
By using the search box you can search for items. This will search in the name and the tags assigned to an item.

By clicking on create category you can create a new category for items. You can think of categories as folders in the file system. This way you can organize your different items.  
A category can be given a name, a description and an image. The description will be shown on mouse hover over the image or icon of the category.  
Each category can be edited using the pencil icon on the top right of the tile. You can also delete a category by pressing the trash bin icon. Please note: You can only delete empty categories.

By clicking on the create item button you can choose a template and create a new item based on this template. If no templates are shown there you will have to create a new template first by clicking on the manage template link in the drop down list.

## Manage Templates
On the manage templates page you see all templates that currently exist. By pressing Create template the template form will open and you can create a new template. By clicking on an existing template you can edit the existing template.

## Item Form
By clicking on an existing template, existing item, creating a new item or creating a new template you will be redirected to the item form.

### Buttons
At the top of the form you will find several buttons:
 * **Save**: Will save the current item or template
 * **Save & distribute fields to items**: This button is only available if you are working on a template. By pressing this button the template will be saved and all new fields will be distributed to all items based on this template. Please note: If you delete a field from an item and distribute the fields of the template this field will be added again.
 * **Add field**: This drop down list allows you to add a new field to the current item or template. You can choose between a single line text field, multi line text field and, a number field and a dropdown field. After selecting a field type you must provide a name of the field and add it to the item or template.
 * **Mark as implemented**: This button will only be available if the current user is an implementation status tracker and working on a item. If the current item is not implemented you can click on this button to see the changes to the item and flag it as implemented. If the current item is already implemented this button will be labeled with implemented and be disabled.
 * **Delete**: Allows the user to delete the item or template.

### Image
On the left side the picture of the current item will be displayed. If no picture is uploaded a placeholder icon will be displayed. You can add a picture to the item or template by clicking on the picture or simply dropping an image on the icon. Please note: You can only add an image to an item or template after saving the current form.

### Field list
In the main part of the form you will see the name of the item and the list of fields of the item. Here you can change the values of the fields. Additionally you can use one of the following buttons on the right of the name of the field:
 * **Arrows**: By clicking on the arrows you can rearrange the fields
 * **Door with arrow**: By clicking this icon you can change the script settings of the field.  
 Please note: Currently this has no effect since script exporting is not yet implemented. I've implemented this to allow users to already set these values when creating quests to be ready for exporting.  
 This is not available for multi line text fields since they will not be exported to a script any way.  
 In the dialog you can set the following values:
   * **Additional script names**: You can provide additional names for script exporting here. This allows you to export the field to the script multiple times with different names. This way you can export CurrentHealLeft as MaxHeal as well for example.
   * **Dont export to script**: Dont export the selected field to the script.
 * **Pencil**: You can rename the field by clicking this icon and edit the available options for an option field.
 * **Trash bin**: You can delete the field by clicking this icon.

### Tags
In the tag box you can assign tags to the current template or item. These tags are used in the item search (either in the item list page or when choosing an item in the object select dialog).

### Reference Display
If you have an item open and not a template you can see a list of references where the current item is used. This will show you the quests, wiki pages, maps, dialogs and inventories in which the item is used.