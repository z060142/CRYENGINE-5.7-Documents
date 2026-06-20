# Tutorial - Adding a Speedometer to a Vehicle

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306546
- Page ID: 23306546
- Breadcrumb: CRYENGINE Code Tutorials > Miscellaneous Tutorials > UI Examples > Tutorial - Adding a Speedometer to a Vehicle
- Parent: UI Examples

## Content

![Image](https://www.cryengine.com/docs/static/attachments/23461382)

### Overview

In this tutorial you will learn how to use Flow Graph by enabling a new HUD element and linking it to the speed of a vehicle. You will also learn how to debug problems and make your Flow Graph more robust.

### Getting Started

#### Load the file

To get started load the Sandbox editor, then open the sample level located: `GameSDK/Levels/_Testmaps/Vehicle_UI (coming soon!)`

#### Exploring the scene

Press **Ctrl+G** to start the game.

In this very simple level you can find a HMMWV, tank, boat and helicopter.

Go to the left door of the humvee and press **F** to get inside.

You should see a dial on the left of the screen which shows your current speed, gear and RPM.

![Image](https://www.cryengine.com/docs/static/attachments/23461407)

Press **F** again to get out, then and get into the left hand side of the tank (you can skip to it by pressing J). If you get into the wrong vehicle seat, change to the driver position by pressing ** c**.

As you can see, the tank has no special UI set up, so that will be the subject of this tutorial.

Press **Esc** to return to the editor.

### Adding the basic Speedometer

First we are going to create a new flowgraph for the vehicle, and make it call up the speedometer UI element.

#### Creating a Flowgraph for the Tank

Select the tank by left clicking on it.

Right click on the tank and select **Create Flow Graph**.

![Image](https://www.cryengine.com/docs/static/attachments/23461406)

This will bring up a popup window which says "Choose Group for the Flow Graph".

Select **Demo_HUD** and click OK.

The group name is just to help organize your flow graphs and doesn't affect the functioning of the flowgraph.

This opens the **Flow Graph** view pane. If you close it by mistake, it can be reopened from ** View -> Open View Pane -> Flow Graph**.

To the left of the window is a tree showing the all the flow graphs associated with your scene. If you "lose" your Abrams1 flow graph you can get it back by clicking the icon here.

![Image](https://www.cryengine.com/docs/static/attachments/23461405)

#### Adding your first Flowgraph Nodes

##### Adding the tank entity to Flow Graph

Make sure the tank is still selected in your game window (if not, just left click on it).

Right click on the main part of the Flow Graph pane (the part with the grid) and choose **Add Selected Entity**.

This will add a new Node called entity:Abrams. This is the starting point for hooking the tank up to the UI element.

##### Adding the UI Element to Flow Graph

Right click again and choose **Add Node->UI->Action->Control**. This adds a node which we will use to start the speedometer UI element.

![Image](https://www.cryengine.com/docs/static/attachments/23461404)

On the UI:Action:Control node, double click the section that says **UIAction=**, then click the two dots.

This brings up a Choose Action window. Select **Demo_HUD** from the list and click OK.

![Image](https://www.cryengine.com/docs/static/attachments/23461403)

Hover your cursor over the OnPassengerEnter on the entity:Abrams node, then click and drag a connector to the Start section on UI:Action:Control.

![Image](https://www.cryengine.com/docs/static/attachments/23461402)

#### Try out your new Speedometer

Now to test it in the game. Click in the game window, hit Ctrl+G and get into the tank. You should see a Speedometer appear. It won't actually animate yet.

Just like the real thing, we need to wire it up to the vehicle's speed.

### Quickly Hooking up the Speed

Next we'll connect the speedometer HUD element to the speed of the vehicle.

#### Adding the Velocity Node

##### Add the nodes

Press **Esc** to return to the editor.

Click on the Flow Graph view pane.

Press **q**. This brings up a search box. Type the word ** velocity** and press Enter. This will bring up the Entity:Velocity node.

You can add any Flow Graph node by right clicking, choosing Add Node and selecting it from the list. If you already know part of the name of a node you can search for it by pressing **q** and typing the name. If there are multiple options, the up and down arrow keys will cycle through them. To cancel your selection press **Esc**.

If you want to reposition the node, you can drag it to a sensible space. The middle mouse button scrolls around the view pane, and the mouse wheel zooms in and out.

Right Click on the background and select **Add Node->UI->Functions->Demo_Speedo->UpdateSpeedometer**.

This will create a new node which is used to set the speed display on the speedometer UI element.

##### Connecting the Speedo to the Velocity Node

Now click-drag a connector from the**Velocity_ForwardBackward** section of Entity:Velocity and join it to the **_speed** section of the new UpdateSpeedometer node.

Nothing will happen yet, because we need to Call the UpdateSpeedometer for it to do anything.

Click drag another connector from Velocity**_ForwardBackward** to the ** Call** section of UpdateSpeedometer.

Finally, make sure the Tank is selected, then on Entity:Velocity, right click on the red section called **Choose Entity**. Click Assign Selected Entity.

![Image](https://www.cryengine.com/docs/static/attachments/23461401)

##### The Speedometer - Now with added Speed!

Now to try it out. Go to the main window and **Ctrl+g** to run the game, get in the tank, and you should have a working speedometer.

Now would be a good time to save! It's a good idea to save your level each time you add something and try it in game to prove it works. If you wire up your Flow Graph incorrectly later on, you can just go back to the previous save.

![Image](https://www.cryengine.com/docs/static/attachments/23461400)

You will notice that when you get out of the tank the speedometer doesn't go away - so we will fix that in the next section.

### Fixing Problems - Making the Speedometer Unbreakable

Whenever you work with scripting or programming on a game, getting something to work first time is an achievement, but making it work *every time* is your ultimate goal.

The most obvious problem we need to fix is the fact that the Speedometer doesn't go away when we get out of the tank.

#### Making the Speedo Disappear

Press **Esc** to get out of the game, then go to the Flow Graph view pane.

Right click on the background and add another UI:Action:Control node.

Double Click on the**UIAction=** section, then click the... Choose Demo_HUD_Hide from the Choose Action list and press OK.

Drag-click a connection from the OnPassengerExit section of the entity:Abrams node to the Start section of your new UI:Action:Control node.

Try this in the game. Now the Speedometer will disappear when you get out of the vehicle.

#### Looking for Hidden Problems

Visually everything looks fine, but we need to check that things are working correctly under the hood - otherwise we could risk breaking our game.

We need to see Flow Graph and the game at the same time, so we need to reorganise the view.

##### Organizing your view

Click and drag the Flow Graph view pane. As you drag, small window icons will appear at various points on the screen. These are used to dock the current view pane.

Drag the view pane onto the icon to the left of the screen. This will dock the pane to the left of the game window, making it easier to see both at the same time.

![Image](https://www.cryengine.com/docs/static/attachments/23461399) | ![Image](https://www.cryengine.com/docs/static/attachments/23461398)
--- | ---

If necessary, make some more space by dragging the vertical separators between the sections of the Flow Graph View pane.

Use the middle mouse button and mouse wheel to zoom out so that you can see as much of your Flow Graph as possible.

If you work with the Flow Graph a lot, you may find it useful to use 2 monitors so that you can have the game on one screen and Flow Graph on the other.

![Image](https://www.cryengine.com/docs/static/attachments/23461397)

##### Turning on the Visual Debugger

At the top left of the Flow Graph view pane, click the icon with a bug on it. This turns on the visual debugger, which will let you see your script working whilst you play the game.

![Image](https://www.cryengine.com/docs/static/attachments/23461396)

Press the **Debug icon**. It will have a blue square around it when it's active.

Click on the game window and press **Ctrl+g** to start the game.

Get into the vehicle. You will notice that the link between **OnPassengerEnter** and ** Demo_HUD Start** turns yellow to indicate that that action has happened.

If you get into and out of the vehicle multiple times, a small number will appear next to the link which shows you how many times it was triggered.

![Image](https://www.cryengine.com/docs/static/attachments/23461395)

##### Too much Velocity!

You will also notice that the link between the **Enitity:Velocity** and ** UpdateSpeedometer** is going crazy. It's actually setting the velocity once every frame, all the time.

While we are in the vehicle this constant updating isn't necessarily a problem, but at other times this is using up precious processing power for no benefit. If you added more vehicles, more of your **frame rate** would be eaten up by this node firing all the time.

![Image](https://www.cryengine.com/docs/static/attachments/23461394)

Many nodes in Flow Graph are **Enabled** by default. Sometimes you need to disable them to make things work as you expect.

#### Optimizing your Flow Graph

So now we need to turn off the Entity:Velocity node when it isn't being used.

##### Adding an On / Off switch to Flow Graph

The **Enabled** input on the ** Entity:Velocity** node works like a power button - it can be either on or off. In technical terms this is uses a Boolean - a value which is True or False.

To find out what type of input or output a node uses, make sure you have the Flow Graph window selected, then hover over the section you want to know about. A small text box will pop up showing the data type, along with a short description.

![Image](https://www.cryengine.com/docs/static/attachments/23461393)

Move your entity:Abrams node to the left to create some space.

With your mouse hovering over the space, press **q** to bring up the search box. Type ** BooleanTo** and press Enter.

This will create a **Math:BooleanTo** node, which will output True or False depending on which of the inputs are triggered.

Drag a connector from the **out** part of the new Math:BooleanTo node and connect it to **Enabled** on Entity:Velocity.

Now drag a connector from **OnPassengerEnter** on the entity:Abrams node to ** true** on the Math:BooleanTo node.

At this point, the Flow Graph will work the same as before, but now we have the option to turn off the Velocity node by connecting something to the false connector.

![Image](https://www.cryengine.com/docs/static/attachments/23461392)

##### Switching off the Engine

Add a connector from **OnPassengerExit** on the entity:Abrams node to the ** false** part of the Math:BooleanTo node.

At the top left of the window press the **trash can** icon. This will clear the current flow graph debug information.

![Image](https://www.cryengine.com/docs/static/attachments/23461391)

Move your flow graph view so that you can see the Entity:Velocity and UpdateSpeedometer nodes.

Make sure that the Debug icon is hilighted, then press **Ctrl+g** to run the game again.

This time when you get out of the vehicle, the Velocity node will stop running. We have successfully turned it off.

#### Stopping the Velocity Node when the Game Starts

The next step is to prevent the Entity:Velocity node from running when the game begins.

##### Changing to a better view for editing

Press **Es** c to exit the game engine if you haven't already.

Hover your mouse over the title of the Flow Graph view pane, then **click-drag** it so that it becomes a floating window again. Resize it so that you can see your Flow Graph more easily.

![Image](https://www.cryengine.com/docs/static/attachments/23461390) | ![Image](https://www.cryengine.com/docs/static/attachments/23461389)
--- | ---

##### Adding a Game:Start Node

With the Flow Graph window selected, move your cursor into the space under the entity:Abrams node, then press **q** to bring up the search box. We want the default option, ** Game:Start**, so press Enter to create a new Game:Start node.

This new **Game:Start** node will trigger as soon as you begin the game. We can use this to turn off the Entity:Velocity node straight away, but at the moment we have no way of connecting Game:Start * and*the OnPassengerExit to Math:BooleanTo at the same time.

![Image](https://www.cryengine.com/docs/static/attachments/23461388)

##### Accepting more than one input with the Any node

Move the entity:Abrams and Game:Start nodes to the left to make some more space.

Right Click in the space and go to the Add Node->Logic section. There are various nodes here which can be used to control the logic of your flow graph. Select the one called **Any**.

The **Logic:Any** node will trigger the output each time any of the inputs are activated. Other useful nodes include Logic:All, which triggers when all of the connected inputs have been activated.

- Connect **OnPassengerExit** to the ** in1** part of Logic:Any.
- Connect the output from Game:Start to the **in2** part of Logic:Any.
- Connect the **out** of Logic:Any to the **false** part of Math:BooleanTo.

Dock the Flow Graph window and organize it so that you can see the **Entity:Velocity** and ** UpdateSpeedometer** nodes.

Start the game with **Ctrl+G**.

Now you should see that the Entity:Velocity node only updates when you are in the vehicle.

![Image](https://www.cryengine.com/docs/static/attachments/23461387)

### Adding Comments

Now your Flow Graph is getting quite complex it might be helpful to add some comments so that you know what is going on if you return to it later.

Arrange your nodes so Logic:Any, Math:BooleanTo, Entity:Velocity and Demo_Speedo are lined up with each other.

Right click on the background and select Add Comment->Add Comment Box.

Drag the edges of the box to resize it around the nodes.

Double click on the title which says "This is a comment box" and change it to *Enable / Disable Speedometer Update.*

### Result

You have added a simple speedometer to the tank vehicle, and learned the basics of using Flow Graph in CryEngine.

![Image](https://www.cryengine.com/docs/static/attachments/23461386)

### Try it yourself - More improvements

If you're feeling confident, here are some ways you could tweak the Speedometer even more. For example if you drive the boat, you will notice the speed is in knots, and it only has two gears.

![Image](https://www.cryengine.com/docs/static/attachments/23461385)

#### Changing the Units (Beginner)

The Demo_Speedo HUD element has a few functions which you can use to make the vehicles seem different.

You can change the units from KMH to Miles per hour, Knots or Meters per second by adding a UI:Functions: Demo Speedo: SetSpeedUnits node. Setting the _speedUnits section to kmh, mph, mps or kn changes the units and adjusts the relative speed on the dial.

Take a look at the flowgraph for the boat for an example.

![Image](https://www.cryengine.com/docs/static/attachments/23461384)

#### Changing the Gears and Rev Limits (Intermediate)

Even though the Speedo has gear changes and a rev counter, these are all faked within the UI component. A more complicated change would be to change the speeds at which the speedometer fakes the gear change.

To do this you would need to create a UI:Variable:Array with the new speeds. The first number should be 0, and the last number slightly higher than the top speed.

To set the values in an array you need to use the UI:Util:ToArray node.

For an example of how this should be set up, take a look at the flowgraph for the boat.

![Image](https://www.cryengine.com/docs/static/attachments/23461383)

#### Make the Speedometer play nice with the other HUD elements (Intermediate)

Just now the speedometer gets in the way of the standard HUD. You could play with the UI: Display: Constraints node to position the speedometer better. If you want to go into even more depth you could delve into the flowgraph in UI Actions/HUD and make the various elements turn off so that they don't overlap.

#### Creating a Vehicle with real gears (Advanced)

The default vehicles don't give out any information about gears or revs, but in theory you could make a more detailed vehicle model that outputs this information.

#### Adding Functionality to the Demo HUD and Speedometer Element (Advanced)

If are interested in more complex scripting such as Action Script, you could add new features to the Demo HUD or Speedometer Flash files, such as an Altimeter and Vehicle health bar.

[Getting Started](#getting-started)[Adding the basic Speedometer](#adding-the-basic-speedometer)[Quickly Hooking up the Speed](#quickly-hooking-up-the-speed)[Fixing Problems - Making the Speedometer Unbreakable](#fixing-problems-making-the-speedometer-unbreakable)[Adding Comments](#adding-comments)[Result](#result)[Try it yourself - More improvements](#try-it-yourself-more-improvements)
