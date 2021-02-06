The state machine of an npc describes the behaviour of an npc. You can access the state machine by navigating to an npc in [Kortisto](/steffendx/GoNorth/wiki/Kortisto) and then pressing the State machine button at the top.  
Please note: While a user edits a state machine this state machine will be readonly for other users to prevent them from overwriting each others changes.

On the page you will see the following buttons at the top:
 * **Save**: Saves the current state machine.
 * **Back to npc**: By clicking this button you will return to the npc to which the state machine belongs.

Below the buttons you will find the available nodes and node system. Each node can be linked to another node by simply dragging from one node to the other.    
The start node of the state machine is already added to the node system. Only one of these nodes will exist in each state machine.  
You can drag a node into the node graph below to add it to the state machine.  
The following nodes are available:
 * **State**: A state describes a state the npc can reach. By entering a name inside of the textbox you can label the state. In addition you will find the following buttons inside a state node:
   * **Cross**: This icon is the handle used to move the node around in the canvas
   * **Gear**: This opens the detail setting for a state. You can find details below.
   * **Trash bin**: By clicking this icon you can remove the state and all associated transitions.
 * **Endpoint**: This node is used to mark the ending of the state machine. You can use the trash bin to delete the node. By pressing and holding outside of this trash bin you can move the node around.

In addition to adding new nodes you can also click on a transition to label this transition and describe the event which leads to the new state.  

## State Settings
Afer clicking the gear icon inside of a state the advanced settings dialog will open.  
You can provide a detailed description for this state here as well as a script.
By clicking on the script name you can either create a node system or enter a script code. 
The script there works similiar to the creation of [export snippets](/steffendx/GoNorth/wiki/Export-Snippets).  
The checkbox below can be used to exclude the state machine when exporting the associated npc.

## State machine export
GoNorth provides a list of placeholders inside of the npc template to export the state machine when exporting the npc. You can check these placeholders inside of the export template. See the [export templates](/steffendx/GoNorth/wiki/ExportTemplates) page for details on exporting.