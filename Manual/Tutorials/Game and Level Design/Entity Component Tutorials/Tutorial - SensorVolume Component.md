# Tutorial - SensorVolume Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28181813
- Page ID: 28181813
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - SensorVolume Component
- Parent: Entity Component Tutorials

## Content

##
Using the Sensor Volume Component

This tutorial will help you in setting up a sensor volume component. The sensor volume can also act as a trigger, whenever another sensor volume hits or passes the current sensor volume, it will execute an event trigger. For example, it can be used to create a door trigger whenever a player walks into that sensor volume, the door could open or close on contact. It is recommended to refer the Entity Components - Components Panel documentation to understand or look up the behavior of specific attributes.

##
To use a Sensor Volume Component

In this tutorial, we are going to create a new entity and add a sensor volume to it.

-
Open a level in the CRYENGINE Editor, and then click on the
**
Empty Entity
**
 icon in the
**
Create Object
**
 panel to place an empty entity in the level.

-
Select the entity and click on the
**
Add Component
**
 button in the
**
Properties
**
 panel, and then select
**
SensorVolume
**
 option.

[Image: /docs/static/attachments/28254511]

-
Now, you can see the Entity component has a shape assigned to it. This shape will act as a trigger area for that component. You can switch between a box or a sphere by clicking on the
**
Shape
**
 attribute and then select the desired shape. You can also modify the size or radius of the shape using the Size attribute box.

[Image: /docs/static/attachments/28254512]
 |
[Image: /docs/static/attachments/28254513]
 |

-
You need to add tags to the SensorVolume.
**
Tags
**
 are labels that you can set to your sensor volume to assign more attributes. For example, you don't want to receive an event every time something triggers the sensor volume, you maybe just want to only listen to a tagged player.

-
To add
**
Tags
**
 to the SensorVolume, click on the
**
Attributes
**
menu and then select
**
Add
**
 in the context menu. After that, you should be able to see a new attribute field. Now, you can select a predefined tag that needs to be assigned to this sensor volume. You can have as many tags as you desire.

[Image: /docs/static/attachments/28254514]
 |
[Image: /docs/static/attachments/28254515]
 |

The Tags works similar to a
**
Listener
**
 attribute. The Listener determines the attribute that it needs to listen which means if another sensor volume with a defined tag makes a contact with the current sensor volume you are going to receive an event. For example, you have set a campfire and you want to only listen to entities that are flammable. You can have multiple listeners or none if you don't want to receive any events.

You can also have multiple sensor volumes with different attributes on the same entity.
