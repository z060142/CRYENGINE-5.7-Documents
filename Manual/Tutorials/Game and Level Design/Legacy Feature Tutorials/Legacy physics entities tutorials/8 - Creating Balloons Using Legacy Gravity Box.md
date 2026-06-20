# 8 - Creating Balloons Using Legacy Gravity Box

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29793749
- Page ID: 29793749
- Breadcrumb: Tutorials > Game and Level Design > Legacy Feature Tutorials > Legacy physics entities tutorials > 8 - Creating Balloons Using Legacy Gravity Box
- Parent: Legacy physics entities tutorials

## Content

Prior to this lesson in a previous chapter we experimented with the idea of using buoyancy to make certain objects float or possibly sink inside of a water volume within your scene. Now we will take this the other direction and make the objects float with another RigidBodyEx Entity attached to the bottom through a dynamic rope setup like we did before.

#### Floating Objects Into The Air

You need to follow these below mentioned steps to have your objects floating away:

- First go to Create Object->Legacy Entities->Physics and grab the Gravity Box to add it to the Viewport and scene.
- Next, with the Gravity Box entity selected we want to scroll to the bottom of its properties to adjust the gravitational influence. Seeing as how the default world is set to -13 we can go ahead and change the influence of the Gravity Box to something to 100 to see the effects of our player floating in the space.
- Lastly we will look to trigger this on and off by using Flow Graph and triggering it with a switch inside of a volume. We will need to add 3 Basic Entities initially and then set their mass to be 100 within the volume of the Gravity Box.
- Now that we have the entities positioned as shown below we will look to add a trigger to the scene to be able to control the influence of the box when switched on.

##### Step 1

![Image](https://www.cryengine.com/docs/static/attachments/29929014)

##### Step 1

![Image](https://www.cryengine.com/docs/static/attachments/29929014)

##### Step 1

![Image](https://www.cryengine.com/docs/static/attachments/29929014)
