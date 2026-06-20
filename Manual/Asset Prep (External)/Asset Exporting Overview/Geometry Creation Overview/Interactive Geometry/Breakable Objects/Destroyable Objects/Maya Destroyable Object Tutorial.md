# Maya Destroyable Object Tutorial

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308025
- Page ID: 23308025
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Interactive Geometry > Breakable Objects > Destroyable Objects > Maya Destroyable Object Tutorial
- Parent: Destroyable Objects

## Content

### Sample File

- [ma_destroyable.rar](/docs/static/attachments/23994688)

### Destroyable Objects

Destroyable objects are structures that contain the original object and pre-created pieces that appear when the original object is destroyed. Its setup is similar to a [jointed breakable](../Jointed%20Breakable%20Objects.md) but it doesn't use any bones. Instead it uses the model in its unbroken state and the pieces in the broken state embedded in one cgf. It can be used to completely destroy specific types of objects in the environment. It shatters into the pre-created pieces by taking more damage then the specified "health" property of the object. It is placed using the [DestroyableObject Entity](../../../../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Legacy%20Entities/Physics%20Entities.md) in the engine.

A DestroyableObject can be in two states, an "Alive" state, or a "Dead" state. In the "Alive" state, it acts exactly like a normal physical entity. It can be set up to be a rigid body or a static physical entity. After taking more damage then the specified "health", it will go into the Dead state. When going into the Dead state, it can optionally generate a physical explosion and apply area damage on the surrounding entities, spawn a particle effect (for example, an explosion), and replace the original geometry of the entity with either destroyed geometry and/or pre-broken pieces of the original geometry. If the object breaks due to a hit (bullet), that hit impulse is applied to the pieces in addition to any explosion (outward) impulse.

### Destroyable Objects Setup

- Create your object with physics geometry, LOD's and a [pickup helper](/docs/static/engines/cryengine-3/categories/1114113/pages/1310892) if needed.
- Duplicate your rendermesh. Cut it into the amount of pieces that you want (Be reasonable - This can become expensive quite fast. 8 Pieces should be enough for most objects, the smaller the object the less pieces you need).
- Create LOD's and collision for your pieces.
- Call your unbroken piece **main** and call your broken pieces ** remain_xx** (xx=01,02,03,etc).
- Enter mass a [UDP](/docs/static/engines/cryengine-3/categories/1114113/pages/1310799) to the main piece and enter mass and entity [UDP's](/docs/static/engines/cryengine-3/categories/1114113/pages/1310799) to your broken pieces. The amount of mass of your broken pieces should ideally add up to the mass of your main, unbroken piece.
- Center all pivots to your export helper.
- Export with merge all nodes off and Export file per node on.
- Place your destroyable object as a DestroyableObjects Entity in the editor, set up the correct [values](../../../../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Legacy%20Entities/Physics%20Entities.md) and shoot it. It should now break.

![Image](https://www.cryengine.com/docs/static/attachments/23994689)

### Using plane cgfs without embedded pieces

Instead of embedding the pieces into one cgf, you can create two different cgf's. One in its un-destroyed state, one in its destroyed state.

Place the object as a destroyable Object Entity and specify the cgf's and a health value. It will switch when the object has taken more damage then specified in the health value.

When not specifying anything in the ModelDestroyed tab and not using a cgf that has pieces embedded, the object will disappear when the health is drained.

![Image](https://www.cryengine.com/docs/static/attachments/23994687)

After you've created your Destroyable object cgf(s), add a particle effect, health values and explosion effects. I've used **Props.electrical.aircon_med_a** in the example screenshot.

### General Rules

A CGF containing broken object pieces as sub-models must be created for the object. Depending on how you want to set it up, the CGF can also contain the main unbroken model as a separate sub-model. Each sub-model should also have a physics proxy geometry.

The sub-model's name and text properties determine its behavior, as follows:

- The object must consist of the main original piece named Main that will act as an alive geometry. It is the (only) pre-destruction sub-model.
- It should also consist of the destroyed geometry named Remain that will replace the original geometry and acts as the dead geometry. It is the permanent post-destruction sub-model, which replaces Main. Otherwise, it is a destruction piece.
- It should consist of different pieces that will be spawned as particles or entities.
- Every piece needs to have a physical proxy.
- The orientation in world coordinates should be 0/0/0 (see Debug section).
- Turn OFF "Merge All Nodes" on export.
- Objects should be placed as Destroyable entity.
- Spawn Location: By default, the pieces spawn in the position in which they are placed in the CGF, relative to the original model. The following text properties alter this behavior:
- bone = name: (Only for breakable skinned characters) - This is the name of the bone that this piece is attached to. The sub-model's origin will be placed at the bone origin, and the sub-model's X-axis will align with the bone direction.
- generic = count: This causes the piece to be spawned multiple times in random locations, throughout the original model. The count specifies how many times it is spawned. There can be multiple generic pieces.
- sizevar = var: For generic pieces, this randomizes the size of each piece, by a scale of 1-var to 1+var.
- rotaxes axes: For generic pieces, this generates random rotation. Set this to the axis letter(s); for example, =z or xyz, to cause the piece to rotate randomly about the selected local axis/axes. If not set, the pieces will spawn in their authored rotation.
- entity: If this is set, the piece is spawned as a persistent entity. Otherwise, it is spawned as a particle.
- density (density or =mass) = mass: This overrides either the density or the mass of the piece. Otherwise, it uses the same density as the whole object.
- Surface Material Setting: It's important to make sure that each piece has an appropriate surface type (for example, wood or ice) because this is used to spawn secondary breakage effects.

A plain CGF, with only one sub-model, can also be destroyed. Its model will disappear, but if the model's surface material specifies a destroy effect, it will be spawned. For breakable skinned characters, the CGF should not contain Main or Remain pieces; only "bone" and "generic" pieces.

### Creating Pickable Destroyable Objects

The setup for making your destroyable object pickable is fairly simple. Refer to the [Pickable Objects](../../Pickable%20Objects.md) documentation for more information.

### Secondary Particle Effects

When the object breaks, by default, secondary particle effects are automatically spawned, based on each piece's surface material type. The effects are read from the material script, and there are two kinds of effects that can be specified:

- **breakage.particle_effect:** This specifies an effect to spawn on each broken piece of this material type, around its edges.
- **destroy.particle_effect:** This specifies an effect to spawn throughout the unbroken object volume, at the point where it is destroyed. This effect is useful for destroying simple objects that don't have a multi-part CGF. The object disappears and is replaced by the destroy.particle_effect. However, the destroy effect can also be used along with the breakage effects.

### Troubleshooting

**Q: The object doesn't break.**

A: Check the health value in your Destroyable object entity. Check your object for correct use of naming conventions (main, remain_xx). Check that every piece has its own collision geometry.

**Q: The object spawns no pieces or they get spawned in wrong positions.**

A: Set all your pivots on the export helper and reset transformations.

**Q: The pieces jitter when broken.**

A: The physics geometry pieces intersect with each other. Make sure that there are gaps between the collision.

### Properties

Please see the [Pickable Objects](../../Pickable%20Objects.md) document for information on placing a DestroyableObject and their property values.

[Sample File](#sample-file)[Destroyable Objects](#destroyable-objects)[Destroyable Objects Setup](#destroyable-objects-setup)[Using plane cgfs without embedded pieces](#using-plane-cgfs-without-embedded-pieces)[General Rules](#general-rules)[Creating Pickable Destroyable Objects](#creating-pickable-destroyable-objects)[Secondary Particle Effects](#secondary-particle-effects)[Troubleshooting](#troubleshooting)[Properties](#properties)
