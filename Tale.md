Tale is the dialog editing component of GoNorth. You can access this by navigating to a npc in [Kortisto](/steffendx/GoNorth/wiki/Kortisto) and then pressing the Dialog button at the top.  
Please note: While a user edits a dialog this dialog will be readonly for other users to prevent them from overwriting each others changes.

On the page you will see the following buttons at the top:
 * **Save**: Saves the current dialog
 * **Mark as implemented**: This button will only be visible if you are a member of the Implementation Status Tracker role. If the current dialog is not implemented you can click on this button to see the changes to the dialog and flag it as implemented. If the current dialog is already implemented this button will be labeled with implemented and be disabled.
 * **Back to npc**: By clicking this button you will return to the npc to which the dialog belongs.

Below the buttons you will find the available nodes. You can drag a node into the node graph below to add it to the dialog.  
The following nodes are available:
 * **Player line**: A simple text line said by the player
 * **Npc line**: A simple text line said by the npc
 * **Choice**: A choice for the player to select an answer. By pressing the "+" at the top next to the "x" you can add a new choice. Next to each choice you find the following icons:
    * **Arrows**: Using the arrows you can rearrange the the different choices
    * **Question Mark**: By pressing the question mark you can edit the condition which controls if the choice should be shown or not. You can find more details in the section condition dialog below.
    * **Circle arrow**: By clicking this icon you can toogle if the answer can be said multiple times or just once.
    * **Trash bin**: By clicking this icon you can delete the choice
 * **Action**: An action to trigger. The following actions are available:
    * **Change player value**: Change a value of the player. This can be used for training or paying gold etc.
    * **Change npc value**: Change the value of the npc to which the dialog belongs.
    * **Spawn item in player inventory**: Spawn a new item in the player inventory
    * **Spawn item in npc inventory**: Spawn a new item in the npc inventory
    * **Give item to the player**: Removes an item from the npc inventory and add it to the player inventory
    * **Give item to the npc**: Removes an item from the player inventory and add it to the npc inventory
    * **Change pick quest value**: Allows you to pick a quest and change a value of this quest (like counting found objectives etc.)
    * **Change quest state**: Allows you to change the state of a quest
    * **Add quest text**: Allows you to add text to a quest log
    * **Wait**: Allows you to specify an amount of time to wait. The time can be specified in real time or game time.
    * **Change player state**: Allows you to change the state of the player. If you are using a state machine for npcs you can use this as a state in the state machine, if not you can use this to specify if the player is confused for example.
    *  **Change npc state**: Allows you to change the state of the npc. If you are using a state machine for npcs you can use this as a state in the state machine, if not you can use this to specify if the npc is angry for example.
    * **Player learns skill**: Allows you to select a skill the player learns
    * **Player forgets skills**: Allows you to select a skill the player forgets
    * **Npc learns skill**: Allows you to select a skill the npc learns
    * **Npc forgets skills**: Allows you to select a skill the npc forgets
    * **Change player skill value**: Allows you to select a skill of the player and change the value of the skill.
    * **Change player skill value**: Allows you to select a skill of the npc and change the value of the skill.
    * **Save dialog state**: Marks this point in the dialog as a continue point if the dialog is stopped and the player talks to the npc again. This way you can mark the dialog state after an introduction and the next time the player talks to the npc the dialog will continue at this state.
 * **Condition**: A condition to branch the dialog. By pressing the "+" at the top next to the "x" you can add a new condition. By pressing on the condition text you can edit the condition, see condition dialog below. Next to each condition you find the following icons:
    * **Arrows**: Using the arrows you can rearrange the the different conditions
    * **Trash bin**: By clicking this icon you can delete the condition

You can move the nodes by clicking on them and dragging them to a new position.  
On the left side of each node you will find a red input port, on the right side of each node you will find one or more output ports. You can drag the output port of a node into the input port of a different node. This way you can control the flow of the dialog.  
On the top right of each node you will find a "x" button which allows you to delete the node.  
You can move the view by clicking outside of a node in the gray area and drag the screen and zoom using the mouse wheel. Alternatively you can use touch control.  
On the top left of the node system you will find a display of your current position and zoom in the node system. Next to these coordinates you can find an arrow to expand or collapse the mini map of the node system.

## Condition dialog
When editing a condition the condition dialog will open. At the top of the condition dialog you will find the following buttons:
 * **Add condition**: Adds a new condition. By default all conditions on the root level are grouped with and "And" operator
 * **And**: Group the selected conditions with an "And" operator
 * **Or**: Group the selected conditions with an "Or" operator

Below you find a list of conditions. You can select a type of condition from the drop down list. The following conditions are available:
 * **Check player value**: Check a value of the player. This could be used to give a different answer based on the charisma of the player etc.
 * **Check npc value**: Check a value of the npc.
 * **Check npc alive state**: Allows you to pick a npc and check if the npc is alive or dead
 * **Check player inventory**: Allows you to pick an item that will be searched in the player inventory and compare the count to a value you define
 * **Check npc inventory**: Allows you to pick an item that will be searched in the npc inventory and compare the count to a value you define
 * **Check pick quest value**: Allows you to pick a quest and check a value of this quest
 * **Check quest state**: Allows you to pick a quest and check the state of the quest
 * **Check game time**: Allows you check if the current game time is before or after a specified 
 time.
 * **Check player skill value**: Checks the value of a skill the player can cast. You can pick the skill using a dialog and specify the value condition.
 * **Check npc skill value**: Checks the value of a skill the npc can cast. You can pick the skill using a dialog and specify the value condition.
 * **Player can use skill**: Checks if the player can use a skill
 * **Player can not use skill**: Checks if the player can not use a skill
 * **Npc can use skill**: Checks if the npc can use a skill
 * **Npc can not use skill**: Checks if the npc can not use a skill

On the right of each condition you will find the following icons:
 * **Arrows**: Allows you to rearrange the conditions
 * **Move indicator**: Allows you to drag the condition into a different condition group
 * **Trash bin**: Allows you to delete the condition. If you click this for a group the conditions will stay and just the grouping will be removed

At the bottom you can press confirm to confirm the condition and cancel to cancel the editing of the condition.

