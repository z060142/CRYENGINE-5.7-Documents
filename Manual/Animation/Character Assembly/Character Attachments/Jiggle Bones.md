# Jiggle Bones

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959411
- Page ID: 44959411
- Breadcrumb: Animation > Character Assembly > Character Attachments > Jiggle Bones
- Parent: Character Attachments

## Content

![Image](https://www.cryengine.com/docs/static/attachments/44959412)

## Overview

To complete this tutorial we will now be moving into CRYENGINE. We'll be using the Character Tool and using the character attachment system within.

### Tutorial Files

Please download and unzip the tutorial file contents to your <CRYENGINE_ROOT> folder. The "SkeletonList.xml" is normally located at "<DRIVE_LETTER>:\<CRYENGINE_ROOT>\GameSDK\Animations".

Source 3ds Max / Maya scenes with exported CRYENGINE files:

**[jiggle_bone_tutorial.zip](/docs/static/attachments/24004040)**

**[skeletonlist.zip](/docs/static/attachments/24004041)**

Since the skeleton list is not used in Engine release 5.6 onwards, the Tutorial SkeletonList.xml file doesn't need to be downloaded. Any other references to this file within this tutorial can also be ignored.

**Please backup your "SkeletonList.xml" before overwriting!**

If you want to open the provided tutorial CDF in Character Tool immediately, you'll have to add the pony tail CHR file to your custom "SkeletonList.xml" first.

### Set up the exported assets in CRYENGINE's Character Tool

Depending on the DCC program you used to follow this tutorial, you may have to replace any <3ds Max> with <Maya> related names. Though there are some distinctions of how 3ds Max "**bone**" & Maya "**joint**" are implemented, they represent the same concept, so don't get confused when we use "joints" and "bones".
From the last section you should have these files exported:

- **ponytail_skel.chr** (primary base skeleton you want to attach the pony tail SKIN attachment to)
- **ponytail_msh.skin** (the SKIN attachment to extend your base character/skeleton)
- **ponytailMAT.mtl** (a standard blank material)
- **default.i_caf** (an uncompressed animation to drive the physics of the pony tail)

In this section we will go through the process of how to get the *.chr file into the "SkeletonList.xml", create a new character and extend the new character with a pony tail "Skin Attachment". Thereafter, we will go into the next section demonstrating the "Character Tool's" Attachment System with some use cases. By the end you will have...:

- edited the SkeletonList.xml
- added a *.cdf file
- added a *.chrparams file
- added an *.animsettings file
- (generated the compressed *.caf file)

##### Add a new Character in CRYENGINE's Character Tool

- Fire up the Sandbox Editor and open the Character Tool. Add the exported *.chr file to the SkeletonList.xml
*Add the exported *.CHR skeleton file to the "SkeletonList.xml"*
![Image](https://www.cryengine.com/docs/static/attachments/51347619)
- Your new entry should look like this, depending if you want to modify the skeleton's name and how many skeleton entries have already been added.
*![Image](https://www.cryengine.com/docs/static/attachments/51347620)*
- Don't forget to save the "SkeletonList.xml", otherwise you cannot find the skeleton after you made the CDF and try to point the CDF to the skeleton/CHR file!
*Save your "SkeletonList.xml"*
![Image](https://www.cryengine.com/docs/static/attachments/51347621)
- Now it's time to add a new CRYENGINE Character by creating a new *.CDF file. On the Character Tool menu bar, go to "File" -> "New Character..." and a new dialog window opens. Go to your project folder (ours is located under "GameSDK\Objects\jigglebone_tutorial_maya") and give the CDF a proper name. In our case, we chose "attachment_ponytail.cdf"
*Add a new CDF (Charcater Definition File)*
![Image](https://www.cryengine.com/docs/static/attachments/51347622)
- Look at the pane on the left of the Character Tool. You will find your new character CDF file under: Characters -> Objects -> jigglebone_tutorial_maya\attachment_ponytail.cdf. Double-click it to open the character. Notice the asterisk in front of the name?
Whenever you see an asterisk "*" in front of names in CRYENGINE, the recent changes you made have not been saved yet. So press the "Save" icon when you are happy with the changes.
On the right pane the properties of the CDF are displayed, there browse for the *.chr you exported and added to the "SkeletonList.xml": * Add the skeleton again to the CDF!*![Image](https://www.cryengine.com/docs/static/attachments/51347624)
- You can turn on the display of Joints and Joint Names to see you have your skeleton without any geometry skinned to it.
*Display of joints to verify you correctly exported your skeleton!*
![Image](https://www.cryengine.com/docs/static/attachments/51347625)
- Since we only added an abstract skeleton as a representation of a human character (only a pelvis and a head along with the root joint was made!) we don't even need a human-like mesh bound to this skeleton. It is just to show you how minimalistic we can go with a base skeleton and focus on the physics part that comes in the next section.

##### Add the pony tail as "Skin Attachment" to extend the base skeleton

- We must add the pony tail skin attachment. With the character CDF still active, we can add an attchment and change from the default "Joint Attachment" to a "Skin Attachment" and choose the "ponytail_MSH.skin" file.
*Add the pony tail skinned object as "Skin Attachment"*
![Image](https://www.cryengine.com/docs/static/attachments/51347626)

##### Get the exported animations showing up by adding a *.CHRPARAMS file to your skeleton CHR

- Click on the skeleton CHR file to get access to its chrparams. CRYENGINE will automatically create the *.chrparams file for you if it cannot find one. The next step is to tell the Character Tool where you exported the animations.
*Add *.CHRPARAMS file by clicking on the skeleton CHR entry in your CDF*
![Image](https://www.cryengine.com/docs/static/attachments/51347627)
- Browse to the folder where the Character Tool will find our animations.
*Set the animation folder*
![Image](https://www.cryengine.com/docs/static/attachments/51347628)
- After you finished and saved the *.chrparams file, you should see the animation we made and called "default" under the Animations drop-down list. Look at the left pane of the Character Tool window and find this animation:
*Animation set you exported:*
![Image](https://www.cryengine.com/docs/static/attachments/51347630)
- Check the correctness of the exported animation by double-clicking on the "default" file or just hit the "Play" button in the bottom "Playback" section. The Character Tool should also create an *.animasettings file for you and compress the exported *.i_caf files to *.caf

##### Add "Joint Attachments" to let the physics of the Attachment System drive the pony tail skin joints

- For each joint of the pony tail taking part in the simulation, we will add a "Joint Attachment" in your character's CDF. Look at the pony tail joint names. We prefixed them with "sim". So, for these specified joints please do the following:
- Activate the "Redirect to Joint" checkbox, repeat this for each subsequent simulation joint
- A unique name must be given to each Joint Attachment, repeat this for each subsequent simulation joint
- Browse and point to the joint/bone skinned to the pony tail geometry, repeat this for each subsequent child joint going from root to its leaf joint
- Choose the Simulation type: "Pendulum Cone" for each Joint Attachment
*How to activate the physics of the Attachment System, be certain you have set these five areas correctly!*
![Image](https://www.cryengine.com/docs/static/attachments/51347631)
- After you added a "Joint Attachment" for all pony tail simulation joints and set the five parameters shown in step 1, your basic setup is done.
*Resulting "Joint Attachments" added*
![Image](https://www.cryengine.com/docs/static/attachments/51347632)
Next you will be playing with the settings of the "Pendulum Cone" physics. This will be explained in the next section and which parameters make the big changes.

### Joint Attachment Physics in Character Tool

Before we dig deeper into the simulation parameters, let's change the layout for the properties on the right side of the Character Tool window. This is an important step to be able to tweak the values across multiple "Joint Attachments" concurrently.

#### Switch Layout for manipulating physics parameters across multiple Joint Attachments

*Split the right pane in the "Properties" section into two right and left halves*![Image](https://www.cryengine.com/docs/static/attachments/51347633)

Try selecting multiple Joint Attachments on the left and make changes for the same parameter in the right. Cool, eh?

*Always use this layout for tweaking parameter across several attachments.*![Image](https://www.cryengine.com/docs/static/attachments/51347634)

In addition, you should turn on/off the debug view when you make changes to the simulation parameters:

*Debug View![Image](https://www.cryengine.com/docs/static/attachments/51347636)*

#### I. Physics Use Case 1: (File: attachment_ponytail.cdf)

#### Pony Tail Setup using Pendulum Cones

****First, pendulum physics will only produce rotations to your simulated nodes.****If you need translations, use the spring attachments or at least mix the spring and pendulum simulated attachments. You will see bending of the joint chain.

The strategy to changing the physics parameters is to only change one of a kind at the same time, ideally starting from the top. For the Pendulum physics system we highlighted the parameter names by using a **Blue** color.

*Take special care of these two parameters for each "Joint Attachment" in the attachment list.*![Image](https://www.cryengine.com/docs/static/attachments/51347637)

##### Physics Parameters you normally do not have to change

- **Gravity:** Except you want to simulate outer space or being on other planets.

##### Pendulum Physics Primary Parameters:

- **Simulation Axis** is the **pendulum vector and length.** Thus, a vector v1 = [500, 0, 0] is not equal to v2 = [1, 0, 0] the physics calculations.
The reason that we took special care of the orientation of the "Local Rotation Axis" of every joint in Maya/3ds Max now pays off. We only need to type in x-values for the simulation axis as the joints aim axis is its local x-axis.
For a more "stable" simulation, one or two of the top joints should receive bigger pendulum lengths than the ones at the end of the chain. Open the provided character CDF and examine the values.
- **Damping** has a domain range from [0..10]. For a nice swinging pony tail, keep it at some lower values, like 2 or 3.
- **Joint Spring** domain ranges from 0 to 1000, so don't be shy to increase this to something like 50 or 200. This value drives the force to pull the simulation back to its original joint. This value will make it behave more like stiff "** Spring Ellipsoid" simulation**.
- **Cone Angle** is the degree of freedom of movement. The standard 45deg works fine on most cases though and only needs re-adjustment once or twice. Remember, this parameter also depends on the number of joints and the degree of freedom for the whole joint chain. In some some cases you must increase it, e.g. for an iron chain with many links.

##### Pendulum Physics Secondary Parameters:

- **Simulation FPS** may be set to the FPS you exported (30FPS?), just stay reasonable. The standard 10 FPS works fine for slower primary animations. Increase to 120FPS if you have "unstable" simulation results. This is especially true for springs in the next section.
- **Spring Target** lets you deform the initial shape of your joint chain. The Joint Spring will pull to this target from the joint chain initial location. You haven't modeled the pony tail joint chain into a nice looking "S" shape? Now use the spring target to reshape it.
- **Pivot Offset** lets you move the simulation pivot to a different place. If you did the joint orientation and joint placement correctly in your 3D application, you don't need to re-adjust.
- You can add offset **T**ranslate or **R**otate each joint in your pony tail skeleton by these two vectors:
*For the first joint we added a rotation offset to make the pony tail look like it's sticking out of the back of the head and then hanging down.*
![Image](https://www.cryengine.com/docs/static/attachments/51347638)

##### Parameters having no impact on the simulation of "Pendulum Cone"

- **Mass**
- **Hinge Rotation** is only applicable to the ** Pendulum Hinge**simulation and will be overwritten by Cone Angle

All other mentioned parameters are applicable to the other pendulum types: Pendulum Hinge, Pendulum Half Cone, etc...

How to set up "Pendula" attachments:
Try using the same parameter values for the simulated joints, especially true with equidistant joints.

If you leave the "Pendulum Cone" simulation joints to the default values, you may want to play with the Damping, Joint Spring and the Cone Angle to get nice results:

use low Damping values around 0.3 in 0.05 steps.

start with Joint Spring values around 20 and advance in steps of plus/minus 5.

increase the Cone Angle, if the simulation becomes jerky. Re-evaluate Damping and Joint Spring.

#### II. Physics Use Case 2: (File: attachment_antenna.cdf)

#### Antenna Setup using Spring Ellipsoids

**First, spring physics will produce only translations.** If you need rotations, get the pendulum or at least mix the spring and pendulum simulated attachments.

You will see stretching of the joint chain, along with them translated each on a disk or ellipsoid shape, when using this simulation type.

##### Spring Ellipsoid Primary Parameters:

- **Mass** - While not affecting the pendulum physics it does have a huge impact for springs. Apply small values between 0 and 1.
- **Gravity** - You may want to change the Gravity for ** Spring Ellipsoid** simulations. Try lowering Gravity and Mass for all simulated joints when your springs tend to collapse or go wild.
- **Damping** - Takes the energy out of the spring movement
- **Stiffness** is how stiff you want the springs to be. The higher the stiffness the more force must be applied to make the joint chain deform.
- **Disk Radius**and ****Sphere Scale****are used for defining the freedom of movement for the springs.
Disk radius is most important to limit the spring elongations. If the simulation becomes "unstable" and the joint vibrating like crazy, try increasing the Disk Radius.
Sphere Scale value not equal to 1 will deform the range of movement to an ellipsoid shape. If one value is 0, this will limit the spring movement to a disc.
- **Simulation FPS** should be set to higher values for **Spring Ellipsoid** than the default 10 fps, we recommend 60+ FPS.

##### Spring Ellipsoid Secondary Parameters:

- **Disk Rotation** is linked to the Disk Radius and Sphere Scale. When the borders of the spring movement are shaped like a disc (Sphere Scale = [0, 0]), you can turn the disc using this parameter.
- **Spring Target** defines the target position to which the direction and additional force are applied. This will result in an offset of the initial spring rest position.
- **Pivot Offset** will move the initial position of the simulation. If you aligned the joints in your source 3D application scene correctly, you normally do not need to change this value.

*Example of a "Spring Ellipsoid" simulation setup (File: attachment_antenna.cdf)*![Image](https://www.cryengine.com/docs/static/attachments/51347639)

**Springs are much harder to control than the pendulum. Your main goal should be:**

**Avoid****the springs hitting the limits of the Disk Radius/Sphere Scale. You set the Stiffness, Gravity, Mass & Damping to prevent this. Otherwise, the procedural animation may look jerky.**
How to set up "Springs" attachments:
Start using same parameter values for the simulated joints, but vary the pendulum length (Simluation Axis) to "stabilize" the joints.

With Debug View turned on:

increase the Disk Radius, so the springs have full freedom of movement,

lower Gravity to small values, e.g. 0.2,

increase Damping to high values up to 10,

lower Mass below 1.0,

play with Stiffness values, in steps of 5, start with 30.

#### III. Physics Use Case 3: (File: attachment_springytail.cdf)

#### Mixing Pendulums & Spring Ellipsoids

Open the "attachment_springytail.cdf" in Character Tool.

Perhaps you may have noticed in the previous **Use Case 2,** that to *offset rotate* * up* the antenna, we added a "**Pendulum Cone**" with initial rotation. This way, we could rotate the whole joint chain. Hence, you may have SEVERAL simulations running on ONE joint:

*Achieve a similar pendulum simulation with springs*![Image](https://www.cryengine.com/docs/static/attachments/51347640)

We used a different setup to make a pony tail, but the difference between the CDF using springs and pendula is the following **(beside the stretching (translation) of the springs and bending (rotation) of the pendula simulation)**:

**With the springs, the whole joint chain is tilted as the "head joint" (the node that is animated) ends up tilted, while with the pendula, the whole joint chain rotates to point down, as gravity pulls it downwards.**

*Comparing the difference in setups with Springs & Pendula, while in a rest pose.![Image](https://www.cryengine.com/docs/static/attachments/51347641)![Image](https://www.cryengine.com/docs/static/attachments/51347642)*

With the spring sample CDF, we added in front of the springs a pendulum simulation joint to offset rotate the joint chain. We could also replicate the pendulum-only setup by tweaking the value for the pendulum pulled downwards by gravity.

### Summary

What we achieved in this tutorial:

- Create a simplified, abstract character skeleton (as the primary skeleton)
- Create a simple 3ds Max bone/Maya joint chain (as the secondary skeleton)
- Create and smooth bind a poly cylinder to the joint chain (the secondary skeleton)
- Learn the requirements/rules for a secondary skeleton to be attachable to the primary character skeleton in CRYENGINE
- Make the Maya scene export-ready for CRYENGINE, in 3ds Max we don' t have to change the scene hierarchy
- Make the CRYENGINE nodes and a basic material to be able to export to CRYENGINE
- Gather the exported 3ds Max/Maya assets inside CRYENGINE's Character Tool
- Set up a new *.CDF file (a typical CRYENGINE character)
- Extend a character with a pony tail
- Set up physics simulation parameters for "Joint Attachment"
- Understand the different use cases of CRYENGINE's "Joint Attachments"

[Tutorial Files](#tutorial-files)[Set up the exported assets in CRYENGINE's Character Tool](#set-up-the-exported-assets-in-cryengines-character-tool)[Joint Attachment Physics in Character Tool](#joint-attachment-physics-in-character-tool)[Summary](#summary)
