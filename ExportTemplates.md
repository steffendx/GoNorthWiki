GoNorth uses customizable templates for exporting objects to script or language file format.  
These templates can be customized after selecting the menu button "Export".

**Please note:** A user needs the "ManageExportTemplates" role to be allowed to export any object. 

## Default Templates
The application includes some default templates to help you getting a feel for how to use these templates and allowing you to change the existing templates and see the effects.  
These default templates are created in LUA, but you will have to adjust them to suite your needs.

## Customizing Templates
After navigating to the export module of the system you will see a list of the different templates.  
On the left you have different categories to help you keep track of the different templates.  
After selecting a template you will be navigated to the template editing page.  
Here you can find a code editor for updating the template.  
Above the code editor a list of usable placeholders for the current template type will be shown. This list will always show you which placeholders can be used and what their meaning and usage is in the current context. For this reason I will not list all the different placeholders here since there are quite a few, but recommend you to take a look at them in GoNorth itself.  
The included editor will also provide intellisense for the different placeholders. These will be marked as placeholder on the right in the intellisense dropdown.  
**Please note:** A placeholder must always be wrapped in "{{" and "}}".

### Rendering Engines
GoNorth supports two rendering engines for templates: Legacy mode and [Scriban](https://github.com/lunet-io/scriban). All new templates will use Scriban for rendering as this is a lot more flexibel.  
But to help users switching from an old version of GoNorth to a newer version, the old templates are still supported. This way you can adjust the templates to Scriban when needed and your exports will still work.  
**Please note**: I will probably drop support for Legacy mode in the future so that I can clean up the export code. Therefore I recommend you to switch to Scriban templates.  

## Include Templates
You might want to share code between a lot of different templates. To help you prevent duplicated code and make the implementation of new templates faster and less error prone, GoNorth supports so called Include Templates.  
By selecting "Include Templates" in the categories of the export template overview you can create new templates or edit existing ones.  
Inside of the include template create / edit page you will have a code editor along with a list of templates that are using this include template. **Please note:** If you are referencing an include template using a variable or function, this reference will not be listed here.  

You can use these include templates by using the following command:

    {{ include "<NAME OF THE TEMPLATE>" }}  

This can not only be helpful for including actual text in different templates, but also to provide utility [Scriban Functions](https://github.com/lunet-io/scriban/blob/master/doc/language.md#7-functions) to templates.  

**Please note**: Include templates are not supported in legacy mode.

## Dialog Function Generation Rules
To allow you to have control at which point the generated script for a dialog will branch into a new function you can press the "Dialog function generation" button at the top of the template list.  
Here you can create rules that will determine at which point a new function is generated in the dialog export.  
The following conditions can be used:
 * **Multiple parents**: The current node will start a new function if it has multiple parents. This is useful to not have redundant code in the resulting script.
 * **Parent node type**: If any of the parent nodes of the current node is of the specified type, the current node will generate a new function.
 * **Node type**: If the current node is of the specified type, the current node will generate a new function.
 * **Child node type**: If any of the child nodes of the current node is of the specified type, the current node will generate a new function.
 * **Parent action type**: If any parent node of the current node is an action node and of the specified action type, the current node will generate a new function.
 * **Action type**: If the current node is an action node and of the specified action type, the current node will generate a new function.
 * **Child action type**: If any child node of the current node is an action node and of the specified action type, the current node will generate a new function.

GoNorth comes with a set of default rules for function generation to help you get started. These are mainly creating a new function if the dialog branches because of a choice node or because of a condition. I recommend to keep these rules.  
There are also rules that a new function will be generated if the previous action is of type "Persist dialog state". This is meant as an example of a different type of conditions.

## Export Settings
At the template list page one can also change the export settings. This can be done using the "Settings" button at the top of the page.  
The following settings can be changed here:
 * **Script language**: Script language to be used for the script export. This will change the syntax highlighting in the code editor as well as the file extension when downloading the file.
 * **Escape character**: Character used for escaping characters in a string, i.e. "\"
 * **Characters needing escaping**: Characters that need escaping, they will be escaped using the escape character specified above. Usually characters like " or \ need to be escaped.
 * **Newline character**: Character used for creating a newline. This will be used to replace linebreaks with to prevent a string taking multiple lines. Leaving this blank will leave line breaks as they are.
 * **Language file language**: Language file language to be used for the language file export. This will change the syntax highlighting in the code editor for the language file template as well as the file extension when downloading the file.
 * **Language Escape character**: Character used for escaping characters in a string for the language file export, i.e. "\"
 * **Language Characters needing escaping**: Characters that need escaping during the language file export, they will be escaped using the escape character specified above. Usually characters like " or \ need to be escaped.
 * **Language Newline character**: Character used for creating a newline during the language file export. This will be used to replace linebreaks with to prevent a string taking multiple lines. Leaving this blank will leave line breaks as they are.
 

