This page is intended to give you a brief overview what you have to do if you want to create a new node type, node action or node condition for the node graph used in [Tale](/steffendx/GoNorth/wiki/Tale) and [Aika](/steffendx/GoNorth/wiki/Aika).

## New Node Type
If you want to create a new node type I recommend you take a look at the Tale Text line node. You can find the the file at "/wwwroot/js/Tale/dialogForm/textLine.js". This is a very simple node and should give you a good start on what you have to do if you want to create a new node type:
 * Adjust the createTextShape (or in your case different shape) function to provide your new properties in the model. The choice node for example adds an array of choices in the model. The values you specify here will be available to you while saving your node.
 * Adjust the createTextView (or in your case different shape) function to provide the template that suits your needs. You also have to specify the functions and logic in here. For this you can take a look at the "/wwwroot/js/Tale/choiceNode.js" file which is one of the more complex nodes.
 * Some logic can also be found in the baseNode implementation which you will find in the file "/wwwroot/Shared/nodeGraph/baseNode.js"
 * You have to create a new serializer for the node type. You can take a look at the text line serializer for this in the textline.js file. The classType needs to be the Shape Type you defined, like this in the TextLine for a Player Text Line:  
    
    joint.shapes.tale.PlayerText = createTextShape(playerTextType);  

   The type must be the string type of the node, like "tale.PlayerText" for the Player Text line.  
   The array name is the array to which all the nodes of this type will be serialized. This must match the array name in the backend.  
   You will have to adjust the serialize and deserialize function of the serializer class to use your node values. Like I mentioned before, you will have all the properties available in the serialize method that you added to the model in the create shape function.
 * Create a class in the backend for serializing and deserializing the node data. See "/Data/Tale/TextNode.cs" for the Text Node as an example. The properties here must match the values you serialize in your JavaScript Serializer "serialize" and "deserialize" function
 * Add a List of this class type to the TaleDialog or Aika classes. The name of this list must match the array name specified in the serializer.
 * Add a new node that can be dragged in the node graph. See "/Views/Tale/index.cshtml":  
   `<div data-bind="draggable: 'clone'" class="gn-nodeInsertContainer gn-nodePlayerText" data-nodetype="tale.PlayerText">`  
   You will have to change the data-nodetype to your node type name. This will allow you to add the node to the graph.

## New Condition Type
If you want to create a new condition type you should take a look at the "/wwwroot/js/Shared/nodeGraph/conditions/baseCondition.js", "/wwwroot/js/Shared/nodeGraph/conditions/checkValueCondition.js" and "/wwwroot/js/Tale/dialogForm/conditions/checkNpcValueCondition.js" files. You will have to do the following:
 * Change the template name to your template name for the html display. You can find the existing templates in "/Views/Shared/NodeConditionBase.cshtml". This template will be used for the rows in the condition dialog.
 * Change the getLabel function to return the label of your condition
 * Change the getType function to return the type number of your condition. This is important to identify the action.
 * Change the buildConditionData to build your condition data knockout logic. You can think of this as a mini viewmodel.   
  existingData will be your serialized condition data after opening the dialog again.
 * Change the serializeConditionData function to serialize your condition data. 
 * Change the getConditionDependsOnObject function to return the objects on which the condition depends (if the condition depends on a object). This will be used to determine the relations in the different forms and show a link to the dialog or quest.
 * Change the getConditionString function to build your condition string which will be shown in the node
 * Add the condition type to the condition manager:  
   GoNorth.DefaultNodeShapes.Conditions.getConditionManager().addConditionType(new Conditions.*YourConditionClass*());
 * Add your condition file in the bundleconfig to the Tale and/or Aika Viewmodels to be available.


## New Action Type
If you want to create a new action type you should take a look at the "/wwwroot/js/Shared/nodeGraph/actions/baseAction.js", "/wwwroot/js/Shared/nodeGraph/actions/changeValueAction.js" and "/wwwroot/js/Tale/dialogForm/actions/changeNpcValueAction.js" files. You will have to do the following:
 * Change the getContent function to return your html content for editing the action
 * Change the onInitialized function to add your event handlers and deserialize your values (see deserializeData in changeValueAction.js)
 * Change the buildAction function to return your new action
 * Change the getLabel function to return the label of your action
 * Change the getType function to return the type number of your action. This is important to identify the action.
 * Add your new action as an available action:  
   GoNorth.DefaultNodeShapes.Shapes.addAvailableAction(new Actions.*YourActionClass*());
 * Add your action file in the bundleconfig to the Tale and/or Aika Viewmodels to be available.