If you have admin rights you can navigate to the Admin Area by clicking on "Administration" in the navbar, left to your user name.  

## User Management
On this page you will be able to add new users to the portal or edit existing users.  
If you create a new user and have the email settings configured this user will receive an email to verify his or her email address.  
**Please note**: If a user does not confirm their email address they will not be able to use the "Forgot your password?" functionality.  

Below the create user button you will find a list of existing users in the portal. In the most right column you will find the following buttons:
 * **Star**: This star is used for adjusting the roles of a user. You can move a role from the available roles to the assigned role box by selecting the role in the list and then pressing "Add role". In the same way you can remove a role by selecting the role in the assigned roles list and click "Remove role".
 * **Clip**: By pressing this button you can refresh the security stamp of a user. This will sign out a signed in user. This is usefull if an account gets hijacked and you want to sign out the attacker after changing the password.
 * **Paper plane**: By pressing this button you can confirm the email address of a user. This is useful if a user did not confirm their email address and forgot their password.
 * **Trash bin**: By clicking this button you can delete a user.

### Roles
The following roles are available for users:
 * **Administrator**: Allows a user to access the Administration area.  
 Please note: This does not grant access to all modules. You will still have to assign the other roles.
 * **Task**: Allows a user to access the task tracking area and create / edit task groups and tasks.
 * **TaskBoardManager**: Allows a user to create, edit and close or reopen task boards in the task tracking area.
 * **Kortisto**: Allows a user to create and edit categories and npcs in the npc planning module Kortisto.
 * **KortistoTemplateManager**: Allows a user to create and edit npc templates in the npc planning module Kortisto.
 * **KortistoPlayerManager**: Allows a user to mark an npc as the player character.
 * **Styr**: Allows a user to create and edit categories and items in the item planning module Styr.
 * **StyrTemplateManager**: Allows a user to create and edit item templates in the item planning module Styr.
 * **Evne**: Allows a user to create and edit categories and skills in the skill planning module Evne.
 * **EvneTemplateManager**: Allows a user to create and edit skill templates in the skill planning module Evne.
 * **Kirja**: Allows a user to access the wiki component Kirja.
 * **Tale**: Allows a user to edit the dialogs of npcs in the dialog planning module Tale.
 * **Aika**: Allows a user to edit chapters and quests in the quest planning module Aika.
 * **ImplementationStatusTracker**: Allows a user to flag objects to which he or she has access as implemented. A user which has no access to Styr for example will not be able to track the implementation status of items.

## Project Management
To be able to extend GoNorth to allow multiple projects in parallel on which different users are working in the future I've implemented projects. At the moment all objects will be associated to the current default project. This means you have to have at least one default project at any time to be able to work with GoNorth.

After creating a project you will see a list of projects. The current default project will be printed in bold. In the most right column you will find the following buttons:
 * **Pencil**: Allows you to edit a project
 * **Trash bin**: Allows you to delete a project. Please note: You will only be able to delete empty projects.

## Encrypt value
On this page you can encrypt values for the config file. Simply enter your value in the config value textbox and press encrypt. Afterwards you can copy your encrypted value from the encrypted config value box into your config file.

## Setup DB
If you click on this page GoNorth will create all missing collections in the MongoDB. This is not really required since your MongoDB will create the collections once you access them as well. I mainly needed this for some tests. But maybe I will create some indices on this page or migrate old data in the future.