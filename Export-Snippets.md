Sometimes you might want to have a special behaviour when an item is equipped or the player picks it up. This could be a change in the stats of the player or maybe add a new entry in the quest log.  
The same might be required if a special npc dies and so on.  

To accomplish this you could change the template of that npc or item, but by doing this you would loose the inheritance from the shared template and changes would require a lot more work. This would also require the person to do the change to have coding skills because you can not use a node system for that.  

To create special logic for each object like this in a way that is easier and better to maintain, I have implemented support for export snippets. You can think of these as special hooks in the different templates which can be adjusted per object (or not be filled at all). To fill them the user can use a node system or enter code. This way you still keep inheritance and the snippets can be filled even by users who have no coding skills by using a node system.

## Adjusting the templates
At the moment the npc, item and skill templates support export snippets. To specify one you can simply add a placeholder called "{{CodeSnippet_*NAME_OF_SNIPPET*}}". By replacing NAME_OF_SNIPPET with the name of the snippet you can create a new snippet which can be filled for each object that is using this template. To add a new snippet that can be filled with special logic when an item gets picked up you could for example create a snippet called {{CodeSnippet_OnPickup}}.  

Since a node system might need to generate additional functions there exists also a placeholder called "{{CodeSnippetAdditionalFunctions_*NAME_OF_SNIPPET*}}". This will be replaced by the additional functions of that node snippet.

You can also render a certain part of the template only if a template is filled by using the "{{HasCodeSnippet_*NAME_OF_SNIPPET*_Start}}" and "{{HasCodeSnippet_End}}" placheolders.

So to put this all together, this is an example of what a code snippet in an item template might look like:  

    {{HasCodeSnippet_OnPickup_Start}}function OnPickup(this)
      {{CodeSnippet_OnPickup}}
    end{{Has_CodeSnippetAdditionalFunctions_OnEquip_Start}}
    
    {{CodeSnippetAdditionalFunctions_OnEquip}}

    {{Has_CodeSnippetAdditionalFunctions_End}}{{HasCodeSnippet_End}}


One can find more details about the supported template placeholders when editing the export template of a npc, item or skill.

## Filling Export Snippets
If the user has export permissions, that user can press the export button in the npc, item or skill form and then select export snippets.  
This will open a new dialog in which all the available export snippets of the template are listed.  
By pressing on one of the snippets you will be presented with a choice: Create a node system or enter code. **Please note:** This can not be changed later on, you will have to delete the existing snippet and then fill it again.  
After you have made your choice you will have to enter a name (used to be able to know at a quick glance what this snippet does in this special case) and fill the content. Once you press confirm the snippet will be saved and when you export the object the next time, this snippet will be filled.  

If you want to delete a filled snippet, you can press the trash bin icon next to that snippets name. **Please note:** This will only remove the filled content for that snippet for the current object, not the placeholders in the template.

## Sample Snippets
The following code is an example for a npc template to add an OnDeath Snippet (Check the region after the "----- Hooks ---" Section for the interesting parts):

    ----- Includes ----------

    include_file("_BaseNpc.lua")

    include("Npc")

    ----- Init Functions ----

    function OnInit(this)
        -- Values
        this:add_localized_string_value("Name", "{{FlexField_Name_LangKey}}")

        {{FlexField_UnusedFields}}

        {{Npc_HasItems_Start}}-- Inventory
        {{Npc_Inventory}}
        {{Npc_HasItems_End}}
        {{Npc_HasSkills_Start}}-- Skills
        {{Npc_Skills}}
        {{Npc_HasSkills_End}}
        {{Npc_HasDailyRoutine_Start}}-- Daily Routine Events
        {{Npc_DailyRoutine_Events}}{{Npc_HasDailyRoutine_End}}

        {{Dialog_HasDialog_Start}}this:register_message_function("OnTalk", "DialogStart"){{Dialog_HasDialog_End}}
    end

    ------ States -----------

    {{Dialog_HasDialog_Start}}
    ------ Dialog -----------

    function DialogStart(this)
        {{Dialog_Start}}
    end

    {{Dialog_Additional_Functions}}
    {{Dialog_HasDialog_End}}

    {{Npc_HasDailyRoutine_Start}}
    ------ Daily Routine ----
    {{Npc_DailyRoutine_Functions}}
    {{Npc_HasDailyRoutine_End}}{{HasAnyCodeSnippet_Start}}
    ------ Hooks ------------
    {{HasCodeSnippet_OnDeath_Start}}
    function OnDeath(this)
        {{CodeSnippet_OnDeath}}
    end{{Has_CodeSnippetAdditionalFunctions_OnDeath_Start}}

    {{CodeSnippetAdditionalFunctions_OnDeath}}
    {{Has_CodeSnippetAdditionalFunctions_End}}{{HasCodeSnippet_End}}{{HasAnyCodeSnippet_End}}