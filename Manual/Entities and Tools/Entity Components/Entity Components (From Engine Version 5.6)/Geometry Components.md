# Geometry Components

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966057
- Page ID: 44966057
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6) > Geometry Components
- Parent: Entity Components (From Engine Version 5.6)

## Content

### Advanced Animations

The Advanced Animations Component can be used to play complex animation setups. This could be used for controlling the animation of player or npc in the game.

Property | Description
--- | ---
**Advanced Animations Settings** | Setting | Description --- | --- **Type** | Determines the behavior of the static mesh. ** Character** | Determines the character to load. ** Material** | Assigns a different material to the character that has been chosen. Some characters might not support materials.
Setting | Description
**Type** | Determines the behavior of the static mesh.
**Character** | Determines the character to load.
**Material** | Assigns a different material to the character that has been chosen. Some characters might not support materials.
**Rendering Settings** | Setting | Description --- | --- **Minimum Shadow Graphics** | Minimum graphical setting at which shadows will be cast. ** Ignore Visareas** | Whether this component will ignore Vis Areas placed in the level. For more information about Vis Areas, please refer to the [Vis Area](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md) page. ** Ignore Terrain Layer Blending** | Controls blending with terrain layers. For more information, please refer to the [Terrain Layer Blending into Objects](../../../Materials/Terrain%20Layer%20Blending%20into%20Objects.md) page. ** Ignore Decal Blending** | Controls blending with decals. For more information about Decals, please refer to the [Decal](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Misc%20Objects/Decal%20Entity.md) page. ** View Distance** | View distance from 0 to 100 - where 100 = always visible. ** LOD Distance** | Level of Detail distance from 0 to 100 0 - where 100 = best LOD. ** GI and Usage Mode** | Type of SVOGI to use. - ** Disabled -** Object is excluded from voxelization and mostly does not affect the GI. (But it receives all GI effects from the rest of the scene). - ** Static Voxelization -** Object is voxelized allowing in-directional occlusion effects, large scale AO and more precise light bounce. - ** Analytical Proxy Soft -** An occluder applied during the cone tracing stage and used like a true replacement of voxels allowing also light bouncing from it. Occlusion fades with distance allowing softer shadow effects. - ** Analytical Proxy Hard -** An occluder applied during cone tracing stage and used like true replacement of voxels allowing also light bouncing from it. - ** Analytical Occluder -** An occluder applied in a deferred way after all cone tracing is performed. ** Analytical occluders** checkbox must be ** ON** in ** Total Illumination v2 settings** (** Tools -> Level Editor -> Level Settings ->****Total Illumination v2**) - ** Integrate into Terrain -** Integrates this mesh into the terrain mesh. This allows support for all terrain material features like 3-planar texturing. ** Integrate Objects** must be ** ON** in** Level Settings** (** Tools -> Level Editor -> Level Settings -> Terrain**). ** Animation Database** | Path to the Mannequin.adb file. ** Controller Definition** | Path to the Mannequin controller definition file ** Default Scope Context Name** | Name of the default Mannequin scope context to use. ** Default Fragment Name** | Name of the default Mannequin fragment to play. ** Animation Driven Motion** | Whether or not to use root motion in the animations for physical movement. ** Use Ground Alignment** | Enables adjustment of leg positions to align to the ground surface.
Setting | Description
**Minimum Shadow Graphics** | Minimum graphical setting at which shadows will be cast.
**Ignore Visareas** | Whether this component will ignore Vis Areas placed in the level. For more information about Vis Areas, please refer to the [Vis Area](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md) page.
**Ignore Terrain Layer Blending** | Controls blending with terrain layers. For more information, please refer to the [Terrain Layer Blending into Objects](../../../Materials/Terrain%20Layer%20Blending%20into%20Objects.md) page.
**Ignore Decal Blending** | Controls blending with decals. For more information about Decals, please refer to the [Decal](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Misc%20Objects/Decal%20Entity.md) page.
**View Distance** | View distance from 0 to 100 - where 100 = always visible.
**LOD Distance** | Level of Detail distance from 0 to 100 0 - where 100 = best LOD.
**GI and Usage Mode** | Type of SVOGI to use. - **Disabled -** Object is excluded from voxelization and mostly does not affect the GI. (But it receives all GI effects from the rest of the scene). - ** Static Voxelization -** Object is voxelized allowing in-directional occlusion effects, large scale AO and more precise light bounce. - ** Analytical Proxy Soft -** An occluder applied during the cone tracing stage and used like a true replacement of voxels allowing also light bouncing from it. Occlusion fades with distance allowing softer shadow effects. - ** Analytical Proxy Hard -** An occluder applied during cone tracing stage and used like true replacement of voxels allowing also light bouncing from it. - ** Analytical Occluder -** An occluder applied in a deferred way after all cone tracing is performed. ** Analytical occluders** checkbox must be ** ON** in ** Total Illumination v2 settings** (** Tools -> Level Editor -> Level Settings ->****Total Illumination v2**) - ** Integrate into Terrain -** Integrates this mesh into the terrain mesh. This allows support for all terrain material features like 3-planar texturing. ** Integrate Objects** must be ** ON** in** Level Settings** (** Tools -> Level Editor -> Level Settings -> Terrain**).
**Animation Database** | Path to the Mannequin.adb file.
**Controller Definition** | Path to the Mannequin controller definition file
**Default Scope Context Name** | Name of the default Mannequin scope context to use.
**Default Fragment Name** | Name of the default Mannequin fragment to play.
**Animation Driven Motion** | Whether or not to use root motion in the animations for physical movement.
**Use Ground Alignment** | Enables adjustment of leg positions to align to the ground surface.
**Physics** | Setting | Description --- | --- **Weight Type** | Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized. - ** Mass -** Mass of the object in kg. - ** Density-** Density of the object in Kg/m3. - ** Immovable -** Prevents the mesh entity from moving it is physicalized. ** Mass (pre-scale)** | Appears when ** Mass** is selected on the Weight Type list. It pre-scales the mass of the object in kg. ** Density** | Appears when ** Density** is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.
Setting | Description
**Weight Type** | Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized. - **Mass -** Mass of the object in kg. - ** Density-** Density of the object in Kg/m3. - ** Immovable -** Prevents the mesh entity from moving it is physicalized.
**Mass (pre-scale)** | Appears when **Mass** is selected on the Weight Type list. It pre-scales the mass of the object in kg.
**Density** | Appears when **Density** is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.

### Alembic Mesh

The Alembic Mesh Component let's you add [Geom Caches](../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/Animated%20Geometry/Geom%20Cache%20(Alembic).md) to the entity.

Setting | Description
--- | ---
**File** | The geom cache file (.abc or.cbc) to load.
**Speed** | Determines the play speed of the animation.
**Material** | Specifies the override material for the selected object.

### Animated Mesh

The Animated Mesh Component play animation for an animated mesh. This would normally be used for basic geometry with one simple animation like a fan.

Property | Description
--- | ---
**Animated Mesh Settings** | Setting | Description --- | --- **Type** | Determines the behavior of the mesh. ** File** | Determines the animated mesh to load. ** Material** | Assigns a material to the object.
Setting | Description
**Type** | Determines the behavior of the mesh.
**File** | Determines the animated mesh to load.
**Material** | Assigns a material to the object.
**Rendering Settings** | Setting | Description --- | --- **Minimum Shadow Graphics** | Minimum graphical setting at which shadows will be cast. ** Ignore Visareas** | Whether this component will ignore Vis Areas placed in the level. For more information about Vis Areas, please refer to the [Vis Area](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md) page. ** Ignore Terrain Layer Blending** | Controls blending with terrain layers. For more information, please refer to the [Terrain Layer Blending into Objects](../../../Materials/Terrain%20Layer%20Blending%20into%20Objects.md) page. ** Ignore Decal Blending** | Controls blending with decals. For more information about Decals, please refer to the [Decal](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Misc%20Objects/Decal%20Entity.md) page. ** View Distance** | View distance from 0 to 100 - where 100 = always visible. ** LOD Distance** | Level of Detail distance from 0 to 100 - where 100 = best LOD ** GI and Usage Mode** | Type of SVOGI to use. - ** Disabled -** Object is excluded from voxelization and mostly does not affect the GI. (But it receives all GI effects from the rest of the scene). - ** Static Voxelization -** Object is voxelized allowing in-directional occlusion effects, large scale AO and more precise light bounce. - ** Analytical Proxy Soft -** An occluder applied during the cone tracing stage and used like a true replacement of voxels allowing also light bouncing from it. Occlusion fades with distance allowing softer shadow effects. - ** Analytical Proxy Hard -** An occluder applied during cone tracing stage and used like true replacement of voxels allowing also light bouncing from it. - ** Analytical Occluder -** An occluder applied in a deferred way after all cone tracing is performed. ** Analytical occluders** checkbox must be ** ON** in ** Total Illumination v2 settings** (** Tools -> Level Editor -> Level Settings ->****Total Illumination v2**) - ** Integrate into Terrain -** Integrates this mesh into the terrain mesh. This allows support for all terrain material features like 3-planar texturing. ** Integrate Objects** must be ** ON** in** Level Settings** (** Tools -> Level Editor -> Level Settings -> Terrain**). ** Default Animation** | Specifies the animation to play by default. ** Loop Default** | Whether or not to loop the default animation. ** Default Animation Speed** | Controls the speed of the animation. Higher value means play the animation faster, smaller value means play the animation slower.
Setting | Description
**Minimum Shadow Graphics** | Minimum graphical setting at which shadows will be cast.
**Ignore Visareas** | Whether this component will ignore Vis Areas placed in the level. For more information about Vis Areas, please refer to the [Vis Area](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md) page.
**Ignore Terrain Layer Blending** | Controls blending with terrain layers. For more information, please refer to the [Terrain Layer Blending into Objects](../../../Materials/Terrain%20Layer%20Blending%20into%20Objects.md) page.
**Ignore Decal Blending** | Controls blending with decals. For more information about Decals, please refer to the [Decal](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Misc%20Objects/Decal%20Entity.md) page.
**View Distance** | View distance from 0 to 100 - where 100 = always visible.
**LOD Distance** | Level of Detail distance from 0 to 100 - where 100 = best LOD
**GI and Usage Mode** | Type of SVOGI to use. - **Disabled -** Object is excluded from voxelization and mostly does not affect the GI. (But it receives all GI effects from the rest of the scene). - ** Static Voxelization -** Object is voxelized allowing in-directional occlusion effects, large scale AO and more precise light bounce. - ** Analytical Proxy Soft -** An occluder applied during the cone tracing stage and used like a true replacement of voxels allowing also light bouncing from it. Occlusion fades with distance allowing softer shadow effects. - ** Analytical Proxy Hard -** An occluder applied during cone tracing stage and used like true replacement of voxels allowing also light bouncing from it. - ** Analytical Occluder -** An occluder applied in a deferred way after all cone tracing is performed. ** Analytical occluders** checkbox must be ** ON** in ** Total Illumination v2 settings** (** Tools -> Level Editor -> Level Settings ->****Total Illumination v2**) - ** Integrate into Terrain -** Integrates this mesh into the terrain mesh. This allows support for all terrain material features like 3-planar texturing. ** Integrate Objects** must be ** ON** in** Level Settings** (** Tools -> Level Editor -> Level Settings -> Terrain**).
**Default Animation** | Specifies the animation to play by default.
**Loop Default** | Whether or not to loop the default animation.
**Default Animation Speed** | Controls the speed of the animation. Higher value means play the animation faster, smaller value means play the animation slower.
**Physics** | Setting | Description --- | --- **Weight Type** | Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized. - ** Mass -** Mass of the object in kg. - ** Density-** Density of the object in Kg/m3. - ** Immovable -** Prevents the mesh entity from moving it is physicalized. ** Mass (pre-scale)** | Appears when ** Mass** is selected on the Weight Type list. It pre-scales the mass of the object in kg. ** Density** | Appears when ** Density** is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.
Setting | Description
**Weight Type** | Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized. - **Mass -** Mass of the object in kg. - ** Density-** Density of the object in Kg/m3. - ** Immovable -** Prevents the mesh entity from moving it is physicalized.
**Mass (pre-scale)** | Appears when **Mass** is selected on the Weight Type list. It pre-scales the mass of the object in kg.
**Density** | Appears when **Density** is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.

### Mesh

The Mesh Component adds static geometry to the entity which can be physicalized with a Rigid-body component.

Property | Description
--- | ---
**Mesh Settings** | Setting | Description --- | --- **Type** | Determines the behavior of the static mesh. ** File** | Determines the CGF to load. ** Material** | The material used for the entity. Changing this will change for example a rock to a bush, but won't change the name. Be careful when changing this!
Setting | Description
**Type** | Determines the behavior of the static mesh.
**File** | Determines the CGF to load.
**Material** | The material used for the entity. Changing this will change for example a rock to a bush, but won't change the name. Be careful when changing this!
**Rendering Settings** | Setting | Description --- | --- **Minimum Shadow Graphics** | Minimum graphical setting at which shadows will be cast for this object. ** Ignore Visareas** | Whether this component will ignore VisAreas. ** Ignore Terrain Layer Blending** | Defines if this component will ignore Terrain Layer Blending. ** Ignore Decal Blending** | Defines if this component will ignore Decal Blending. ** View Distance** | View distance from 0 to 100, 100 being always visible. ** LOD Distance** | Level of Detail distance from 0 to 100, 100 being always best LOD. ** GI and Usage Mode** | Type of SVOGI to use. - ** Disabled -** Object is excluded from voxelization and mostly does not affect the GI. (But it receives all GI effects from the rest of the scene). - ** Static Voxelization -** Object is voxelized allowing in-directional occlusion effects, large scale AO and more precise light bounce. - ** Analytical Proxy Soft -** An occluder applied during the cone tracing stage and used like a true replacement of voxels allowing also light bouncing from it. Occlusion fades with distance allowing softer shadow effects. - ** Analytical Proxy Hard -** An occluder applied during cone tracing stage and used like true replacement of voxels allowing also light bouncing from it. - ** Analytical Occluder -** An occluder applied in a deferred way after all cone tracing is performed. ** Analytical occluders** checkbox must be ** ON** in ** Total Illumination v2 settings** (** Tools -> Level Editor -> Level Settings ->****Total Illumination v2**) - ** Integrate into Terrain -** Integrates this mesh into the terrain mesh. This allows support for all terrain material features like 3-planar texturing. ** Integrate Objects** must be ** ON** in Level Settings (** Tools -> Level Editor -> Level Settings -> Terrain**)
Setting | Description
**Minimum Shadow Graphics** | Minimum graphical setting at which shadows will be cast for this object.
**Ignore Visareas** | Whether this component will ignore VisAreas.
**Ignore Terrain Layer Blending** | Defines if this component will ignore Terrain Layer Blending.
**Ignore Decal Blending** | Defines if this component will ignore Decal Blending.
**View Distance** | View distance from 0 to 100, 100 being always visible.
**LOD Distance** | Level of Detail distance from 0 to 100, 100 being always best LOD.
**GI and Usage Mode** | Type of SVOGI to use. - **Disabled -** Object is excluded from voxelization and mostly does not affect the GI. (But it receives all GI effects from the rest of the scene). - ** Static Voxelization -** Object is voxelized allowing in-directional occlusion effects, large scale AO and more precise light bounce. - ** Analytical Proxy Soft -** An occluder applied during the cone tracing stage and used like a true replacement of voxels allowing also light bouncing from it. Occlusion fades with distance allowing softer shadow effects. - ** Analytical Proxy Hard -** An occluder applied during cone tracing stage and used like true replacement of voxels allowing also light bouncing from it. - ** Analytical Occluder -** An occluder applied in a deferred way after all cone tracing is performed. ** Analytical occluders** checkbox must be ** ON** in ** Total Illumination v2 settings** (** Tools -> Level Editor -> Level Settings ->****Total Illumination v2**) - ** Integrate into Terrain -** Integrates this mesh into the terrain mesh. This allows support for all terrain material features like 3-planar texturing. ** Integrate Objects** must be ** ON** in Level Settings (** Tools -> Level Editor -> Level Settings -> Terrain**)
**Physics Settings** | Setting | Descripion --- | --- **Weight Type** | Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized. - ** Mass -** Mass of the object in kg. - ** Density -** Density of the object in Kg/m3**.** - ** Immovable -** Prevents the mesh entity from moving it is physicalized. ** Mass (pre-scale)** | Appears when ** Mass** is selected on the Weight Type list. It pre-scales the mass of the object in kg. ** Density** | Appears when ** Density** is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.
Setting | Descripion
**Weight Type** | Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized. - **Mass -** Mass of the object in kg. - ** Density -** Density of the object in Kg/m3**.** - ** Immovable -** Prevents the mesh entity from moving it is physicalized.
**Mass (pre-scale)** | Appears when **Mass** is selected on the Weight Type list. It pre-scales the mass of the object in kg.
**Density** | Appears when **Density** is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.

[Advanced Animations](#advanced-animations)[Alembic Mesh](#alembic-mesh)[Animated Mesh](#animated-mesh)[Mesh](#mesh)
