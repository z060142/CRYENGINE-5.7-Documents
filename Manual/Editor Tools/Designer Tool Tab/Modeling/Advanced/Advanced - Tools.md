# Advanced - Tools

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450455
- Page ID: 29450455
- Breadcrumb: Editor Tools > Designer Tool Tab > Modeling > Advanced > Advanced - Tools
- Parent: Advanced

## Content

## Overview

The Tools section shows the following tools:

![Image](https://www.cryengine.com/docs/static/attachments/28900727)

### LoopCut

The Loopcut tool can be used for cutting polygons by several loop edges in an intuitive way. This tool is only available to quad-shaped polygons.

#### How it Works

- Choose a loop or ring that you want to 'cut' by moving the mouse cursor over it. You'll see a purple line appear:
![Image](https://www.cryengine.com/docs/static/attachments/28900721)
- You can then hold **Ctrl** and scroll the mouse wheel to increase and decrease the number of cuts:
![Image](https://www.cryengine.com/docs/static/attachments/28900720)
- Press **LMB** and the cuts will turn orange, meaning that you can move them around if you want to:
![Image](https://www.cryengine.com/docs/static/attachments/28900726)
- Polygons crossed by loop edges will be cut as follows:
![Image](https://www.cryengine.com/docs/static/attachments/28900725)

#### On Boxes

Of course, this is also possible on boxes as they also have quad-shaped polygons:

![Image](https://www.cryengine.com/docs/static/attachments/28900724)![Image](https://www.cryengine.com/docs/static/attachments/28900723)![Image](https://www.cryengine.com/docs/static/attachments/28900722)

### Bevel

A bevel tool is to smooth edges of a shape. Most shapes in reality have not sharp but blunt edges, so applying the bevel to edges of a shape can give the world more realism.

*![Image](https://www.cryengine.com/docs/static/attachments/28900719)![Image](https://www.cryengine.com/docs/static/attachments/28900718)*

#### How it Works

You can use the bevel tool both with Edges and with polygons.

##### Edges

- First, select the edges you want to apply the effect to using the **Edge** button in the ** Selection** section. (Generally, this would be all the edges around the polygon you want to modify, but you can also apply the bevel effect to single edges.)
- Then, click the **Bevel** button.
- Thirdly, move the mouse up and down to determine the width of the bevel. Press **LMB** to confirm.
- After determining the width, you move the mouse up and down to determine the number of subdivide bevels. The more subdivide bevels, the smoother the bevel will be. Press **LMB** to confirm.

![Image](https://www.cryengine.com/docs/static/attachments/28900717)![Image](https://www.cryengine.com/docs/static/attachments/28900716)![Image](https://www.cryengine.com/docs/static/attachments/28900715)

##### Polygons

Making bevels using polygons is very similar to doing it using Edges, except that you click the Polygon button and select one or more polygons.

After that, you can continue from step 2 above.

If you want to move the mouse without subdivision or widening, move the mouse while holding the **Ctrl** key.

### Subdivision

Click the Subdivision button and the following options will appear in the Subdivision options:

*![Image](https://www.cryengine.com/docs/static/attachments/28900687)*

The buttons shown above do the following:

Button | Description
--- | ---
**Slider** | Changes the subdivision level of the mesh.
**Smoothing Surface** | Uses smooth shading on the produced mesh as opposed to the default flat shading.
**Freeze** | Applies the subdivision result to the mesh.
**Add** | Adds an edge set to be sharpened on subdivision.
**Delete** | Deletes and edge set.
**Delete Unused** | Deletes unused edge sets at a value of zero.
**Clear** | Clears all edge sets.

Apart from the buttons, there is also the Semi-sharp Creases panel, where you can see two columns:

Column | Description
--- | ---
**Name** | Name of crease set.
**Sharpness** | Intensity of creased edge set.

#### How It Works

- Make a Designer object with plenty of edges
![Image](https://www.cryengine.com/docs/static/attachments/28900686)
- Select it and move the slider to get the desired subdivision level.
*![Image](https://www.cryengine.com/docs/static/attachments/28900685)*
You'll see that there are still boxes around the object that corresponds to the original boxes of the Designer object. Right now, you can still change the subdivision level.
At this stage you can also smoothly shade the polygons of the object by ticking the box in front of **Smoothing Surface**.
This is similar to the way [Smoothing Groups](Advanced%20-%20Groups%20UV.md#Advanced-Groups%2FUV-SmoothingGroup) work.
- If you're satisfied with the subdivision level, you can click Freeze to confirm your choice:
*![Image](https://www.cryengine.com/docs/static/attachments/28900684)*

### Boolean

With the Boolean tool, you can modify one Designer tool object by using the shape of another.

In order to use this tool you need to select at least two Designer objects. These shapes need to overlap to be able to see the effect.

When you have selected the Designer objects, click the **Boolean** button and the following options will appear in the Boolean properties:

![Image](https://www.cryengine.com/docs/static/attachments/28900714)

These three options have different effects.

#### Union

The Union option merges together the Designer objects you have selected, resulting in them behaving as one object (with one Pivot etc.) Most importantly, union tool also merges the geometry surface/volume so both objects have a continuous surface. Any internal geometry is removed - you can see that if you delete some of the geometry of the new object.

![Image](https://www.cryengine.com/docs/static/attachments/28900713)![Image](https://www.cryengine.com/docs/static/attachments/28900712)

#### Subtract

Subtract takes the object you selected **first** and removes it, taking with it any part of the ** second** object that it overlapped. In the example below, the ** sphere** was selected ** first**:

![Image](https://www.cryengine.com/docs/static/attachments/28900711)![Image](https://www.cryengine.com/docs/static/attachments/28900710)

#### Intersection

The Intersection option only leaves the area where the objects overlap intact and removes the rest:

![Image](https://www.cryengine.com/docs/static/attachments/28900709)![Image](https://www.cryengine.com/docs/static/attachments/28900708)

### Slice

Makes a green line appear along which the Designer object will be cut. You can move this line with the standard translation modes. The green arrow marks in which direction some of the actions below will occur.

#### How It Works

##### Take Away

These two options simply remove one part on either side of the green line; **Front** takes the part on the side of the green arrow away and ** Back** the part on the other side.

Before/Front/Back![Image](https://www.cryengine.com/docs/static/attachments/28900669) **![Image](https://www.cryengine.com/docs/static/attachments/28900668)![Image](https://www.cryengine.com/docs/static/attachments/28900667)**

##### Split

These two options split the object in two, after which you can do different things with each half.

***Clip***

Separates the objects into two objects (you will see two Designer objects in the Level Explorer).

***Divide***

Adds a new edge along the green slice line. This means the polygons on each side of the line are now separate and can be manipulated (extruded etc.)

##### Alignment

Depending on which button (X, Y or Z) is pressed, the green arrow is aligned to this axis.

##### Invert

Points the green arrow in the opposite direction to where it is currently pointing.

### Mirror

With this tool, you can mirror a mesh along an arbitrary plane as well as its local X, Y or Z axis plane, making every action performed in one half happen in the other half as well.

When you click on the Mirror button, the following buttons appear underneath:

![Image](https://www.cryengine.com/docs/static/attachments/28900679)

Button | Description
--- | ---
**Apply** | Splits a mesh by the mirror plane and one half of the object to the other half and then starts the mirror editing.
**Invert** | Inverts the direction of the mirror plane, shown by the arrow direction changing after pressing this button.
**Center Pivot** | Moves the pivot position to the center of the bound box.
**Alignment** | Aligns the mirror plane by the X axis, Y axis or Z axis.
**Freeze** | After you finish mirror editing and freeze the current geometry, you should press this button. The mirrored part will then come to the general part and you can edit the part separately. (Only visible when the **Apply** button has been clicked.)

#### How it Works

- Create a Designer object
![Image](https://www.cryengine.com/docs/static/attachments/28900683)
- Select it and go to **Advanced -> Tools** in the Designer Tool and click the **Mirror** button.
When you mouse over the object in the viewport, you'll now see a gizmo and two green lines. These lines determine the lines along which your actions are mirrored:
![Image](https://www.cryengine.com/docs/static/attachments/28900682)
- With the **Rotate** and **Move** tools, you can move these lines to make sure your actions are mirrored on the correct side.
When the lines are in the right place, click Apply to make sure the Mirror tool is activated.
Modify the object to your heart's content and you'll see that your changes will be mirrored on the opposite side of the line. Below, you can see that the mirror plane is in the middle of the box and when the rectangle is extruded to the right, the same happens on the left side of the box:
![Image](https://www.cryengine.com/docs/static/attachments/28900681) ![Image](https://www.cryengine.com/docs/static/attachments/28900680)

### Lathe

The **Lathe** tool is used to create a mesh by extruding each edge of a profile polygon along a path. You can make a complicated model with this tool with fairly little effort.

#### How it Works

- Draw a path that you want your profile polygon to be following. This can be a closed shape like a Rectangle or a Disc, or an open one like a Polyline (if not looped around to the starting point) or a curve. You can choose and make any shape that you want, but in the example, we'll use a circle.
This needs to be a 2D Shape for the Lathe tool to work properly, so no Box, Sphere, Cylinder or Cone.
- Make a profile polygon. This will be the shape that will be drawn all along the path that you drew earlier. Again, you can use the Shapes to make this profile polygon, and additionally, you can use other **Shapes** and the tools in the ** Advanced** section to modify the profile polygon. Below, a Rectangle was used, which was modified by drawing a Curve onto it. The chunk was then taken out with the ** Remove** tool under ** Extrude/Delete** in the ** Advanced** section:![Image](https://www.cryengine.com/docs/static/attachments/28900707)
The profile polygon and the path polygon need to be in the same designer object.
- Click the **Lathe** button and select the polygon you want to use as the profile polygon. When you mouse over it, it will show blue and green points on the polygon:
![Image](https://www.cryengine.com/docs/static/attachments/28900706)
The blue points mark the vertices of the profile polygon and the green points mark the polygon's bound vertices and the center of the polygon's edges.
- Now, you need to pick which vertex to use as the pivot of the profile polygon, in other words: which point of the polygon will touch the ground along the path.
- After you selected this vertex, you need to determine which direction is up compared to the pivot by selecting another vertex. You'll see that the vertex you selected first, the pivot vertex, will turn orange and a blue line will appear. Drag this line to another vertex to determine the up direction:![Image](https://www.cryengine.com/docs/static/attachments/28900705)
You can make the profile polygon tilt by selecting a vertex in this step that is not directly opposite, like for example the green vertex in the top-left of the profile polygon.
- Now, move the mouse cursor to one of the vertices of the path polygon. You'll see the profile polygon snap to this point:
![Image](https://www.cryengine.com/docs/static/attachments/28900704)
- Now press **LMB** to confirm and your profile polygon will be drawn all along the path:
![Image](https://www.cryengine.com/docs/static/attachments/28900703)

#### Examples

Some more examples to show what you can achieve with this tool:

1.

![Image](https://www.cryengine.com/docs/static/attachments/28900702)![Image](https://www.cryengine.com/docs/static/attachments/28900701)![Image](https://www.cryengine.com/docs/static/attachments/28900700)

2.

![Image](https://www.cryengine.com/docs/static/attachments/28900699)![Image](https://www.cryengine.com/docs/static/attachments/28900698)

3.

![Image](https://www.cryengine.com/docs/static/attachments/28900697)![Image](https://www.cryengine.com/docs/static/attachments/28900696)

### Circle Clone

With the **Circle Clone** tool, you can make clones of a Designer object and spread them evenly around in a circle.

#### How it Works

- Place a Designer object and modify it if you want:
![Image](https://www.cryengine.com/docs/static/attachments/28900695)
- Choose how many clones you want to make in the Circle Clone properties:![Image](https://www.cryengine.com/docs/static/attachments/28900694)
You can change the Clone Count up until step 4 if you decide there are not enough or too many.
- Click and drag on the object you created to create the clones and determine the radius of the circle in which they are created:
![Image](https://www.cryengine.com/docs/static/attachments/28900693)]
- Click the **Confirm** button in the Circle Clone properties to confirm the positions of your cloned objects.

### Array Clone

The Array Clone tool works in a fairly similar way as the Circle Clone tool, with the difference that it creates clones in a row instead of a circle.

#### How it Works

- Place a Designer object and modify it if you want:
![Image](https://www.cryengine.com/docs/static/attachments/28900692)
- Choose how many clones you want to make in the Array Clone properties:
![Image](https://www.cryengine.com/docs/static/attachments/28900691)
- Choose the **Placement Type**. You have two options here:
![Image](https://www.cryengine.com/docs/static/attachments/28900688)
**Divide:** Creates *all* clones within the distance from the original to the mouse cursor.
**Multiply:**Creates the first clone at the mouse cursor and takes the distance between the original and the mouse cursor and applies this as the distance between all the clones.

##### Divide

![Image](https://www.cryengine.com/docs/static/attachments/28900690)

##### Multiply

![Image](https://www.cryengine.com/docs/static/attachments/28900689)
Finally, click the **Confirm** button in the Array Clone properties to confirm the position of your cloned objects.

[LoopCut](#loopcut)[Bevel](#bevel)[Subdivision](#subdivision)[Boolean](#boolean)[Slice](#slice)[Mirror](#mirror)[Lathe](#lathe)[Circle Clone](#circle-clone)[Array Clone](#array-clone)
