# RigidBodyEx Entity (GameSDK)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26870703
- Page ID: 26870703
- Breadcrumb: Physics > RigidBodyEx Entity (GameSDK)
- Parent: Physics

## Content

##
Overview

This article will show you some of the various physics setups you can add to your world to make it more dynamic.

This page depends on an entity that is only available in GameSDK.

##
Adding The Object

If you haven't done so already, start off by creating a new level.

In  the
**
Create Objects
**
 tab, go to
**
Legacy Entity
**
 ->
**
Physics
**
 ->
**
RigidBodyEx
**
 and drag it into your level. It should be a sphere by default:

The RigidBodyEx entity ("RigidBody Extended", an advanced version of the deprecated "RigidBody" entity) is the best choice when dealing with physicalizedobjects. It contains the most amount of features and this makes it the most stable, reliable and physically realistic option. There are cheaper physicalizable objects which can be used, such as the BasicEntity or AnimObject but these only support basic features and cannot be controlled as precisely.

You can change the visual representation of the RigidBodyEx entity to just about anything. By default its a sphere CGF and using the
**
Model
**
 property, you can change it to something else.

##
Physics Settings

Now that we have our RigidBodyEx in the level, if you've already tried it, you'll notice it doesn't actually physicalize by default.

First thing we need to do is tell the engine how much this object weighs. This is done in the
**
Mass
**
 parameter, so set that to 100. This will tell the engine it weighs 100kg. If it weighs -1kg, like it does by default, then the engine is told to make it unmovable (unless mass is also set in the cgf directly in node's UDP). Jump in game (CTRL+G) and shoot the sphere and it should roll along the ground.

If you place the sphere so that it is floating above the ground, you may notice that it does not fall/move on its own when you enter game (or activate AI/Physics). By default, the object is told to "sleep" so that it doesn't use any resources from the physics engine until it is required to do so. You can tell the object to be "awake" by default by unchecking the
**
Resting
**
 parameter. Now jump in game and it should fall this time.

Alternatively to Mass, you can also set the object's
**
Density
**
. Density is primarily used for objects which should float. Note that the word "alternatively" is important here as you cannot use both Mass and Density on the same object, the physics engine will prioritize Mass over Density in the event that both are used. So go ahead and set the Mass back to -1 to disable it and then set the Density to 0.5. You should now see the sphere float upwards.

It's worth noting that
**
Mass
**
 and
**
Density
**
 are just different ways to set up the same property (mass). If you specify only density, mass will be computed as density times physics proxy's volume. Correspondingly, density is mass/volume. So if you have two RigidBodyEx entities, one is a soda can and the other is a tractor and both have the exact same settings and a Mass of 1, the tractor will go flying up into the air and the soda can will drop to the ground, because of their big difference in size and thus in density.

Two handy CVars which can give you crucial information about physics is
**
p_draw_helpers=1
**
 to activate physics proxy visualization:

Additionally, set
**
p_debug_joints=1
**
 to display weight values of joints.

*
**
Left:
**
 Mass value is set to 100, Density to -1.
**
Right:
**
 Density value is set to 100, Mass to -1. Density of 100 for a Sphere of this size results in 418kg.
*

##
Example - Balloons

In this example we have three sets of balloons to show how you can create realistic physics simulations, be it a small helium balloon or a massive hot air balloon which can carry a player.

At the base of each set is a RigidBodyEx entity which has a
**
Mass
**
 of 4kg. We use
[Ropes](/docs/static/engines/cryengine-3/categories/1114113/pages/1048831)
 with standard settings to physically connect the objects.

-
On the
**
right
**
 we have a single sphere-shaped RigidBodyEx entity to represent our balloon. It has a
**
Mass
**
 of 1kg and a diameter of 2m. On its own, it is unable to lift the 4kg weight.

-
In the
**
center
**
 we have the exact same setup except this time we have two balloons. This setup is able to lift the weight. Using the
[Entity:Velocity](../Editor%20Tools/Flow%20Graph/Flow%20Graph%20Node%20Reference/Entity%20Nodes.md)
 Flow Graph node we can measure it is able to lift the object at a rate of around 4m/s.

-
On the
**
left
**
 we have the same setup again but using four balloons. It can of course lift the weight and measures in at around 8m/s lift speed.
![Image](https://www.cryengine.com/docs/static/attachments/21864582)

And don't forget the hot air balloon mentioned earlier!

This can even be controlled via a simple Flow Graph setup to increase the speed value for the linked WindArea entity. This WindArea entity can be found in
**
Legacy Entity
**
 ->
**
Physics
**
 ->
**
WindArea
**
.

##
Example - Floating Objects

Floating in the water is determined by the relation of the object's density to that of the water, which is 1000 (same is true for floating in the air, except its density is 1). If the object's density is above 1000, it'll sink, and if below it'll float. If you don't want to change the object's density (and thus its mass as well), you can adjust water settings independently in the "Buoyancy" section in the RigidBodyEx properties. Whether you want the object to plummet through the water, float lightly on the surface, or slowly sink to the floor, these can all be achieved with a just a couple of parameters.

Each of the objects shown are RigidBodyEx entities with only 3 parameters set differently on each.

-
On the right we have a "floating" cube. It has a
**
Mass
**
 of 1000,
**
water_density
**
 of 1000 and
**
water_resistance
**
 of 1000.

-
In the middle, the "plummet" cube has a
**
Mass
**
 of 1000,
**
water_density
**
 of 100 and
**
water_resistance
**
 of 1000. The 1/10th density value is what allows it to plummet through the water.

-
On the left we have our "sinking" cube with a
**
Mass
**
 of 1000,
**
water_density
**
 of 130 and
**
water_resistance
**
 of 1000. The more specific 130 value for the density allows it to sink deep into the water and then slowly climb its way back to the surface. In this case, anything less than 125 will cause the cube to continue to sink until it hits the floor, the lower the value, the faster it will sink.
These values are all of course arbitrary because it depends on the size of your object as to how buoyant it will be. Offsetting Mass for Density will also provide slightly different reactionary results, for example.

![Image](https://www.cryengine.com/docs/static/attachments/21864584)

##
Example - Falling Rocks

In this example we'll show how to setup some rocks tumbling down the side of a hill. It's a very simple setup that shows one simple rule: heavy rocks falling down a hill will cause mass destruction.

Using RigidBodyEx entities again, we have three different types: small (500kg) medium (1000kg) and large (2000kg), all from the same geometry just with a simple scaling applied to each. This allows some variety in the reaction from the rocks to give it a bit more realistic representation.

The actual setup for this is slightly different in the sense that we leave the
**
Resting
**
 flag enabled. This means when you start the game, the rocks will be floating in resting state:

However, this leaves us with the issue that we need a way to wake the rocks up into their "Awake" state when we're ready for the physics system to take over. This could be for a cutscene, from a player interaction, or just some random world event. In any case, it can be triggered very easily through Flow Graph:

Using the
**
Iterator:GetEntitiesInBox
**
 node we can find all of the RigidBodyEx entities in a specified area.

We place two
[Tagpoints](/docs/static/engines/cryengine-3/categories/1114113/pages/1048823)
 to easily figure out the minimum and maximum bounds for the "box". This "box" is the area where the node will check for the entities:

Once we have our box defined and we identify all of the entities within that box, we can apply a simple
**
Physics:ActionImpulse
**
 to every entity which will wake them up and allow them to physicalize.

![Image](https://www.cryengine.com/docs/static/attachments/21863454)

##
Example - Breakable Wall

For this example we're going to create a fully destructible and physicalized brick wall made from individual bricks.

First thing we're going to need is a brick! So create a simple Box object (0.5m x 0.25m x 0.25m) with the Designer tool, apply a brick material of your choosing, setup the
[Texture Mapping](/docs/static/engines/cryengine-5/categories/23756816/pages/29798807)
 and then Export to CGF. Once that is done we can add another RigidbodyEx entity and use our brick as the Model.

Once you've got your RigidBodyEx brick in the world, start copy-pasting it to build up a decent sized wall. You can also do a double-brick setup (2x thickness) and then turn the end bricks 90 degrees to cap it off nicely.

It's worth noting that this of course is not the most optimal way of adding physical destruction to your world (with the likes of GeomCache for example, or breakable object with joints you can do some huge set pieces with minimal performance hit), however, this is probably one of the easiest and most flexible methods to get started with.

Set the
**
Mass
**
 to 50, uncheck
**
Resting
**
 and scroll down to the "Simulation" section in the properties. In here we have some advanced physics settings and because the brick is a relatively small object, set the
**
max_time_step
**
 to 0.01, this will improve stability for small objects (otherwise the wall might collapse on itself). If this is still not enough, you can also reduce the world gravity with p_gravity_z=-9.81 (instead of the default -13). Finally, you can also increase the
**
p_max_MC_iters
**
 from 6000 to 12000, but by this stage it should already be quite stable.

Jump in game and start chipping away at the bricks with a weapon to see if it looks stable enough.

When dealing with perfectly square structures like these bricks, there may be some cases where decreasing the
**
p_max_contact_gap
**
 CVar from 0.01 (default) to something like 0.002-0.005. If you increase it to something far too high like '1' (1m penetration) then the bricks will sag almost to the point where it looks like they're melting (which could be a desired effect in some cases!):

Let's step it up a bit and use the HMMWV to take it down:

Using
**
p_profile=1
**
 we can see some performance stats for the physics system, as you may notice a slight jitter when running physics simulations over 300+ rigidbodies in one hit. By increasing the max_time_step from 0.01 to 0.015 (default 0.02) we still have a stable wall and no more jittering when it crumbles, so that's a nice balance between performance and stability.

Lastly, this wouldn't have been complete without a wrecking ball!

![Image](https://www.cryengine.com/docs/static/attachments/21863451)

[Adding The Object](#adding-the-object)
[Physics Settings](#physics-settings)
[Example - Balloons](#example-balloons)
[Example - Floating Objects](#example-floating-objects)
[Example - Falling Rocks](#example-falling-rocks)
[Example - Breakable Wall](#example-breakable-wall)
