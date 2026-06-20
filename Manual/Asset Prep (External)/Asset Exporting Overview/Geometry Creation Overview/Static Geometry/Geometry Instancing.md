# Geometry Instancing

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29799646
- Page ID: 29799646
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Static Geometry > Geometry Instancing
- Parent: Static Geometry

## Content

[Image: /docs/static/attachments/29934002]

##
Overview

##
Sections

Please be aware that this feature natively does not work for consoles and as a result its overall usability is considered questionable.

Usually each separate mesh of a model results in an additional draw call for the engine. In order to reduce the number of drawcalls, the engine can make use of a hardware feature that is called 'geometry instancing'. By using this feature, the engine can combine identical meshes of a model and draw them in a single drawcall. Instancing is mainly useful for complex objects consisting of a lot of separate elements that have the same geometry but a different transformation.

[#sections](
Sections
)
[#general-setup-in-dcc-tools](
General Setup in DCC Tools
)
[#debugging](
Debugging
)

##
General Setup in DCC Tools

The engine can automatically determine when elements of an object can be instanced. However, there are a few rules that need to be followed or instancing will not be possible:

-
The meshes to be instanced need to have the exact same vertex coordinates and indices, the same UV coordinates, and the same material.

-
Only the transformation may be different. The Elements can be translated, rotated, and uniformly scaled.

-
Naming is not important.
[Image: /docs/static/attachments/35400749]

*
Fence consisting of instanced elements (instances are blue).
*

##
General Modeling Workflow Tips

-
Use the instance function to ensure identical mesh data.

-
Rotate and scale objects to obtain variation.

-
Do not apply a
*
Reset XForm
*
 on the instances because the vertex data will become different.

##
Setup in Sandbox

No special setup is required in Sandbox, just place your object as a brush or simple entity.

##
Debugging

**
r_GeomInstancing
**

```

Toggles HW geometry instancing.
Usage: r_GeomInstancing [0/1]
Default is 1 (on). Set to 0 to disable geom. instancing.

```
