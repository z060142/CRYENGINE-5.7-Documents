# Tutorial - Environment Probe Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28181741
- Page ID: 28181741
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Environment Probe Component
- Parent: Entity Component Tutorials

## Content

##
Using the Environment Probe Component

In this tutorial we are going to explain the environment probe component and what it's for. With Environment Probes you have the ability to place cubemaps easily throughout a level just as you would a light. It is very useful especially with reflective materials because it will automatically assign the cubemap to anything within its radius.  I would also recommend seeing the
[/docs/static/engines/cryengine-5/categories/23756816/pages/28180907](
Entity Components
)
 documentation to understand or look up what the specific attributes do.

To explain the environment probe component we are going to work in the Rolling Ball template.

First, we are going to delete the already existing environment probe component in the Rolling Ball level. To find the already existing entity go to the Level Explorer and double click on the "EnvironmentProbe1" entity. If you can't find the Level Explorer go to
**
Tools -> Level Editor -> Level Explorer
**
. Press the
**
Delete
**
 key on your keyboard or right click on the entity in the Level Explorer and click on the delete option.

*
Deleting the already existing EnvironmentProbe1 entity in the Rolling Ball template.
*

[Image: /docs/static/attachments/28254261]

*
After deleting the environment probe component.
*

[Image: /docs/static/attachments/28254262]

As you can see the shadows are now really black and rough. So this might already show what the environment probe is for, it generates a cubemap of the scene and enables the Physically Based Shading. It's also used for reflection on reflective materials in your scene. Now we are going to create an empty entity and add a new environment probe component to it. To do so click on the "Empty Entity" button in the "Create Object" panel and place the entity in the level. After that select the entity and click on the "Add Component" button in the "Properties" panel and select the environment probe component.

Creating an empty entity and add the environment probe component to it.

*
[Image: /docs/static/attachments/28254264]
*

After adding the component you can a box around the entity, that's the visual representation of the area where the environment probe will be active. First, we should expand the size of the effective range of the environment probe, adjust the values of the "Box Size" attributes in the properties inspector of the entity and change the box size to something bigger.

Changing the box size of the Environment Probe Component.

[Image: /docs/static/attachments/28254269]

But the shadows still didn't change even after changing the box size. That's because the cubemap wasn't generated yet, to do so click on the "Generate" button under the "Generation Parameters" in the properties inspector. After the generation is done the lighting is now physical based and you should see smoother shadows in the area of your environment probe.

*
Level after generating the cubemap.
*

[Image: /docs/static/attachments/28254268]

Now you can start to play around with the attributes of the components and adjust for example the color of the shadows. Just click on the color field next to the color attribute in the inspector and select the color you like.

*
Changing the color of the environment probe component.
*

[Image: /docs/static/attachments/28254273]
