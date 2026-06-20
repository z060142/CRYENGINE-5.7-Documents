# Pre-Baked Physics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308031
- Page ID: 23308031
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Interactive Geometry > Breakable Objects > Pre-Baked Physics
- Parent: Breakable Objects

## Content

### Overview

The pre-baked physics pipeline allows you to bake out a physics simulation in a 3D asset creation package to keyframe data, and load it into CRYENGINE. Once the pre-baked physics are in the engine, the pieces can be detached from the animation and become physicalized.

### The Destructible Object

- The model should be broken up into pieces in an interesting way (The break points should make sense, think about how the material would break).
- The pieces should have very low-res physical proxies, try to use boxes whenever possible.
- Make sure the Crytek Shader material for all objects is set to "physical".

### Setting Up the Simulation in 3ds Max

#### Creating a Rigid Body Collection

- Select all of the objects that you would like to be simulated and then select **reactor -> Create Object -> Rigid Body Collection**.
- Any object that you do not want to move can be set to "unyielding" in the![Image](https://www.cryengine.com/docs/static/attachments/23994761).
- It helps to put a large flat cube down as an "unyielding" floor.
- In the reactor utility roll-out you can give your items "mass" and other properties.

#### Applying a Force to the Rigid Bodies

The reactor is very simple when it comes to applying a force to your objects, there are two basic ways:

- **Wind:** You can create a Wind force by selecting **reactor -> Create Object -> Wind**.
- Wind values can be keyframed over time when changed in autokey mode.
- **Animated Objects:** You can animate other rigid body physical objects to collide with your object in order to create an interesting simulation.
- Animated items should be set to "unyeilding" in the reactor utility rollout, if not, upon hitting a rigid object, they will start to simulate and not stick to their keyframed animation.
- Character bones can be physicalized and used if you have a cinematic sequence where a character interacts with your breaking object.
- Spheres can be used to break apart buildings, simulating explosions (delete these spheres after the simulation).

#### Previewing the Simulation

- Select **reactor -> Preview Animation...** to see a preview of your simulation.

#### Baking the Simulation to Keyframe Data

- Select **reactor -> Create Animation** and wait for it to bake your simulation to keyframe data.

Note
This cannot be undone, so save a copy of your scene before baking it to keys.

### Exporting to CRYENGINE

Here are some things to keep in mind when exporting your pre-baked physics into the engine:

- You will export the animation as a CGA:
- All the position and rotation controllers of the objects in the CGA need to be set to **TCB**. The easiest way to do this is with the [CryAnim Tools](/docs/static/engines/cryengine-3/categories/1114113/pages/1310776) (On the General Tools rollout).
- Select **merge all nodes** in the export options.
- Turn off all bone export options, but tell it to export **every '1' frames**.
- Select one object that is not moving and parent all the other pieces to it. This object can be one you set to "unyeilding". In buildings, use the foundation.
- You can add special metadata to your individual CGA objects, either through the Meta Data Editor found in CryTools ([Rigging Tools](/docs/static/engines/cryengine-3/categories/1114113/pages/1310724)), or by using these flags in the **User Defined Properties** of an object:
- **Mass**
- **Box**
- **Entity**

- The current animation will show up as Default in the CGA you export, no CAL file is needed to play it.
- Name your CGA with the same name as the original object, this way the material will work with it.
- Open your CGA in the Character Editor and play the animation labelled "Default", you should see your animation play.
- As always, obey the [Character Rigging Guidelines](../../Animated%20Geometry/Basics%20(animated)/Rigging%20(animated)/Character%20Rigging%20Guidelines.md) for CRYENGINE; pay particular attention to having no scales and transformations.

### Creating an AnimObject Entity

Once you have exported the CGA, place it into the engine as an AnimObject.

- Drag in and place an AnimObject from **Entity Panel -> Physics -> AnimObj**.
- Remember that **ActivatePhysicsThreshold** is a fraction of gravity, thus a heavier piece will be harder to activate since the gravity force that acts on it is stronger.
- **Mass** is the overall value for the entire CGA, for instance, a Mass of 100 on a CGA with 100 pieces would yield 1kg per piece.
- You can set the mass in the UDP metadata of your CGA as mentioned above.

### Entity Properties

| **Name** | **Description**
--- | --- | ---
**n** | **ActivatePhysicsDist** | **[FLOAT]** - This is the distance from the pivot (in meters) after which the objects are forcefully detached from the animation.
**n** | **ActivatePhysicsThreshold** | **[FLOAT]** - The amount of force needed to physicalize an object. This value is a fraction of the current gravity.
**?** | **AutoGenAIHidePts** | **[BOOL]** - The amount of force needed to physicalize an animated object.
**?** | **Model** | **[MODEL]** - The CGA model you created.
**?** | **ModelFrozen** | **[MODEL]** -
**?** | **Pickable** | **[BOOL]** - Defines whether or not the object can be picked up.
**Ai** | **Pickable** | **[Smart Object Classes]** -
**?** | **Usable** | **[BOOL]** - Defines whether or not the object can be used.
**ab** | **UseMessage** | **[String]** - The message displayed when the object is in the crosshairs for use.
| **Animation** |
**?** | **AlwaysUpdate** | **[BOOL]** -
**ab** | **Animation** | **[String]** - The animation to be played, in this case it is usually Default.
**?** | **Loop** | **[BOOL]** - This will cause the animation to loop.
**?** | **PhysicalizeAfterAnimation** | **[BOOL]** - Select this to physicalize all of the pieces after the animation has played.
**?** | **Playing** | **[BOOL]** - With this selected, the animation will start immediately.
**n** | **Speed** | **[FLOAT]** - A multiplier for the playback speed of the animation.
**ab** | **playerAnimationState** | **[String]** -
| **Physics** |
**?** | **ActivateOnDamage** | **[BOOL]** - With this selected, any piece damaged will immediately become physicalized and detach from the animation.
**?** | **Articulated** | **[BOOL]** - You need to have this selected if you are using a CGA, however, it is not selected by default.
**n** | **Density** | **[FLOAT]** - Can be used instead of Mass (if mass is -1) to set the density of each node.
**n** | **Mass** | **[FLOAT]** - This is the overall mass for the entire CGA.
**?** | **Physicalize** | **[BOOL]** - Selects whether or not the CGA can become physicalized.
**?** | **PushableByPlayers** | **[BOOL]** - Allows the object to be pushed by players.
**?** | **Resting** | **[BOOL]** - Whether the object is resting initially (it is better to have it set).
**?** | **RigidBody** | **[BOOL]** - If deselected, the object is static. Pre-baked physics objects must have it selected.

[The Destructible Object](#the-destructible-object)[Setting Up the Simulation in 3ds Max](#setting-up-the-simulation-in-3ds-max)[Exporting to CRYENGINE](#exporting-to-cryengine)[Creating an AnimObject Entity](#creating-an-animobject-entity)[Entity Properties](#entity-properties)
