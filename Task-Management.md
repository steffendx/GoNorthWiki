By clicking the tasks home icon or selecting tasks in the navigation bar at the top you can open the task management page.
At the right you will find a drop down list that allows you to switch the current board. If you have created board categories they will be displayed here as well and you can expand or collapse them by simply clicking on the category. The category that houses the board that is first displayed on the task page will always be expanded.   
In case you have the Manage Task Boards role you can select "Manage task boards" to open the manage task boards page.  
If you are a member of the TaskTypeManager role you will be able to press "Manage task types" to navigate to the task type management page. 

## Task Board
If you have a task board selected you can click on "Create task group" to create a new task group. In the dialog you can select a task type, add a title, description, assignee and status. The task type will mainly influence the color with wich the task will be displayed in the board. The toolbar above the description has the same icons as the [Kirja wiki page](/steffendx/GoNorth/wiki/Kirja) toolbar.  
**Please note**: While a user edits a task group or task this task group or task will be readonly for other users to prevent them from overwriting each others changes.  
After pressing the save button you will see the task group in the board.  
By clicking the arrow left to the task group you can collapse or expand the task group. You can click on the name of the task group to edit the task group. The same dialog as for creating a task group will open in this case. While editing a task you will aslo find a delete button in this dialog, as well as a "Move to board" button. If you select "Move to board" button a dialog will prompt you for the target board, after confirming the task group and all the tasks that are associated with this group will be moved to the new board.  
Directly on the task group card you can also assign the task to someone or adjust the status of the task group.  
By dragging a task group card you can order your task groups to help you prioritize the most important task groups.  
**Please note**: A closed task group will be collapsed by default upon loading the board.  


On the right of the task group you can find a "+" button which allows you to add a new task to the task group. The same dialog as for task groups will open in this case. After adding a task it will be shown as a card in the task group. By using the dropdown list you can quickly assign a task to someone. By dragging a task card you can order the tasks, move the task to different columns in the same group or even move the task to a different group to better organize your board.  
You can now click on the name to edit the task and view details. In the bottom left of the task dialog you will also find a button to delete the task or move the task to a different board. If you click on "Move to boaard" a dialog will prompt you for the target board. After selecting the target board the task groups on this board will be loaded and you will have to select the target task group to which the task must be associated when being moved. Upon confirming the task will be moved to the new board and associated with the task group.  

## Task Board Management
On the task board management page you can click the "Create task board" button. In the dialog you have to provide a task board name. You can also specify a planned start date and planned end date which will be displayed next to the board name.  
Below you will find a list of open and closed task boards. You can click on a task board name to open the board. In the most right column you will find the following buttons:
 * **Pencil**: Allows you to edit the board name and dates.
 * **Trash bin**: Allows you to delete the board. Please note: Only an empty board can be deleted.
 * **Checkmark or Circle arrow**: Allows you to close the board or reopen the board. A closed board will not appear in the list of boards in the board selection.

### Task Board categories
If you have a lot of different task boards (i.e. scripting boards, art boards, story boards...) the dropdown list toswitch between the boards might get crowded. For this task board categories were implemented. You will have to be amember of the TaskBoardCategoryManager role to be able to create task board categories.  
You can create a new category by pressing "Create new category" in the task board categories section below the boardlist. After specifying a name and if the category must be expanded by default it will be created.  

Underneath this button you will find a list of existing board categories. In the last column you can find the following buttons:  
 * **Pencil**: Allows you to edit the board category name and flag it as expanded/collapsed by default.
 * **Trash bin**: Allows you to delete the board category. Please note: If a board is associated with this category, this association will be removed.

**Please note:** When navigating to the task management page the category that houses the displayed board will be expanded by default, even if this is not selected here. This way you can collapse all categories by default and artistswill have their boards visible, while engineers will have the scripting boards visible by default.

## Task Type Management
GoNorth provides a default task group and task type. If you want to mark some tasks in a different way you can create youown task types. These task types will be displayed in a different color on the board. Using task types you can highlightbugs in red for example. If you are a member of the TaskTypeManager role, you can navigate to the task type managementpage by pressing "Manage task types" in the dropdown list on the top right of the task board page.  
On this page you will find two sections: One for managing task group types and one for managing task types. The usage ofthis section is the same.
By pressing the create button you can open the task type dialog. In this dialog you can enter a name, select a color andflag the type as the default type for task groups or tasks. The color will influence the board of the card on the taskboard. If you flag a task type as default it will be selected by default if you create a new task group or task.  
**Please note:** After creating the first custom task type the default type for this kind of task (task group or task) will be disabled and this type will be used. If you delete all custom task types again, the default task types will be used as a fallback.  
**Please note:** If you flag a type as the default type and there are task groups or tasks that have no reference to atask type, this type will be used for them until you edit the task or define a new default type. This can happen if youcreated tasks with an older version of GoNorth or you created tasks before creating custom types.

Below the create button you can find a list of existing task types. The default type will be highlighted in bold. In the most right column you will find the following buttons:
 * **Pencil**: Allows you to edit the task type name, color and flag it as the default type.
 * **Trash bin**: Allows you to delete the task type. Please note: Upon deleting the type you will have to select a different task type to which the existing task groups or tasks using this type will be remapped. If you are deleting the last task type the default types will be used as a fallback.
