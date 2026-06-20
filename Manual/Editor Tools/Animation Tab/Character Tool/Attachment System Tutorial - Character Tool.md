# Attachment System Tutorial - Character Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450433
- Page ID: 29450433
- Breadcrumb: Editor Tools > Animation Tab > Character Tool > Attachment System Tutorial - Character Tool
- Parent: Character Tool

## Content

##
Attachment System in Character Tool

The character pipeline uses an attachment system to customize the appearance of the character model in a variety of ways. In general this allows you to choose different skins and accessories in order to create a unique look.

In CRYENGINE, four attachment types are supported;

**
1-Skinned Attachment and Skeleton-Extensions
**

With skinned attachments entire body parts such as; heads, hands, or upper & lower body parts can be replaced, furthermore these parts are automatically animated and deformed by the base skeleton. With the older version of CRYENGINE it was only possible to attach a new skin if every joint already existed and was available in the base skeleton. However, since CRYENGINE3.6 we have supported a new feature called
**
Skeleton-Extensions
**
 that allows the use of skinned attachments that have more joints and different joints then the base skeleton. It is also possible to merge all types of skeletons together, even skeletons from totally different characters
**
.
**

**
2-Joint Attachment
**

Joint attachments provide a socket in which you can optionally place a CDF, CGF or skin. Sockets are linked to a joint and move with the joint when the skeleton is animated. Since CRYENGINE 3.6 secondary animations can be enabled on a socket, these are additional motions based on a physical simulation and are generated in response to the movements of the character to make loosely attached objects behave more realistically when the character is undertaking fast movements. These secondary animations can also be redirected to the skeleton of the character itself and apply the simulated motion to all vertices that are part of the skinned mesh and weighted to the joint (this is very useful when animating hair and cloth). By enabling collision detection, then these simulated objects can also interact with the character.

**
3-Face Attachment
**

Face attachments provide a socket in which you can optionally place a model, a light or another entity. The socket of a face attachment is attached to one particular triangle (=face) on the surface of the mesh and moves along with the triangle when the skeleton is animated and the mesh gets deformed. The location of the face attachment can be relative to the triangle and it is possible to assign face attachments to all skinned meshes of a character.

**
4-Proxy Attachment
**

To deal with collision detection and response on living characters, then a special geometric object called a
[V80-Lozenge.wmv](/docs/static/attachments/28900328)
 is used. Lozenges are normal attachments that are linked to the joints and move with the skeleton. A lozenge is represented by 4 numbers, and with these 4 numbers points, spheres, capsules, line-segments, rectangles, boxes, 2D-lozenges and 3D-lozenges can be created. That’s 8 different shapes (and everything in-between) that can be used to approximate the shape of arms, legs and the torso of a human body.

##
Creating a Character Definition File (CDF)

If you want to attach something to a character, then the first step is to create a Character Definition File (CDF). A CDF is an XML file that combines different character parts such as; skeletons, meshes, materials and attachments. Below are the steps to create a CDF.

Go to the file menu and click on
**
New character
**
. A file dialog opens, choose the filepath and type in the filename for the new CDF, for example “attachment_00.cdf”. If you click
**
Save
**
 it will create an empty CDF in the specified folder, but without a skeleton or an attachment. The property panel for CDF’s will show the following warning:

![Image](https://www.cryengine.com/docs/static/attachments/28900322)

Next, double-click on the
**
Folder
**
 button next to
**
Skeleton
**
, then select a skeleton, i.e. objects/characters/human/generic/skeleton_player_generic.chr, and click
**
Open
**
 to load the skeleton. This will assign the skeleton automatically to the CDF. To make the skeleton visible, click on
**
Display Options
**
 (the button at the top of the viewport) and open up the section
**
Skeleton
**
 then activate the check box
**
Joints
**
. You should then see the following image in the viewport, and at this point you have a CDF with an empty skeleton and no attachments (however, it is already possible to play animations on this skeleton).

*
**
![Image](https://www.cryengine.com/docs/static/attachments/28900321)
**
*

##
Setup of Attachment Sockets

If you want to attach something to a character, then the first step is to create an "empty" socket.

**
Step 1: Creating a Socket
**

Go to the property panel for CDF’s (click on the name of the CDF next to character in the scene parameters), then click on the button next to Attachments and select
**
Insert
**
. This creates an unnamed empty socket. Enter an arbitrary name for the socket, for example "fullbodymesh".

![Image](https://www.cryengine.com/docs/static/attachments/28900320)

**
Step 2: Setting the Type of Socket
**

An empty socket is basically a placeholder for different attachment types and in its most simple form just holds the
**
name,
**

**
flags
**
 and
**
type
**
 of the socket. However, more complex sockets (i.e. joint and face attachments) also have a position for the socket which moves when the character is animated. Empty sockets are often used by the game code to plugin and process typical game objects such as; entities, lights and particle effects. These objects are created by the game code and attached to the sockets, for example to give a character different weapons while the game is running. You can visualize all empty sockets on a model with the console command
**
ca_DrawEmptyAttachments=1
**
. In the Character Tool you can also visualize all available sockets on a character if you use
**
DisplayOptions
**
 and activate the check box
**
Attachment/ModifierGizmo
**
. However, most sockets are not usually empty. In Character Tool you can use them to plugin different meshes (skinned and static), collision proxies and you can also apply physical simulations to them.

**
Skinned Attachments:
**
 The socket just created, has by default, the type
**
Joint Attachment
**
. Click on the socket and change the type to
**
Skin Attachment
**
. Then go to
**
geometry
**
 and click on the
**
Folder
**
 button
. This opens a file dialog showing all the *.skin files in the folder. Select "objects/characters/human/sdk_attachment_tutorial/rebels/bodymesh.skin" and click on
**
Open
**
. This will load a skin file and attach it to the skeleton. Each skinned attachment can also have its own set of blend shapes stored in the same file, but they CANNOT have their own set of joint animations. To animate a skinned attachment and deform its mesh, then we always use the skeleton pose of the base character.

You should see the following image in the viewport. In this case all the joints in the skin file are identical to the base skeleton.

**
*
**
**
*
**
![Image](https://www.cryengine.com/docs/static/attachments/28900319)
**
*
**
**
*
**

Skeleton extensions are also created in the same way. Go to the property panel for CDF’s and create a new socket for a skin attachment (as previously described). Call the new attachment "GlottSkull". Then go to geometry and click on the
**
Folder
**
 button
 and select "objects/characters/human/sdk_attachment_tutorial/glottskull/glottskull.skin" and click on
**
Open
**
. This will load a new skin file and attach it to the skeleton. However, in this case the "GlottSkull.skin" has many additional joints that are not available in the base skelet
on, so in order to attach it, simply add the new joints to the base skeleton. In the log file you may see a warning line for every new joint added to the skeleton.

Log file Warning!
*
[Warning] Extending Skeleton, because the joint-name (hairstrand01_chain01) of SKIN (objects/characters/human/sdk_attachment_tutorial/glottskull/glottskull.skin) was not found in SKEL: objects/characters/human/generic/skeleton_player_generic.chr
*

The warning above only appears in Character Tool and can be ignored. It's there to just inform the user who creates a CDF that certain skin attachments require an extension of the skeleton. The following image should be seen in the viewport.

Glottskull attached:

**
![Image](https://www.cryengine.com/docs/static/attachments/28900277)
**

From a user perspective a skeleton-extension is identical to a normal skin attachment (no additional parameters are required). So in the case where a different head skeleton is required (but using the same body) then other elements such as cloth pieces i.e. capes and skirts, helmets and hair styles can all be attached and at the same time - this can be seen the file
**
attachment_03 (skin).cdf
**
.

**
**
![Image](https://www.cryengine.com/docs/static/attachments/28900318)
**
**

That means you can have a minimalistic base skeleton which can be extended by an arbitrarily complex skinning skeleton. Furthermore, the extension of a base skeleton with different skins takes place at loading time (when used in a game) and it is only in the Character Tool where it is allowed to extend at run-time while an animation is playing.

With skeleton-extensions you can only add new child joints to the base skeleton; however you cannot change the existing hierarchy of the base skeleton. This means you cannot remove joints from the hierarchy, you cannot change the location of existing joints and you cannot turn a spine with 4 joints into a spine with 5 joints.

-
To ensure that the extended joints of the skinning skeleton animate properly with the base skeleton, both skeletons need to have at least one joint in common. So for example, if you were to attach a skirt, then you would just need a single common joint (usually at the pelvis) between the two skeletons concerned.

-
Some attachments may require several overlapping joints. For example, if you wanted to attach a new head that needs proper skinning in the neck and shoulder regions, you would need the neck joint and maybe two other joints at the shoulders which are shared between the base skeleton and the head skin.
The system can even handle the situation where both skeletons have no single joint in common - in this case the system creates a new branch from the root. This is shown using the deer in the screen shot below. Want to know more? Then take a look at the file
**
attachment_04 (skin).cdf
**
. You can also animate the deer independently of the human by playing a (partial body) animation in a higher layer.

**
**
![Image](https://www.cryengine.com/docs/static/attachments/28900317)
**
**

This might be a somewhat unusual application, but it’s a great example of the flexibility and beauty of the system. This means that you don’t have to know in advance the type of joint(s) you might need (in the base skeleton) nor do you have to carry extra joint (s) around just in case you might need them, instead the system allows you to add new joints at will and whenever they are required.

**
Joint Attachments:
**
 Go back to the CDF that was originally created i.e.
**
attachment_01.cdf
**
. Do this by double clicking on it in the tree on the left. In the property panel click on the button next to Attachments and select
**
Insert
**
, this creates a new empty socket (without a name). Enter an arbitrary name, for example "weapon" and set the type to
**
Joint Attachment
**
. Then go to
**
Joint
**
 and click on the button next to it:

![Image](https://www.cryengine.com/docs/static/attachments/28900316)

This opens a window showing all the joints in the hierarchy. Finally, select the joint name
**
weapon_bone
**
 and click the
**
OK
**
 button. This creates a socket close to the character’s right hand. Next, go to geometry and click on
**
Folder
**
 button
 and select objects/weapons/rifle/rifle_tp.cgf to assign a rifle to the socket. The socket just created (and the attached rifle) are perfectly aligned with the
**
weapon_bone
**

joint
. This is because all weapons are modeled in such a way that allows them to be attached automatically to the weapon_bone - this alleviates extra work. The character with the rifle should look like the character in the screen shot below.

![Image](https://www.cryengine.com/docs/static/attachments/28900315)

However, not all attached objects are perfectly aligned with the joint, as we shall see in the next example.

In this case create a new attachment socket of type joint, name it "sniperscope" and choose the joint
**
Bip01 L Thigh
**
. This creates a socket at the left hip of the character.

Next, go to geometry and click on the
**
Folder
**
 button
 and select "objects/weapons/attachments/sniper/sniper_scope_a_tp.cgf" to assign a CGF to the socket. The socket just created is now aligned with the joint
**
Bip01 L Thigh
**
 rendering the sniper scope inside the left leg of the character (picture on the left of screen shots below).

Changing the location of
**
Bip01 L Thigh
**
 is not possible, because it is part of the main hierarchy and adding a new joint takes too much time, however we can move the socket away from the leg. First, click on the
**
Move
**
 button:

![Image](https://www.cryengine.com/docs/static/attachments/28900314)

Then drag the gizmo to move it slightly to the right. However, the scope has a horizontal orientation, so click on the
**
Rotate
**
 button and rotate the scope about the z and y axes to obtain the correct orientation. After the adjustment the sniper scope should be attached to the character:

**
**
![Image](https://www.cryengine.com/docs/static/attachments/28900313)
**
**

Moving and rotating attachments can also be done by using the Transform options in the
**
Properties
**
 of the attachment:

![Image](https://www.cryengine.com/docs/static/attachments/28900312)

Joint attachments are stored relative to a joint and move with that joint when the skeleton is animated. There are actually two ways to store this relative location in the CDF file: you can store it
**
Relative to Joint
**
 or
**
Relative to Character
**
. It's also possible to store rotation and position in different spaces.

**
**
**
*
**
**
*
![Image](https://www.cryengine.com/docs/static/attachments/28900311)
*
**
**
*
**
**
**

Both storage modes are identical at run-time because we convert them into the same space at loading time. However, using
**
Relative to joint
**
 has the advantage that if the skeleton proportions should change during development, then the attachment will still keep the same relative location. If you want to align the socket perfectly with the joint, then you need to choose
**
Relative to joint
**
 and set all values in the position and rotation fields to 0.

**
Face Attachments:
**
Go to the property panel for CDF’s, click on Attachments and select
**
Insert
**
. This creates a new empty socket (without a name) at the origin of the character. Enter an arbitrary name, for example "facesocket" and set the type to
**
Face Attachment
**
. This will create a new socket at (0,0,0) in character space. Do note that unlike joint attachments, face attachments are not linked to a joint with a unique name, rather they are connected to the closest triangle on the mesh and that this triangle may change if the mesh changes.

Using the move and rotate tool allows the socket to be moved to the desired location on the mesh - it is recommended to put the character in
**
Bind Pose
**
 during this process. To activate the
**
Bind Pose
**
 function, check
**
Bind Pose
**
 in the Scene Parameter panel:

![Image](https://www.cryengine.com/docs/static/attachments/28900310)

When you move the socket with the gizmo in character space it will connect automatically to the closest triangle it can find on the mesh. With
**
ca_DrawAttachmentProjection=1
**
 the closest triangle on the mesh is highlighted with a white wire-frame - you can also see a line-segment from the socket to the center of the triangle.

![Image](https://www.cryengine.com/docs/static/attachments/28900309)

Face attachments are perfect for quick experimental set-ups, because in practice it’s much easier to place an attachment directly on the surface of the mesh. A typical problem with joint attachments are that some need a dedicated "helper joint" in the model and adding these joints takes extra time and can only be done in the tool in which the original skeleton was created. Face attachments however, can be created by everyone in the Character Tool.

Another advantage is that no matter how complex the deformations are, the attachments always follow the movement of the face precisely. Such a behavior is extremely hard to emulate with joint attachments, because a skinned triangle is almost always influenced by several joints (up to 12 joints) and each joint has a small impact on the overall movement.

It is also possible to change a face attachment into a joint attachment (and vice versa). However, converting a skin attachment into a joint or face attachment does not make any practical sense.

##
Other Attachment Properties

##
Geometry

Geometry selection of the assigned object. In the case of joint and face attachments then this file is a *.CGF file. In the case of skin attachments it is a *.SKIN file.

##
Material

By default each attached geometry contains the name of a material file (*.MTL) in the same folder. If such a material file doesn't exist (in that case you will see a red ReplaceMe texture) you can use material selection to assign a material file manually. This also works if you want to overwrite an existing material.
**
Note:
**
 The assigned material has priority over the default material in the geometry.

##
Attachment Flags

-
**
Hidden:
**
Hides the currently selected attachment. This feature can be set by default and saved in the file, but usually it’s a run-time feature.

-
**
Physicalized Rays:
**
Only available for joint and face attachments. If this object has a valid physics proxy, then this check box will enable ray hit detections.

-
**
Physicalized Collisions:
**
Only available for joint and face attachments. If this object has a valid physics proxy, then this check box will enable collision detection within the environment.

-
**
Software Skinning:
**
Only available for skin attachments. If this flag is activated, then the mesh gets skinned on CPU instead of GPU. Software skinning is currently necessary if you also want to use blendshapes, or want to have tangent frames recalculated every frame.

##
Using Sockets for Secondary Animations

The attachment system supports simulated movement of joint and face attachments. This type of animation is always a reaction to previous (primary) motion, hence the reason it is called secondary animation.

It can be used to improve the movement of attached static objects (e.g. sword-sheaths, pockets, weapons etc.)

-
It can be used to simulate parts of the mesh directly (e.g. the simulation of fat and muscles in a human body).

-
It can be used to create complex rope set-ups to simulate hair, tentacles, leather straps, chains, necklaces and all other types of loose hanging parts on a character. Ropes can be complex and more so than was possible with CryPhysics, i.e. they can have branching strings and different physical properties for each link. In a later version of the
 SDK it will be shown how to use this system even for cloth set-ups (i.e. pendula cloth).
For the first test create an attachment socket (as explained in ("Setup of Attachment Sockets"). Name it "spring", then choose the type
**
Joint Attachment
**
 and link it to the joint with the name
**
Bip01 Neck
**
. Then put a CGF into the socket, for exam
ple objects\characters\human\attachments\pumpkin\pumpkin.cgf. The pumpkin.cgf is now in the same position as the character’s head, so click on the
**
Move
**
tool and move the pumpkin 1m in front of the character - this gives better visualization. Then rotate the pumpkin 90-degree’s around the y-axis of the gizmo. In the viewport you should see the following configuration:

**
**
**
*
**
**
*
**
![Image](https://www.cryengine.com/docs/static/attachments/28900308)

**
*
**
**
*
**
**
**

If you play an animation on the character, then you'll see that the "pumpkin.cgf" always keeps the same relative distance and orientation relative to the neck joint. We are now ready to apply dynamic simulations to this socket.

Simulated motions in games are usually just a crude approximation of real word physics. In our case the properties of
**
Springs
**
and
**
Pendula
**
 are used to approximate the physical movement of objects attached to characters. To activate the simulation on a socket open the list under
**
Simulation
**
 and select from
**
Pendulum_Cone
**
,
**
Pendulum_Hinge,
**
**
Pendulum_HalfCone,
**
or
**
Spring_Ellipsoid
**
:

**
**
**
*
**
**
*
**
![Image](https://www.cryengine.com/docs/static/attachments/28900307)
**
*
**
**
*
**
**
**

The first three entries with the prefix "Pendulum" activate a pendulum simulation. The suffixes "Cone", "HingePlane" and "HalfCone" are different camp-types to constrain the motion of the pendulum. The entry
**
Spring_Ellipsoid
**
 activates a spring simulation that is constrained by the shape of an ellipsoid. The last entry
**
Translational_Projection
**
 actually has as little to do with simulations and is more related to collision response. Each of the options are discussed below.

##
Setup of a Spring Simulator

In our case a spring is defined as a particle with mass connected to an elastic rope. The concept is pretty similar to a bungee rope. After selecting
**
Spring_Ellipsoid
**
 the pumpkin will fall 0.5meter downwards. The panel shows all the options available to set-up the physics for a spring in a socket.

**
**
**
*
**
**
*
**
![Image](https://www.cryengine.com/docs/static/attachments/28900306)
**
*
**
**
*
**
**
**

##
Debug Setup

If you activate this check box it shows a green spherical shape subdivided by a disk through its middle. This is the bounding volume for the simulated particle and by default has the shape of a sphere. The pivot of the pumpkin is at the bottom of the sphere and if an animation is played on the character you will see that the simulated particle (that's only the pivot of the pumpkin) can only move inside the bounding volume. In our case the simulated particle is represented by a blue sphere - but actually the particle has no radius at all.

The status of this check box is not saved in the CDF.
**
**
**
*
**
**
*
**
![Image](https://www.cryengine.com/docs/static/attachments/28900305)
**
*
**
**
*
**
**
**

##
Debug Text

This check box activates more debug information, for example the update time and the number of timestep subdivisions. If you redirect the simulation to a joint (this feature will be covered later) it will also show all the children of that joint which are affected by the simulation.

##
Activate Simulation

This check box activates the simulation for springs and pendula, by default it is always activated. If deactivated, then it shows the attached object in the default pose.

The status of this check box is not saved in the CDF.

##
Simulation FPS

This slider determines the framerate at which to update the physical simulation - values set on the slider can be higher than the framerate of the renderer.

This is only the lower limit for the physical update and values between 10-255 can be chosen.
If you choose a default value of 10 and the render framerate is higher, then there will be at least one physical update per render frame. Frames are never skipped.

If you choose a value that is higher than the framerate, then the physics system will subdivide the timestep automatically and execute several simulation steps in-between render frames. Obviously a higher Simulation FPS will take more CPU time, so use this value with caution. Simulations with high spring values also require a higher simulation update rate to guarantee a precise and stable simulation.

**
Physical Parameters of a Spring:
**
 there are four characteristics used to control the physical parameters:
**
mass, gravity ,damping
**
stiffness. There is always a counter balance between mass, gravity and stiffness, hence, if the stiffness is too low then gravity will pull the object down. Equally, if the stiffness is increased then the object will gravitate toward the stiffness target. The spring simulation creates a new translation every frame, which moves the attached object relative to the attachment socket. Note: Spring simulations have no impact on the orientation of the attached object.

-
**
Mass:
**
Defines the mass of the particle connected to the spring. As long as stiffness is 0 or very low, the mass will simply pull the particle down until it touches the boundaries of the ellipsoid.

-
**
Gravity:
**
The default value of
**
9.81m/sec
**
 is the standard acceleration rate of falling objects due to gravity acting on the Earth. In a vacuum (Damping=0) a free falling object increases its velocity by 9.81m/sec for each second of its descent and so all objects (no matter what their mass) when dropped from the same height will hit the ground at the same time.

-
**
Damping:
**
 This value can be used to simulate
**
velocity dependent forces
**
, for example air resistance. The faster an object moves the more air friction it encounters. This means the friction force decelerates the object at a rate proportional to the velocity. In the case of higher damping values, then this will make oscillating objects come to rest faster. With Damping=0 the oscillation of the spring will go on forever.

-
**
Stiffness:
**
 This value can be used to simulate
**
position dependent forces
**
, which are typical for springs. The more you stretch a spring, then the harder it tries to return to its relaxed position. This parameter can also be called spring tension and is a value between 0-999. A value of 0 has no stiffness at all and the object connected to the spring will hang downward when it comes to rest. The higher the value, then the faster the particle vibrates and gravitates towards the
**
Spring Target
**
. It is important to mention that stiffness is a counter force to gravity & mass and where a higher mass will always pull the object downwards. Very high stiffness values usually cause multiple oscillations in a single timestep.

To avoid instabilities it may be necessary to increase the Simulation FPS.

-
**
Spring Target:
**
The parameters
**
spring target
**
 and
**
stiffness
**
 are closely related. This is an x,y,z position relative to the socket. By default it’s (0,0,0) and is directly aligned with the socket. If stiffness is 0, then the spring target will have no effect. However, with any other value, then the object is attracted by the spring target which can be outside of the bounding volume. Also, the spring target is a counter force to gravity & mass and while gravity always drags the object downwards to the center of the earth the spring target can attract the object to any other location.
You can find different test setups for spring simulators in the files
**
spring_simulation_02.cdf-spring_simulation_05.cdf
**
.

**
Defining the Bounding Volume:
**
As long as the motion of the particle is unconstrained (which means the motion depends only on mass, gravity, stiffness and damping) then it can theoretically oscillate in any direction and even move far away from the origin (=socket). However, this can create some undesired effects so to constrain the motion of the particle a special bounding volume is used which can also be modified using 3 parameters.
**
Note:
**
 Debug Set-up must be activated to see the change of shape.

**
Disk Radius:
**
The
**

**
radius slider can be used to alter the radius of the disk in the middle of the bounding volume.

-
**
Sphere Scale:
**
There are two different sliders that allow to independently scale both half-spheres of the bounding volume. These scale values are relative to the radius of the disk meaning that it can be deformed into an
**
ellipsoid
**
, an
**
egg
**
 or a
**
half
**
-
**
sphere
**
 with one side completely flat. It's also possible to create a
**
disk
**
 if both sides are scaled to zero or to create a
**
line segment
**
 if the radius of the disk is reduced and an extreme scale is added to both half-spheres.

-
**
Disk Rotation:
**
 with these two sliders yaw & pitch rotations can be undertaken relative to the coordinate frame of the socket. The first slider rotates around the x-axis and the second around the z-axis of the socket.
**
Note:
**
 The disk rotation tool can rotate the bounding volume

independently from the socket, while the rotate tool rotates 3 things at the same time; the socket, geometry and the bounding volume.
Here are some examples for different shapes that you can create with a single bounding volume:

![Image](https://www.cryengine.com/docs/static/attachments/28900325)

*
In clockwise order: egg, flat disc in 3D-space,
*
ellipsoid
*
, line-segment (ellipsoid with very small disk radius and scaled sides).
*

##
Pivot Offset

The Pivot Offset allows you to offset the location of the attached render object, in effect this is just a visual feature and has no impact on the simulation itself and only adds an offset to the attached object at the rendering stage. By default it is the pivot of the model (offset=0,0,0) and those three values are an x,y,z offset that translates the rendered geometry in the direction of the socket axes. For example, an offset of (0,0,1) would displace the geometry 1m in the direction of the z-axis and changing the offset doesn’t change the position of the socket, it only renders the attached geometry at another location which can also be outside of the bounding volume.

If
**
Redirect to Joint
**
 is enabled, then the pivot offset will change the location of the joint and all its children. This is discussed in the example below.

##
Redirect to Joint

If you activate this check box, then the relative motion of the simulate particle is transferred to the joint that its attached to. In other words, we simply add the distance between and particle and the joint. In the case of a spring simulation, then we only change the translation of the joint, which will move all vertices that are part of the skinned mesh and weighted to the joint.

Previous SDK Versions!
*
In previous SDK versions there was a rule that the attachment-name had to be identical with the joint-name, this made it impossible to have more than 1 simulated attachment per joint. The advantage of the
**
Redirect to Joint
**
 check box is that you can attach several simulated sockets to the same joint and execute them one after another in order to create more complex procedural effects.
*

Here are some simple examples:

**
Spring_Simulation_06.cdf:
**
Select the spring attachment and click the
**
Redirect to Joint
**
 check box to see what happens to the head. Instead of the pumpkin the head is now bouncing around in the range of the bounding volume. In this case the location of the socket doesn’t really matter for the neck translation, because we only apply the relative distance from the socket to the simulated spring to the neck joint (although the simulation still takes place at the socket location).

![Image](https://www.cryengine.com/docs/static/attachments/28900304)

**
Spring_Simulation_07.cdf:
**
 If you change the
**
Pivot Offset
**
 while
**
Redirect to Joint
**
 is enabled, then it will apply the offset to the position of the joint that it is attached to. In the screen shot below the z-offset has been changed and a translation of the neck along the z-axis of the gizmo created.

**
Note:
**
 Applying this offset does NOT change the position of the socket, the bounding volume or the gizmo. However, it does have an impact on all other succeeding joints and sockets which are children of the joint that has been translated.

**
**
**
*
**
**
*
**
![Image](https://www.cryengine.com/docs/static/attachments/28900303)
**
*
**
**
*
**
**
**

##
Setup of a Pendulum Simulator

The set-up of a pendulum simulator is similar to that of a spring simulator; however there are differences and the physical properties of a pendulum are also a little harder to understand.

Load
**
pendulum_simulation_00.cdf
**
, this has a joint socket at the left leg and a face socket at the right leg. In both sockets
**
sniper scope.cgf
**
 is attached.

To activate the simulation on a socket, click on the socket-name
**
Pendulum
**
 and next to  select
**
Pendulum_Cone.
**
This will activate the full panel showing all the physical properties of a pendulum. If you click on
**
Debug Setup
**
 you should see the following picture (screen shot below).

![Image](https://www.cryengine.com/docs/static/attachments/28900279)

![Image](https://www.cryengine.com/docs/static/attachments/28900302)

![Image](https://www.cryengine.com/docs/static/attachments/28900291)

![Image](https://www.cryengine.com/docs/static/attachments/28900290)

![Image](https://www.cryengine.com/docs/static/attachments/28900281)

![Image](https://www.cryengine.com/docs/static/attachments/28900280)

That's all you need to do to get a physicalized socket with a pendulum simulator for the scope, which is loosely connected to the right leg and can dangle around. If you play an animation, then you can see that it actually reacts to movement.

##
Physical Parameters of a Pendulum

A pendulum is a
**
bob
**
 (with mass) connected to a
**
fixed rod
**
 which is connected with a
**
spherical joint
**
 to the attachment socket. In an unconstrained state it will swing back and forth in any direction until air resistance or another force slows it down. The motion depends on physical parameters such as; mass, gravity, damping and stiffness. The swinging of the pendulum creates a
**
new orientation
**
 for every frame, which is used to change the orientation of the attachment object.

-
**
Simulation Axis:
**
This is a vector i.e. a direction and a length and this defines the default rod of the pendulum. It is also a segment between the socket and the bob and is the center of the cone which doesn't move. The direction of the simulation axis is relative to the orientation of the socket and has a default value of (0,0.5,0), meaning it points in the direction of the y-axis. This length (of the rod) has a large impact on the amplitude of the pendulum, the longer the rod, then the longer it will take for the pendulum to oscillate back and forth. The length of the rod is a hard constraint, which ensures that the bob always keeps a fixed distance to the socket

-
**
Mass:
**
Defines the mass of the pendulum bob and as long as the
**
joint spring
**
 is 0, then the mass has no impact on the period of oscillation. The driving force for a pendulum is gravity, hence if the pendulum has twice the mass, then gravity pulls twice as hard. The force required to move the mass and the force provided by gravity are both determined by the mass of the object, so they cancel each other out and that is why there is no effect. Hence, in the case of pendula the weight of the bob does not affect how it moves

-
**
Gravity:
**
The default value of
**
9.81m/sec
**
 is the standard acceleration of falling objects due to gravity acting on Earth. While the mass of the bob has no effect on the oscillation of the pendulum the force of gravity does. For example, on the moon where gravity g=9.81/6 not only would the bob weigh less, but it would also swing more slowly

-
**
Damping:
**
 This value can be used to simulate
**
velocity dependent forces
**
, for example air resistance. So the faster an object moves then the more air friction it encounters. This means that the friction force decelerates an object at a rate that is proportional to the velocity, hence higher damping values will make oscillating objects come to rest more quickly. If you use Damping=0, then theoretically the swing of the pendulum will go on forever, however in practice energy dissipation will slow it down sooner or later

-
**
Joint Spring:
**
This value can be used to simulate
**
position dependent forces,
**
and is a value between 0-999 applied to the spherical joint. The further the pendulum swings away from the axis of the
**
spring target
**
, then the harder it tries to return. A value of 0 has no spring effect, so the pendulum will hang downward when it comes to rest. The higher the value, then the faster the bob oscillates and is attracted by the
**
Spring Target
**
, which can point in any direction. It is important to mention that the tension of the spring is a counter force to the mass & gravity and that a higher mass will always pull the bob downwards.

A joint spring with a high value can have multiple oscillations in a single time step, so to avoid instabilities it may be necessary to increase the
**
Simulation FPS
**
.

-
**
Spring Target:
**
The parameters
**
spring target
**
 and
**
joint spring
**
 are closely related. Also, the spring target is an axis relative to the simulation axis and by default is identical to the simulation axis. Additionally, there are two planes of rotation that a user has at their disposal and these permit the spring target axis to rotate about the simulation axis and thus allow any position to be reached both inside and outside of the cone, half-cone or hinge-plane. If the joint spring is 0, then the spring target will have no effect. However, the higher the value used for the joint spring, then the more attraction the rod will get from the spring target. Furthermore, the spring target is a counter force to gravity and while gravity always drags the pendulum rod downwards, the axis of the spring target can attract the pendulum rod in any other direction too. For example, if we turn the pendulum around and increase the joint spring value, then we can create an inverted pendulum
**
Defining the Bounding Volume:
**
As long as the motion of the pendulum is unconstrained (which means the motion depends only on mass, gravity, joint spring and damping), then it can oscillate in any direction and even accomplish 360 rotations about the origin (=socket). So to constrain the motion of the rod of the pendulum we use three types of bounding volume. If you activate the check box
**
Debug Setup
**
it shows a cone, a half-cone or a hinge-plane. These are the three bounding volumes for the pendulum and the pendulum can only swing inside the boundaries of these geometrical shapes. In other words the motion is clamped or constrained to the shape of the bounding volume.

-
**
Cone Angle:
**
This slider allows you to choose the opening angle for the cone, half-cone or hinge-plane and by default is set at 45-degrees. A range of angles is available (0-179) and where values larger than 90-degrees create an inverse cone.

If the angle selected is 179, then the rod can rotate in all directions.

-
**
Hinge Rotation:
**
Rotates the hinge-plane and the half-cone around the rod of the pendulum. This only rotates the clamp type and not the socket itself or the attached object.

Rotating a cone doesn't affect the simulation.

##
Some Examples of Pendulum Simulations

**
Pendulum_Simulation_01.cdf:
**
 This CDF shows a loose hanging scope which is only constrained by a cone with an angle of 45-degrees. The main issue with this set-up is that the scope sometimes clips the characters right leg.

**
![Image](https://www.cryengine.com/docs/static/attachments/28900301)
**

**
Pendulum_ Simulation_02.cdf:
**
 One way to avoid the clipping with the characters leg is to use a
**
hinge
**
-
**
plane
**
 instead of a cone. In this case the scope can only slide on the plane and clipping with the characters leg is impossible. However, the disadvantage of this option is that the scope now appears to be over constrained, because it can only move in one direction.

**
**
![Image](https://www.cryengine.com/docs/static/attachments/28900300)
**
**

**
**
Pendulum_Simulation_03.cdf:
**

**
A better method is to use a half-cone, where one side is completely flat. If the flat side is oriented towards the body, then the scope cannot intersect with the characters leg. This is a simple and efficient solution to attach loose hanging objects to a body and where you don't want to use "more expensive" collisions.

![Image](https://www.cryengine.com/docs/static/attachments/28900299)

**
Pendulum_Simulation_04.cdf:
**
 A better (and more realistic looking) solution is to use real collisions. In this case we can approximate the scope and the right upper leg with a capsule, and in many cases this creates a much more realistic look than can be obtained with the hinge-plane or a half-cone. In the screen shot below the motion is firstly constrained by the capsule on the upper leg and then by the pendulum cone. We will explain the set-up of collision proxies later.

![Image](https://www.cryengine.com/docs/static/attachments/28900293)

##
Redirect to Joint

If you activate this check box, then the simulated motion is transferred to the joint that it is attached to, which means that the relative motion of the pendulum is added to the joint. So as long as the pivot offset is (0,0,0) then we only modify the orientation of the joint and this moves all vertices which are part of the skinned mesh and weighted to this joint. Here are some simple examples;

**
Pendulum_ZombieArm1.cdf
**
: In this example we have created an injured or partially paralyzed right arm. Three pendula set-ups have been used for the joints of the arm; a half-cone to limit the motion of the shoulder, a hinge plane at the elbow to limit the motion of the lower arm and a cone at the hand. Because the value for the
**
joint spring
**
 on all three pendula is very low, the simulation completely overwrites the mocap animation for the arm (which is still active). The arm is now hanging totally lifeless from the shoulder; however increasing the value for the
**
joint spring
**
 will partially reactivate the original arm animation.

![Image](https://www.cryengine.com/docs/static/attachments/28900298)

**
Pendulum_ZombieArm2.cdf:
**
In this example both arms are paralyzed and lifeless and an "inverted pendulum" has been applied to the spine joint to make the whole upper body react to the motion. This kind of set-up will make any animation look like a Zombie motion.

![Image](https://www.cryengine.com/docs/static/attachments/28900297)

##
Pivot Offset

This feature is identical for both pendula and springs. The purpose is to offset the attached object or the redirected joint and all its children. In
**
pendulum_ScareCrow.cdf
**
 this feature was used to move both shoulder joints 30cm away from the body. The gizmo, the socket and the pendulum half-cone remain at the original location and only the joint gets a translation.

![Image](https://www.cryengine.com/docs/static/attachments/28900296)

##
Simulating a Chain of Linked Joints

A chain of pendula can be created by attaching a pendulum at each link, this in turn enables us to create interesting effects by linking the simulated joints. Hence, when we activate the simulation each parent joint will then transfer its motion to the children. In such a case the primary motion is not coming from the animation, but from a previous simulation.

In the previous section we created a similar example with the "Zombie Arms" and in the following we will show how to use the same concept to simulate hair and leather straps using collision detection and response.

##
Simulating Hair

In
**
ChainOfJoints1 (braids).cdf
**
 we have a model with three braids linked to a skull. The two front braids have 4 joints, the back braid 5 joints and where the range of motion for each link on a braid is limited by a cone. The obvious problem with this set-up is that the braids go straight through the body when playing certain motions - this is particularly obvious for the front braids. We will show you later how to avoid this with proper use of collision detection.

![Image](https://www.cryengine.com/docs/static/attachments/28900295)

##
Simulating Leather Straps

In
**
 ChainOfJoints2 (leather straps).cdf
**
 we have a belt with 10 leather straps, where each leather strap has 3 joints and the range of motion for each link on a strap is limited by a hinge-plane. The obvious problem with this set-up is that the leather straps at the front clip through the character’s legs when playing an animation. Notice that this issue only occurs to the front straps, for the rear straps it was possible to prevent such clipping with the set-up of the hinge-plane.

![Image](https://www.cryengine.com/docs/static/attachments/28900294)

That kind of rope set-up is called a "pseudo rope" or "pendula rope", but such a set-up does not behave like a real rope; the parent joints can only transfer the motion to the child joints, but the child joints have no impact on the motion of the parent (with real ropes the moment transfer travels in both directions). Overall this is a simple and fast method to add a simulation to linked joints and with the right combination of parameters it can be visually very close to the behavior of real ropes. We can also mix springs into the same chain and define the constraints for each link individually. The major problem with this set-up is that the braids and the leather straps always clip through the body. Finding a solution for this is the topic of the next section.

##
Using Collision Detection and Response

The attachment system supports a simple system to handle collisions of simulated objects with the body of a character. The first step is to correctly set-up the collision proxies on the body. A "collision proxy" is an object that is used to approximate parts of a human body such as; the legs and torso with a simple geometry shape. Using a proxy like this is more efficient than undertaking all the necessary computation required for collision detection and response with the polygonal mesh.

The geometric object in our case is called a
**
lozenge
**
which is represented by 4 numbers. Using these 4 numbers we can create points, spheres, capsules, line-segments, rectangles, boxes, 2D-lozenges and 3D-lozenges. That’s 8 different shapes (and everything in-between) that are all managed by the same algorithm and internally represented by just 4 numbers.

![Image](https://www.cryengine.com/docs/static/attachments/28900352)

To deal with collision detection and response on living characters we use 2 types of proxies which are displayed using 2 colors:

-
The
**
pink proxies
**
 (=lozenges) are linked to the joints, move with the skeleton and represent an approximation of the body shape. The pink proxies are normal attachments the only exception being that the attached object can only be a lozenge.

-
The
**
blue proxies
**
 (=capsules/spheres) are a property of a simulated socket and handle the collision detection and response with the pink proxies. The blue proxies are the dynamic collision proxies, which means that the pink proxies always push the blue proxies away.
**
Note:
**
 It will never happen the other way around.
The set-up of both proxy types is interactive. You can tweak the size, shape and all the physical parameters while the animation is running and see the effect immediately on screen.

##
Setup of Lozenges

Go to
**
Display Options -> Secondary Animation
**
 and enable
**
Dynamic Proxies
**
 (the blue ones) and
**
Auxiliary Proxies
**
 (the pink ones):

![Image](https://www.cryengine.com/docs/static/attachments/28900292)

To set-up the pink proxies (=lozenges) on a character just create a new socket, give it a name and set the type to
**
proxy attachment
**
. This enables a new panel where you can choose the purpose of the proxy (at the moment only
**
Auxiliary
**
 is supported) and four sliders to define the shape of the lozenge. The screen shots below show the set-up of a capsule (that's a 1D Lozenge at the right leg).

A lozenge is defined by a radius and 3 scaling values for the axes. The axes will scale in both directions of the coordinate system so a value of (0,1,1,1) will create a box of 2*2*2 meters. The radius can be added on top of the box. The XML file
**
ChainOfJoints3 (grey proxy).cdf
**
 is an example of how to set-up lozenges for arms, legs and the upper-body.
**
Note:
**
 Collision detection is not activated in this file.

##
Enabling Collision Detection

Collision detection is a simple overlap test between a lozenge and either a capsule or a sphere.

To enable collision detection for a pendulum the blue proxies must first be set-up. However, because the blue proxies are entangled with the different types of simulation, then the set-up is part of the simulation panel. Here is an example for the set-up of
**
hairstrand01_chain01
**
:

-
A socket with a simulated pendulum can have a
**
capsule
**
 for collision detection. One end of the capsule is always connected to the attachment socket (pivot), meaning you can only change the
**
length
**
 along the rod-axis and the
**
radius
**

-
Next choose a
**
Projection Type
**
, i.e.
**
Shortarc Rotation
**
. We will explain later what that means. This will activate another list called
**
Available Collision Proxies
**

-
The list under
**
Available Collision Proxies
**
 shows all pink proxies (lozenges) which are currently available for this model.
**
Note:
**
 Collisions between blue and pink proxies can be enabled and disabled as required. In our case the capsule for
**
hairstrand01_chain01
**
 is located at the back close to the head and can only collide with the proxies at the upper body and the arms (it's very unlikely that it can ever collide with the proxies on the legs). That's why we select only the first 5 proxies (they are all located at the upper body) for collision detection.
**
Note:
**
 Collisions are tested in the order that the proxies appear in the list, and the fewer checks that are needed then the faster the system will run.
![Image](https://www.cryengine.com/docs/static/attachments/28900289)

##
Collision Response

To deal with collision response we use a technique called
**
projection
**
. If a capsule/sphere overlaps with a lozenge, then we simply
**
project it out
**
 of the lozenge. A "projection" means moving the overlapping capsule/sphere as little as is possible and until it no longer overlaps with the lozenge. This either means translating the capsule/sphere perpendicularly out towards the closest collision surface or rotating the capsule out of the lozenge.

When we detect an overlap between a lozenge and a capsule/sphere, then we use one of 4 different methods to project them back to a non-colliding state.
**
Note:
**
 Not all 4 methods are available at the same time and which methods are available depends on the configuration of the simulation.

**
Spring simulation
**

-
**
No Projection:
**
ignore the overlap and do nothing else.

-
**
Shortvec Translation:
**
 translates the sphere out of the lozenge by using the shortest translation possible. In the case of springs only sphere versus lozenge is supported.

**
Pendulum simulation with a cone or a half-cone
**

-
**
No Projection:
**
ignore the overlap and do nothing else.

-
**
Shortarc Rotation:
**
 rotate the capsule out of the lozenge by using the shortest angle possible.
**

Pendulum simulation with a hinge-plane
**

-
**
No Projection:
**
 ignore the overlap and do nothing else.

-
**
Shortarc Rotation:
**
 rotate the capsule out of the lozenge by using the shortest direction that is possible. In the case of a hinge-plane there are only 2 ways to rotate out of a lozenge, hence the system will always choose the shortest way available.

-
**
Directed Rotation:
**
 rotate the capsule out of the lozenge using the direction of the hinge-plane. A "directed rotation" means that there is only one way available to rotate out of a lozenge - rotation is always towards the "green" direction of the hinge-plane.
In the case of a pendulum, a shortarc or directed rotation, rotation is only possible if the pivot of the capsule is outside of the lozenge. The "pivot" is the spherical part of the capsule which is connected to the socket. If this part of the capsule is inside the lozenge, then the following warning will appear on the screen.

On-screen Warning
"Capsule for 'hairstrand01_chain01' starts inside of proxy: 'spine3' (dist: 0.004)"

Whenever the above message appears, then a collision could NOT be resolved and the capsule and lozenge will remain in the overlapping state.
**
Note:
**
 The capsule responsible for the warning will be rendered in red to show immediately where the issue has occurred.

This issue might only occur when playing certain animations that move the joints in an unnatural way. However, for some set-ups it may occur all of the time, for example with the front straps when playing a normal walk animation. You can see this effect in
**
ChainOfJoints4 (collisions).cdf
**
. This of course means that we must find strategies to avoid such invalid states.

![Image](https://www.cryengine.com/docs/static/attachments/28900288)

##
Translational Projections

We have just mentioned that it is absolutely critical that the pivot of the capsule must be outside of the lozenge in order for the shortarc or directed rotation to work - however in many situations this will not be the case. For example, a typical problem occurs with secondary animations on characters where the
**
simulation
**
-
**
update
**
 is triggered after the
**
animation
**
-
**
update
**
 and it happens that the animation itself moves the proxies into each other or creates invalid proxy configurations which break the simulation. The obvious solution in this case is to check if the root of the rope is inside one of the pink proxies - if it is, then to move it out of the pink proxy in question.

Firstly, create a new socket and at the same joint where you want to perform the translation. However, it is crucial that the new socket is on the
**
same joint
**
 and appears in the list of attachments
**
ahead of
**
 the pendulum attachment that you want to move out (it is possible to change the order of attachments in the Character Tool directly). This order defines the order of execution, so the translation operation moves the joint out of the proxies before the pendulum attachment is executed.

In the
**
Simulation
**
 field select
**
Translational Projection
**
. This is a special type that is always aligned with the joints that it is attached too. It is also not possible to move or rotate them with the gizmo because it can only operate on joints and it is automatically redirected to the joint that it is attached to.

![Image](https://www.cryengine.com/docs/static/attachments/28900287)

This opens a new panel which allows you to choose two methods for translational projections.

**
Shortvec
**
**
 Translation:
**
For this type of translation you can only specify the radius of a sphere around the joint. If an overlap is detected, we translate the sphere out of the lozenge along the
**
shortest vector
**
 to the surface. This type of translation is the easiest, but it's not without its issues. For example, let’s say you have a set-up with 2 lozenges, then it’s possible that the first shortvec translation moves the capsule out of the first lozenge and directly into the second lozenge. You then test against the second lozenge, which translates the capsule back into the first lozenge. These issues are very likely with complex set-ups, and where many lozenges are close together and even overlap (as in the case of our example torso set-up). It can also happen that it projects out in the wrong direction and produces undesired "tunneling" effects. Therefore, it is recommended to use shortvec translations only for set-ups with just a few lozenges and where the results are predictable.

![Image](https://www.cryengine.com/docs/static/attachments/28900286)

**
Directed
**
**
 Translation:
**
The result of a directed translation is easier to predict because we have control over the translation direction.

So, we can either define a translation axis and translate the capsule out of the lozenge in the negative direction of that translation axis (=left picture screen shot below).
**
Note:
**
 The translation axis is relative to the joint and socket orientation.  Or we can choose a joint, which forms a translation axis between the location of the joint and the socket (=right picture screen shot below).

Both cases allow you to specify a capsule in the direction of the translation axis, however the capsule will always be projected out in the predefined direction, even if the capsule is 'behind' the lozenge which makes "tunneling" very unlikely.

![Image](https://www.cryengine.com/docs/static/attachments/28900285)
 |
![Image](https://www.cryengine.com/docs/static/attachments/28900284)
 |

When using collision proxies, the system performs two consecutive constraint checks. First, it projects the capsule/sphere out of the lozenge, and second it clamps the spring particle or the pendulum rod to the shape of the bounding volume.

After these 2 checks, then we expect the object to be
**
outside
**
 of the lozenge and
**
inside
**
 of the bounding volume. However, this is not always possible, and the bounding volume has the last word. This is because if it is too small, then it might happen that the collision system resolves the collision successfully, but the bounding volume pushes the capsule/sphere back into the lozenge. In other words, a small bounding volume can lock a capsule/sphere inside a lozenge.

The easiest way to become familiar with these features is to load the example CDF’s and to experiment 'play around' with the settings.

In
**
ChainOfJoints5 (projections).cdf
**
 you can find an example set-up with proper collision detection and response for 3 braids and 5 leather straps.

In
**
ChainOfJoints6 (projections).cdf
**
 there is a more complex example with 28 physicalized braids. The set-up in both files is similar.

**
Note:
**
 Only “translational projection” has been sued for the root of the braids and leather straps. The length of each capsule is a little longer then the joint and overlaps by 25% with the child capsule. It’s important to mention that the radius of each child capsule is around 0.002 (=2mm) smaller. With this simple trick we can be sure that if the parent capsule gets properly projected out of the lozenge, then the pivot of the child capsule will be outside as well.

##
Simulating a Grid of Linked Joints

Experimental Feature!
This is an experimental and "work in progress" feature. It may be completely changed in future releases of CRYENGINE.

We are very interested to hear feedback and suggestions. Any comments and suggestions please post on our forums
.

In previous sections we explained how to set-up a "chain of linked joints" to simulate effects such as hair and leather straps, this was called a "pendula rope". In this section the concept is extended to a "grid of linked joints
*
"
*
 and is used to simulate cloth - this set-up is called "pendula cloth". This is an experimental method that uses a special set-up of pendula for cloth simulation.

The main advantage of this method is the controllability and the stability of the simulation. In games, characters often need to perform many different physical movements, such as 180-degree flips, instant pose changes and teleporting from one position to another. These movements are important for responsive game play, but are very likely to interfere with the simulation.
With pendula cloth it is possible to use special constraints in simulations to avoid typical problems such as
**
particle tunneling
**
 (when cloth particles end up on the wrong side of the body) and
**
particle explosions
**
 (when the particles get into an unstable state due to an impulse and cannot recover). Furthermore, pendula cloth removes all the stretching along the vertical axes, gives precise control for cloth bending and eliminates the need to solve a network of constrains.

##
Basic Setup

Pendula cloth operates on joints and this particular joint configuration needs to be arranged in a grid and with special naming convention. The screen shot below shows this type of set-up being used for a cape with 13*11=143 pendula. Each pendulum is connected to a joint and where the vertical pendula strains are identical to the joint chains used for hair. In the case of joint grids each pendulum is also horizontally connected to its neighbor (this is shown by a red line) and this ensures that the ropes do not move too far away from each other or too close together.

![Image](https://www.cryengine.com/docs/static/attachments/28900283)

There are two requirements for the set-up of the joints.

The first requirement is that each joint needs to have a tag at the beginning of its name (i.e. "cape_*", "skirt_*" or "coat_*"), and an x-counter for the horizontal position and a y-counter for the y-position. The joint-name for the top/left joint in this example is "cape_x00_y01".

The second requirement is that the x-axis of each parent joint points in the direction of the child-joint. In CharTool there is an automatic check for this. Hence, if an x-axis does not point precisely in the direction of the child joint, then a warning appears on screen, for example "Joint 'cape_x12_y04' not aligned with x-axis". There is also a red and a green line rendered at the default location of the joint which shows how large the misalignment is.

On-Screen Warning!
It is not possible to disable the misalignment warning - the warning will only be cleared/removed once the user remedies the joint set-up issue.

**
Attaching Cloth Pieces:
**
 Re-load one of the first CDF’s that was created earlier, for example
**
attachment_01 (skin).cdf
**
 and add a new socket for a skin attachment. Do this by double-clicking on it in the tree on the left. In the property panel click on the button next to Attachments and select
**
Insert
**
, this creates a new empty socket. Enter an arbitrary name, for example "cape" and set the type to
**
skin attachment
**
.

Next, go to geometry and click on the
**
Folder
**
 button and select "objects/characters/human/sdk_attachment_tutorial/ romanarmor/cape.skin". This skin file will also extend the skeleton. Because the cape looks a little disconnected from the body create another skin attachment and select the file "objects/characters/human/sdk_attachment_tutorial/romanarmor/shoulderplates.skin".

This set-up can be found in
**
GridOfJoints_01_(cape).cdf
**
. The character with the cape and the shoulder plates should look like the character in the screen shot below. The cape is completely rigid; this is because there is no simulation on it.

**
![Image](https://www.cryengine.com/docs/static/attachments/28900282)
**

**
Activating the Simulation:
**
 Load the CDF named
**
GridOfJoints_01_(cape).cdf
**
. Do this by double clicking on it in the tree on the left. Next, in the property panel click on the button next to
**
Attachments
**
 and select
**
Insert
**
, this creates a new empty socket (without a name). Enter an arbitrary name, for example "caperow_01".

For this socket we will set the type to
**
PRow Attachment
**
. The name "PRow" stands for "pendula row". This is a new attachment type that only stores the simulation parameters for an entire row of pendula. Once you have selected the type "PRrow Attachment" a new panel will open (left screen shot below). This panel has many similarities to the panel used to set-up the physical properties of a pendulum - the only difference is that each pendulum in a row uses the same parameters.

The final step (before we can start tweaking the cloth parameters) is to select the pendula for a row. Go to
**
Row JointName
**
 and click on the
**
Joint
**
symbol. This opens a window showing all the joints in the hierarchy. Choose the first joint in the first row of the cape; this is named "cape_x00_y01". Part of the name is the counter "x00". The system will then automatically look for "cape_x00_y01", "cape_x01_y01", "cape_x02_y01", "cape_x12_y01". This process will add all matching joint names to the row of pendula.

Finally, change the
**
Clamp Mode
**
 to
**
Pendulum Cone
**
. If the
**
Debug Setup
**
 is now activated it will show all 13 cones on one row.

##
Physical Parameters of a Pendula Row

As mentioned before, a
**
PRow Attachment
**
 is a row of pendula, which means that (with a few exceptions) the physical parameters are similar to a pendulum. If we change one value in the panel, then it will apply that value to all pendula in the row.

![Image](https://www.cryengine.com/docs/static/attachments/28900278)

-
**
Simulation FPS:
**
 This slider determines the framerate at which to update the physical simulation, values between 10-255 can be selected. In the case of pendula cloth, the value chosen is actually the real physical update per second. Furthermore, with a fixed simulation framerate then the simulation will be more deterministic. If the default value of 10 is selected, then there will not be any more than 10 physics updates per render frame. If the difference between the render and simulation framerates is large, then the simulation fps may demonstrate some stuttering - this stuttering can be visually very unpleasant. Therefore, it is recommended to set the simulation framerate to something between 30 and 60 fps. If the game is using a fixed framerate, then the physics should ideally use the same framerate.

-
**
Mass:
**
Defines the mass of the pendulum bob and as long as the
**
joint spring
**
 is 0, then the mass has no impact on the period of oscillation.

-
**
Gravity:
**
The default value of
**
9.81m/sec
**
 is the standard acceleration of falling objects due to gravity acting on the Earth. While the mass of the bob has no effect on the oscillation of the pendulum the force of gravity does.

-
**
Damping:
**
 This value can be used to simulate
**
velocity dependent forces
**
, for example air resistance. So, the faster an object moves then the more air friction it encounters. This means that the friction force decelerates an object at a rate that is proportional to the velocity, hence higher damping values will make oscillating objects come to rest more quickly.

-
**
Joint Spring:
**
This value can be used to simulate
**
position dependent forces
**
, and is a value between 0-999 applied to the spherical joint. The further the pendulum swings away from the axis of the
**
spring target
**
, then the harder it tries to return. A value of 0 has no spring effect, so the pendulum will hang downward when it comes to rest. The higher the value, then the faster the bob oscillates and is attracted by the
**
Spring Target
**
, which can point in any direction. It is important to mention that the tension of the spring is a counter force to the mass & gravity and that a higher mass will always pull the bob downwards.

-
**
Cone Angle:
**
The movement of the pendula can be constrained by three bounding volumes: cone, half-cone and hinge-plane. This slider allows you to choose the opening angle for the cone, half-cone or hinge-plane and by default is set at 45-degrees. A range of angles are available (0-179) and where values larger than 90-degrees create an inverse cone.

-
**
Cone Rotation:
**
 Enables rotation of the cone, half-cone and the hinge-plane relative to the joint.

-
**
Rod Length:
**
 Defines the length of the rod. The length of the rod has a large impact on the swinging frequency of the pendulum, so the longer the rod then the longer it will take for the pendulum to oscillate back and forth.

-
**
Spring Target:
**
The parameters
**
spring target
**
 and
**
joint spring
**
 are closely related, and where the spring target is an axis relative to the x-axis of the joint. Furthermore, there are two planes of rotation that a user has at their disposal and these permit the spring target axis to rotate about the simulation axis – in this way any position can be reached both inside and outside of the cone, half-cone or hinge-plane.

-
**
Turbulence:
**
This is a modulation of the dampening value and is based on the movement speed of the character. The first value controls the frequency, the second the amplitude and by using the turbulence feature subtle noise can be added to the simulation to simulate elements such as the effect of the wind on cloth.

-
**
Max Velocity:
**
 The bob of the pendulum can reach very high velocities, especially when the character is undertaking sudden pose changes or is teleported from one position to another. Clamping the velocity prevents large impulses which can bring the simulation into an uncontrolled state.
**
Horizontal Constraint Solving
**

Constraints are restrictions and rules that can be added to the simulation to control/guide where particles can and cannot go. One of these restrictions is collision detection and this can be used to prevent particles from existing on the inside of a body. Another constraint is to control the distance particles are from one another. In the case of cloth each particle has a vertical and horizontal distance, with pendula cloth then the vertical distance is restricted by the distance between the parent and its child joint. Finally, the horizontal is controlled by the following three parameters:

-
**
Cycle:
**
Pendula cloth operates on a joint set-up that has a rectangular grid structure. In the case of capes and coats the left and right side of the grid are not connected to each other. However, in the case of skirts all pendula need to be connected on the horizontal axis. By activating the
**
Cycle
**
 checkbox the last joint in the row gets connected to the first joint in the row. Hence, the row is actually a circle of pendula.

-
**
Stretch:
**
This value is used to define
**

**
how much the
**

**
cloth can stretch horizontally. A value of 0 (combined with a high value for Relaxation Loops) enforces a fixed horizontal distance between the pendula. A value of 0.2 means the distance can stretch or shrink by 20%. The default horizontal "default distance" is the distance between the joints in the default pose.

-
**
Relaxation Loops:
**
This method uses an iterative approach to keep the pendula together and in a horizontal row. Each iteration brings them closer together and this occurs every frame. For most instances a value of 2-4 is recommend.
**
Collision Detection and Response
**

For collision detection and response between cloth and body we once again use a combination of pink and blue proxies.

-
The
**
pink
 proxies
**
 (=lozenges) are linked to the joints and move with the skeleton and represent an approximation of the body shape.

-
The
**
blue proxies
**
(=capsules/spheres) are directly linked to the joint and handle the collision detection and response with the
pink
 proxies. The
pink
proxies always push the blue proxies away.
![Image](https://www.cryengine.com/docs/static/attachments/28900347)

**
Capsule
**

Collision detection is a simple overlap test between a lozenge and either a capsule or a sphere. To enable collision detection for a pendula row the blue proxies
**

**
must first be set-up.
**

**
Each joint in a pendula row can have a
**
Capsule
**
 for collision detection and one end of the capsule is always connected to the joint (pivot), this means that you can only change the
**
length
**
 along the rod-axis and the radius. Changing these values will change the capsule for the entire row.

**
Projection Type
**

If you choose a
**
Projection Type
**
, it will activate the list for
**
Available Collision Proxies
**
. These proxies are applied for the whole row of capsules. Collision response has been covered in the previous section under
**
Enabling Collision Detection
**
.

[Attachment System in Character Tool](#attachment-system-in-character-tool)
[Creating a Character Definition File (CDF)](#creating-a-character-definition-file-cdf)
[Setup of Attachment Sockets](#setup-of-attachment-sockets)
[Other Attachment Properties](#other-attachment-properties)
[Using Sockets for Secondary Animations](#using-sockets-for-secondary-animations)
[Simulating a Chain of Linked Joints](#simulating-a-chain-of-linked-joints)
[Using Collision Detection and Response](#using-collision-detection-and-response)
[Simulating a Grid of Linked Joints](#simulating-a-grid-of-linked-joints)
