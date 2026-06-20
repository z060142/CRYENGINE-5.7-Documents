# Tutorial - Animated Blendshapes - Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959494
- Page ID: 44959494
- Breadcrumb: Tutorials > Animation and Characters > Maya > Tutorial - Animated Blendshapes - Maya
- Parent: Maya

## Content

##
Overview

This article covers how to create and implement animated blendshapes in Maya.

*
Pic1: Models
*

![Image](https://www.cryengine.com/docs/static/attachments/44959515)

This tutorial may rely on the GameSDK Sample Project. We recommend that you download this from the
**
[Asset Database](https://www.cryengine.com/marketplace/product/crytek/cryengine-gamesdk-sample-project)
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

Source Maya ASCII scenes with exported CRYENGINE files:

**
[sdk_blendshape_maya_tutorial.zip](/docs/static/attachments/44959495)
**
 (2.9mb)
(Extract this to the Assets folder in your GameSDK folder. See above for the default location of this folder.)

##
Setup Your Content In Maya

##
Requirements for the blendshape scene in Maya:

-
All blendshape meshes (do not delete them!) must exist in your Maya scene and should be in the same world space location as the skinned base mesh. So, move your blendshape meshes on top of the skinned base mesh:

![Image](https://www.cryengine.com/docs/static/attachments/44959497)

-
In some rare situations you may have set up your Maya as a Z-Up. If that is the case then for this tutorial you will need to reset it to a Y-Up. You must also set your scene to
**
 30 fps
**
 and to
**
centimeter
**
 when it comes to exporting:

![Image](https://www.cryengine.com/docs/static/attachments/44959496)

-
You must "smooth bind" at least one joint to the blendshape base mesh.

In the tutorial scene the base head mesh was bound to some common joints (top spine, neck, head, jaw, etc.).

The maximum influence count is eight. For performance's sake keep it to four.

CPU/Software Skinning supports 8 weights per vertex and blendshapes.

GPU Skinning support supports 8 weights per vertex, but no blendshapes.

The top-level bound joint is "Spine04". Don't skin the "root" joint into your character mesh - it is for CRYENGINE export:

![Image](https://www.cryengine.com/docs/static/attachments/44959512)

-
Notice the empty "SceneRoot" group and "root" joint created for CRYENGINE orientation:

![Image](https://www.cryengine.com/docs/static/attachments/44959511)

![Image](https://www.cryengine.com/docs/static/attachments/44959510)

-
Make sure the root node of the skeleton hierarchy has "zero" rotations - this means CRYENGINE interpretes it as Zero. Since CRYENGINE 3.8 and in respect to Maya there is a a properly orientated, empty "SceneRoot" group node and a "root" joint as the top-level node of the deforming skeleton. They have been setup with both looking forward with their Z-axes aligned to the World Y-axis and the their Y-axes aligned to the World Z-axis:

![Image](https://www.cryengine.com/docs/static/attachments/44959509)

-
For each blendshape mesh you must create a joint in the origin and name it <BLENDSHAPE_MESH_NAME> + "_
*
blendWeightVertex", e.g.
*
"sdk_player_head_brows_raise_blendWeightVertex". The "blendWeightVertex" joints have been parented under the root joint for the skeleton hierarchy. (Use the script below in step 5!)

![Image](https://www.cryengine.com/docs/static/attachments/44959508)

-
You must map the output range of the blendShape node weights from 0 to 1 to 0 to 100 of the translateX attribute of these joints. (Add an in-between MultiplyDivide node!)

![Image](https://www.cryengine.com/docs/static/attachments/44959507)

-
Rather than manually creating the joints and connections you may want to use the Python script below for the setup:

```

`
from maya import cmds

def createBlendControlVertex(node, p=None, connect=True, debug=1):
    '''
    Check outgoing "weight" connections of a blendShape node, create the appropriate blendWeightVertex joints.
  Optional: Connect and map the "weight" output range [0,1] of the blendShape node to [0,100] to the
  translateX attribute of these helper joints.
  Optional: Parent all blendWeightVertex joints under a transform node
    '''
    if debug: print node
    blendNodes=[]
    blendVertexJnts=[]
    try:
        shapes = cmds.blendShape(node, t=1, q=1)
        shapeNode = cmds.listRelatives(node, children=1, shapes=1)
        blendShapeNode = cmds.ls(cmds.listHistory(node),type='blendShape')[0]
        for shape in shapes:
            n = shape.split('mesh__')[-1] + '_blendWeightVertex'
            if n not in blendVertexJnts:
                cmds.select(cl=1)
                jnt = cmds.joint(name=n)
                blendVertexJnts.append(jnt)
                blendNodes.append(jnt)
            if connect:
                try:
                    mult = cmds.shadingNode('multiplyDivide', asUtility=1, name = shape + '_MULT')
                    cmds.connectAttr((blendShapeNode + '.' + shape.split('mesh__')[-1]), mult + '.input1.input1X')
                    cmds.setAttr(mult + '.input2X', 100)
                    cmds.connectAttr(mult + '.output.outputX', (n + '.translateX'))
                except Exception as e:
                    print e
    except:
        print 'createBlendControlVertex>>>', node, 'has no blendshapes!'
    if p:
        if blendNodes:
            cmds.parent(blendNodes, p)
    return blendNodes

`

```

Paste the script into a Python script tab of Maya's Script Editor and execute it just once. Then run the script by the command.
**
REMEMBER:
**
If you decide to use another head mesh then don't forget to replace the
*
"sdk_player_head"
*
:

**
createBlendControlVertex( 'sdk_player_head', p=None, connect=True, debug=1 )
**

You should parent those blendWeightVertex joints to the CRYENIGINE "root" joint. However, you can also run the command (shown below) if the "root" joint has already been created:

**
createBlendControlVertex( 'sdk_player_head', p='root', connect=True, debug=1 )
**

-
A dummy quad/triangle polymesh object must be created and smooth skinned to a node of the skeleton hierarchy - it's best to select and include the top-most deforming influence as the only deforming joint.

*
Why do you need this dummy?
*
Because this node only includes information about the skeleton hierarchy and thus keeps the model with skin and joint data separated from the skeleton. Hence, when you attach a "skin attachment" in CRYENGINE's Character Tool both model + skinning data are separated from the actual skeleton/joint (s) data. You could also attach the head mesh, then consecutively add more upper body apparel, etc.

![Image](https://www.cryengine.com/docs/static/attachments/44959506)

-
Finally, you can add some blendshape animation. If you have animated the blendshape node beforehand, then you will notice the "blendWeightVertex" joints are moving when scrubbing the timeline.

##
Requirements before exporting to CRYENGINE: (applies to all character exports with ".SKIN" and *.CHR files)

-
A cryExportNode must be created for the skinned mesh with the BlendShape node. Use the "TOOLS" from Crytek shelf or create as shown in the screenshots below:

![Image](https://www.cryengine.com/docs/static/attachments/44959505)

-
A second cryExportNode must be created for the skinned dummy quad/triangle mesh object:

![Image](https://www.cryengine.com/docs/static/attachments/44959504)

-
In the cryExportNode of the skinned mesh with your blendshapes, set the export file type as "*.SKIN". Activate
**
Eight Weights Per Vertex
**
:

![Image](https://www.cryengine.com/docs/static/attachments/44959503)

-
In the cryExportNode of the skinned dummy mesh, set the export file type as "*.CHR".

![Image](https://www.cryengine.com/docs/static/attachments/44959502)

-
Add a proper material to the skinned blendshape mesh and perhaps a standard Phong material to the dummy object. Click the
**
MAT.ED
**
 icon from the Crytek shelf to add a new material group, then add the shaders you have created. A dx11Shader has been added for the "sdk_player_head" mesh and a standard Phong for all the rest. The dxShader will be used later for the wrinkle maps in the wrinkle map tutorial for CRYENGINE.

![Image](https://www.cryengine.com/docs/static/attachments/44959501)

##
Exporting

-
Make sure you have saved the Maya scene (if you haven't already) before the next step. Press the
**
EXPORT
**
 icon in the Crytek shelf and export both cryExportNodes:

![Image](https://www.cryengine.com/docs/static/attachments/44959500)

Pay special attention to/from what frame you export your "*.SKIN" and "*.CHR" files. Rewind your Maya timeline to the frame where your bind pose is.
In our case we bound the geometry to the skeleton in Frame 0.

-
In the
**
Animation Export
**
 tab add a new animation for export. Type in a name for the animation (that will be displayed in CRYENGINE), plus the start and end frame positions. Then point the Exporter to the root node of the skinned character: this is the "root" joint in our case - you may also want to manually add the export folder (this should be a sub-folder of
`
**
YOUR_PROJECT_FOLDER\Animations\...
**
`
).

Finally, press
**
Export all Anims
**
.

**
Note:
**

**
Export Selected Anims
**
 will show up if you have an animation selected!

![Image](https://www.cryengine.com/docs/static/attachments/44959499)

The animation named "
**
default
**
" is the standard animation and will be played automatically in the Sandbox Editor (i.e. when you add this character as "AnimObject" entity).

-
There are 4 files you have exported: a *
**
.CHR
**
 file, a *
**
.SKIN
**
 file the intermediate animation *
**
.I_CAF
**
 file and perhaps the CRYENGINE *
**
.MTL
**
 material file.

![Image](https://www.cryengine.com/docs/static/attachments/44959498)

Now we have successfully exported out our assets, it's time to move to the CRYENGINE portion of this tutorial.

[![Image](https://www.cryengine.com/docs/static/attachments/24151097) Tutorial - Animated Blendshapes - CRYENGINE 5.5.2](/docs/static/engines/cryengine-5/categories/23756816/pages/24285808)

[Tutorial Files](#tutorial-files)
[Setup Your Content In Maya](#setup-your-content-in-maya)
[Exporting](#exporting)
