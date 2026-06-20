# Tutorial - Fog Volume Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28181744
- Page ID: 28181744
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Fog Volume Component
- Parent: Entity Component Tutorials

## Content

##
Using the Fog Volume Component

In this tutorial, we are going to explain the fog volume component and how to set it up. The fog volume creates fog in a specific area. I would also recommend seeing the
[Entity Components](../../../Entities%20and%20Tools/Entity%20Components.md)
 documentation to understand or look up what the specific attributes do.

First of all, we have to create a new empty entity and add a fog volume component to it. Go to the "Create Object" panel and click on the "Empty Entity" button and place the entity in the level. Select the entity and click on the "Add Component" button the "Properties" panel and search for the fog volume.

*
Creating the entity and add the fog volume component to it.
*

![Image](https://www.cryengine.com/docs/static/attachments/28254274)

There should be now a small fog volume by the entity. To see the fog volume better we are going to make the area of effect bigger, to change the size of the fog volume go to the "Size" attribute and adjust the values right next to it. It's also possible to change the shape type of the volume between "Ellipsoid" and "Box". To change the type click on the button right next to the "Type" attribute, which opens a drop-down list where you can choose.

*
Changing the size and type of the fog volume.
*

![Image](https://www.cryengine.com/docs/static/attachments/28254275)

As you can see now the fog covers the box size, but we can't see our entities anymore since the fog is too thick. To change that, adjust the "Global Density" attribute of the component, which defines the thickness of the fog.

*
Changing the density of the fog.
*

![Image](https://www.cryengine.com/docs/static/attachments/28254276)

Now we can see the level again but the fog is thicker on the right side, that's because the "Height Falloff Scale" attribute is 1 by default. Changing it to 0 will remove the falloff and the fog is the same density everywhere. It's also possible to change the color of the fog or to use the global fog color defined by the
[Environment Editor (Old as of 26/2)](/docs/static/engines/cryengine-5/categories/23756816)
. Just click on the color field right next to the "Color" attribute and pick any color.

*
Setting the "Height Falloff Scale" to 0 and changing the fog color.
*

![Image](https://www.cryengine.com/docs/static/attachments/28254277)
