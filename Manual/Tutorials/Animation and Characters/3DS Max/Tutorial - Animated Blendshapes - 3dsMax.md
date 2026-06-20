# Tutorial - Animated Blendshapes - 3dsMax

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959524
- Page ID: 44959524
- Breadcrumb: Tutorials > Animation and Characters > 3DS Max > Tutorial - Animated Blendshapes - 3dsMax
- Parent: 3DS Max

## Content

##
Overview

This tutorial section covers how to set up
**
animated
**
 morph targets/blendshapes scene in 3dsMax and get them into CRYENGINE. The terms "blendshape" and "morph target" are interchangeable, as they are named differently in 3dsMax/Maya/modo, etc. In this section we try to avoid the term blendshapes, since
as 3dsMax users,
you will be more familiar with morph targets.

This tutorial may rely on the free GameSDK sample project. We recommend that you download this from the
**
[Asset Database](https://www.cryengine.com/marketplace)
**
, import it into your Launcher, start it from there and then create a new level.

See
**
[this page](/docs/static/engines/cryengine-5/categories/23756816/pages/36870288)
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

Source 3dsMax scenes with exported CRYENGINE files:

**
[sdk_blendshape_max_tutorial.zip](/docs/static/attachments/44959540)
**
 (8.6 MB)
(Extract this to the Assets folder in your GameSDK folder. See above for the default location of this folder.)

From engine version 5.6 onwards, the skeleton list is not used anymore, so you can
 ignore any references to it on the rest of the page.

Backup your "SkeletonList.xml" before overwriting it!

##
Prerequisites for this Tutorial

The project folder is set to <
`
**
GameSDK folder (see above)>\Objects\tutorial\animated_blendshape_tutorial\max
**
`
.

Please take this into account if you wish to use a different project location, but always stay inside your project folder when saving your project 3dsMax source files.

Before you continue with this tutorial, make sure to have read and understood the following:

-
**
[How to install CryMaxTools](/docs/static/engines/cryengine-3/categories/1114113/pages/1310877)
**

-
**
[Basic Asset Setup and Export - 3ds Max](../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Preparing%20Assets%20for%20CRYENGINE/Basic%20Asset%20Setup%20and%20Export%20-%203ds%20Max.md)
**

-
**
[CRYENGINE Exporter](../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%203ds%20Max%20Tools/CRYENGINE%20Exporter%20in%203dsMax.md)
**

-
**
[3dsMax unit scale to match up with CRYENGINE unit system](../../../Asset%20Prep%20(External)/Measurement%20Reference%20-%20(DCC%20Unit%20Setup).md)
**

##
Helpful information about 3dsMax "Morpher" modifier in conjunction with CRYENGINE:

-
If you just want to have
**
non-animated
**
 morph targets available in your CRYENGINE characters, you can export your character as CRYENGINE *.skin format. A standard 3dsMax "Morpher" inserted before the "Skin" modifier is all you need.

Decrease the morph target position threshold in the Exporter options to 0.001 or lower if you get bad morph targets. This will
 make the Exporter include even minimal displaced vertices.

*
Pic1: Morph target export option in 3dsMax

*
![Image](https://www.cryengine.com/docs/static/attachments/44959539)

The blue colored vertices are marked for CRYENGINE to update these vertex normals when morph targets are blended in addition to skin deformation.

-
3dsMax "Morpher" modifier is limited to 100 morph targets. If you intend to use more, then you must add a morph target, which also has a "Morpher" modifier with the morph targets no. 100 - no. 199, to your base mesh. Apply the same procedure to the next 100 morph target, etc.

-
Keep the names of your morph target meshes unique and reasonable. If you change their names after you set up the Morpher and the "*_blendWeightVertex" nodes ( which will be explained later in this tutorial), you must rebuild the
"*_blendWeightVertex" nodes.

-
You must have a bound skeleton and a "Skin" modifier to be able to get animated morph targets/blendshapes into CRYENGINE.

-
You also need to create the skeleton triangle mesh for the CRYENGINE
*.CHR file
and have it skinned to a bone node, which is in the top of the deformation hierarchy, in our case the "Spine04" bone.

-
Your "Morpher" modifier is usually inserted between the base mesh object and the Skin modifier with Skin being on top of the modifier stack.

-
You are allowed to delete the morph targets after you added them to the Morpher modifier. In contrast to the Maya export pipeline, the morph targets are not needed for 3dsMax to CRYENGINE export.

-
You must be careful with move/rotate/scale transformations in your base mesh. Reset XForm and collapse the modifier stack of your base mesh before skinning and making the morphs.

Keep the maximum influence count to 8! For performance's sake keep it to 4.

CPU/Software Skinning supports 8 weights per vertex and morph targets/blendshapes.

GPU Skinning support supports 8 weights per vertex, but no morph targets/blendshapes.

##
Set up Your Content In 3dsMax

We provide the CRYENGINE "sdk player" head with morph targets with this tutorial. Therefore, we only need to get the pieces together and make the 3dsMax scene ready for exporting to CRYENGINE.

-
In the tutorial scene the base head mesh was already bound to provided skeleton ( spine, neck, head, jaw, etc. bones). The morph target haven't been hooked up in a
**
Morpher
**
 modifier yet.

If you want to recreate the skinning steps. The bone "Spine04" is the top level skin bone to add into the deformation bone list of the
**
Skin
**
 modifier. Therefore, please don't add the "root" bone node to the
**
Skin
**
 or
**
CrySkin
**
 if you want to.

Please open the start scene max file:
**
*
 animated_blendshape_tutorial_start.max
*
**

**
*

*
**
*
Pic2a: 3dsMax scene with head geometry skinned to a skeleton
*

![Image](https://www.cryengine.com/docs/static/attachments/44959538)

-
We will add a
**
Morpher
**
 modifier to our base mesh and include the three provided morph targets into it. Keep in mind you insert the
**
Morpher
**
in front of the
**
 Skin
**
 modifier. Please test the three morph channels to see if they are hooked up correctly to the three morph targets.

See the result in the scene file:
**
*
animated_blendshape_tutorial_mid01.max
*
**

**
*

*
**
*
Pic3: Add the 3 morph target meshes to the Morpher modifier
*

![Image](https://www.cryengine.com/docs/static/attachments/44959537)

-
Before proceeding to animation we will show you how to set up the dummy triangle mesh for the skeleton CHR. This *.CHR file is required for CRYENGINE's attachments system. We can only have morph targets/blendshapes with CRYENGINE *.SKIN file format. The *.SKIN file is always an attachment. This implies we need to make a CHR with just the skeleton. For this skeleton we need a simple mesh object which holds all information about the skeleton hierarchy, a triangle mesh object.

*
Pic4: Created CHR triangle mesh for the skeleton
*
*

![Image](https://www.cryengine.com/docs/static/attachments/44959536)

*

*

*

-
You may have notice the dummy triangle mesh named "sdk_player_head_max_skel" in the 3dsMax scene. This triangle mesh has a
**
Skin
**
 modifier added with just the "Spine04" bone added to its bone list. CRYENGINE will extract the hierarchy data from this skinned triangle mesh piece when you export it as *.CHR file.
*

*

*
*
Pic5: CHR skeleton mesh dummy with a Skin modifier
*

![Image](https://www.cryengine.com/docs/static/attachments/44959535)
*

##
Add the "blendWeightVertex" Nodes for Animation

As already mentioned, if you want to have
**
non-animated
**
 morph targets/blendshapes with your CRYENGINE characters you do not need to follow the steps in this section any further. Export the dummy triangle mesh as a *.CHR skeleton file and the sdk_player_head mesh as a *.SKIN file. Also, check the morph target position threshold in the Max to CRYENGINE Exporter options.

We will go through each step required to set up a working "blendWeightVertex" node by "Parameter Wiring", but also provide a MaxScript to automate this process.

-
This step is optional: O
nce you set up the
**
Morpher
**
 with its morph targets, you may hide or even delete the morph meshes you modeled.

-
By default the morph channels of the
**
Morpher
**
 modifier are set to the range of [0..100] percent. Leave it as is since CRYENGINE expects values between 0 and 100.

-
For each animated morph channel you must create a node named <BLENDSHAPE_MESH_NAME> + "_blendWeightVertex", e.g. "sdk_player_head_brows_raise_blendWeightVertex". The "blendWeightVertex" nodes are then parented under the root node of the skeleton hierarchy.

*
*
Pic6a
*
: Create a "Point Helper" node in 3dsMax and rename it following the naming convention
*

![Image](https://www.cryengine.com/docs/static/attachments/44959534)

-
After created the the "blendWeightVertex" nodes you need to use the 3dsMax' "
*
Parameter Wire"
*
 feature to map the values of each morph channel to drive the
*
 "Position_X"
*
of the corresponding
*
 "blendWeightVertex"
*
 node. The follwing images below will show you what to connect in this process:

*
Pic6b: Start Parameter Wiring the base mesh with the Morpher to a "blendWeightVertex" helper node
*

![Image](https://www.cryengine.com/docs/static/attachments/44959533)

*
Pic6c: Continue the parameter wiring to connect the morph channel to the "Position X" of the "blendWeightVertex" node

*
*
![Image](https://www.cryengine.com/docs/static/attachments/44959549)
*

*
Pic6d: Pick the destination track of the connection

*
*
![Image](https://www.cryengine.com/docs/static/attachments/44959532)
*

*
Pic6e: Finalize the control direction of the parameter wiring process

*
*
![Image](https://www.cryengine.com/docs/static/attachments/44959531)
*

*

*

-
Rather than manually creating the helper nodes we provide a MaxScript below for the setup. All you need to change is the base mesh node name and the root of your rig if you have a different morph target/blendshape scene.

-

```

`
-- Delete any existing "*_blendWeightVertex" nodes you may have before re-running the script!
function ceCreateBlendWeightVertex argBaseMesh argRigRoot =
(
  clearListener()

  morphMod = undefined
  hasMorpher = False

  numMods = argBaseMesh.modifiers.count
  currModNum = numMods
  morphModStackNumber = undefined

  blendWeightVertexList = #()
  listOf_ID_MorphName_Helper = #()

  while ( (not hasMorpher) OR (currModNum > 0) ) do
  (
    if ( classOf argBaseMesh.modifiers[currModNum] == Morpher ) then
    (
      hasMorpher = True
      morphMod = argBaseMesh.modifiers[currModNum]
      morphModStackNumber = currModNum
    )
    currModNum -= 1
  )

  if ( hasMorpher ) then
  (
    for n = 1 to 100 do
    (
      if ( (WM3_MC_HasData morphMod n) ) then
      (
        currChannelName = WM3_MC_GetName morphMod n
        format ("\nMorph Target Channel Name: %") currChannelName

        newPoint = Point size:15.0 axistripod:True cross:False box:True wirecolor:orange name:( currChannelName + "_blendWeightVertex")
        newPoint.parent = argRigRoot
        append blendWeightVertexList newPoint

        fromSrc = argBaseMesh.modifiers[morphModStackNumber][n]
        toTgt = newPoint.position.controller[1]
        myStr = substituteString (fromSrc as string) "SubAnim:" ""
        expr =  myStr + "_"
        paramWire.connect fromSrc toTgt expr

        format ("\nParameters wired from % to %\n") fromSrc toTgt

        tmpList = #(n, currChannelName, newPoint)
        append listOf_ID_MorphName_Helper tmpList
      )
    )
  )
  else
  (
    messageBox ( "WARNING: Your base mesh object DOES NOT have a Morpher modifier. No \"_blendWeightVertex\" nodes created." )
  )
  select blendWeightVertexList
  max zoomext sel
  format "\n"
  listOf_ID_MorphName_Helper
)
--ceCreateBlendWeightVertex $sdk_player_head_max $root

`

```

-
Paste the script into a tab of 3dsMax' Script Editor and execute it once. This function is now in memory. Run the command :
**

**

**
c
**
**
eCreateBlendWeightVertex $sdk_player_head_max $root
**

If you decide to use another head mesh then don't forget to replace the
**
$sdk_player_head_max
**
**

**
and
**
$root
**
 with your skinned mesh and root node name prefixed with a dollar sign $ as you've seen in the notation in our example.

You can also "un-comment" the last line of code by removing the double dashes "--"  and r
un the script again (CTRL+E in MaxScript Editor).

-
All "*_blendWeightVertex" helper nodes must be inside the skeleton hierarchy. If you do not use this script then don't forget to parent them to your root nod of your rig.

-
Finally, you can add some morph target/blendshape animation. You will notice the "blendWeightVertex" joints moving while scrubbing the timeline when your have animated the three morph channels.

*
*
Pic6: Created and "parameter-wired" the "blendWeightVertex" nodes to the morph channels

*
*
*
*
![Image](https://www.cryengine.com/docs/static/attachments/44959530)
*
*

-
For the results, please open the scene:
*
**
animated_blendshape_tutorial_mid02.max
**
*

##
Add Animation to the Morpher

We will keep it short and let you consult the Autodesk 3dsMax documentation/tutorials on how to make animation.

Here are the steps in short:

-
Press the 3dsMax "Animate" button, the 3D viewport will be framed red.

-
Go the Morpher modifier, scrub the timeline, change the morph channel values.

-
Rotate some bones so that you have both skeletal and morph animation.

-
When you're done animating, you are ready to export the assets.
Or you could open this animated scene:
*
**
animated_blendshape_tutorial_mid03.max
**
*

##
Some Pitfalls using Morph Targets:

-
The meshes to be skinned and built morph targets with ought to have clean transformations ("Reset Xform" and collapse modifier stack) before they are bound to a Skin modifier. Omitting these steps may get you some deformation weirdness in CRYENGINE when you turn on blendshapes.

-
Decrease the morph target position threshold on export until no vertices stay behind when morph targets/blendshapes are active.

-
Never change the mesh topology on the morph targets. This will render them useless. Though, there are some ways to fix it, if you find out, e.g. that you need to increase the mesh density on some areas of the base model.

-
Pay attention to the deformation order of Morph targets/Blendshapes with a Skin. Skin modifier is usually on the top of the modifier stack.

**
Pay special attention when you export your "*.SKIN" and "*.CHR" files! Rewind your current frame slider to the frame where your skin pose is! This is usually frame 0 in 3dsMax "Skin" modifier.
**
The animation named "
**
default
**
" is the standard animation and will be played automatically in the Sandbox Editor (i.e. when you add this character as "AnimObject" entity).

##
Export Animated Morph Targets to CRYENGINE

Please save your final 3dsMax scene file to your project directory first. Instead, you could also open the provided final export scene:
*
**
animated_blendshape_tutorial_end.max
**
*
.

We will create three files by export. The exported *.CHR and *.SKIN file should be at the same location where you saved your source 3dsMax files. The animation *.I_CAF should be in a sub-folder of your
`
**
YOUR_PROJECT_FOLDER\animation
**
`
 directory.

-
a *.
**
CHR
**
 file containing the skeleton hierarchy

-
a *.
**
SKIN
**
 file containing the actual skinned mesh with the morph targets

-
an *.
**
I_CAF
**
 animation file which will be converted to a compressed animation file automatically by CRYENGINE when we go into the Sandbox Editor

-
Select the CHR skeleton triangle mesh and go into 3dsMax Utility tab open up the CRYENGINE Exporter. Include just the CHR skeleton triangle mesh into the Geometry Export List and check "Export file per node", so that the exporter generates the *.CHR file name based on the original 3dsMax node name. Otherwise it will choose the 3dsMax scene file name. Finally hit the blue
**
Export Nodes
**
 button. Check if you have a *.CHR file in your project directory.

*
Pic8a: Set CHR export options
*

![Image](https://www.cryengine.com/docs/static/attachments/44959529)

-
Next file we want to write if the actual skinned mesh with the Morpher as CRYENGINE *.skin file. Make sure you reset the Geometry Export list in the CRYENGINE Exporter options before adding the "sdk_player_head_max" mesh.

*
Pic8b: Export options needed to generate the *.SKIN file with morph targets
*

*
![Image](https://www.cryengine.com/docs/static/attachments/44959528)
*

*

*

-
Output the animation to test out the morph targets with the skeletal animation. Choose the file name "default", this is going to be the animation name inside CRYENGINE later. Save this "
*
default.i_caf
*
" file to:

`
**
YOUR_PROJECT_FOLDER\Animation\tutorial\animated_blendshape_tutorioal\max
**
`

*
Pic8c: Export animation to an *.i_caf file:
*

*
![Image](https://www.cryengine.com/docs/static/attachments/44959527)

*
*

*

-
There are three CRYENGINE files you exported: a *.CHR file, a *.SKIN file the intermediate animation *.I_CAF file.

*
Pic9a: Two geometry files
*

*
![Image](https://www.cryengine.com/docs/static/attachments/44971238)

*

*
Pic9b: One intermetdiate animation file

*
![Image](https://www.cryengine.com/docs/static/attachments/44959525)
The next tutorial section will cover how to set up the exported character assets in CRYENGINE's Character Tool.

[![Image](https://www.cryengine.com/docs/static/attachments/24151097) Tutorial - Animated Blendshapes - CRYENGINE 5.5.2](/docs/static/engines/cryengine-5/categories/23756816/pages/24285808)

[Tutorial Files](#tutorial-files)
[Prerequisites for this Tutorial](#prerequisites-for-this-tutorial)
[Helpful information about 3dsMax "Morpher" modifier in conjunction with CRYENGINE:](#helpful-information-about-3dsmax-morpher-modifier-in-conjunction-with-cryengine)
[Set up Your Content In 3dsMax](#set-up-your-content-in-3dsmax)
[Add the "blendWeightVertex" Nodes for Animation](#add-the-blendweightvertex-nodes-for-animation)
[Add Animation to the Morpher](#add-animation-to-the-morpher)
[Some Pitfalls using Morph Targets:](#some-pitfalls-using-morph-targets)
[Export Animated Morph Targets to CRYENGINE](#export-animated-morph-targets-to-cryengine)
