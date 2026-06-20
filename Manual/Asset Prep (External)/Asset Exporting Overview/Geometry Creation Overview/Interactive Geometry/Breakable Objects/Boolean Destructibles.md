# Boolean Destructibles

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308030
- Page ID: 23308030
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Interactive Geometry > Breakable Objects > Boolean Destructibles
- Parent: Breakable Objects

## Content

### Overview

The underlying physics technology is versatile enough to break many things, not only tree trunks. It is just a matter of setting up the assets. For the examples below we will concentrate on tree trunks, though.

The Boolean Destructibles system allows you to cause dynamic physical mesh damage (holes) to an otherwise solid object from gunshots or explosions. This is done without the need to pre-model broken states for the object. It uses a pre-modeled 3D shape that is subtracted (boolean operation) from the original object in real-time in the exact location of bullet impacts.

Because the boolean operations happen in real time, the system dynamically re-triangulates the original model (adding polygons) as necessary in order to maintain the original solid shape with the additional holes or missing pieces. The new interior faces that are added to the object take on the material properties and textures (including UVs) of the boolean (subtractive) shape.

### Sample Files

- Explosion shape example: [cut_shape.max](/docs/static/attachments/23994757)
- Tree example: [sample_tree.max](/docs/static/attachments/23994760)

### Performance Impact

The actual performance impact of the boolean system depends on a combination of the geometric complexity of the breakable object:

- Geometric complexity of the boolean shape.
- The number of breakable objects used in the level.
- The number of successive booleans applied to the breakable object.
- The number of shooters firing at the breakable object simultaneously.

General performance guidelines:

- Keep breakable object very low poly.
- Keep boolean object very low poly.
- Use breakable objects sparingly in levels, for interesting/strategic gameplay situations.
- Create and use Surface Type parameters to limit how often a boolean occurs.
- Create and use Surface Type parameters to limit the maximum number of booleans a single object can take.
- Performance can lag noticeably when multiple shooters are firing rapidly at a single breakable object, causing multiple booleans simultaneously – to avoid this lag, try not to place boolean breakable objects in an area populated with a lot of shooters.

### Components of the System

The system involves a combination of various components (art assets, surface material types, physics script parameters) in order to function fully. Creating new destructible surface types and/or boolean shapes will require some engineer intervention.

These are the required components of the system:

#### Destructible 3D object (i.e. pillar)

By using an available destructible Surface Type in this object's material (in the Sandbox Material Editor), this object will be boolean-destructible.

##### Requirements:

- **Art:** Model, material, textures.

#### Destructible Surface Type (material on the destructible object)

Each different type of desired destructible surface (i.e. wood, concrete, brick, etc.) must be defined in the SurfaceTypes.xml and identified with a particular boolean 3D shape (modeled and textured by an artist).

- Once the required Surface Type(s) have been defined, they will be available in the Sandbox Material Editor for assignment to a destructible object, and the boolean functionality will then work automatically.

##### Requirements:

- **Code**: Surface defined in the SurfaceTypes.xml (this points to the particular boolean shape to be used for subtractions).
- **Code**: Surface effects defined in MaterialEffects.xml.

#### Boolean 3D shape

- Each different Surface Type must have an associated boolean shape to be used for subtracting from the original surface.
- A boolean shape can be used by multiple Surface Types, however the boolean shape should be textured to suit the original surface (i.e. wood, metal, concrete), and the 3D shape should visually suit the type of destruction the object can receive.

##### Requirements:

- **Art**: Model, material, textures.
- **Code**: Shape object registered in physics.lua.

Once a variety of SurfaceTypes (code) and Boolean shapes (art & code) have been created and defined, artists can then easily create destructible 3D objects (art only) to be placed in their levels without additional engineering support.

### Setup in 3dsMax

For the Trunk Material, turn on "physicalize" in the Material Editor in 3dsMax. Set the Parameter for the physics to "default".

![Image](https://www.cryengine.com/docs/static/attachments/23994759)

**Important:**

- Remove any proxy physics objects from parts you want to be breakable.
- Be sure your procedural breakable mesh is closed and has no gaps.

Create a predefined mesh in an extra cgf file, which is used to "cap" the broken parts.

![Image](https://www.cryengine.com/docs/static/attachments/23994758)

Please take a look at the files shipped with the CRYENGINE SDK, they are located in `Game\Objects\natural\trees\explosion_shape`. It is not necessary for example, to build splinters, but these could be used later to create the particle effects around the breaking part.

### Setup in Sandbox

- In the Sandbox material editor, the trunk's material surface type needs to be set to "mat_wood_breakable".
- The SurfaceType defines the particle effect and physics parameters for the breakability.
- The physics.lua defines the predefined mesh that is used to cap the tree trunk. It also defines the "splinters" particle effect which would be used together with the breaking.
The file is located at: `Game\Scripts\physics.lua`
- The SurfaceType.xml defines which particle effect to use during breaking and it also defines various physical properties. In the example below, you could set up different effects for joint break, joint shatter and the destroying.
The file is located at: `Game\Libs\MaterialEffects\SurfaceTypes.xml`

```
<SurfaceType name="mat_wood_breakable" type="wood">
<Physics friction="0.5" elasticity="0.05" breakable_id="2" pierceability="7"  break_energy="7000" hole_size="1.4" hit_points="10" hit_radius="0.4" hit_maxdmg="10" can_shatter="1" />
<BreakageParticles type="joint_break" effect="breakable_objects.tree_break.small" />
<BreakageParticles type="joint_shatter" effect="breakable_objects.tree_break.small" />
<BreakageParticles type="destroy" effect="breakable_objects.tree_break.small" count_per_unit="1" count_scale="1" scale="1" />
<AI fImpactRadius="2.5" fImpactSoundRadius="30" fFootStepRadius="20" proneMult="0.2" crouchMult="0.5" movingMult="2.5" />
</SurfaceType>
```

- Breakable trees need to be placed as vegetation objects.
- The **breakable_id** number is whatever number you defined in the breakability index in your Physics.lua file.
- The particle effects can use the splinters as geometry.

```
Physics.RegisterExplosionShape("Objects/default/explosion_shape/tree_broken_shape.cgf", 7, 2, 1, "",0,"");
Physics.RegisterExplosionShape("Objects/default/explosion_shape/tree_broken_shape2.cgf", 1.3, 3, 1, "",0,"");
Physics.RegisterExplosionShape("Objects/default/explosion_shape/tree_broken_shape3.cgf", 1.3, 5, 1,
"Objects/default/explosion_shape/trunk_splinters_a.cgf",1.6,"breakable_objects.tree_break.small");
```

- Information on physics.lua content can be found inside the file.

Note
The surface type includes only an explosion shape id. The actual mesh is registered in the `Game\Scripts\physics.lua` file. New explosion shape meshes must be added by code. After adding the mesh to physics.lua the surface types has to be changed.

#### Debugging

- **p_draw_helper 1** - To show the proxies.
- **p_debug_joints 1** - To check weights.

Shoot at the tree to check if it's breakable.

[Sample Files](#sample-files)[Performance Impact](#performance-impact)[Components of the System](#components-of-the-system)[Setup in 3dsMax](#setup-in-3dsmax)[Setup in Sandbox](#setup-in-sandbox)
