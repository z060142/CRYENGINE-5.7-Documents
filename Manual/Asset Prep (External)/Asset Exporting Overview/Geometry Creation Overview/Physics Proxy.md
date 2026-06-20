# Physics Proxy

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215358
- Page ID: 26215358
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Physics Proxy
- Parent: Geometry Creation Overview

## Content

[Image: /docs/static/attachments/29934005]

##
Overview

##
Sections

The physics proxy is the geometry that is used for collision detection. It can be part of the visible geometry or linked to it as a separate node. Usually the physics proxy geometry is a simplified version of the render geometry but it is also possible to use the render geometry directly for physics. However, for performance reasons the collision geometry should be kept as simple as possible since checking for intersections on complex geometry is very expensive, especially if it happens often. A physics proxy is set up in the DCC tool exclusively. The only setup needed in Sandbox is assigning the surface type.

[#sections](
Sections
)
[#general-setup-in-dcc-tools](
General Setup in DCC Tools
)
[#current-allowed-proxy-settings](
Current Allowed Proxy Settings
)
[#level-of-detail-settings](
Level of Detail Settings
)
[#complexity-of-geometry](
Complexity of Geometry
)
[#linking-objects-to-simplify-export](
Linking Objects to Simplify Export
)
[#setup-in-sandbox](
Setup in Sandbox
)
[#debugging](
Debugging
)

##
General Setup in DCC Tools

##
3ds Max

In 3ds Max you need to assign a separate sub material ID for the proxy. Furthermore, make sure that all faces of your proxy are in smoothing group one. The physics proxy is configured in the shader settings in the 3ds Max material editor. The physics properties can only be changed here and not later in Sandbox. If you want to change the physics settings, you need to re-export your object. Physicalization is enabled with the checkbox
Physicalize
 in the CryShader
Physicalization
 panel. If physicalization is disabled, all entities can pass through the object.

The screenshot below shows a physics proxy surrounding a standard render mesh.

[Image: /docs/static/attachments/35400698]

##
Using Primitives

CRYENGINE will automatically try to replace physics proxies with parametric primitives by comparing the proxy geometry against the supported primitive shapes and approximating the potential primitive within some calculative limits. The shape is generated around the general bounding box of the geometry and uses the original pivot point to attempt to rotate the primitive to match the geometry as good as possible.

Primitives are a lot more efficient performance-wise than custom collision geometry (one single face of custom geometry is as expensive as a single primitive), so it is important to use them as much as possible.

It is possible to explicitly specify a collision primitive that should be used. In this case the engine will replace the physics proxy by the specified primitive. In 3ds Max the primitive can be specified in the
*
User Defined Property
*
 dialog of a node. The following primitive tags are available:

-
nonphysical (use only with characters that have no separate phys skeleton).

-
box.

-
sphere.

-
capsule.

-
cylinder.
[Image: /docs/static/attachments/35400697]

*
Box, sphere, capsule and cylinder
*

##
Maya

1. Create a group called 'cryexportnode_@' replacing the '@' with the filename to export to.

[Image: /docs/static/attachments/35400696]

2. Create a group under the 'cryexportnode'.

3. Name the new group '#_group' replacing the '#' with the name of the model you want to export.

4. Group the meshes to the group you created in step 3.

[Image: /docs/static/attachments/35400695]

5. Group the physics mesh to the group you created in step 3.

[Image: /docs/static/attachments/35400694]

6. Create a new phong material named 'proxy'.

[Image: /docs/static/attachments/35400693]

7. Assign the new material to the physics mesh.

8. Be sure to add your material to the material group with the rest of your materials.

[Image: /docs/static/attachments/35400692]

9. Click the export button on the 'Crytek' toolbar to open the 'Crytek Export' dialog.

10. Click the 'Add Attributes' button

11. Modify the physics proxy material and set its physicalise flag to
Proxy No Draw

[Image: /docs/static/attachments/35400691]

12. Select the 'cryexportnode' group.

13. Select the file type from the drop down that appears in the 'Node Options' section. You can also find this drop down menu in the 'Extra Attributes' section in Maya's Attribute Editor.

14. Ensure the
Do Not Merge
 option is checked.

[Image: /docs/static/attachments/35400690]

15. Click the
Export
 button on the 'Crytek Export' dialog.

[Image: /docs/static/attachments/35400689]

An example Maya scene with the hierarchy setup for the static geometry exporting can be downloaded
[/docs/static/attachments/23994590](
proxytest.mb
)
.

##
Current Allowed Proxy Settings

The following physics proxy settings are available.

Value

 |
Entity/Player Interaction

 |
Details

 |

Default (None)

 |
Entities are blocked

 |
The render geometry is used as physics proxy.

This is expensive for complex objects, so use this only for simple objects like cubes or if you really need to fully physicalize an object.

 |

Physical Proxy (NoDraw)

 |
Entities are blocked

 |
Mesh is used exclusively for collision detection and is not rendered.

 |

No Collide

 |
Entities can pass through object

 |
Special purpose proxy which is used by the engine to detect player interaction (e.g. for vegetation touch bending).

 |

Obstruct

 |
Entities can pass through object; AI View is blocked

 |
Used for
*
Soft Cover
*
 to block AI view (i.e. on dense foliage).

 |

These properties are assigned in the materials in each 3D package:

*
[Image: /docs/static/attachments/35400688]

Material Editor in 3ds Max.
*

[Image: /docs/static/attachments/35400687]

*
Extra Attributes tab in the material's attribute editor.
*

*
NOTE
*
*
: This attribute needs to be manually added through the exporter's "add attribute" button
*
.

The physics proxy is not allowed to have open edges. Open edges can confuse the physics engine and have a negative effect on performance. It is helpful to assign an extreme color (like a strong red) to the proxy in order to keep track of it.

##
Level of Detail Settings

Proxies are only created for LOD0. Every successive LOD will automatically take the proxy from LOD0. The same happens if different quality settings are used (e.g. Lowspec).

##
Complexity of Geometry

The physics proxies of environment objects (fences, crates, containers, trees, rocks, ladders, stairs, etc.) should be as simple as possible.

Avoiding geometric complexity for physics proxies is important to reduce redundant memory requirements and physics computations but also for making player movement smoother. The more complicated a proxy is, the more memory it will take and the more performance is lost when checking collisions against its polygons. This affects both single player and multiplayer, including the performance of a dedicated server. Besides the performance issues, a complex proxy with a lot of concavity increases chances that the player can get stuck or bounces undesirably against the proxy.

An ideal proxy is always a primitive (i.e. a box, a sphere, a capsule or a cylinder). CryENGINE recognizes primitives from meshes but the default tolerance is very low; in order to force the recognition, put the corresponding keyword ("box", "sphere", etc) into the node's user defined properties. Note, however, that meshes with several surface types cannot be turned into primitives. Primitives should be considered as an option even for more complex objects. In most cases it is preferable to have a multipart object (i.e. "merge nodes" off) with primitive parts instead of a single part mesh object.

The proxy is used for blocking character movement as well as first pass tracing of projectiles (bullets and decals). If a hit was detected against the physics proxy, projectile impact and decal locations are refined using the render mesh. The render mesh should be fully encapsulated by the physics proxy, so that the player camera does not intersect the render geometry and first pass projectile culling does not miss the physical part of the object even though it hits the visual part of the object. There is also support for creating a special raytrace proxy that, if provided, will be used for projectiles. This would then allow the main proxy to not have to encapsulate the render mesh and thus the proxy could be even simpler.

Simple objects like for example crates and fences can usually be approximated with a simple box which has 6 sides (12 triangles). The top of stairs should usually be simple ramps, resulting in just 2 triangles. More organic or irregularly shaped objects like rocks and trees can still be approximated with a fairly simple hull by allowing slight and acceptable inaccuracies between the render mesh and the physics proxy.

##
Linking Objects to Simplify Export

The physics proxy can be part of the render object (in 3ds Max as an Element) or as a separate object, linked to the render object.

##
Setup in Sandbox

In Sandbox you need to assign a surface type to your physics proxy in the Material Editor, as well as to your render geometry. The surface type gives information about sound and the particle effects of your surface.

You also need to assign a NoDraw shader in the material editor. Make sure that no textures are assigned to your proxy sub material. The physics proxy will never be rendered in the Sandbox Editor without debug view. Even if you assign an illum shader it will stay invisible.

To reload the physics proxy you need to reload your object, delete it, and undo delete.

##
Debugging

**
p_draw_helpers
**

```

Same as p_draw_helpers_num, but encoded in letters
Usage [Entity_Types]_[Helper_Types] - [t|s|r|R|l|i|g|a|y|e]_[g|c|b|l|t(#)]
Entity Types:
t - show terrain
s - show static entities
r - show sleeping rigid bodies
R - show active rigid bodies
l - show living entities
i - show independent entities
g - show triggers
a - show areas
y - show rays in RayWorldIntersection
e - show explosion occlusion maps
Helper Types
g - show geometry
c - show contact points
b - show bounding boxes
l - show tetrahedra lattices for breakable objects
j - show structural joints (will force translucency on the main geometry)
t(#) - show bounding volume trees up to the level #
f(#) - only show geometries with this bit flag set (multiple f's stack)
Example: p_draw_helpers larRis_g - show geometry for static, sleeping, active, independent entities and areas

```

Example picture without physics proxy visualization:

[Image: /docs/static/attachments/35400686]

The same object with physics proxy visualization:

[Image: /docs/static/attachments/35400685]

**
p_proxy_highlight_range
**

```

Changes the triangle count threshold of the physical debug view for marking proxies in red.

Usage: p_proxy_highlight_range [number]

Number - Any positive integer.

```

**
e_PhysProxyTriLimit
**

```

Maximum allowed triangle count for phys proxies

```

If you notice your assets are wrapped in a message stating "No Collisions, Proxy Too Big!" then the physics proxy for that asset is over the triangle count specified in
e_PhysProxyTriLimit
.

It will look something like this:

[Image: /docs/static/attachments/35400684]
