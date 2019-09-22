Aika is the chapter and quest management of GoNorth. It allows you to build a complex node system which shows how each quest is connected to other quests.  
You can navigate to Aika by clicking on the Aika home tile or pressing the Aika link in the navbar.

## Chapter
When first navigating to Aika you will start at the chapter overview page. At the top of the page you will find the following buttons:
 * **Save**: Saves the chapter overview
 * **Open quest list**: Opens the quest list

Please note: While a user is editing the chapter overview the chapter overview will be readonly for other users to prevent them from overwriting each others changes.

Below the buttons you will find the possible nodes you can drag into the graph system. The following nodes are available:
 * **Chapter**: The chapter node will create a new chapter in Aika. Once you have added the node to the graph system you can enter the name of the chapter. Below the name you will have to specify the number of the chapter.  
 Please note: You can have two ore more chapters with the same number if there are different chapter with the number two for example. This can be used if the player can join one faction or another and the next chapter is different depending on which faction the player joined for example.  
 After saving the chapter will be created and a button "Open detail view" will be shown to open the detail view of the chapter. Each chapter node has one red input port and multiple outport ports. These outport ports represent the finish node in the detail view (see more below). By connecting the different output ports to the different input ports you can define your overall chapter flow.

Like every node graph system you can move the nodes by dragging them with the mouse.  
On the top right of each node you will find a "x" button which allows you to delete the node.  
You can move the view by clicking outside of a node in the gray area and drag the screen and zoom using the mouse wheel. Alternatively you can use touch control.  
On the top left of the node system you will find a display of your current position and zoom in the node system. Next to these coordinates you can find an arrow to expand or collapse the mini map of the node system.

## Chapter detail
In a chapter detail view you will find the following buttons at the top:
 * **Save**: Saves the chapter detail view
 * **Open quest list**: Opens the quest list

Please note: While a user is editing a chapter detail the chapter detail will be readonly for other users to prevent them from overwriting each others changes.

Below the buttons you will find the possible nodes you can drag into the graph system. The following nodes are available:
 * **New quest**: When dragging a new quest node into the graph system a new window for creating a new quest will open. Upon saving the new quest the quest node will be inserted. You can click on the name of the quest to open the quest detail view. If the quest is flagged as a main quest a star on the left of the name will indicate this. Each quest node has one input port and one output port for each possible quest finish. This will be defined by finish nodes in the quest. See below. 
 * **Existing quest**: When dragging an existing quest node into the graph system a dialog will open which allows you to choose an existing quest. Afterwards the quest node will be inserted.
 * **All done**: An all done node can be used to indicate that multiple quests need to be finished before the next step can proceed. This way you can drag the success output of three quests into the input port of the All done node and then drag the output port of the node into the next quest node for example. This shows that all three quests must be completed successfully to start the next quest.
 * **Finish**: A finish node indicates a possible finish of the chapter. You have to provide a name for the finish and can select a color. This way you can for example have two finish nodes for the first chapter: "Joined rebels", "Joined troops of the king". In the chapter overview these finishes will be shown as output ports and the lines going away from this output port will have the selected color. This way its easy to follow the different story path in the overview.
 * **New detail view**: By dragging this node into the node graph system a new window will open to create a new chapter detail. This can be used to create a detail view for shared quests in a chapter that has multiple versions (like "rebels" or "king troops"). This way you dont have to manage the quests twice.
 * **Existing detail view**: By dragging this node into the node graph system a dialog will open that allows you to choose an existing detail view. This way you can add the shared quest to the other chapter version after creating it in the first chapter version.

## Quest detail view
In the quest detail view you will find the following buttons at the top:
 * **Save**: Saves the quest
 * **Add field**: This drop down list allows you to add a new field to the quest. You can choose between a single line text field, multi line text field and, a number field, a dropdown field and a field group. After selecting a field type you must provide a name of the field and add it to the quest.
 * **Mark as implemented**: This button will only be available if the current user is an implementation status tracker. If the quest is not implemented you can click on this button to see the changes to the quest and flag it as implemented. If the current quest is already implemented this button will be labeled with implemented and be disabled.
 * **Delete**: Allows the user to delete the quest. Please note: A quest can only be deleted if not used in any chapter detail view.

Please note: While a user is editing a quest the quest will be readonly for other users to prevent them from overwriting each others changes.

### Header data
Below the buttons you will find the header data area of the quest which you can collapse or expand. Here you can define the quest name and a brief description. The description is useful if one user defines the rough description and adds the possible finish nodes to connect the quest in the chapter. A different user can now flesh out the quest based on the description and the known finish nodes. You can also flag the quest as a main quest using the checkbox.  

### Fields
Below the header data you will find the fields area which you can collapse or expand. Here you will see all the fields that are currently added to the quest. On the right to each field you will find the following icons:
 * **Arrows**: By clicking and dragging the arrows you can rearrange the fields
 * **Door with arrow**: By clicking this icon you can change the script settings of the field.  
 Please note: Currently this has no effect since script exporting is not yet implemented. I've implemented this to allow users to already set these values when creating quests to be ready for exporting.  
 This is not available for multi line text fields and field groups since they will not be exported to a script any way.  
 In the dialog you can set the following values:
   * **Additional script names**: You can provide additional names for script exporting here. This allows you to export the field to the script multiple times with different names. This way you can export StartHintCount as CurrentHintcount as well for example.
   * **Dont export to script**: Dont export the selected field to the script.
 * **Pencil**: You can rename the field by clicking this icon.
 * **Trash bin**: You can delete the field by clicking this icon.

### Connections
Below the fields you will find the connections of the quest which you can collapse or expand. Here you will see in which detail views, other quests, Kirja wiki pages, Tale dialogs and Karta maps the quest is used.

### Node Graph System
The following nodes can be dragged into the node graph system:
 * **Text**: A text node can be used to describe a step required in the quest.
 * **Condition**: A condition to branch the quest. By pressing the "+" at the top next to the "x" you can add a new condition. By pressing on the condition text you can edit the condition, see condition dialog below. Next to each condition you find the following icons:
    * **Arrows**: Using the arrows you can rearrange the the different conditions
    * **Trash bin**: By clicking this icon you can delete the condition
* **Action**: An action to trigger. The following actions are available:
    * **Change current quest value**: Change a value of the quest
    * **Change pick quest value**: Allows you to pick a quest and change a value of this quest (like counting found objectives etc.)
    * **Change quest state**: Allows you to change the state of a quest
    * **Add quest text**: Allows you to add text to a quest log
    * **Quest status will be changed in npc dialog**: Allows you to pick a npc dialog and a state to which the current quest must be changed. GoNorth will check if an action node to change the quest state exists in the selected dialog and will display a warning if no node exists. 
    * **Quest text will be changed in npc dialog**: Allows you to pick a npc dialog in which the text of the current quest will be adjusted. GoNorth will check if an action node to change the quest text exists in the selected dialog and will display a warning if no node exists. 
    * **Wait**: Allows you to specify an amount of time to wait. The time can be specified in real time or game time. This action has two output ports: One output port that will be run once the timeout has finished and one to directly continue the flow without waiting. 
    * **Player learns skill**: Allows you to select a skill the player learns
    * **Player forgets skills**: Allows you to select a skill the player forgets
    * **Change player skill value**: Allows you to select a skill of the player and change the value of the skill.
    * **Fade to black**: By using this action you can fade the screen to black (for example if you want to change the time or teleport the player). You can specify how long it will take to fade the screen to black.
    * **Fade from black**: By using this action you can fade the screen back to normal after fading it to black before. You can specify how long it will take to fade the screen back to normal.
    * **Set game time**: Allows you to set the game time. If your project is not using a 24 hour day, you can change this in the [Project Config](/steffendx/GoNorth/wiki/Project-Config).
    * **Disable daily routine event**: This action disables the daily routine event of an npc. You can pick the daily routine by searching for the npc and then expanding it to select the daily routine.
    * **Enable daily routine event**: This action enables the daily routine event of an npc. You can pick the daily routine by searching for the npc and then expanding it to select the daily routine.
    * **Teleport player**: This action will teleport the player to a target marker. You will have to specify an export name for a marker to be able to find it in the picker dialog, check the [Karta](/steffendx/GoNorth/wiki/ Karta#editing-markers) wiki page for details.
    * **Teleport pick npc**: This action allows you to pick an npc using a picker dialog and a target marker to which this npc will be teleported. You will have to specify an export name for a marker to be able to find it in the picker  dialog, check the [Karta](/steffendx/GoNorth/wiki/Karta#editing-markers) wiki page for details.
    * **Walk pick npc**: This action allows you to pick an npc using a picker dialog and a target marker to which this npc will walk. You will have to specify an export name for a marker to be able to find it in the picker dialog,  check the [Karta](/steffendx/GoNorth/wiki/Karta#editing-markers) wiki page for details.  
    This node has two output ports: One output to specify a node flow after the goal is reached, and one to continue the flow without a break. This can be useful if you want to continue the dialog without waiting for the npc to arrive at is goal and at the same time change some values or play an animation as soon as the npc has reached its target.
    * **Teleport pick npc to npc**: This action allows you to pick an npc using a picker dialog and a target npc to which this npc will be teleported.
    * **Walk pick npc to npc**: This action allows you to pick an npc using a picker dialog and a target npc to which this npc will walk.  
    This node has two output ports: One output to specify a node flow after the goal is reached, and one to continue the flow without a break. This can be useful if you want to continue the dialog without waiting for the npc to arrive at is goal and at the same time change some values or play an animation as soon as the npc has reached its target.
    * **Spawn npc at marker**: This action allows you to pick an npc and a marker. The selected npc will be spawned at the selected marker. You can also specify the rotation of the spawned npc.
    * **Spawn item at marker**: This action allows you to pick an item and a marker. The selected item will be spawned at the selected marker. You can also specify the rotation of the spawned item.

 * **All done**: An all done node can be used to indicate that multiple steps need to be finished before the next step can proceed. This way you can drag the success output of three nodes into the input port of the All done node and then drag the output port of the node into the next step for example. This shows that all three steps must be completed successfully to continue the quest.
 * **Finish**: A finish node indicates a possible finish of the quest. You have to provide a name for the quest and can select a color. This way you can for example have two finish nodes for the quest "Success", "Failed" after an action node to set the quest status. But you could also have to different success finishes. In the chapter detail view these finished will be shown as output ports and the lines going away from this output port will have the selected color. This way its easy to follow the different story path in the detail view.

### Condition dialog
When editing a condition the condition dialog will open. At the top of the condition dialog you will find the following buttons:
 * **Add condition**: Adds a new condition. By default all conditions on the root level are grouped with and "And" operator
 * **And**: Group the selected conditions with an "And" operator
 * **Or**: Group the selected conditions with an "Or" operator

Below you find a list of conditions. You can select a type of condition from the drop down list. The following conditions are available:
 * **Check current quest value**: Check a value of the quest.
 * **Check pick quest value**: Allows you to pick a quest and check a value of the quest
 * **Check quest state**: Allows you to pick a quest and check the state of the quest
 * **Check npc alive state**: Allows you to pick a npc and check if the npc is alive or dead
 * **Check game time**: Allows you check if the current game time is before or after a specified time. If your project is not using a 24 hour day, you can change this in the [Project Config](/steffendx/GoNorth/wiki/Project-Config).
 * **Check player distance to quest marker**: Allows you to pick a quest marker and specify a distance to which the player needs to be. This way you can specify a certain point the player needs to be or maybe is not allowed to leave.
 * **Check player skill value**: Checks the value of a skill the player can cast. You can pick the skill using a dialog and specify the value condition.
 * **Player can use skill**: Checks if the player can use a skill
 * **Player can not use skill**: Checks if the player can not use a skill
 * **Check random value**: Allows you to compare a random value to a certain value using different operators. This can be used if you want to add some varity in a quest.
 * **Check daily routine event is disabled**: Checks if a daily routine event of an npc is disabled. You can pick the daily routine by searching for the npc and then expanding it to select the daily routine.
 * **Check daily routine event is active**: Checks if a daily routine event of an npc is enabled. You can pick the daily routine by searching for the npc and then expanding it to select the daily routine.

On the right of each condition you will find the following icons:
 * **Arrows**: Allows you to rearrange the conditions
 * **Move indicator**: Allows you to drag the condition into a different condition group
 * **Trash bin**: Allows you to delete the condition. If you click this for a group the conditions will stay and just the grouping will be removed

At the bottom you can press confirm to confirm the condition and cancel to cancel the editing of the condition.

### Quest list
At the top of the quest list you can find the following buttons: 
 * **Create quest**: Allows you to create a new quest
 
Using the search box you can also search for quests.  
Below you can find a table with the different quests and open them by clicking on the name of the quest. In the right column you will see if the quest is a main quest.
