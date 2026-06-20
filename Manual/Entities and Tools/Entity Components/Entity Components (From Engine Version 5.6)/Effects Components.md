# Effects Components

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966055
- Page ID: 44966055
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6) > Effects Components
- Parent: Entity Components (From Engine Version 5.6)

## Content

### Decal

The Decal Component will project a texture onto geometry and terrain. A typical use case for a decal would be for example blood splashes.

Setting | Description
--- | ---
**Default Spawn** | Whether or not to automatically spawn the decal.
**Material** | The material we want to use on the decal.
**Follow Entity** | Whether or not the decal follows the entity.
**Projection Type** | The method of projection to be used. - **Planar -** The decal will be displayed in the exact same position in space as where you placed the center of the object. It is advised to only use this project type on flat surfaces, otherwise you may find the decal "floating" in the air. Planar projection offers the cheapest performance. - ** Static Objects -** The decal will be projected onto the geometry of an object in the level. It will be projected along the opposite direction of the blue Z axis. This method is automatically done as a deferred pass. - ** Terrain -** The decal will be projected directly on to the terrain of your level, ignoring any assets that might otherwise receive the projection. - ** Terrain and Static Objects -** This projection type is a combination of type 2 and 3, and will be displayed on both the terrain and objects. This method is automatically performed as a deferred pass.
**Projection Depth** | The depth at which the decal should be projected.
**Sort Priority** | Sorting priority - used to resolve depth issues with other decals.

### Fog Volume

The Fog Volume Component adds an area of fog around the components position. This can be used to create local areas of fog instead of global fog through the environment editor.

Property | Description
--- | ---
**Fog Volume** | Settings | Description --- | --- **Active** | Whether or not the fog volume is currently active. ** Type** | The type of shape to use for rendering the fog volume. ** Size** | Size of the fog volume. ** Color** | Albedo color of the fog volume, as revealed by external light sources. (with no external light, this will be black) ** Emission** | At luminance values greater than 0, assigns an emissive color to the fog volume (i.e., a color that doesn't require external light to be visible). Only works when Volumetric Fog is enabled. ** Emission Intensity** | Specifies how much luminance (kcd/m2) the fog emits. Only in effect if the Emission color has a luminance greater than 0.
Settings | Description
**Active** | Whether or not the fog volume is currently active.
**Type** | The type of shape to use for rendering the fog volume.
**Size** | Size of the fog volume.
**Color** | Albedo color of the fog volume, as revealed by external light sources. (with no external light, this will be black)
**Emission** | At luminance values greater than 0, assigns an emissive color to the fog volume (i.e., a color that doesn't require external light to be visible). Only works when Volumetric Fog is enabled.
**Emission Intensity** | Specifies how much luminance (kcd/m2) the fog emits. Only in effect if the Emission color has a luminance greater than 0.
**Options** | These options changes different aspects of the Fog Volume that would be attached to the entity. Setting | Description --- | --- **Use Global Fog Color** | Whether or not to use the fog volume fog uses the color set globally in the environment editor's Variables → Volumetric Fog → Color (Entities). ** Ignore VisAreas** | Whether the fog volume ignores the use of VisAreas in the level. ** Only Affect This Area** | When enabled, * constrains* the fog volume only to a clip volume if placed inside it, or, if placed * outside* a clip volume and * linked* to it, * excludes* the fog from the clip volume. **Global Density** | Controls the density of the fog volume. ** Density Offset** | Scales the density inside the fog volume. ** Near Cutoff** | Stop rendering the object, depending on camera distance to object. ** Soft Edges** | Specifies a factor that is used to soften the edges of the fog volume when viewed from outside. A value of 0.0 produces hard edges. Increasing this value up to 1.0 will gradually soften the edges. ** Height Falloff Longitude** | Direction of the falloff. 0 = East; i.e. a positive X value. Determines how strong the fog loses density in the longitude/horizontal direction. ** Height Falloff Latitude** | Direction of the falloff. 90 = up. ** Height Falloff Shift** | Controls how much to shift the fog density along the falloff direction. ** Height Falloff Scale** | Scales the density distribution along the falloff direction. Higher values will make the fog fall off more rapidly. ** Ramp Start** | Defines the distance where the fog starts density begins to increase from 0, multiplied by Ramp Influence Only works when volumetric fog is enabled. Also scales with Ramp influence. ** HDR Dynamic** | Lighting multiplier for when LDR is being used to make lighting fit to HDR lighting manually. ** Ramp End** | The distance at which the fog density reaches the value set by the Global Density property, multiplied by Ramp Influence ** Ramp Influence** | Scaler how much Ramp Start / End should influence the fog density. ** Wind Influence** | Scaler how much wind influences the fog. Only works with volumetric fog enabled. Scales with Density Noise Scale. ** Density Noise Scale** | Scaler for the noise distribution that generates the fog density. Only works with volumetric fog enabled. ** Density Noise Offset** | Offset on the noise distribution function that generates the fog density. Only works with volumetric fog enabled. ** Density Noise Time Frequency** | Controls the time frequency of the noise for the density. High frequencies produce fast changing fog. ** Density Noise Frequency** | Controls the spatial frequency of the noise for the density. High frequencies produce highly detailed fog.
Setting | Description
**Use Global Fog Color** | Whether or not to use the fog volume fog uses the color set globally in the environment editor's Variables → Volumetric Fog → Color (Entities).
**Ignore VisAreas** | Whether the fog volume ignores the use of VisAreas in the level.
**Only Affect This Area** | When enabled, *constrains* the fog volume only to a clip volume if placed inside it, or, if placed * outside* a clip volume and * linked* to it, * excludes* the fog from the clip volume.
**Global Density** | Controls the density of the fog volume.
**Density Offset** | Scales the density inside the fog volume.
**Near Cutoff** | Stop rendering the object, depending on camera distance to object.
**Soft Edges** | Specifies a factor that is used to soften the edges of the fog volume when viewed from outside. A value of 0.0 produces hard edges. Increasing this value up to 1.0 will gradually soften the edges.
**Height Falloff Longitude** | Direction of the falloff. 0 = East; i.e. a positive X value. Determines how strong the fog loses density in the longitude/horizontal direction.
**Height Falloff Latitude** | Direction of the falloff. 90 = up.
**Height Falloff Shift** | Controls how much to shift the fog density along the falloff direction.
**Height Falloff Scale** | Scales the density distribution along the falloff direction. Higher values will make the fog fall off more rapidly.
**Ramp Start** | Defines the distance where the fog starts density begins to increase from 0, multiplied by Ramp Influence Only works when volumetric fog is enabled. Also scales with Ramp influence.
**HDR Dynamic** | Lighting multiplier for when LDR is being used to make lighting fit to HDR lighting manually.
**Ramp End** | The distance at which the fog density reaches the value set by the Global Density property, multiplied by Ramp Influence
**Ramp Influence** | Scaler how much Ramp Start / End should influence the fog density.
**Wind Influence** | Scaler how much wind influences the fog. Only works with volumetric fog enabled. Scales with Density Noise Scale.
**Density Noise Scale** | Scaler for the noise distribution that generates the fog density. Only works with volumetric fog enabled.
**Density Noise Offset** | Offset on the noise distribution function that generates the fog density. Only works with volumetric fog enabled.
**Density Noise Time Frequency** | Controls the time frequency of the noise for the density. High frequencies produce fast changing fog.
**Density Noise Frequency** | Controls the spatial frequency of the noise for the density. High frequencies produce highly detailed fog.

### Particle Emitter

The Particle Emitter Component can emit particles at the position of the parent entity.

Property | Description
--- | ---
**Particle Emitter Settings** | Setting | Description --- | --- **Enabled** | Whether or not the particle should emit by default. ** Effect** | Determines the particle effect to load. To load a particle effect, click on the ** Browse** button; to edit the particle effect that you would like to use, click on the ** Edit** button. ** Emitter Attributes** | Adjustable values which can be defined in the particle effect itself. ** Emitter Features** | Adds new features to the particle editor in use. The features displayed on the ** Emitter Features** dropdown menu are the same features that can be found in the Particle Editor. For more information about the functionality of each particle effect feature, please refer to the [Particle Effect Features](../../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features.md) page.
Setting | Description
**Enabled** | Whether or not the particle should emit by default.
**Effect** | Determines the particle effect to load. To load a particle effect, click on the **Browse** button; to edit the particle effect that you would like to use, click on the ** Edit** button.
**Emitter Attributes** | Adjustable values which can be defined in the particle effect itself.
**Emitter Features** | Adds new features to the particle editor in use. The features displayed on the **Emitter Features** dropdown menu are the same features that can be found in the Particle Editor. For more information about the functionality of each particle effect feature, please refer to the [Particle Effect Features](../../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features.md) page.
**Spawn Parameters** | Setting | Description --- | --- **Prime** | Advances emitter age to its equilibrium state. ** Uniform Scale** | Emitter uniform scale. ** Count Scale** | Particle count multiplier. ** Speed Scale** | Particle emission speed multiplier. ** Time Scale** | Emitter time multiplier. ** Particle Spec** | Overrides Particle Spec for this emitter. ** Ignore Vis Areas** | Whether this component will ignore Vis Areas placed in the level. For more information about Vis Areas, please refer to the [Vis Area](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md) page. ** Ignore Terran Layer Blend** | Controls blending with terrain layers. For more information, please refer to the [Terrain Layer Blending into Objects](../../../Materials/Terrain%20Layer%20Blending%20into%20Objects.md) page. ** Ignore Decal Blend** | Controls blending with decals. For more information about Decals, please refer to the [Decal](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Misc%20Objects/Decal%20Entity.md) page. ** Custom Random Seed** | Controls if the effect should follow a specific seed, which makes the effect deterministic, or if it should be entirely random.
Setting | Description
**Prime** | Advances emitter age to its equilibrium state.
**Uniform Scale** | Emitter uniform scale.
**Count Scale** | Particle count multiplier.
**Speed Scale** | Particle emission speed multiplier.
**Time Scale** | Emitter time multiplier.
**Particle Spec** | Overrides Particle Spec for this emitter.
**Ignore Vis Areas** | Whether this component will ignore Vis Areas placed in the level. For more information about Vis Areas, please refer to the [Vis Area](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md) page.
**Ignore Terran Layer Blend** | Controls blending with terrain layers. For more information, please refer to the [Terrain Layer Blending into Objects](../../../Materials/Terrain%20Layer%20Blending%20into%20Objects.md) page.
**Ignore Decal Blend** | Controls blending with decals. For more information about Decals, please refer to the [Decal](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Misc%20Objects/Decal%20Entity.md) page.
**Custom Random Seed** | Controls if the effect should follow a specific seed, which makes the effect deterministic, or if it should be entirely random.

### Rain

This component creates rain in a radius around the entity that you attach this component to. This is the quickest way to introduce rain into the level; however, if you want to create a rain effect with different properties, please refer to the [Creating an Omnipresent Colliding Effect](../../../Tutorials/Graphics/Particle%20Tutorials/Tutorial%20-%20Creating%20an%20Omnipresent%20Colliding%20Effect.md) page.

Setting | Description
--- | ---
**Enable** | Enables rain around the Entity.
**Color** | **DEPRECATED**
**Amount** | Set the overall amount of the rain entity's various effects.
**Ignore Visareas** | Continue to render rain when player is inside a visarea.
**Disable Occlusion** | Don't check if object should be occluded from rain (is under cover).
**Radius** | The size of the area around the entity Entity in which the rain will be falling.
**Glossiness** | **DEPRECATED**
**Reflection Amount** | **DEPRECATED**
**Diffuse Darkening** | Defines how dark the puddles and rain are.
**Rain Drops Amount** | Set the amount of rain drops that can be seen in the air.
**Rain Drops Speed** | Set the speed at which the rain drops travel.
**Rain Drops Lighting** | Set the brightness or backlighting of the rain drops.
**Mist Amount** | **DEPRECATED**
**Mist Height** | **DEPRECATED**
**Puddles Amount** | Amount of puddles the rain creates on the ground Scaler value depends on the surface normal and puddle mask for location.
**Puddles Mask Amount** | Set the strength of the puddle mask to balance different puddle results.
**Puddles Ripple Amount** | Set the strength and frequency of the puddles generated by the rain (offset PuddlesAmount).
**SplashesAmount** | Amount of splashes the rain creates on the ground (it just scales the amount of splashes)

### Water Ripple

Allows to spawn ripples on water surfaces. It is especially useful for cutscenes when non-physicalized entities are moving through a body of water.

Setting | Description
--- | ---
**Scale** | Size of the ripple effect.
**Strength** | Strength of the ripple effect. Also affects size. The most noticeable changes happen in the range from 0 to 1.
**Frequency** | Sets the interval for **AutoSpawn** in seconds.
**Random Frequency** | Randomly changes the frequency of the ripple effect. The value specified is the maximum frequency that will occurr.
**Random Scale** | Randomly sets the scale of the ripple effect. The value specified is the maximum scale that can be set.
**Random Strength** | Same as Random Scale, but for the Strength value.
**Enable** | Turns the entity on/off.
**Auto Spawn** | If enabled, water ripples will be spawned regularly even if the entity doesn't move. The spawn interval is determined by the Frequency and RandomFreq properties.
**Spawn On Movement** | If enabled, ripples will be spawned when the entity moves.
**Random Offset** | Randomly spawns ripples at an offset position relative to the entity. These values set the maximum offset on the X and Y axes (local coordinate system). Only works if **AutoSpawn** is enabled.

[Decal](#decal)[Fog Volume](#fog-volume)[Particle Emitter](#particle-emitter)[Rain](#rain)[Water Ripple](#water-ripple)
