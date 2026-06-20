# Clip Volume

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869891
- Page ID: 36869891
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Area > Clip Volume
- Parent: Area

## Content

##
Overview

Clip Volumes define geometric shapes that can restrict the influence of lights, cube maps, and fog volumes in the world. This feature is intended to replace the deprecated Light Boxes and Deferred Clip Shapes functionality.

We currently support generic geometric shapes as long as they are
**
water tight
**
. Note that in the following the term 'light' is used for both, lights and cube maps.

[Image: /docs/static/attachments/36849673]

*
Left: clip volume, right: Red light clipped by the volume
*

On CRYENGINE 5.6 and beyond,

-
**
View Dist Ratio
**
 is exposed for clip volumes to enable more efficient culling (this can be adjusted under the Clip Volume properties, pictured below).

-
New cvar
**
e_ClipVolumes
**
 is added to allow turning off Clip Volumes (mostly useful for debug purposes). This can be enabled or disabled by setting
**
e_clipvolumes
**
 to either of 0 or 1 via the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44967641](
Console
)
.

##
Properties

Property

 |
Description

 |

**
Filled
**

 |
Just for visibility in the editor this option defines if the area should be rendered as filled or not.

 |

**
Ignore Outdoor AO
**

 |
Ignores the outdoor
Ambient Occlusion.

 |

**
View Dist Ratio
**
 |
Defines the distance from which the Clip Volume can be seen.
 |

##
Clip Volume Editing

Clip Volumes can be created directly in the Editor by going to Operators in the Properties and choosing
**
Volume → Edit
**
. Any of the Shapes can be then picked.

As an alternative, Clip Volume geometry can also be loaded from CGF files via the
**
Load CGF
**
 button.

-
Once a Clip Volume has been defined via
**
Area -> Clip Volume
**
, be sure to close the tool from the top of the Viewport to prevent additional vertices from being added to the geometry.
[Image: /docs/static/attachments/44967986]

Clip Volumes need to be water tight and cannot overlap.

##
Restricting Lights to Clip Volumes

Lights can be associated with Clip Volumes by either placing the light directly inside the volume or by creating an Entity Link from the light to the Clip Volume.

Before with Light Boxes/Shapes, performing an entity link was a requirement, but with Clip Volumes this is optional and this makes setup much easier!

Once an association has been established, the
**
Affects This Area Only
**
 property on the light source will clip the light's influence to the geometry inside the Clip Volume.

One example could be with environment probes, if the global probe is set to
**
Affects This Area Only
**
 then the Clip Volume will occlude the ambient lighting:

[Image: /docs/static/attachments/44967989]

 |
[Image: /docs/static/attachments/44967990]

 |

Global Probe Affect This Area Only True
 |
Global Probe Affect This Area Only False
 |

When editing a shape or area, it is possible to snap a vertex to terrain or physicalized objects using
**
Ctrl + Shift + LMB
**
.

This is true for all Area objects, except Occluders.

##
Restrictions

-
The Clip Volume mesh needs to be watertight.

-
Clip Volume mesh
complexity has an impact on performance.

-
Each light can be linked to a maximum of two Clip Volumes.

-
Clip Volumes must not overlap.

-
For performance reasons, forward rendered objects perform the 'inside' test based on their pivot only.
[#properties](
Properties
)
[#clip-volume-editing](
Clip Volume Editing
)
[#restricting-lights-to-clip-volumes](
Restricting Lights to Clip Volumes
)
[#restrictions](
Restrictions
)
