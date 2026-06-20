# Tutorial - Animated Objects (cga) Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23299333
- Page ID: 23299333
- Breadcrumb: Tutorials > Animation and Characters > Maya > Tutorial - Animated Objects (cga) Maya
- Parent: Maya

## Content

##
Overview

This tutorial takes you through the process of getting a *.cga file into CRYENGINE. This covers the Maya pipeline, covering the basic *.cga with a single animation *.anm file that holds the animation data up to exporting out a *.cga file with multiple *.anm animation files.

Throughout this tutorial you will notice differences between a *.cga export from Maya compared to a *.cga export in 3dsMax. For example, in 3dsMax a *.cga with a single animation does not create an *.anm file.

This tutorial may rely on the GameSDK Sample Project. We recommend that you download this from the
**
[https://www.cryengine.com/marketplace](
Asset Database
)
**
, import it into your Launcher, start it from there and then create a new level.

See
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/36870288](
this page
)
**
 to find out how to import a project to your Launcher. (The default folder for the GameSDK Sample Project when downloaded is
`
**
C:\Program Files (x86)\Crytek\CRYENGINE Launcher\Crytek\gamesdk_<XXX>\GameSDK
**
`
)

##
Tutorial Files

Source Maya ASCII scenes with exported CRYENGINE files:

**
[/docs/static/attachments/25523857](
tutorial_cga_maya.zip
)
**

Please extract this zip file to
`
**
YOUR_PROJECT_FOLDER\Assets
**
`
.
Rules for CGA's and Exporting Animations

-
*.cga animations (*.anm) do not support compression! This means you get keyframes on every frame of the animation, so for example a 10 second animation at 30FPS will result in 300 keyframes for every animatable channel and for every object.

-
Multiple animations for the same object must be saved and exported out as *.anm files. However, you do not need to follow a specific naming rule (as in 3dsMax) because the UI of the Exporter in Maya handles the naming for you.

-
Multiple animations for the same object must be saved and exported out as *.anm files.
**
These have to follow a strict naming convention.
**

-
Must be prefixed with the *.cga's name

Correct
:
**
hmmwv
**
_door_left_front_enter.anm

Incorrect
: door_left_front_enter.anm

-
The
**
first underscore
**
 within the filename denotes the start of the animation name in the engine.

-
Inside the Character Tool, when previewing the *.cga's animation(s) only the animation name is shown and not the entire filename.
*
Pic1: Note the filename difference between the actual filename in the *.pak file vs. what's seen in the Character Tool
*

[Image: /docs/static/attachments/23434655]

Do not use the name
**
"*_helper"
**
 for anything else! It is a
keyword
 for the CRYENGINE Maya Exporter which looks at the lower hierarchy nodes for
**
multiple children
**
transform
**

**
nodes from the
**
"*_helper"
**
 parent group!

##
Prerequisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following:

-

-
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310902](
How to Install CryMayaTools
)

-
[/docs/static/engines/cryengine-3/categories/1114113/pages/17826030](
The Basic CRYENGINE Maya Workflow
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/13205569](
CRYENGINE Exporter
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308289](
Maya Unit Scale to Match up With CRYENGINE Unit System
)

##
Setup for a Single Animation CGA

Set up your Maya scene and save it to an appropriate directory, for example
`
**
YOUR_PROJECT_FOLDER\Assets\Objects\tutorial_cga
**
`
. Be sure that the folder containing the Maya scene and exported files for CRYENGINE is a sub-folder of
**
your project folder
**
.

**
Very important!
**
 You can use underscores in the folder structure and in the filename of the animation, however the Exporter works in such a way that it looks for the first "_" in the animation filename. After that, everything else is considered as the animation name. See above for example filenames under the 'Rules for CGA's and Exporting Animations' section at the top of this page.

We recommend to avoid using more than the standard 'one underscore' for your "cryExportNode_*" node name, for example valid *.cga names should look like the following examples: "cryExportNode_ball" or "cryExportNode_polySphere1".

##
Basic Object Setup/Maya Scene Hierarchy for CGA Export

For this tutorial we will use a simple ball as the content.
Configure the object properly with a material, a collision proxy as well as the visible render mesh.

**
NOTE:
**
 This process is more involved in Maya than in 3dsMax:

Create a poly sphere in the "Perspective View" and move it above the ground. Open the "Crytek" shelf and click on the "Tools" icon. This will bring up the
**
Cry Tools
**
 window where the
**
Create CryExportNode
**
 script button is run.

With the poly sphere selected it will create the typical CRYENGINE export hierarchy.

*
Pic2: Maya initial setup
*

[Image: /docs/static/attachments/23455270]

After you have created the export hierarchy the result is shown in Maya's
**
Outliner
**
. You may want to rename the poly sphere geometry to
**
ballRender_MSH
**
. Do keep in mind that the
**
cryExportNode_ball
**
 and
**
ballmesh_group
**
 nodes illustrated in the screenshot below reflect the CRYENGINE export hierarchy and should not be modified.

**
NOTE:
**
 Be consistent with your naming convention.

*
*
Pic3: Export hierarchy without physics/collision proxy
*

*
*
[Image: /docs/static/attachments/23455271]
*

There is an important difference between Maya and 3dsMax
scenes that are made for a *.cga export
. In the case of Maya:

-
You must create an empty group named
**
"*_helper"
**
(replace the asterisk * with any name).

-
Put this
**
"*_helper"
**
 group under your "cryExportNode_*" group node as its direct descendant.

-
Because this
**
"*_helper"
**
 acts as the ROOT of the whole *.cga object hierarchy it must not have any animation(s).

-
Parent your multiple "*_group" nodes that you created manually to this new
**
"*_helper"
**
 group node.

-
Parent the geometry pieces to the corresponding "*_group" nodes.

-
Do not have any "*_group" named like the "*_helper", for example "ball_helper" and "ball_group" this will create an export error. Rename your group nodes to something like "ball_helper" or "ballmesh_group" or "ballWhatever_group".
*
*
Pic3a: Export hierarchy with an extra "*_helper" group sitting between the "cryExportNode_*"group and any "*_group" nodes
*

*
*
[Image: /docs/static/attachments/23455430]
*

To create a collision/physics proxy, duplicate the poly sphere and the input history. Reduce the complexity of the collision/physics proxy mesh. (You can also add a User Defined Property (UDP) called "sphere" to automatically generate an efficient CRYENGINE collision mesh). Give this collision proxy mesh a proper name, for example "ballProxy_MSH". Check the size of your collision mesh - it should encompass the render mesh geometry. Finally, increase the radius of the input history node if you wish.

*
*
Pic4: Collision/proxy mesh on top of the current render mesh
*

*
*
[Image: /docs/static/attachments/23455272]
*

Place the collision/proxy mesh under the "ballmesh_group" node (the order does not matter). CRYENGINE will recognize the collision/proxy mesh by its material assignment and the group node under which it resides.

*
Pic4a: Collision proxy hierarchy

[Image: /docs/static/attachments/23455273]

*

##
Material Setup

Materials are required for the export from Maya to CRYENGINE.

Create two "Blinn" shaders - the first named "proxy_SUB". the second "render_SUB". Assign the "render_SUB" to the render mesh and the "ballRender_MSH" object. The "proxy_SUB" should be assigned to the collision/proxy mesh object. For better visual feedback inside Maya we have added some transparency to the proxy shader and have set the diffuse color to red (see screenshot below).

*
Pic5: Create two Maya shaders before adding to the CRYENGINE Material Group Editor
*

[Image: /docs/static/attachments/23455274]

The two Maya shaders have to be added to a new CRYENGINE Maya Exporter "Material Group":

Go to the "Crytek" shelf and click on the "MAT.ED" shelf button. The CRYENGINE "Material Groups" window will open and it's here that a material group is created, we have named it "ballMAT". (See Pic6):

*
Pic6: Create a new "Material Group"
*

[Image: /docs/static/attachments/23455280]

Next add the two blinn shaders to your new Material Group "ballMAT".

**
NOTE:
**
 It is good practice to reserve slot no. 1 of any "Material Group" for the CRYENGINE physics/proxy shader.

*
Pic7: Add Maya shaders to the CRYENGINE Material Group
*

[Image: /docs/static/attachments/23455281]

##
Physicalise Maya Shaders Used for Collision/Proxy Meshes

Before your collision mesh is detected as a CRYENGINE collision mesh a "physicalise" extra attribute needs to be added to the shader:

-
Open the
**
Crytek shelf
**
 and click on the
**
Export
**
 shelf button.

-
Select the
**
proxy_SUB
**
 in Maya's
**
Outliner
**
.
In the
**
Crytek Export
**
 window there is an
**
Add Attributes
**
 button. With the
**
proxy_SUB
**
 shader selected (or the collision mesh object (s)), click on the
**
Add Attributes
**
 button.

**
NOTE:
**
 There will be no feedback whenever you press this button!
*

*

[Image: /docs/static/attachments/23455286]

*
Pic8: Add "Physicalise" extra attribute to the proxy shader
*

In to order to verify that the
**
Physicalise
**
 attribute has been added to the proxy shader selected, open Maya's
**
Attribute Editor
**
 (CTRL-A). Under the
**
proxy_SUB
**
 tab go to the
**
Extra Attributes
**
 rollout and open it. The
**
Physicalise: None
**
 attribute will be activated - change its value from
**
None
**
 to
**
ProxyNoDraw
**
 (see
*
Pic9
*
 below).

[Image: /docs/static/attachments/23455287]

*
Pic9: Validate the added extra attribute "Physicalise: ProxyNoDraw"!
*

So far there are no great differences between an export to a CRYENGINE *.cgf file and *.cga file in Maya.

##
Add a Simple CGA Animation

For this tutorial we have made
*
one
*
 simple animation, have named the animation as "Default" and have exported it to a CRYENGINE *.cga file.

Please review the Autodesk Maya doc/help pages to learn about setting keyframes and making simple animations. This information is not covered in this tutorial - we just show the results.

So we want to add a simple animation that moves up/down and rotates for the
**
*_group
**
 node, i.e. in our case the
**
ballmesh_group
**
:

-
Grab the
**
ballmesh_group
**
 and keyframe some
translation
 and
rotation
 animation to it.

-
Avoid keying
**
ballRender_MSH
**
 or the
**
ballProxy_MSH
**
 nodes! These animations won't be exported.

[Image: /docs/static/attachments/23455441]

*
Pic10: Only animate the "group" transform node! Pay attention as to where the group node pivot is located - any children mesh objects will be animated around it!
*

We only animate the group node of the (render) mesh objects. This is because the CRYENGINE Exporter for Maya only samples animation data on the
**
*_group
**
 nodes, and does not sample any animation data not on the mesh nodes.

You should always create a parent group for each piece of geometry which needs an independent animation. You may have noticed the different pivot location of the
**
*_group
**
 node and the render mesh + physics proxy object!

You may want to verify this for yourself. Animate the mesh object
**
ballRender_MSH
**
 and check if you are getting any animation after you have exported to the CRYENGINE Sandbox Editor!

##
Exporting

##
Add an Animation to Anim Manager

Open the
**
Crytek Export
**
 Tool from your
**
Crytek shelf
**
. Go to the mid section and click on the
**
Anim Manager
**
 button. Add a new animation to be exported and set the options as shown below in
*
Pic11:
*

[Image: /docs/static/attachments/23455459]

*
Pic11: Add a Default animation for export
*

Below you see the settings before *.cga animation export in
**
Crytek Export
**
. Make sure to activate
**
Export *.anm's with *.cga's
**
!

[Image: /docs/static/attachments/23455462]
[Image: /docs/static/attachments/23455461]

*
Pic12 & 13: Last settings to check before export
*

When you are ready, hit the
**
Export All/Selected
**
 button. The next steps will involve adding this *.cga/*.anm file as an
**
AnimObject
**
 entity to the CRYENGINE Sandbox Editor and making a Flow Graph to play the
**
Default
**
 animation.

##
Checking the Object in the Editor

Open your Level or create a new one.

In the
**
Create Objects
**
 panel, click the
**
Entity
**
 button and then expand the
**
Physics
**
 option. Select the
**
AnimObject
**
 option and drag it into the viewport. By default it is assigned a windsock model.

*

*
[Image: /docs/static/attachments/25034783]

*
Pic14a: Adding an AnimObject to the Level
*

To change the model to the object that you have just created go to the
**
Entity Properties
**
 menu. One of the options available is a field called
**
Model
**
. Here you can click to browse to the folder where you have saved the new *.cga (and select it).

**
NOTE:
**
Further down the property tree under the
**
Animation
**
 menu is the
**
Animation
**
 option which is preset to the "Default" animation.

It could be that the windsock model is fluttering in your Level, if so then this is because it is playing its default animation. Once you swap out the source model of the Entity to be your new model, it should automatically play the bouncing ball loop.

[Image: /docs/static/attachments/25034784]

*
Pic14b: AnimObjects - model & animation path
*

##
Final Results

[Image: /docs/static/attachments/25034785]

*
Pic14c: AnimObject using the newly exported *.cga
*

*

*

As you can see in the above screenshot we have the AnimObject Entity using the exported *.cga. Also highlighted in the screenshot is the model path that links to your object (objects/tutorial_cga/tutorialcga.cga).
**
Loop
**
 and
**
Playing
**
 are also ticked - this gives you instant play feedback of the animation.

**
NOTE:
**
 The play speed can be set to a different value.

A play speed of 1 is the exact speed of the animation as setup in the Maya scene. A play speed of 0.5 will play at 1/2 speed while a play speed of 2 will play at twice the speed.

In the screenshot above, the bounding box is highlighted. This shows the default position of the object. However, as the object is currently 1/2 way through the animation, it is shown outside of the bounding box.

##
Flow Graph

Sometimes having an object looping an animation at the start is not the behavior you require. Maybe you want the animation to only trigger when a certain event happens. In these situations the "Flow Graph" tool is used to control this type of interaction.

**
Preparation:
**
 In the
**
Create Object
**
 panel, click the
**
Entity
**
 button, expand the
**
Physics
**
 option and then double click on the
**
AnimObject
**
 menu option. In
**
Entity Properties
**
, under the
**
Animation
**
 menu,
untick the
**
Playing
**
 checkbox.

If you want your animation to be a 'one-shot' animation, then you should also untick the
**
Loop
**
 checkbox. However, in our example once triggered we want it to play continuously.

Flow Graph Tool
In respect to the next part of this tutorial it is assumed that you have some basic knowledge of the
**
Flow Graph
**
 tool and can add objects and link them together.

*

*
[Image: /docs/static/attachments/23434885]

*
Pic14d: Flow Graph used to trigger an animation on an AnimObject
*

-
Create a Flow Graph, either directly on the
**
Entity
**
 or on another object. (It doesn't matter where you store it).

-
Having the
**
AnimObject
**
 selected, right click inside the Flow Graph and
**
Add Selected Entity
**
.

-
Add the 3 preceding nodes (
**
Game:Start
**
,
**
Time:Delay
**
,
**
Logic:Any
**
) and connect them as you see above.

-
Finally, add the
**
Debug:InputKey
**
 and assign a key to it. This is so you can reset and re-trigger the animation whenever you want.

-
Note how the
**
InputKey
**
 also passes through the
**
Logic:Any
**
 node. This is because you have to restart the animation when you reset it. If not, it will reset the animation, but not trigger it again.
The delay node (with a 3 second delay) is set that way so as to avoid triggering as soon as you jump in game. This can be replaced with a
**
Proximity Trigger
**
 or once a certain value has been met within a game token. How you want the trigger logic to operate is of course entirely up to you (we have used just one example here).

In the next section we will export multiple *.cga animations, and in addition to the standard *.cga file, multiple *.anm files also. This is all achieved in one go in Maya.

##
Setup for Multiple Animations on a Single CGA

So far we have only been using the *.cga with the default animation. Sometimes this is all you need - a single animation on the object. However, you can go a lot further with *.cga objects. For example, the vehicles shipped in the Sandbox Editor are also *.cga objects. The HMMWV for example has several animations for the opening and closing of the doors.

In Maya we simply add new animations using the
**
Anim Manager
**
 inside the
**
Crytek Export tool
**
 from the shelf. This was shown in the previous section about exporting a single *.cga. The screenshot below illustrates the result before hitting the
**
Export All
**
 button.

[Image: /docs/static/attachments/23455465]

*
Pic15: Shown is the stack of animations to be exported
*

As can be seen exporting multiple *.anm files is not as difficult as it is in 3dsMax. To verify if you 'have' all the files from the export process go to the folder where you saved the Maya source file and check for the following files: a *.cga file for every
**
cryExportNode_*
**
 group node, and an *.anm file for every animation you added to the
**
Anim Manager
**
.

##
Testing the New ANM Files in the Character Tool

The following screenshot shows the
**
Character Tool
**
 is open, the asset (*.cga) is selected and the available animations are on display.
[Image: /docs/static/attachments/23455479]

*
Pic16: "Character Tool" showing the selected *.cga and the created animations that are associated with it
*

[#tutorial-files](
Tutorial Files
)
[#prerequisites-for-this-tutorial](
Prerequisites for this Tutorial
)
[#setup-for-a-single-animation-cga](
Setup for a Single Animation CGA
)
[#setup-for-multiple-animations-on-a-single-cga](
Setup for Multiple Animations on a Single CGA
)
