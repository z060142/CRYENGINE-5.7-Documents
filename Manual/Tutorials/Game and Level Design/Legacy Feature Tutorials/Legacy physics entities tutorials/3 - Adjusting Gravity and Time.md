# 3 - Adjusting Gravity and Time

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27591009
- Page ID: 27591009
- Breadcrumb: Tutorials > Game and Level Design > Legacy Feature Tutorials > Legacy physics entities tutorials > 3 - Adjusting Gravity and Time
- Parent: Legacy physics entities tutorials

## Content

##
How Do We Adjust Variables Globally?

If this is the first time you have touched Flow Graph or adjusted console variables I recommend that you go through the Flow Graph Quick Start to become familiar with the concepts. To adjust our path for a moment we will look at two console variables in this section that will allow us to adjust the universal settings  of both gravity but also the speed in which time is played out. Generally speaking if you wanted to expose this permanently you should go about doing so within Flow Graph on game start or program it directly into your game. Below is a short description of each of the console variables we will expose through Flow Graph:

-
**
t_scale
**
 - This variable allows you to define the scale of time and opens up the possibilities to effects like bullet time as seen in the popular Matrix franchise.

-
**
p_gravity_z
**
 - by default this range can change to -13 or physically accurate in a model of -9.81 and is a precise gravitational force cast over the entire level to mimic real world conditions. Lowering the negativity of this will cause the world to mimic the effects of other planets or large masses like the moon.

##
Manipulating the Time and Gravity Console Variables

Follow these below mentioned steps to change the speed of time and the influence of gravity:

-
Create a basic Entity by going to
**
Create Object -> Legacy Entities -> Physics -> BasicEntity
**
 and drag it into the scene. Scrolling down on the right-hand side in the properties panel we will want to change the mass from -1 to 50 in order for it to have proper physics applied.

-
Right click the sphere and choose
**
Create Flow Graph
**
. Name it "physicsQuickStart" if you have not done so prior.

-
Create a
**
Game:Start
**
 node to connect our console variables into. To access the default node we will use to house the variable, right click the graph and navigate to
**
Add Node -> Debug -> ConsoleVariable
**
.
**

**
Add one to the scene, along with copy-pasting a second one as we have two variables to declare.

-
We can begin feeding in the variables and their values into their respective nodes. For the setting of gravity we look to reduce to about a 1/3 of the Earth's at a setting of
**
-3
**
. Alongside this we will be looking to trim time down to be half as much when  setting it to
**
.5
**
 in value. Once you have the values in place simply make sure that the
**
Game:Start
**
 node has the output driving into the set input port of each of your Console Variable nodes.

-
Finally, as a quick note you can also declare the console variables within the Cryproject file itself and then it will be universally set on system startup in case you want to always have a setting for the entirety of development. The Cryproject file is located in your project root directory and can be opened inside of any text editor. In my case I have chosen to use Notepad++. Simply enter the text as typed and pictured below into you CryProject file and press save (
*
Editor restart required
*
).

##
Step 1

[Image: /docs/static/attachments/29928956]

##
Step 2

[Image: /docs/static/attachments/29928957]

##
Step 3

[Image: /docs/static/attachments/29928958]

##
Step 4-1

[Image: /docs/static/attachments/29928959]

##
Step 4-2

[Image: /docs/static/attachments/29928960]
