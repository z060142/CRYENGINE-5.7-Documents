# Exporting using Crytek Shelf in Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25531270
- Page ID: 25531270
- Breadcrumb: CRYENGINE - Getting Started > Installing CRYENGINE > CRYENGINE Plugins and Tools > Installing the Maya Tools > CRYENGINE User Interface in Maya > Exporting using Crytek Shelf in Maya
- Parent: CRYENGINE User Interface in Maya

## Content

##
Overview

This section describes the general overview of the export process
from Maya into the CRYENGINE using the
Crytools
 that are available.

##
Maya Object Export

The most important thing to keep in mind while preparing for export are naming conventions. If the described objects are not named correctly then the exporter will not work. Also, since the position of up-axis in Maya is different than the CRYENGINE, the exporter will compensate by swapping the values accordingly.

**
To export an object from Maya:
**

-
Create a group called
**
cryexportnode_@,
**
and replace  the '
**
@
**
' with the filename that you want to export.

*
Pic1: Naming an object correctly

![Image](https://www.cryengine.com/docs/static/attachments/25503330)
*

-
Create a group under the
**
cryexportnode,
**
and name the new group '
**
#_group
**
' where you can replace the '
**
#
**
' with the name of the model that you want to export.

-
Now, group the meshes to the group that you just named '
**
#_group
**
'.

*
Pic2: Creating a group
*

![Image](https://www.cryengine.com/docs/static/attachments/25503331)

-
Click the
**
Export
**
 button on the
**
Crytek
**
 toolbar to open the
**
Crytek Export
**
 dialog, and then click the
**
Add Attributes
**
 button. By clicking this you will add various options to shaders, such as joints and meshes.

*
Pic3: Attributes added
*

![Image](https://www.cryengine.com/docs/static/attachments/13271328)

![Image](https://www.cryengine.com/docs/static/attachments/13271329)

-
Select the 'cryexportnode' group.

-
Select the file type from the drop-down menu that appears in the
**
Node Options
**
 section. You can also find this drop-down menu in the
**
Extra Attributes
**
 section in Maya's Attribute Editor.

Make sure you have selected the Parent tree node (in our case,
**
cryexportnode_@
**
) to enable the properties options under the Node Options.

*
Pic4: Export window
*

![Image](https://www.cryengine.com/docs/static/attachments/25506985)

-
Click the
**
Export
**

**
Selected
**
button on the
**
Crytek Export
**
 window.

An example Maya scene with the hierarchy setup for the static geometry exporting can be downloaded here:
**
[statictest.mb](/docs/static/attachments/13271330)
**
.

##
Maya Bone Export

With a character model at hand, you should be ready for rigging. For this tutorial, we will use a standard humanoid figure.

**
To export a bone structure from Maya:
**

1. Parent the physicalized mesh to the joints as depicted below.  You can also create one by adjusting very basic polygons surrounding your skeleton. Once finished, make sure you are blocking out your skeleton, and parent these new physics proxies to the skeleton.

Given that Maya does not allow spaces in names you can use a double underscore (__) as a space, this way the RC will convert it automatically when the character is exported.

*
Pic5: Character model in Maya
*

![Image](https://www.cryengine.com/docs/static/attachments/13271331)

-
Create a group called '
**
cryexportnode_@
**
',
**

**
and replace  the '
**
@
**
' with the filename that you want to export.

-
Create a group under the '
**
cryexportnode
**
', and group the
**
bones
**
 to the
**
cryexportnode
**
.

-
Now, create a group and name it '
**
#_group
**
', and replace
**
#
**
 with the name of the mesh to export.

-
Group the node which we created in above step to the
**
cryexportnode
**
.

-
Now, bind all of the
**
skin
**
 geometry to the skeleton.

*
Pic6: Skin geometry bound to skeleton

*
![Image](https://www.cryengine.com/docs/static/attachments/25503332)

-
Ensure you have bound the skin and the bones so that when you animate a joint the skin is animated relative to it.

Be sure that your workplace has been set to the CRYENGINE directory. For example
*
C:\CRYENGINE\GameSDK\Objects\mayaTest\animation\
*
 would be where you are saving and exporting to.

-
Click the
**
Export
**
 button on the
**
Crytek
**
 toolbar to open the
**
Crytek Export
**
 window.

-
In the Crytek Export window, click the
**
Add Attributes
**
 button. You can now notice that all your shaders have been added with a new property in the
**
Extra Attributes
**
 section. And now would be a good time to go back to your Physics shader and change its property to
**
ProxyNoDraw
**
. On your joints (under
**
Extra Attributes
**
), you will also notice new values labelled
**
Spring
**
,
**
Spring Tension
**
 and
**
Damping
**
. CRYENGINE will later use these values to limit the joint's rotation.

*
Pic7: ProxyNoDraw and other Extra Attributes

*
![Image](https://www.cryengine.com/docs/static/attachments/13271329)

![Image](https://www.cryengine.com/docs/static/attachments/13271328)

-
Select the 'cryexportnode' group, and then select the
**
Character (.CHR)
**
 file type from the drop down that appears in the
**
Node Options
**
 section. You can also find this drop-down in the
**
Extra Attributes
**
 section in Maya's
**
Attribute Editor
**
.

-
Ensure the
**
Do Not Merge
**
 option is checked, and then click the
**
Export
**
 button in the
**
Crytek Export
**
 window.

*
Pic8: Exporting a character
*
*

skeleton (*.chr) and its skinned meshes (*.skin)

*
*
![Image](https://www.cryengine.com/docs/static/attachments/25503333)
*

For more information on the character pipeline, please refer to this section for more information:
**
[Character Authoring in Maya](../../../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/Animated%20Geometry/Character%20(animated)/DCC%20Setup%20(animated)/Character%20Authoring%20in%20Maya.md)
.
**

Also you must ensure that Maya exports its animations at 30 fps. This can be changed under
**
Window -> Settings/Preferences -> Preferences,
**
and then navigate to
**
Settings
**
 group in the list, and on the right hand side, under the
**
Working Units
**
 set the
**
Time
**
 setting to
**
30fps
**
 and then click
**
Save
**
.

[Maya Object Export](#maya-object-export)
[Maya Bone Export](#maya-bone-export)
