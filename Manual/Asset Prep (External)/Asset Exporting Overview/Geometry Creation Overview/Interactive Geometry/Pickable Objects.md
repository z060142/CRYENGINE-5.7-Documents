# Pickable Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308034
- Page ID: 23308034
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Interactive Geometry > Pickable Objects
- Parent: Interactive Geometry

## Content

##
Overview

In CRYENGINE, objects can be turned into pickables. The player can pick them up with one or two hands, carry them around, and drop them again. The picking behavior is dependent on the game script.

As an example, in the Crysis Game script there are two types of picking behavior:

**
One-handed
**
: The player will pick up the object with his left hand and hold the object in this hand. The weapon in his right hand will still be usable. If the player holds a two-handed weapon, the weapon will be switched to the fists.

**
Two-handed
**
: The Player will pick up and hold the object with both hands. The hands themselves will not be visible in the fist person view; also, no weapon will be usable.

##
Requirements

A pickable object can be set up in a DCC tool by having:

-
A NoDraw collision proxy attached to it.

-
The mass or density defined (either set up in the 3ds Max object properties or in the entity in Sandbox).

-
A grab-helper, with the correct name linked to it.

##
Basic Setup In 3ds Max

To define the object's position on the in-game screen, a helper needs to be linked and aligned to the object. The presence of such a grab-helper in the object hierarchy turns the object into a pickable object.

In the one-handed pickup animation, the "item_attachment"-bone position is in the left hand of the player. For a two-handed pickup the bone is located in the center between the player's hands.

Use the "Local" coordinate system when adjusting the rotation of the grab-helper.

![Image](https://www.cryengine.com/docs/static/attachments/23994776)

##
One-Handed Pickable Objects

-
Example file:
[pickable_onehanded.max](/docs/static/attachments/23994785)

-
Example hierarchy:

![Image](https://www.cryengine.com/docs/static/attachments/23994775)
**
Setting up the Helper:
**

1. Open a Max scene and create a "Dummy" helper.

2. Name it
**
"grab_onehanded_01"
**
.

3. Link the grab_onehanded_01 helper to the object.

4. Align it to the object.

5. Proceed with export.

##
Two-Handed Pickable Objects

-
Example file:
[pickable_twohanded.max](/docs/static/attachments/23994787)

-
Example hierarchy:

![Image](https://www.cryengine.com/docs/static/attachments/23994789)
**
Setting Up the Helper:
**

1. Open a Max scene and create a "Dummy" helper. Name it "grab_twohanded_01".

2. Link the grab_twohanded_01 helper to the object.

3. Align it to the object.

4. Proceed with export.

##
Pieces of Destroyable Objects

When a destroyable entity is destroyed, it will spawn pieces as well as a remaining object. These objects can be set up as pickables as well.

The process is equivalent to the one for one-handed and two-handed pickables, but the name of the object the helper that is linked to needs to be added as a prefix in front of the helper name (e.g.
**
remain_grab_twohanded_01
**
). A grab-helper for the non-destroyed version of the object ("main") does not need to have a prefix.

-
Example file:
[pickable_destroyable.max](/docs/static/attachments/23994784)

-
Example Hierarchy:

![Image](https://www.cryengine.com/docs/static/attachments/23994781)
**
Basic Setup in 3ds Max:
**

-
Open the max scene and create a dummy helper for the object. Name it as described in the overview:

-
**
remain_grab_twohanded_01
**
 or
**
piece_banana01_grab_onehanded_01
**
.

-
Link the grab-helper to the object.

-
Align it to the object.
In most cases the helper should be positioned below the object so that the player can see the object, since he cannot see his own hands in two-handed mode.

Note
The pivot of these spawned pieces/remain that you can see in your DCC tool doesn't necessarily match the entity position in game. This means that placing the helpers for these objects could require a bit of trial and error. It is a good idea to always use the non-destroyed version of the object as a reference to align your helper.

4. Repeat steps 1-3 for all pieces/remains that should be pickable.

5. Proceed with export.

##
Using the Pickable Helper Template File

During Crysis development, Crytek developed an advanced technique to align one-handed grab-helpers to pickable objects in 3ds Max. There is a template file that contains the player's arms in the grab-pose that will be seen in the first person view of the game, and a camera that replicates the first person-camera of the game. There is also a grab helper included that is connected to a helper with a transformation-constraint. This makes it easier to rotate the whole template file and the grab-helper at the same time without unlinking the helper.

The key about this technique is to rotate the whole arms-template including the grab-helper, until the result looks as desired in the first person camera. The disadvantage of this technique is that the scene might become complex, especially if more than one template is merged into the scene. Efficient layer usage will become helpful for this.

Pickable helper template file:
[pickable_template.max](/docs/static/attachments/23994786)

**
3ds Max Setup:
**

-
Merge in the "pickable_template.max"-file. Select all the objects in the merge-window.

-
Link the "grab_onehanded_01" helper to your object.

-
Adjust the position and rotation of the "pickable_template"-helper until you are satisfied with the position. The "grab_onehanded_01" helper is constrained to the "pickable_template", so it will inherit all transformation changes of the "pickable_template"-helper.

-
Proceed with export.
Example of a well-aligned pickable helper template:

![Image](https://www.cryengine.com/docs/static/attachments/23994788)

##
Export

-
Add the root node of your pickable object to the export list.

-
Make sure "export by node" is selected and "merge all nodes" is deselected.

-
Click
**
export
**
.
Note
Everything linked to this object including all the sub-objects/helpers will be exported into one file.

##
Basic Setup In Maya

##
Maya One-Handed Pickable Objects

-
Example hierarchy:

![Image](https://www.cryengine.com/docs/static/attachments/23994783)
**
Setting up the Helper:
**

1. Open a Maya scene and create a locator.
Name it "grab_onehanded_01_helper".

2.
Insert the grab_onehanded_01_helper to the objects group node.

3.
Align it to the object.

4.
Proceed with export.

##
Maya Two-Handed Pickable Objects

-
Example hierarchy:

![Image](https://www.cryengine.com/docs/static/attachments/23994790)
**
Setting Up the Helper:
**

1. Open a Maya scene and create a locator. Name it "grab_twohanded_01_helper".

2. Insert the grab_twohanded_01_helper to the objects group node.

3. Align it to the object.

4. Proceed with export.

##
Maya Pieces of Destroyable Objects

When a destroyable entity is destroyed, it will spawn pieces as well as a remaining object. These objects can be set up as pickables as well.

The process is equivalent to the one for one-handed and two-handed pickables, but the name of the object the helper that it is linked to needs to be added as a prefix in front of the helper name (e.g. remain_grab_twohanded_01_helper). A grab-helper for the non-destroyed version of the object ("main") does not need to have a prefix.

##
Setup In Sandbox

In order to make your pickable object work in Sandbox, place it as a GeomEntity or any Entity that have "Pickable" and "RigidBody" set to true. "Usable" must be disabled.

Pickable objects-types are:

-
Entities with "Pickable" and "RigidBody" set to "true" and "Usable" to "false".

-
Particles containing a grab-helper.

-
Ragdoll objects containing a grab-helper (e.g. Dead bodies).

-
"Default"-Class entities (pieces of broken vegetation).

-
Procedural Vegetation with "Pickable" flag set to true.
![Image](https://www.cryengine.com/docs/static/attachments/23994782)

##
Picking of Animated Non-AI Characters

Non-AI-Characters can be set up to be pickable as well (animals for example).

In this case you need to use the Character Editor in Sandbox to set up the grab-helper attachment. You cannot do this in a DCC tool.

The grab-helper will be added to the character as a bone attachment. So, the orientation of the helper is dependent on the bone to which it will be attached. You don't necessarily need to apply an object to the attachment, but for easier alignment it is recommended to use an object with a clearly visible orientation. The object will be removed from the attachment later on when the desired result is achieved.

**
Attachment Creation:
**

-
Open the .chr or .cdf file you want to make pickable in the Character Editor.

-
Add a new attachment.

-
Apply this attachment as a bone-attachment to any bone (preferably root-bone of the rig, since it is not animated).

-
Move and rotate the object until you think it might be aligned correctly later in the first-person view.

-
Save your work as a .cdf file.

-
Place your animated non-AI character in the Perspective view in Sandbox (Animals are usually placed from the ArchetypeEntity Library).

-
Go into game-mode, pick up your animated non-AI character and see if its alignment looks as desired in the first-person view.
In order to remove the object that was used as the helper for the alignment, open your .cdf file in Notepad and remove the object path. Repeat steps 4 - 7 until the desired result is achieved.

**
During the alignment:
**

![Image](https://www.cryengine.com/docs/static/attachments/23994780)

![Image](https://www.cryengine.com/docs/static/attachments/23994779)

**
After removing the object path in Notepad:
**

![Image](https://www.cryengine.com/docs/static/attachments/23994777)

![Image](https://www.cryengine.com/docs/static/attachments/23994778)

##
Notes

Changes on the pickable behavior of AI-Characters and procedural breaking environment objects have to be modified in the game code. For AI-Characters, the name of the bone which serves as a grab helper needs to be defined by game code. The grab position of pickable procedural breaking environment pieces is located on an offset to its pivot, which needs to be defined by game code

##
Debugging

The easiest way to test how this is working is to place the asset, go in-game and then grab it by pressing F.

**
e_DebugDraw
**

```

Draw helpers with information for each object (same number negative hides the text)
 1: Name of the used cgf, polycount, used LOD
 2: Color coded polygon count
 3: Show color coded LODs count, flashing color indicates no Lod
 4: Display object texture memory usage
 5: Display color coded number of render materials
 6: Display ambient color
 7: Display tri count, number of render materials, texture memory
 8: RenderWorld statistics (with view cones)
 9: RenderWorld statistics (with view cones without lights)
10: Render geometry with simple lines and triangles
11: Render occlusion geometry additionally
12: Render occlusion geometry without render geometry
13: Display occlusion amount (used during AO computations). Warning: can take a long time to calculate, depending on level size!
15: Display helpers
16: Display debug gun
17: Streaming info (buffer sizes)
18: Streaming info (required streaming speed)
19: Physics proxy triangle count
20: Display object instant texture memory usage
21: Display animated object distance to camera
22: Display object's current LOD vertex count

```

[Requirements](#requirements)
[Basic Setup In 3ds Max](#basic-setup-in-3ds-max)
[Basic Setup In Maya](#basic-setup-in-maya)
[Setup In Sandbox](#setup-in-sandbox)
[Picking of Animated Non-AI Characters](#picking-of-animated-non-ai-characters)
[Notes](#notes)
[Debugging](#debugging)
