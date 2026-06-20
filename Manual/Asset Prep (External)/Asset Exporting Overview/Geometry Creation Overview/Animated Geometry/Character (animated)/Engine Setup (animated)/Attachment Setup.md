# Attachment Setup

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308007
- Page ID: 23308007
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Character (animated) > Engine Setup (animated) > Attachment Setup
- Parent: Engine Setup (animated)

## Content

Since CRYENGINE 3.8 this document has been superseded by [Attachment System Tutorial - Character Tool](../../../../../../Editor%20Tools/Animation%20Tab/Character%20Tool/Attachment%20System%20Tutorial%20-%20Character%20Tool.md).

### Overview

The character pipeline uses a character attachment system which allows to attach separate static objects to joints or directly to polygonal faces of a mesh and update them together with the animated character.

These are autonomous object that that can be replace or detached at run-time by the game-code and fall to the ground under gravity. It's also possible to use skin-attachments to replace entire body parts such as heads, hands, or upper and lower body.

Download and extract the file **[Attachment_exampleFiles.rar](/docs/static/attachments/23994511)** in your Objects directory. Example: `<root>\GameSDK\Objects\Attachment_exampleFiles\Bone_attachment_simulateSocket`

![Image](https://www.cryengine.com/docs/static/attachments/23994512)

#### Bone attachment

Bone-attachments are attached to a joint. The location can be ‘relative’ to a selected joint or they can be perfectly aligned with the selected joint if you click the checkbox "Align Bone Attachment".

#### Face attachment

Face-attachments are projected on the surface of the mesh (to only one particular triangle) and always stay on the surface of the mesh, even if the skinned mesh is deformed in extreme ways. The location of a face-attachment can be relative to a face. Bone-attachments don’t do that. Since SDK3.5 you can assign face-attachments to all meshes, even if these meshes are part of a skin-attachment.

Face-attachments allow faster prototyping. For bone attachments you need bone in the model and adding these bones is complex, time consuming and only tech-artists with Maya/Max installed can do it. Face attachments are easier to use for fast experimental setups and everyone can do it in CharEdit.

#### Skin attachment

With skin-attachments we can replace body parts (head, hands, legs). Each skin-attachment can have its own character features (morph-targets). A skin-attachment can have NO animation. To animate the skin-attachment and deform its mesh, always use the skeleton-pose of the base-character.

1p vs 3p Attachments
There are several special-case names for attachments which define whether they appear in 1p or 3p. These are listed inside **Player.cpp** under ** SetupPlayerCharacterVisibility**. As an example, the reason the players head doesn't render in 1p is because it's called "head" in the character CDF, and "head" is defined as a * ppThirdPersonPart* in this file.

### Attachment-Sockets and Secondary Animations

#### Part 1: Setup of attachment-sockets

If you want to attach something to a character, the first step is to create an "empty" attachment-socket. A ‘socket’ is an attachment slot without anything in it. Empty sockets can also be used by the game-code to plugin (and process) typical game-objects like CEntityAttachment, CLightAttachment or CEffectAttachment. In such a case we use the attachment-system to actually update game-code. In the attachment window you can create a new attachment-socket, by selecting the type of attachment (Bone, Face or Skin).

- In the attachment window you can create a socket for a bone-attachment, by selecting a joint-name, an arbitrary attachment name and then you click the “apply” button. To align it with the joint orientation, click on "align with bone". Internally the socket for a bone-attachment stores a name, a location relative to the selected joint and the joint-name it is attached to. You can visualize all empty sockets on a model with the console-command ca_DrawEmptyAttachments=1. In the "object-field" you can select the file for a static geometry and plug it into the socket. Click "apply" connect the CGF with the socket. With the move and rotate tool can place the socket relative to the joint.
- In the attachment window you can create a socket for a face-attachment, by selecting an arbitrary attachment name and then you click the “apply” button. Internally the empty socket for a face-attachment stores a name and the location relative to the selected joint. You can visualize all empty sockets on a model with the console-command ca_DrawEmptyAttachments=1. In the "object-field" you can select the file for a static geometry and plug it into the socket. Click "apply" connect the CGF with the socket. Initially the socket for a face attachment is placed at the root of the character. With the move and rotate tool can move it to the desired position and make sure it snaps to the right face.
- In the attachment window you can create a socket for a skin-attachment, by selecting an arbitrary attachment name and then you click the “apply” button. Internally the empty socket for a skin-attachment stores only the name of the attachment. In the "object-field" you can select the file for a.SKIN file and plug it into the socket. Click "apply" connect the SKIN with the socket. A.SKIN-file is an that has a skeleton of its own and it's very important that the names of the skeleton in the skin-attachment are identical with the bone-names in the base-skeleton. A skin-attachment can have (and should) have less bones then the base skeleton. For maximum performance a skin-attachment should have only the bones necessary to deform the body part.

It is also possible to change a face-attachment into a bone-attachment (and vice versa) after it was created. Just select a new type and click the "apply" button. Converting a skin-attachment into a bone or face doesn't make practical sense.

##### Objects-field

Object selection for the socket.

##### Material-field

Material selection of the assigned object. The name of the material assigned to the object is shown here, with a button to browse and attach a different object “…” to the right. Dflt assigns a default material.

##### Clear-button

Deletes the assigned model from the attachment-socket. It doesn’t delete the socket itself.

##### Apply

Assign model to animation-socket (CGF or SKIN).

##### Hide attachment check-box

Hides the currently selected attachment. This feature can be set by default and saved in the file, but usually it’s a run-time feature.

#### Part 2: Using Sockets for Secondary Animations

The attachment system in SDK3.5.5 supports simulated movements of bone- and face-attachments. This type of animation is always a reaction to previous (primary) motion, that's why they are called secondary animations. This feature is an extension of an already existing system.

- It can be used to improve the movement of attached static objects (i.e. sword-sheaths, pockets, weapons).
- It is also possible to simulate parts of the mesh directly (i.e. simulation of fat, muscles, bellies, boobs).
- And finally it's possible to create complex rope-setups to simulate hair, tentacles, leather-straps, chains, necklaces and all other types of dangly bits on a character. The ropes can be a bit more complex than what we had so far with CryPhysics, i.e. they can have branching strings and different physical properties for each link.

To approximate the physical movement of objects on characters we use the properties of springs and pendula:

- A pendulum is defined as a bob connected to a non-elastic rod, which experiences simple harmonic motion as it swings back and forth. The equilibrium position of an unconstrained pendulum is the position when the bob is hanging directly downward. In our case, the free swinging can be modifies by physical parameters (stiffness and stiff target) and constrained by different proxies (i.e. cones, half cones, or hinge planes).
- A spring is defined as a bob connected to an elastic rod. Unlike a typical helical spring, this spring can stretch in any direction, but the movement of the spring bob can be constrained to a sphere, ellipsoid, half-sphere, flat plane or a simple line.

![Image](https://www.cryengine.com/docs/static/attachments/23994523)

**Option** | **Description**
--- | ---
**Drop-down list** | This features options for **No Physics**, ** PA_Cone**, ** PA_HalfCone,** ** PA_HingePlane** and** SA_Ellipsoid**. All proxies starting with ** PA_** activate a pendulum simulation. The movement of the pendulum and its attached object is constrained to the limits of these 3 geometrical primitives. If you select ** SA_Ellipsoid** select its activates a spring simulation which is constrained by the shape of an ellipsoid.
**Draw Setup** | You can turn the debug setup on/off. If enabled is shows a green cone, half-code or a hinge-plane. It also shows the pivot-point (blue) and the pendulum-point (cyan) and the axis to connect both.
**Run Simulation** | Activates the simulation. If deactivated, it shows the attached object in the default pose.
**Recommended FPS** | Simulations with high stiffness values require a higher simulation update rate to guarantee a precise and stable simulation. You can choose values between 10-255. If you choose a value of 255, then it assumes the game must run with 255 fps, which is rarely he case. If the framerate of the game is lower than the recommended simulation rate, we subdivide the time-step automatically. A higher value will take more CPU time, so use this value with caution.
**MaxAngle** | Allows you to choose the opening angle for proxies like cone, half-cone or hinge-plane. The angle is in the range (0-179). Values bigger than 90 create an inverse cone. In the case of an ellipsoid it's the radius is centimeter.
**Rotation** | Rotates the hinge-plane, half-cone or ellipsoids. This has no visible impact on the cone.
**ScaleZP** | Only active for springs. It scales the positive half of the spherical proxy. This allows you to constrain the spring movement to a sphere, ellipsoid, half-sphere, flat plane or a simple line.
**ScaleZN** | Only active for springs. It scales the negative half of the spherical proxy. This allows you to constrain the spring movement to a sphere, ellipsoid, half-sphere, flat plane or a simple line.
**Mass** | Defines the mass of the bob. As long as stiffness is 0, the mass has no impact on the period of oscillation. The driving force for a pendulum is gravity. If the pendulum has twice the mass, gravity pulls twice as hard. The force required to move the mass and the force provided by gravity are both determined by the mass of the object, so they cancel each other out and that is why there is no effect. Hence, the weight of the bob does no affect how it moves.
**Gravity** | The default value of **9.81m/sec** is the standard acceleration of falling objects due to gravity on Earth. In a vacuum (Damping=0) any free falling object increases its velocity by ** 9.81m/sec** for each second of its descent and all objects *(no matter of their mass)*, when dropped from the same height will hit the ground at the same time. While the mass of the bob has no effect on the oscillation of the pendulum, the force of gravity does. On the moon (g=9.81/6) not only would the bob weigh less, but it would also swing more slowly.
**Damping** | Fake the effects of air-resistance and friction. Higher dampening-value will make oscillating objects come to rest faster. With Damping=0 the oscillation of a pendulum would never change *(although it does in our simulation, because of fp-precision errors)*
**Stiffness** | Value between 0-999. A value of 0 has no stiffness at all and the pendulum will hang downward when it comes to rest. The higher the value, the faster the bob vibrates and gravitates towards the stiffness target, which can point in any direction. It is important to mention, that stiffness (or spring tension) is a counter force to the mass. A higher mass will always pull the bob downwards. A high stiffness values usually cause multiple oscillation in a single timestep. To avoid instabilities it might be necessary to increase the "recommended FPS" as well.
**Pivot Offset** | Adjusts the pivot rotation point. By default it's the pivot of the model, which is not always the natural simulation pivot. By adjusting the offset you can make the object rotate around another center. If you apply the simulation to a joint directly, you can change the default position of that joint in the rig.
**Simulation Axis** | This is a vector with a direction and a length, which defines the default rod of the pendulum. This length of the rod has a big impact on the amplitude of the pendulum. The longer the pendulum rod, the longer it will take for the pendulum to oscillate back and forth. The simulation axis has no purpose in the case of a spring.
**Stiffness Target** | This is a vector. By default its identical to the simulation axis (=rod of the pendulum). If stiffness is 0, the stiffness target will have no effect. Any other value will make the bob gravitate towards the stiffness target. Stiffness Target is different for pendula and springs: - In the case of a pendulum x is a pitch and y is a roll about simulation axis. With these two parameter you can reach any position. The target can be outside of the code. - In the case of a spring x,y,z are real 3d-coordinates relative to the center of the ellipsoid.

#### A) Add Simulation to the Socket

The socket is created as explained in part1 "Setup of attachment-sockets". Then you have to plugin a CGF into the socket.

The type, size and shape of the CGF (sword-sheath, pistol, dagger) will have no impact on the simulation, but it determines which setup you choose, because we can only mimic the behavior of a real physics object.

To add a dynamic simulation just open the RollupBar under "Simulate Socket" and select either PA_Cone, PA_Hinge, PA_HalfCone or SA_Ellipsoid. The first three are proxies to constraint the movements of a pendulum.

The last one (ellipsoid) constraints the movement of a spring. The ellipsoid is a sphere that you can mold like clay into an non-uniform ellipsoid, a half-sphere, a plane or a single line.

Now you have a physicalized socket which reacts to the movements of the character. You can visualize it with "Draw Setup".

![Image](https://www.cryengine.com/docs/static/attachments/23994524)

Once you have the basic-setup, you can play around with the physics parameters (mass, gravity, dampening, stiffness). You can edit all these parameters while the character animations are playing and see the effects immediately.

To tweak the dynamics it is assumed that the user has a basic understanding of these parameters and their relationship.

##### Adding static geometry to Simulated Sockets and a Collision Triangle (Non-official Feature)

Attach a static object with a collision triangle to an empty socket.

Example file: `Objects\Attachment_exampleFiles\Bone_attachment_triangleCollision\leggun.cdf`

![Image](https://www.cryengine.com/docs/static/attachments/23994527)

Load the exported or downloaded LegGun.chr file and start adding a new empty socket. There we will attach a gun this time to simulate a “thigh” with a attached gun.

The issue here is that the cone for example could penetrate through the leg and the simulation would not look right without collision.

One solution would be to use the half cone but a bone driven solution would be better to make sure to get all movements covered.

For that we are able to assign to each socket 3 bones which are connected and build a collision plane (example for really long hair would be to add to each shoulder bones a “triangle bone” and one on the pelvis).

This feature needs to be added to the cdf file in a text editor we simple add a line which defines the bones for the collision triangle.

Let’s open the `Objects\Attachment_exampleFiles\Bone_attachment_triangleCollision\leggun.cdf` file in a text editor.

![Image](https://www.cryengine.com/docs/static/attachments/23994519)

Adding PA_Align0="bonename01" PA_Align1="bonename02" PA_Align2="bonename03" to an attachment will allow to draw the collision triangle.

The collision triangle will be created counterclockwise, that is why we start in the leggun.cdf with the bone triangle3 – triangle1.

![Image](https://www.cryengine.com/docs/static/attachments/23994526)

The setup works only if you see a colored triangle in the area of the 3 bones. To test the asset you can simple drag in the cdf as a geomEntity in the level and move it with the gizmo around.

One more interactive example would be to replace the local player’s cdf. Download and replace the sdk_player.cdf with the existing one (or only in the.pak file) with `GameSDK\Objects\characters\human\sdk_player\sdk_player.cdf.`

#### B) Transfer the Socket Simulation to a Joint

In this case the simulated objects can be part of the character's mesh (rather than separated CGFs). The main motivation for this feature was the optimization of the render thread.

Because all simulated objects can be part of the mesh, we can add secondary animations without addition draw-calls. So if a model has 256 dangly objects, but all objects are part of the same mesh with the same material ID, then all of them will take only one single draw-call.

Reducing draw-calls is the most important thing if you want to optimize the render-thread. Because this is a very light-weight feature with only minimal impact on CPU, it will work perfectly on PS3 and X360.

To transfer the socket simulation onto a joint, first you need to create and physicalize the socket as explained in **2a)**.

In order to animate the joint directly (and everything that is skinned to that joint) you must leave the "object-field" empty and give the attachment-name the same name as the joint-name. Make sure that the attachment name is lower case.

You can use the "rename" functionality and click the “apply” button. With this simple trick we redirect the simulated animation to the joint and modify the whole character pose.

An update of a joint, is always a full update of the whole branch with all its children. This means we can use exactly the same system so simulate ropes: first we create a pendulum-simulator at the root of the chain, and then you add a new simulator for each link.

It is absolutely important that the rope-links have a child-parent relationship, or the simulation will not look correct.

Example file: `Objects\Attachment_exampleFiles\JiggleJoint\jellyspoon.cdf`

**DCC setup (3ds max)**

Example asset: `Objects\Attachment_exampleFiles\JiggleJoint\jiggleJoint.max`

Simple character setup with bones and a skinned geometry

![Image](https://www.cryengine.com/docs/static/attachments/23994518)![Image](https://www.cryengine.com/docs/static/attachments/23994517)

Load the exported or downloaded example file JellySpoon.chr in the character editor, add one bone attachment and rename it to jelly1 like the name of the bone which you want to influence.

From there make sure to align a **SA_Ellipsoid** to the attachment and adjust the shape and properties to get a nice spring effect to simulate the jelly.

### Advanced setup connected simulate sockets for a chain/rope

#### DCC setup (3ds max)

Example file: `Objects\Attachment_exampleFiles\Pendulum_chain\PendulumChain.max` Example file: ` Objects\Attachment_exampleFiles\Pendulum_chain\pendulum_chain.cdf`

In our example file we will simulate a metal chain a simple bone hierarchy with skinned geometry elements. The chain starts with the root and has 9 bones attached to it as a hierarchy each bone is linked to the next one.

The naming convention isn't important at this stage that is the beauty of this system it allows already existing and exported characters to be used for the simulation of their bones.

By default, the system uses the Y direction to simulate the pendulum therefore we have to make sure that the Y-axis is pointing in the direction of the simulation axis. But in the attachment panel you can set any axis as simulation axis.

![Image](https://www.cryengine.com/docs/static/attachments/23994513)![Image](https://www.cryengine.com/docs/static/attachments/23994520)![Image](https://www.cryengine.com/docs/static/attachments/23994525)

Load the exported or downloaded example file `Objects\Attachment_exampleFiles\Pendulum_chain\Pendulum_chain.chr` in the character editor and start adding new attachments.

We have to create an empty bone attachment which is using exactly the same name as the bone that we want to simulate for our example file. Please make sure that you create a bone attachment and name it exactly as the bone.

It is also really important to write all the names in lower-case otherwise the system won’t be able to recognize the bone. Apply the bone to the attachment by pressing the “Apply” button on the bottom of the attachment menu.

Next, you have to align the socket with simulated joint by clicking on the “Align with bone” button. Now we will enable the simulation by assigning a simulation primitive in the “simulate socket” menu.

![Image](https://www.cryengine.com/docs/static/attachments/23994514)

Now you can play around with the physics parameters (mass, gravity, dampening, stiffness). You can edit all those parameters while the animations are playing and see the effects immediately.

You can also load your created.cdf into the forest level by dragging in the chr file as a geomEntity. The immediate update will only happen in the character editor but you are able to save the new changes to your.cdf and reload the scripts in the level to see it updating in the level.

### Hinge Attachments (CRYENGINE 3.4 or earlier)

Hinged character attachments use a fairly simple dedicated code (directly in the animation system) that can only handle one-hinge attachments with joint limits (they don't even handle collisions with the character or with other attachments).

To turn on dangling for a particular attachment, one has to specify 2 planes that form the edge used as a hinge. Planes are specified in the attachment's coordinate space. The first plane is the one the attachment "lies" on in its resting state, and the second is another plane it contacts with.

For the most typical attachment orientation, natural plane selection would be positive y, positive z (+y,+z).

![Image](https://www.cryengine.com/docs/static/attachments/23994515)

Default attachment orientation corresponds to joint angle 0. The maximum rotation angle is specified as the "limit" property. Use the "damping" property to prevent the "pendulum effect" (values up to 10 are reasonable, but can go even higher when needed).

Note that the changes take effect only after you press **Apply** button.

##### How the planes are defined

The axis of the local coordinate system can be seen as normals on planes with the same name. The +y Axis is the normal to the +y plane. the -y Axis is the normal of the -y plane, +z is the normal on the +z plane (see color coding in the picture below).

In the example above, the +y and +z planes were chosen. The hinge axis is created between them.

![Image](https://www.cryengine.com/docs/static/attachments/23994516)

[Bone attachment](#bone-attachment)[Face attachment](#face-attachment)[Skin attachment](#skin-attachment)[Part 1: Setup of attachment-sockets](#part-1-setup-of-attachment-sockets)[Part 2: Using Sockets for Secondary Animations](#part-2-using-sockets-for-secondary-animations)[A) Add Simulation to the Socket](#a-add-simulation-to-the-socket)[B) Transfer the Socket Simulation to a Joint](#b-transfer-the-socket-simulation-to-a-joint)[DCC setup (3ds max)](#dcc-setup-3ds-max)
