If you want to add a custom format for exporting or implemented a new dialog node type, dialog condition or dialog action you will have to extend the exporter logic.  

All the important exporter logic can either be found in the "ExportApiController" under "/Controller/Api", "/Data/Exporting/"  or in the exporting services under "/Services/Export".

## Implementing a new export file format
If you want to export to a new file format you will have to implement a custom **IObjectExporter**. You should create a new folder under the "/Services/Export" folder for this.  
Here you will have to implement the following method:
 * **ExportObject**: This is the entry method for your object export. The export template will be passed in here based on the object type beeing exported (npc, item or skill). The ExportObjectData parameter will contain the object to export (npc, item, skill). See the ExportConstants class for possible values saved in there, but the most important one is the ExportConstants.ExportDataObject.

I recommend you take a look at the "/Services/Export/JsonExporter.cs" and "/Services/Export/Script/ScriptExporter.cs" files.  

After implementing your new object exporter you will have to add it in the _exporters dictionary in the **ExportApiController**.  
Now your new exporter can be called using the api and all you have to do is add it in the frontend by modifying the "/Views/FlexFieldDatabase/ObjectFormDialogsButton.cshtml" and adding a new button. Your export type must match the key you used for adding the exporter in the _exporters dictionary before.

## Adding a new template type
To add a new template type to GoNorth (for example for a new dialog node type, condition or action) you will have to do the following steps:
 * Add your new template type to the TemplateType enum under "/Data/Exporting".
 * Add the new template type to the _DefaultTemplates list of the **ExportDefaultTemplateProvider** class. You have to choose the category to which your new template belongs. This will make sure that your new template will be shown in the template list.
 * Add a translation in the "/Resources/Controllers/Api/ExportApiController.xx.json" files. The language key must be "TemplateType<<YourNewTemplateTypeEnum>>".
 * Add a new default template content file under "DefaultExportTemplates/<<TheCategoryYouChooseBefore>>/<<YourNewTemplateTypeEnum>>.lua"
 * Use your new template type by using the new enum value when calling the **GetDefaultTemplateByType** of the default template provider.

## Creating a new placeholder resolver
If you want to implement a new class to resolve certain placeholders, you can do so in the "/Services/Export/Placeholders" folder.  
Here you find placeholder resolvers to the different topics (like FlexFieldValues, Inventory, Skills and Dialogs).  
If you want to create a new placeholder resolver you will have to create a class and implement the **IExportTemplateTopicPlaceholderResolver** interface. I personally recommend you inherit from **BaseExportPlaceholderResolver** as well since this will give you some base functions. 
The important methods when implementing a new topic placeholder resolver are:
 * **IsValidForTemplateType**: Return true if the placeholder resolver is valid for a certain template type, otherwise falls. This way you can determine to which template type your placeholder resolver applies and will update placeholders as well as returning a list of placeholders to be displayed in the template edit form.
 * **FillPlaceholders**: Fills the placeholders for a block of code. The ExportObjectData parameter will contain the object to export (npc, item, skill). See the ExportConstants class for possible values saved in there, but the most important one is the ExportConstants.ExportDataObject.
 * **GetExportTemplatePlaceholdersForType**: This method must return the list of placeholder descriptions for a certain template type. This description will be used to display the list above the code editor in the edit form. 

After implementing your new placeholder resolver you will have to add it to the **ExportTemplatePlaceholderResolver** constructor. This way your new placeholder will be called while exporting.  

## Implementing a new dialog node type exporter
If you have implemented a new dialog node type you will have to implement a dialog node renderer for this new node type to allow exporting of this node.  
For this you will have to implement a new class in the "/Services/Export/Dialog" folder and implement the **IExportDialogStepRenderer** interface.I personally recommend you inherit from **ExportDialogBaseStepRenderer** as well since this will give you some functions for basic node placeholder exporting.  
The following methods must be implemented:
 * **RenderDialogStep**: Renders the dialog step. You will have to check if your dialog step renderer applies to the current node passed in for the ExportDialogData. If not you must simply return null to indicate that the next renderer must be checked. Otherwise you will have to fill your template and return the code of the dialog step.
 * **BuildParentTextPreview**: This function will be called to build a preview text for the node to show for the **Tale_Function_ParentPreview** placeholder. This should be one line and fairly short.
 * **HasPlaceholdersForTemplateType**: This function must return true if the current dialog step renderer has placeholders for a template type. This is important for the placeholders to be shown in the list above the code editor.
 * **GetPlaceholdersForTemplate**: Must return the list of placeholder descriptions for a certain template type. This is very similiar to the function **GetExportTemplatePlaceholdersForType** of the **IExportTemplateTopicPlaceholderResolver** interface.   
 **Please note**: This method will only be called if the **HasPlaceholdersForTemplateType** function returned true.

After implementing your new dialog node renderer you will have to add it in the **SetupStepRenderes** method of the **ExportDialogRenderer** class in order to be called.

## Condition element exporter
Similiar to implementing a new dialog step renderer after creating a new node type, you will have to implement a new condition renderer after creating a new dialog condition.  
The classes for condition rendering can be found under "/Services/Export/Dialog/ConditionRendering".  
Here you will have to add your new condition type to the ConditionType enum. The value for the enum must match with the condition type number in the JavaScript condition class.
When implementing a new condition renderer you will have to implement a new class implementing the **IConditionElementRenderer** interface. But I recommend that you inherit from the **BaseConditionRenderer**. This class provides helpful functions for parsing the condition data (see existing condition renderes for details).  
The following methods must be implemented:
 * **BuildSingleConditionElement**: Builds the code for the condition element.
 * **HasPlaceholdersForTemplateType**: Similiar to the functions above, this method must return true if the condition renderer has placeholders for a certain template type. This is important for the placeholders to be displayed above the code editor in the template edit form.
 * **GetExportTemplatePlaceholdersForType**: Must return the list of placeholder descriptions for a certain template type. This is very similiar to the function **GetExportTemplatePlaceholdersForType** of the **IExportTemplateTopicPlaceholderResolver** interface.   
 **Please note**: This method will only be called if the **HasPlaceholdersForTemplateType** function returned true.

After implementing your new condition renderer you will have to add it in the constructor of the **ConditionRenderer** class. Here you will have to add it to the dictionary using the new ConditionType you added before as a key and a new instance of your new condition renderer.

## Action exporter
In order for actions to be able to be exported, an action renderer is required. The code for action rendering can be found under "/Services/Export/Dialog/ActionRendering".  
Here you will have to add your new action type to the ActionType enum. The value for the enum must match with the action type number in the JavaScript action class.
When implementing a new action renderer you will have to create a new class implementing the **IActionRenderer** interface. But I recommend that you inherit from the **BaseActionRenderer**. This class provides helpful functions for parsing the action data (see existing action renderes for details).  
The following functions must be implemented:
 * **BuildActionElement**: Builds the code for the new action type.
 * **BuildPreviewText**: This method must return a small text preview for the action. This is used to fill the **Tale_Function_ParentPreview** placeholder.
 * **HasPlaceholdersForTemplateType**: This function must return true if the action render has placeholders for a certain template type. This is important for the placeholders to be shown above the code editor in the template edit form.
 * **GetExportTemplatePlaceholdersForType**: Must return the list of placeholder descriptions for a certain template type. This is very similiar to the function **GetExportTemplatePlaceholdersForType** of the **IExportTemplateTopicPlaceholderResolver** interface.   
 **Please note**: This method will only be called if the **HasPlaceholdersForTemplateType** function returned true.

After implementing the new action renderer you will have to add it to the action renderer dictionary in the constructor of the **ExportDialogActionRenderer** class. Here you will have to add it to the dictionary using the new ActionType you added before as a key and a new instance of your new action renderer.