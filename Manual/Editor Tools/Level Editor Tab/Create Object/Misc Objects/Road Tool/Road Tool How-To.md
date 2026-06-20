# Road Tool How-To

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966522
- Page ID: 44966522
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Misc Objects > Road Tool > Road Tool How-To
- Parent: Road Tool

## Content

### Creating a Road

Navigate to **Create Objects → Misc → Road**. As with all of the tools in the ** Misc**category, click to activate it.

With the **Road Tool** selected, click on the terrain to place the starting point, which is the first key point of the road.

Continue clicking to place a series of points that will make up the road. The more points that are placed, the greater the degree of control over the general direction, curvature, and height of the road.

![Image](https://www.cryengine.com/docs/static/attachments/44966525) *Road in progress*

For now, simply make sure to place points at varying heights and don't worry about empty or missing terrain underneath the path of the road.

![Image](https://www.cryengine.com/docs/static/attachments/44966526) *Road completed*

To set the last point, **double click** the desired spot.

### Material Setup

#### Material Settings for Roads

Roads are basically decals placed along a spline, so the material setup is fairly similar, with a few additions.

The material must use the [Illum Shader](../../../../../Graphics%20%26%20Rendering/Shaders/Shaders%20in%20CRYENGINE/Shader%20Reference/Illum%20Shader.md). It should also use the Decal and Vertex Colors check-boxes in the Shader Generation Params:

![Image](https://www.cryengine.com/docs/static/attachments/44966527) *Vertex Colors and Decal selected*

![Image](https://www.cryengine.com/docs/static/attachments/44966528) | ![Image](https://www.cryengine.com/docs/static/attachments/44966529) | ![Image](https://www.cryengine.com/docs/static/attachments/44966530)
--- | --- | ---
Decal + Vertex Colors Enabled | Vertex Colors Disabled | Decal + Vertex Colors Disabled

As shown above, using both Decal and Vertex Color options allows for a nice blend with the terrain.

- Decal: Activating this allows the alpha blending on the sides of the road, which comes from the Alpha channel of the Diffuse texture.
- Vertex Colors: Activates a blend fade-out at each end of the road. This is a 100% to 0% fade-out over the length of the final step. Textures/Alpha channel has no influence on the fade-out.

While setting the material Opacity value to 99% or less will also activate the alpha blending, providing get much more control over the material by setting it to 100% and then using the Decal parameters.

#### Applying a Material to the Road

Up until now, the road has only shown its spline helper on top of the existing terrain texture.

To set a material, select the road entity and on the Properties panel, click the **Material** field under the ** General** section.

![Image](https://www.cryengine.com/docs/static/attachments/44966531) *Material field*

After selecting the material, click the **Assign Material to Selection** button (or ** right click** and ** Assign To Selected Objects**).

![Image](https://www.cryengine.com/docs/static/attachments/44966532) *Assigning the material*

The texture will now be applied on to of the terrain texture. The texture is always projected on the surface below the geometry that defines the road. Thus, the road doesn't need to be perfectly aligned on top of the terrain.

The road segments between the key points try to smooth the bends in the road to creating a more realistic look.

### Modifying a Road

After the road has been placed, it can be easily modified with a selection of tools.

Function | Description
--- | ---
**Shape Editing** | **Edit** will allow to modify, add (** CTRL + LMB** on a line) or delete (** double-click** on a point) points on the line of the road shape.
**Angle** | Sets the angle of the road per point.
**Width** | Sets the width of the road per point.
**Split** | Splits the road at the point on which is clicked.
**Merge** | Merges two roads. Roads can only be merged at either start or end nodes. To merge two roads, select the merge button, then select the start/end node of the first road and finally select the start/end node of the second road it needs to be merged with.
**Align Height Map** | Will modify the terrain geometry based on the shape of the road and its border width parameter.

Click **Edit** under**Spline Operators** in the** Properties** of the road.

![Image](https://www.cryengine.com/docs/static/attachments/44966533) *Edit Spline button*

Every key point on the road can now be edited.

When the Edit mode from above if active, It is also possible to snap the individual points to the terrain the same way as with objects: by clicking **Ctrl + Shift + LMB** on any point on the terrain.

The X, Y, or Z positions can be changed separately, X and Y together, or the key point can be moved on top of the terrain. For this, choose one of the axis lock modes in the toolbar.

![Image](https://www.cryengine.com/docs/static/attachments/44966534) *Z Constraint button*

Now, click a key point of the road and drag the point to its new position. Choosing the **Lock on Z Axis** mode makes it possible change the height of this key point to manually smooth the road, if the particular section is too steep.

![Image](https://www.cryengine.com/docs/static/attachments/44966535) *Drawing a road*

With**Align Height Map** and by modifying the key points, the road can be placed exactly where it needs to be.

![Image](https://www.cryengine.com/docs/static/attachments/44966536) *Height map aligned*

In **Edit** mode, it is possible to select individual points of the road. Deselecting ** Default Width** will allow typing a specific width for the road at that point in the type in box below.

#### Splitting Roads

There may be some instances where a road needs to be split into multiple segments. This can be easily achieved by using the **Split** function in the Road entity's ** Properties**.

Select the road that needs to be split. Now activate the **Split** function in the road tool's properties.

![Image](https://www.cryengine.com/docs/static/attachments/44966537) *Road edit mode*

The spline keys will change to a pink color to signify they're in **Edit** mode; otherwise they'd be colored green.

With the split function activated, select one of the keys nearest to where the road needs to be split.

![Image](https://www.cryengine.com/docs/static/attachments/44966538) *Road split*

Now the road has been split and a new instance of the cut-off road is created.

The new road ends abruptly because the final spline key along that road is positioned right near the second last one, thus ending the road fade-out early.

Go into **Edit** mode on the newly created road and drag the final spline key over the top of the other road to blend them nicely together.

![Image](https://www.cryengine.com/docs/static/attachments/44966539) *Two roads combined*

[Creating a Road](#creating-a-road)[Material Setup](#material-setup)[Modifying a Road](#modifying-a-road)
