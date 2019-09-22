GoNorth allows exporting of the following objects:
 * NPCs, their dialogs and daily routines
 * Items
 * Skills

The supported file formats are:
 * JSON
 * Scripts based on customizable [Export Templates](/steffendx/GoNorth/wiki/ExportTemplates) which are extensible using [Export Snippets](/steffendx/GoNorth/wiki/Export-Snippets)
 * Language files

**Please note:** A user needs the "ExportObjects" role to be allowed to export any object. 

## Exporting Objects
To export an npc, item or skill you will have to navigate to the detail page of the corresponding object.  
There you will find the Export Button from which you can choose the target file format to export.  
After selecting the file format a new dialog will open to show you the result of the export and allowing you to download the resulting file.  

### JSON
The JSON export will output all the different values stored for the object in the database.  
For an npc this will also include the dialog from the database which is stored in a different collection in the database, but since it belongs to the npc it will be exported here as well.

### Script
The Script export will generate a script based on the different values of the object. For this different script templates are used which can be changed using different placeholders (see [Export Templates](/steffendx/GoNorth/wiki/ExportTemplates)).  
It is possible to use language keys here instead of the actual text. This way it is possible to localize the resulting script into different languages.

### Language File
The language file export will generate a language file based on the language file template. Here all the generated language keys will be listed using the key and the text of the language key. You can then take these files and translate them to different languages.  
A language key will stay constant even if the object is renamed to prevent a missmatch for existing translations on change of the object name. You can however select the "Regenerate Language Keys" button from the export dropdown button to force GoNorth to generate new keys during the next export. This might require you to update existing translations files however.