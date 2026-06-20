# Tutorial - Using Edit Normals for better Normal Maps

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308608
- Page ID: 23308608
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Texturing > Tutorial - Using Edit Normals for better Normal Maps
- Parent: Tutorial - Texturing

## Content

##
Using Custom Normals

By editing the geometry normals we can achieve various effects and even save a normal map channel that can be used for something else later on.

Basically we want to fake rounded up edges by adjusting the normals without using a normal map

In real life architectural and man made objects, such as buildings, boxes, and mechanical have hard edges with flat surfaces. Please look at the image below where a pedestal is displayed.

[Image: /docs/static/attachments/23999878]

In the image below we have a low poly box that has an normal map applied in which chamfered edges from a high poly box were rendered out.

This box could have been also created without using a normal map at all, with no visual difference.

[Image: /docs/static/attachments/23999879]

[Image: /docs/static/attachments/23999880]

To achieve that we need to create a box and then chamfer it's edges.

The box has hard edges and the corners are not looking rounded as the vertex normals are not edited yet.

[Image: /docs/static/attachments/23999881]

To get all the corners smoothed, we assign one smoothing group to the whole object.

During that process all normals get merged together and give us a very smooth shading, but this is not the result we are looking for since you can see the flat areas are displaying a smooth gradient instead of being flat.

[Image: /docs/static/attachments/23999882]

To get the flat faces looking flat we need to run the script, which you can
get here:
[/docs/static/attachments/23999873](
GetVertNormalsFromFace_0_2.ms
)

Don't forget to have everything assigned to one smoothing group before you apply the script to your object.

For best practice and making it easier it's better to assign the script to a shortcut.

[Image: /docs/static/attachments/23999883]

After applying the script we get the desired result, we have smooth corners, but the faces that are flat look like it.

The geometry didn’t change and there is no Normalmap applied, but the edges look round and the same as we had with our normal map applied.

[Image: /docs/static/attachments/23999884]

To give us a better understanding of what happened, we have prepared following images. To make our vertex normals visible we have to apply the 'Edit Normal' in 3DS Max.

In this image this is how our normals looked once we applied on smoothing group. What happened is that it took all the vertex normals and averaged them. In the process we got smooth corners but lost the flatness of the straight faces.

[Image: /docs/static/attachments/23999885]

In the second image displays how our vertex normals look after we applied our script. What the script did is putting each vertex normal to 90 degrees.

The roundness of the corners come now from the interpolation between both vertex normals.

[Image: /docs/static/attachments/23999874]

Here's an image, making it visible.

[Image: /docs/static/attachments/23999875]

If the shading of your object looks broken, something might be wrong with normals. To fix that simply apply the 'Edit Normals' modifier, select all the normals and rest them.

To export the asset and get it look exactly the same when it's imported in to CRYENGINE, you need to tick on the check box
**
 "custom normals"
**
in the CryExport options.

[Image: /docs/static/attachments/23999877]

[Image: /docs/static/attachments/23999876]

There are some pros and cons to be aware of though:

-
**
Pros:
**
 You save a normalmap, you can avoid unique mapping, it's a timesaver, less normals, higher res looking mesh

-
**
Cons:
**
You use more polygons, the normals have to be reset and then reforced again if the mesh changes

##
See also

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308611](
Tutorial - Preparing Geometry Normals to optimal results in Xnormal
)
