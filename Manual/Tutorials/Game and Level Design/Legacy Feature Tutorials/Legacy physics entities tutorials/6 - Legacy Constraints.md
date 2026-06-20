# 6 - Legacy Constraints

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29793510
- Page ID: 29793510
- Breadcrumb: Tutorials > Game and Level Design > Legacy Feature Tutorials > Legacy physics entities tutorials > 6 - Legacy Constraints
- Parent: Legacy physics entities tutorials

## Content

### Note: there is a newer version of this tutorial for entity components here.

#### What is possible with constraints?

During level design you come across the need to hold an object in place to rotate on an axis or simply break off when a physical impulse hits it (melee or bullet). This is where the constraint entity can come into play in that you can simply arrange two objects within the volume or radius of the constraint. Depending on their dynamic properties you could have a solid object that is the base or have two objects that are completely dynamic yet connected to each other and rotate off the single pivot point.

Along with a fully constrained object you have the possibility of constraining to a single axis or possibly a plane where you can combine two axes. A quick example is possibly a zip line. For this, you would need to constrain down the single line to get to the end, or, if you want to, constrain an entity/player to a single axis or plane to replicate a classic like Pac-Man.

The default volume is called the **Constraint Frame** and can operate as we have described before. It also allows for you to define the frame to be the constraint itself which opens up the option to treat the initial constraint as a hinge if ** Use Entity Frame** is selected. The following are several more of the properties in greater detail:

- **Damping** - Sets the strength of the damping on an object's movement. When several objects are in contact, the highest damping is used for the entire group.
- **Max Bend Torque** - The maximum bending torque (Currently it's only checked against for hinge constraints that have reached one of the x limits).
- **Max Pull Force** - Specifies the maximum stretching force the constraint can withstand.
- **No Self Collisions** - Disables collision checks between the constrained objects.
- **Radius** - Defines spherical area to search for attachable objects.
- **Use Entity Frame** - Defines whether to use the first found object or the constraint itself as a constraint frame.

#### Creating Our Constraint

**You need to follow these below mentioned steps** to create a constraint in which you can shoot off during gameplay:

- Go to **Create Object -> Legacy Entities -> Physics -> Constraint** and drag it into your scene
- Create a Designer box with **Create Object -> Designer ->****Box** and drag it out into our scene so it sits atop the constraint. This box will work as the ceiling in this example.
- Now that the ceiling and constraint are in place, go to **Create Object -> Legacy Entities -> Physics -> Basic Entity** and place this sphere below the constraint entity. This will be the object we will shoot and break off. Scroll down in the ** Properties** panel and adjust the ** Mass** to ** 50** in order to have it fall as it should.
- With everything in position, select the constraint and adjust the **Radius** so that each of the physics proxies on the objects intersect and know to hold the points when gravity is activated.
- Finally, we can hop into the map (**Ctrl+G**) and shoot the ball to see it drop from the hanging ceiling and roll across the terrain.

##### Step 1

![Image](https://www.cryengine.com/docs/static/attachments/29928950)

##### Step 2

![Image](https://www.cryengine.com/docs/static/attachments/29928951)

##### Step 3

![Image](https://www.cryengine.com/docs/static/attachments/29928952)

##### Step 4-1

![Image](https://www.cryengine.com/docs/static/attachments/29928953)

##### Step 4-2

![Image](https://www.cryengine.com/docs/static/attachments/29928954)

##### Step 5

![Image](https://www.cryengine.com/docs/static/attachments/29928955)
