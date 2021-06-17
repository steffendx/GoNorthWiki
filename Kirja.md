Kirja is the wiki component of GoNorth.  
On the top right you will find a button to start a new review, enter edit mode and on the right of these buttons you can find an arrow to expand or collapse the wiki sidebar.  
Please note: While a user edits a page this page will be readonly for other users to prevent them from overwriting each others changes.

## Editor
If the user enters edit mode the button at the top right will be hidden and the following buttons are visible:
 * **Save**: Saves the current page
 * **Delete**: Deletes the current page. Please note: A page can only be deleted if its not marked in a map and no other page is referencing the current page.
 * **Stop editing**: Will leave the edit mode

While editing a page you can rename it using the textbox at the top. You will also find a toolbar at the top for rich text editing. Apart from normal rich text formating you can also find the following icons:
 * **Book**: By clicking on this icon you can eiter choose an existing page and insert a link to this page, or click on "Create new page" to create a new page. If you click "Create new page" a new window will open where you can define the name of the page and enter the text. Upon saving the new page a link to this page will be inserted in the original wiki page.
 * **Chess King**: If you have the Aika role you can click this button to choose a quest and insert a link for this quest in the page.
 * **Person**: If you have the Kortisto role you can click this button to choose an npc and insert a link for this npc in the page.
 * **Apple**: If you have the Styr role you can click this button to choose an item and insert a link for this item in the page.
 * **Flash**: If you have the Evne role you can click this button to choose an skill and insert a link for this skill in the page.

After insert a link and saving a page the current page will be shown in the form for the different objects as a related Kirja page. If you remove the link to the object again it will also remove this reference.

## Sidebar
By clicking the arrow on the top right you can expand or collapse the sidebar. In this sidebar you will find:
 * Other wiki pages that mention the current page
 * Quests that are mentioned in the current page
 * Npcs that are mentioned in the current page
 * Items that are mentioned in the current page
 * Skills that are mentioned in the current page
 * Maps in which the current page is marked
 * Attachments that are added to the current page. If the page is saved, and therefore has an id, you can attach a new file to the page by clicking in the dropzone or dropping a file in the dropzone. On the right of the icons you will find a trash bin to delete the file from the page.
 * A link to open the version list for the current page (see below)
 * A link to open the page list

## Versioning
Kirja supports versioning of wiki pages. This way you can easily see recent changes made by a user or restore an old version if some changes were wrong.  

### Version list
By clicking on the "Show versions" link in the sidebar, one can open the version list dialog. This dialog will list all the versions for the current page. If there are more versions available than fit on one page, you can navigate between the different pages of the list using the two buttons at the bottom left of the dialog.  
On the right of each version there are two icons available:
 * **Two-Arrows**: By clicking this button you can compare this version with the currently displayed version. (see below) This icon will be hidden if this version is the currently displayed version.
 * **Eye**: By clicking this button you can show the page at the state of the selected version. (see below)

### Comparing
If you are comparing two versions of a page (eather because you pressed the button in the version list or by opening a wiki page from the timeline) the changes between the two versions are displayed:
 * **Green**: Text highlighted in green was added in the currently displayed version
 * **Red**: Text highlight in red was removed in the currently displayed version

At the top a banner will be shown that displayes the version number that is used for the comparison along with a button to exit the comparison mode.

### Restoring an old version
If you want to restore an old version you will have to first display an old version of a page by clicking the eye icon in the version list.  
Afterwards the old version is displayed and a banner will be show at the top. This will show the currently displayed version along with two buttons:
 * **Restore this version**: By clicking on this button a dialog will be shown where you will have to confirm that you want to restore this version. The links in the old version will also be validated. If one of the linked objects, like an npc or item, was deleted in the meantime these broken links will be shown. If you decide to restore the page, these broken links are removed (while the text content is kept).
 * **Display current version**: By pressing this button the most recent version will be shown again. If you are currently in comparison mode as well, the comparison mode will also be deactivated.

### Merging of versions
To prevent the versions of a page to be flooded if a user saves often, versions can be merged. As an example: If a user edits a wiki page and saves the page every 5 minutes, a new version will be added for every save action if the versions would not be merged.  
If the merge feature is activated, GoNorth will merge this version to just one version.  

To configure the timespan in which two versions will be merged you can adjust the value of the appsetting key **KirjaVersionMergeTimeSpan** in the Misc section. The timespan is configured in minutes. Only if the timespan between two versions is lower or equal to this timespan the events will be merged.  
If this timespan is below or equal to zero, the merge feature will be disabled.   
**Please note:** After a merge the new timestamp for the version is the current time.  

### Max version count
If you want to save disk space you can configure the maximum amount of versions to be saved for each page. For this you can adjust the value of the appsetting key **KirjaMaxVersionCount** in the Misc section.  
The following values are viable here:
 * **Any value above zero:** Kirja will not save more versions than specified here. If more versions would be saved, Kirja will delete the oldest version of this page to stay within this limit. If an image is only used in the version that is deleted, the image will also be deleted.
 * **Zero:** The versioning feature will be disabled
 * **Below zero:** An unlimited amount of versions will be saved for each page.

## Review
After starting a review one can list all reviews for each page by pressing the small down arrow button next to the start review button.  
Each review has one of the following states:
 * **Open**: The review was started and is still in progress
 * **Completed**: The reviewer has finished the review and the review is ready to be merged into the main page
 * **Merged**: The review is done and was merged into the wiki page

Each review will display the current version of the wiki page in the beginning. The users can then modify the text to give feedback or add a comment using the button in the toolbar of the richtext editor. In addition a comment can be provided at the bottom of the page.

Using the buttons at the top the review can be marked as completed. A completed review is readonly, but can be reopned.  

### Merging
If a review is marked as completed a banner at the top will offer a button to merge the feedback into the page. Once the button is pressed the review is compared against the latest version of the wiki page and each change is displayed. You can now click on the changes and accept or reject them (or manually adjust the page).  
**Please note:** Comments are removed in the merge mode.

Once all changes are merged you can confirm the merge and the main page will be updated accordingly. In addition the status of the page is changed to merged.

### External sharing
If external sharing for wiki pages is enabled a button at the top will be displayed in order to generate an external share link. You can then send this link to external people, allowing anonymous access to the wiki review. This link includes a strong token to ensure only people in possession of the share link can open the page.  

External users are allowed to edit the review text, provide comments and marking the review as completed.  

**Please note:** You can disable this feature by changing the value for the key **DisableWikiExternalSharing** inside the appsettings.json file to true.

## Page list
The page list will display a list with all the different pages that currently exist in the wiki. By pressing "Create page" you can create a new wiki page.  
The search bar allows you to search for pages by name. This search will not search in the text content.