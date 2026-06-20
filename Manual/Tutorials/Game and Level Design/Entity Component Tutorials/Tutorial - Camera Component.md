# Tutorial - Camera Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28181775
- Page ID: 28181775
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Camera Component
- Parent: Entity Component Tutorials

## Content

##
Using the Camera Component

This tutorial is going to explain the camera component. The camera component adds a camera to the scene which then can be activated from either C++/C# or
[Schematyc](../../../Editor%20Tools/Deprecated%20Tab/Schematyc%20Editor%20(Experimental).md)
. I would also recommend seeing the
[Entity Components](../../../Entities%20and%20Tools/Entity%20Components.md)
 documentation to understand or look up what the specific attributes do.

-
First create a new entity with a camera component. Click on the "Empty Entity" button in the "Create Object" panel and place the entity in the level. After that select the entity and click on the "Add Component" button in the "Properties" panel and select the camera component.

*
Creating an empty entity and adding the camera component to it.
*

![Image](https://www.cryengine.com/docs/static/attachments/28254508)

-
The camera component now exposes all attributes and we can start adjusting them. You should also see another component after adding the camera component. That component is the audio listener of the camera and can be ignored in most cases. Now we can change the field of view of the camera or change offset of the near plane, which is responsible for culling the objects too close to your camera. To change any value, click in the attribute box and either drag the value or type in the wanted value.

*
Changing the field of view.
*

![Image](https://www.cryengine.com/docs/static/attachments/28254509)

-
Above the "Field of View" attribute is the "Active" attribute which determines if the camera should be active by default. An important thing to note here is that only one camera can be active at the same time, which means if someone creates a new camera that one will be used by the engine. The camera component can also be moved or rotated. To do so, adjust the values of the "Transformation" attribute.

*

Changing the camera transformation.
*
![Image](https://www.cryengine.com/docs/static/attachments/28254510)
