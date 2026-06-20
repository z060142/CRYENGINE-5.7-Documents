# Character Rigging Guidelines

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23307986
- Page ID: 23307986
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Basics (animated) > Rigging (animated) > Character Rigging Guidelines
- Parent: Rigging (animated)

## Content

[Image: /docs/static/attachments/29934056]

##
Basic Understanding

This tutorial is designed to outline the rules and guidelines for rigging characters to be exported to CRYENGINE. If you are working with
**
Biped
**
, please go to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23307988](
Biped Rigging
)
 tutorial, and if you are interested in character physics authoring, go to
[/docs/static/engines/cryengine-5/categories/23756816/pages/23307978](
Ragdoll
)
.

This tutorial is for people who are building new rigs, or troubleshooting.

##
The Guidelines

**
Check the character mesh before you start, make sure:
**

-
It has no transformations applied (position, rotation, scale), if so Reset XForm.

-
If the model was sculpted to match your existing skeleton, make sure it lines up and matches the joints!

-
The Cryskin and Skin modifier are used in 3ds Max to weight characters.

-
You may notice older assets use Physique.

-
You can use Physique, but understand that it will make it very painful to transfer weights in the future if the model changes.

-
Characters must be in their 'bind' pose, or the pose that is the reference pose for the skin weights.
Bones should have no scale applied to them.

-
There is a bug in Max where mirroring bones causes them to have a -100% scale: be on the lookout for this.

-
When you need to mirror, use the mirror function in Bone Tools, but be careful, this only mirrors bones, so mirror before you convert bones to edit poly.
No bones can be outside of the skeletal hierarchy, the exporter starts at one root bone and steps through all its children.

-
This also means no external bones can be constrained into the skeleton.

-
If you want bones to act like they are outside of the skeleton, you can change their transform inheritance in
**
Command Panel -> Hierarchy -> Link Info -> Inherit.
**

-
Once they are not inheriting transforms from their parents, you can them drive them with constraints as if they were outside the hierarchy.
The bones of the spine and head can match the orientations and names of the biped skeleton for lookIK to work but the names are defined in the chrparams file.

-
The names are
**
'Bip01 Head' 'Bip01 Neck' 'Bip01 Spine3' 'Bip01 Spine2'
**
.
If you want to have rig elements inside the hierarchy, keep them to the periphery and use the prefix '_' to comment them out of export.

-
The '_' prefix effectively comments an object, and all of it's children out on export.

-
If you must have them in the hierarchy, and they are exported into the engine, try not to have them be splines or shapes, convert them to polygons.

-
Keep in mind that any rig elements inside the hierarchy that are exported will be null bones in the engine, and take up memory/cpu time, so do this sparingly.
The Character must have a proper phys mesh.

-
Refer to
[/docs/static/engines/cryengine-5/categories/23756816/pages/23307978](
Ragdoll
)
 for information on setting up phys meshes.
**
The character must have the proper LODs:
**

-
LOD1, LOD2, LOD3.

-
LOD2 and LOD3 are stored in the MAX file with LOD0.

-
LOD1 is stored in the MAX file by itself with the suffix '
**
_LOD1
**
' because the physics data and skeleton in LOD1 is used for ragdoll physics.
If the LOD1 can be set as the LOD0 for lowspec systems.

-
The LOD1 mesh should have the flag '
**
LowSpecLod0
**
' set in its
**
User Defined Properties.
**
It is always a good idea to
 your bone rotations after you have set up your skeleton.

-
It is not mandatory, this is a hold over from high-end rigging practices, keep in mind that this adds a null bone into the rig, so export with 'ignore dummies'.
Collapse your list controllers! The exporter can sometimes have issues with list controllers.
