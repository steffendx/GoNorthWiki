Karta is the map component of GoNorth. It allows you to manage the different maps of your game and mark the positions of npcs, items, wiki pages, map changes and markers for quests on it.  
Please note: While a user edits a map this map will be readonly for other users to prevent them from overwriting each others changes.

## Map Form
In the map form you will see the map as the main part. You can navigate the map with the mouse and the mouse wheel or using touch input. On the top right you will find drop down list to be able to switch the chapter for which you are editing the markers (see more below) and a drop down list to switch the current map.  
On top of the map a bunch of checkboxes exist that allow you to hide / show different marker types.  
On the left of the map the different types of markers that a user can add to the map are shown. You can select an object there and then click in the map to add a new marker to the map. The following types of markers can be selected:
 * **Kirja**: By using the search box you can search for the page you want to add to the map. You can also select &lt;New Page&gt;. If you select &lt;New Page&gt; a new window will be opened on placing the marker that allows you to create a new wiki page. Upon saving the new page a new marker will be added to the mark. This can be used to add more information to a location on the map (like explaining a ruin, the backstory of a tavern and much more)
 * **Kortisto**: You can use the search box to search for a npc you want to place on the map. You can place a npc more than one time on the map. This way you can add a character on the map or add multiple enemies on the map.
 * **Styr**: You can use the search box to search for an item you want to place on the map. You can place an item more than one time on the map. This way you can place items on the map that the user can find.
 * **Aika**: You can use th search box to search for a quest to which you wand to add markers. If you select a quest the already existing markers for this quest will be shown. So if you want to see the markers of a quest you will have to first select the quest. If you place a new marker a dialog will open where you can add a name to the quest marker.
 * **Karta**: You can select a map to which you want to add a map switch. After selecting a map you can add a marker for this map by clicking on the map.
 * **Notes**: If you select &lt;New Note&gt; a dialog will open where you can add a name and description for the note. By using note markers you can mark certain areas as dangerous, magic blocked and so on.

### Editing Markers
You can edit markers by simply dragging them. After releasing the marker it will be saved. By clicking on a marker a popup will be shown. At the bottom right of the popup you will find icons for editing the marker:
 * **Circle**: By clicking this circle you can edit additional geometry for the marker. This geometry can be a line, polygon, rectangle or circle. You can find more info below, see **Editing marker geometry**.
 * **Pencil**: The pencil will only be available for quest markers and notes. By clicking on this icon you can rename the marker or change the description.
 * **Cross**: If you are in the Implementation Status Tracker role you will see a cross if the marker is not implemented. By clicking on the cross a dialog will open that allows you to flag the marker as implemented. If the marker is already implemented a check marker will be shown instead that is not clickable.
 * **Trash bin**: By clicking this icon you can delete the marker.

## Editing geometry
When entering the geometry edit mode, using the circle icon in a marker popup, new toolbar buttons will be shown on the left side of the map. You can find the following buttons there:
 * **Line**: Allows you to draw a line. By clicking you add a new vertex to the line. By clicking on the last vertex again you finish the line.
 * **Polygon**: Allows you to draw a polygon. By clicking you add a new vertex to the polygon. By clicking on the first vertex again you finish the polygon.
 * **Rectangle**: Allows you to draw a rectangle by dragging.
 * **Circle**: Allows you to draw a circle by dragging.
 * **Edit icon**: Allows you to pick the color for the next geometry object you draw.

When in edit mode you can also edit the existing geometry of the marker by simply dragging the highlighted white rectangles. By clicking and dragging on the translucent rectangles between line vertices you can add a new vertex between. Double clicking on an existing vertex will remove it.  
By clicking on the an existing geometry object the edit dialog will open. In this dialog you can change the color of the geometry.  
In the bottom left of the edit dialog a delete button will be shown.

## Editing for Chapters
After creating chapters in [Aika](/steffendx/GoNorth/wiki/Aika) you will be able to select a chapter at the top right. If you dont have the first chapter selected a clock will be shown to remind you that you are not editing the default values for the marker.  
So if you select chapter two for example all changes you are doing will only be valid from chapter two onwards. This means if you add a new marker and you have chapter two selected this marker will only appear after selecting chapter two or any later chapter. The same applies if you change the position or delete a marker. This means you can add a marker in chapter two, move the marker in chapter three and delete the marker in chapter four again. Afterwards the marker will change when changing from chapter one to two, three and four.

## Map Management
By clicking on "Switch map" at the top right you can select "Manage maps" to be redirected to the Manage Maps page.  
On the top you can click on "Create map" to create a new map. After pressing this button a new dialog will open where you can provide a name for the map and upload a high resolution map image. The upload can be done by simply clicking on the image icon below or dropping an image there. After pressing save the image will be uploaded and processed on the server. Afterwards you can select the map in the map form.  
Below of the Create map button you will find a list of maps. By clicking on a map name you can open the map.   
On the right of each map you will find two icons. These icons are:
 * **Pencil**: By clicking on this icon you can edit the name. You can either just rename the map and press save without uploading a new image. You can also upload a new map image. GoNorth will keep the position of the markers by adjusting them based on the resolution of the old and new image. This means you can upload a higher resolution of the map image later on if you want to.  
 * **Trash bin**: By clicking on this icon you can delete the map. Please note: You can only delete a map if its not marked for a map change in a different map.