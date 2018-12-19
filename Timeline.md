The timeline page shows the latest changes in the project. This way a user can easily see the latest changes that happend since the last time the user logged in.  
The events are filtered based on the roles of the user.  
For most event types a link will be provided to immediately show the changes.  

## Merging
To prevent the timeline to be flooded if a user saves often, timeline events can be merged. As an example: If a user edits a wiki page and saves the page every 5 minutes, a new event will be added for every save action if the events would not be merged.  
If a new user opens the timeline afterwards there would be 5 or more events for the update of the same page visible. This does not really help a user looking at the timeline more, compared to just one event beeing shown.  
If the merge feature is activated, GoNorth will merge this event to just one event.  

To configure the timespan in which two events will be merged you can adjust the value of the appsetting key **TimelineMergeTimeSpan** in the Misc section. The timespan is configured in minutes. Only if the timespan between two events is lower or equal to this timespan the events will be merged.  
If this timespan is below or equal to zero, the merge feature will be disabled.   
**Please note:** After a merge the new timestamp for the event is the current time.  