# Audio & Merged Meshes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964912
- Page ID: 44964912
- Breadcrumb: Audio > Audio Overview > Audio & Merged Meshes
- Parent: Audio Overview

## Content

[Image: /docs/static/attachments/44964913]

##
Sounds and Merged Meshes

CRYENGINE allows the usage of
[/docs/static/engines/cryengine-5/categories/23756816/pages/24285889](
Merged Meshes
)
 for patches of vegetation. By default the Merged Mesh feature is disabled - this avoids unnecessary calculations when the feature is not required. In order for Merged Meshes to be calculated and therefore used with sound, the relevant CVar must be set in the
system.cfg
 file. To do this set the CVar
g_enableMergedMeshRuntimeAreas=1.

You can find more details about

[/docs/static/engines/cryengine-3/categories/1638401/pages/1605736](
Using Console and Config Files
)

by following the link.

##
The MergedMeshSurfaceTypes.xml

The Merged Mesh vegetation feature uses the Surface Type of the vegetation in question.

When entering a Merged Mesh vegetation patch the system looks up the Surface Type in an *.xml file named
*
MergedMeshSurfaceTypes.xml.
*
This *.xml file is located in: <
`
Game folder>\Assets\gamedata.pak.
`
Within this *.pak file, the MaterialEffects.xml file can be found in
`

`
`
Libs\MaterialEffects
`
.

Within this xml file you can specify an audio system
*
 Trigger
*
 and an audio system
*
RTPC
*
per surface
*
.
*

Once you enter a Merged Mesh vegetation patch, and based on its assigned Surface Type, the audio system
*
 Trigger
*
 defined in the MergedMeshSurfaceTypes.xml file will be executed and the audio system
*
 RTPC
*
 updated according to the density of the vegetation:

As opposed to audio during collisions through the vegetation.xml, audio for Merged Meshes is played on the entity that is moving through the patch of vegetation and therefore the
*
object_speed
*
 audio system
*
 RTPC
*
 of the entity can be set on the playing vegetation loop. This allows you to control the volume of the vegetation loop according to the density of the vegetation and the speed of the moving entity.

*
Pic2: specified the
*
audio system Trigger
*
 Play_p_veg_mm_grass
*

In the example above, which is taken from the
*
MergedMeshSurfaceTypes.xml
*
, we have specified the audio system
*
 Trigger
*
 Play_p_veg_mm_grass that will be executed when entering a patch of vegetation with the SurfaceType mat_grass. The audio system
*
 RTPC
*
 mm_grass_density is updated according to the density of the vegetation in question.

As soon as you enter the patch of vegetation the setup in your audio middleware should trigger a looping sound. Volume and other parameters can be altered, but this will depend on the connected Audio Middleware Controls, the mm_grass_density audio system
*
 RTPC
*
 and the object_speed audio system
*
 RTPC
*
.
