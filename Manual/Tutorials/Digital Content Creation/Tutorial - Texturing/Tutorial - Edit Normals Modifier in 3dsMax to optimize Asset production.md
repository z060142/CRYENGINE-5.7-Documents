# Tutorial - Edit Normals Modifier in 3dsMax to optimize Asset production

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308607
- Page ID: 23308607
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Texturing > Tutorial - Edit Normals Modifier in 3dsMax to optimize Asset production
- Parent: Tutorial - Texturing

## Content

### Overview

Custom normals are a good way to control the smoothing of your lowpoly and/or to get around having to use a normalmap which results in less texture memory and way more detailed smoothing since it doesn't depend on the resolution of a normalmap.

In this example I want to use one smoothing group and still only have the chamfered edges of the cube to be smooth. The left cube uses standard normals, the right one custom normals.

![Image](https://www.cryengine.com/docs/static/attachments/23999870)

To adjust your normals simply use the "Edit Normals" modifier:

![Image](https://www.cryengine.com/docs/static/attachments/23999871)

The easiest way to get the result mentioned above is to select "Face" and then average all faces that don't belong to the chamfer. In this case that would be the 6 sides of the cube.

![Image](https://www.cryengine.com/docs/static/attachments/23999869)

Now there's no unwanted smoothing gradient along these faces since all their verts share the same normal. However the chamfer looks smooth.

To export your asset with custom normals simply tick the according box in the exporter window:

![Image](https://www.cryengine.com/docs/static/attachments/23999872)
