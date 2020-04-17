Sometimes you might want to have a special behaviour when an item is equipped or the player picks it up. This could be a change in the stats of the player or maybe add a new entry in the quest log.  
The same might be required if a special npc dies and so on.  

To accomplish this you could change the template of that npc or item, but by doing this you would loose the inheritance from the shared template and changes would require a lot more work. This would also require the person to do the change to have coding skills because you can not use a node system for that.  

To create special logic for each object like this in a way that is easier and better to maintain, I have implemented support for export snippets. You can think of these as special hooks in the different templates which can be adjusted per object (or not be filled at all). To fill them the user can use a node system or enter code. This way you still keep inheritance and the snippets can be filled even by users who have no coding skills by using a node system.

## Adjusting the templates
At the moment the npc, item and skill templates support export snippets. To specify one you can simply add a placeholder called "{{ export_snippets.snippets.*NAME_OF_SNIPPET*.all_functions }}". By replacing NAME_OF_SNIPPET with the name of the snippet you can create a new snippet which can be filled for each object that is using this template. To add a new snippet that can be filled with special logic when an item gets picked up you could for example create a snippet called {{ export_snippets.snippets.OnPickup.all_functions }}.  

Since a node system might need to generate additional functions this will be an array of functions used for the code snippet. If you only want to get the initial function or additional functions you can use the following placeholders "{{ export_snippets.snippets.*NAME_OF_SNIPPET*.initial_function.code }}" or "{{ export_snippets.snippets.*NAME_OF_SNIPPET*.additional_functions }}". You can find more details in the listed placeholders of the [export form](/steffendx/GoNorth/wiki/ExportTemplates#customizing-templates)

You can also render a certain part of the template only if a template is filled by using the "{{ if export_snippets.snippets.*NAME_OF_SNIPPET*.exists }}" and "{{ end }}" placheolders.

So to put this all together, this is an example of what a code snippet in an item template might look like:  

    {{~ if export_snippets.snippets.OnPickup.exists ~}}

    {{~ for snippet_function in export_snippets.snippets.OnPickup.all_functions ~}}
    {{ snippet_function | export_snippet_function }}
    {{~ end ~}}
    
    {{~ end ~}}


One can find more details about the supported template placeholders when editing the export template of an npc, item or skill.

## Filling Export Snippets
If the user has export permissions, that user can press the export button in the npc, item or skill form and then select export snippets.  
This will open a new dialog in which all the available export snippets of the template are listed.  
By pressing on one of the snippets you will be presented with a choice: Create a node system or enter code. **Please note:** This can not be changed later on, you will have to delete the existing snippet and then fill it again.  
After you have made your choice you will have to enter a name (used to be able to know at a quick glance what this snippet does in this special case) and fill the content. Once you press confirm the snippet will be saved and when you export the object the next time, this snippet will be filled.  

If you want to delete a filled snippet, you can press the trash bin icon next to that snippets name. **Please note:** This will only remove the filled content for that snippet for the current object, not the placeholders in the template.

## Sample Snippets
The following code is an example for an npc template to add an OnDeath Snippet (Check the region after the "----- Hooks ---" Section for the interesting parts):

    ----- Includes ----------

    include_file("_BaseNpc.lua")

    include("Npc")

    ----- Init Functions ----

    function OnInit(this)
        -- Values
        this:add_localized_string_value("Name", "{{ langkey npc.name }}")
        {{ npc.unused_fields | attribute_list }}
        {{~ if !inventory.empty? ~}}
        
        -- Inventory
        {{ inventory | inventory_list }}
        {{~ end ~}}
        {{~ if !skills.empty? ~}}
        
        -- Skills
        {{ skills | skill_list }}
        {{~ end ~}}
        {{~ if !daily_routine.events.empty? ~}}
        
        -- Daily routine
        {{ daily_routine.events | daily_routine_event_list }}
        {{~ end ~}}

        this:push_state("Idle")
        {{~ if dialog ~}}
        this:set_dialog_entry_function("{{ dialog.initial_function.function_name }}")
        {{~ end ~}}
    end

    {{~ if dialog ~}}
    ------ Dialog -----------

    {{~ for curFunction in dialog.all_functions ~}}

    {{ curFunction | dialog_function }}

    {{~ end ~}}
    {{~ end ~}}

    {{~ if !daily_routine.event_functions.empty? ~}}
    ------ Daily routine -----------

    {{ daily_routine.event_functions | daily_routine_event_function_list }}
    {{~ end ~}}
    {{~ if export_snippets.snippets.OnDeath.exists ~}} 

    -- Hooks --

    {{~ for snippet_function in export_snippets.snippets.OnDeath.all_functions ~}}
    {{ snippet_function | export_snippet_function }}

    {{~ end ~}}

    {{~ end ~}}