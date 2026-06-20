# 2 - Legacy Gravity Spheres

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27591005
- Page ID: 27591005
- Breadcrumb: Tutorials > Game and Level Design > Legacy Feature Tutorials > Legacy physics entities tutorials > 2 - Legacy Gravity Spheres
- Parent: Legacy physics entities tutorials

## Content

Another tool that is provided within the Editor is the Gravity Sphere which allows you to create a spline and then direct an entity that enters it down a path. This could be considered almost like a wind tunnel and is quite easy to setup and customise and has similar functions to that of the Road or River tools if you have used them prior.

##
Turning Gravity Spheres On And Off

Follow these below mentioned steps to tweak a Gravity Sphere within your level:

-
Go to
**
Create Object -> Legacy Entities -> Physics
**
 and grab the
**
Gravity Box
**
 to add it to the Viewport and scene.

-
With the Gravity Box entity selected, scroll to the bottom of its properties to adjust the gravitational influence. As the default world is set to
**
-13
**
 we can change the influence of the Gravity Box to something like
**
100
**
 to see the effects of our player floating in the space.

-
Lastly we will look to trigger this on and off by using Flow Graph and triggering it with a switch inside of a volume. We will need to add 3 Basic Entities initially and then set their mass to be 100 within the volume of the Gravity Box.

-
Now that we have the entities positioned as shown below we will look to add a trigger to the scene to be able to control the influence of the box when switched on.

##
Step 1

[Image: /docs/static/attachments/52593001]

##
Step 2

[Image: /docs/static/attachments/52593002]

##
Step 3

[Image: /docs/static/attachments/52593003]
