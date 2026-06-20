# Reset Transformations

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23307987
- Page ID: 23307987
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Basics (animated) > Rigging (animated) > Reset Transformations
- Parent: Rigging (animated)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934054)

### "Zeroing Out" Transform Values - Why and How

All control objects in rigs should have their transform values 'zeroed out' before you create the rig. In other words, the numeric X, Y, and Z position and rotation values they have. Generally these values depend on the parent object. The child object's position and rotation is based on a relative change from the parent object. For example, let's say you have two objects, A and B. Object A is at X `10 units, and object B is at X` 15 units. If neither object has a parent, then the world is the parent and the X value shown for A is 10, and the X value shown for B is 15. These values are relative to the world origin (0,0,0).

Now suppose you link object B to object A. At this point, object B is the child of A. Object B's values will be relative or offset from those of object A. In this case, A's X position still equals 10. But object B's X position now displays as 5, because it is +5 units away from its parent.

We can use this information to our advantage. If you are in Move or Rotate mode and choose Parent as the reference coordinate system, then Transform type-in values will show you the values in parent space. In fact, these values will be identical to the ones you will see in the Motion panel and in Track View when you are animating.

Most animators prefer to have everything in Track View start at 0,0,0. However, if you take the above example, you'll note that its position is not 0,0,0 but three other numbers. You need to zero it out.

By zeroing out an object's position, the animator can reset that position by entering zeroes while using Track View or the Motion panel. And values relative to zero are easier to read in the Track View Curve Editor.

The way to do this is to create a helper object aligned to the object whose transform values you want to zero out. By inserting the helper into the hierarchy, and linking the real object to the helper, the real object's values will be zero because they are not offset from those of the helper.

### 'Zeroing Out' a controller

1. Create a new Point Helper object. Set the options to have only a Center Marker and Axis Tripod.

2. Align the helper to the XYZ Pivot Point (not Center) position of the controller you wish to zero out.

3. Name this controllerZeroHelp, where 'controller' is the name of the controller.

4. Link controllerZeroHelp to the parent of the controller you want to zero out.

5. Link that controller to controllerZeroHelp.

6. To make it easier to deal with, turn off the Axis Tripod option for the helper, leaving on the Center Marker only.

7. Now select the controller you want to zero out. On the Main toolbar, choose Parent as the reference coordinate system. The values are all zero. The same values will be shown in the Motion panel and Track View.

8. You can repeat this process for all the other control shapes.

#### Automating the process with zeroOut.mcr

There is a macro script for max to allow you to select many controllers and zero them all out with the click of a button/keystroke. It is attached below.

[zeroOut.mcr](/docs/static/attachments/23994292)
