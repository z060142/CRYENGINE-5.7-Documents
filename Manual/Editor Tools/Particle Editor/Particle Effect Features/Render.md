# Render

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868306
- Page ID: 36868306
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Render
- Parent: Particle Effect Features

## Content

## Overview

In order to visualize the particles, a Render feature needs to be assigned to a particle component. Without it, particles will still simulate but will not be rendered. This can be a useful technique for the parent particles that only need to drive visible child particles. Render features will read the properties defined on the [Appearance](Appearance.md) feature and render particles accordingly.

For more information on parent child relationships, see [SecondGen](SecondGen.md).

The following options are available under the Render category:

### Decals

This feature renders each particle as a decal.

Properties | Description
--- | ---
**Thickness** | Specifies how thick the decals should be. Thicker decals can be more easily seen when placed near round scenery objects; but they can also distort more.
**Sort Bias** | Specifies the sorting order relative to the other decals in the scene.

Since decal particles are only visible when they are near other objects with correct alignment, it can be fairly tricky to tweak them. By adding Render: Sprites and setting the **Facing Mode** parameterto ** Free**, it is possible to visualize where decals are and to determine the potential reason why they might not be visible in a particular setup. For more information, please see [Render: Sprites](Render.md#Render-sprites).

### Meshes

This feature renders each particle as a separate static mesh.

Properties | Description
--- | ---
**Mesh** | Selects the mesh resource reference to be used by this feature.
**Scale** | Specifies non-uniform final scale applied to all meshes. Keep in mind that the Scale feature is applied after Size Mode.
**Size Mode** | Specifies how particle size should affect the size of the mesh that is being rendered: - **Size -** Ensures that the Mesh size is exactly the same as the particle size. For example, if the mesh would be a cube with each edge being 2 meters in size and the particle in question would have size 0.5 meters, then cubes would be rendered with 0.5 meters per side instead. - ** Scale -** Particle's size acts as a scale to the size of the mesh instead. Using the example above, the cube would be rendered with 1 meter per size since one meter is half of 2 meters.![Image](https://www.cryengine.com/docs/static/attachments/44107832) * A sample effect using different values*
**Origin Mode** | Determines the mesh's location relative to the particle position. - **Origin -** Enables the mesh's pivot to be aligned with the particles origin. - ** Center -** Creates new mesh pivots based on bounding box.
**Pieces Mode** | In CRYENGINE V, static mesh resources can be composed of sub-meshes. Feature Meshes can apply all sub-meshes to each particle which might only use a single sub-mesh; this is particularly useful for object destruction effects. Under Pieces Mode, the following options are available: - **Whole -** Ignores the sub-meshes and renders all of them together for each particle. - ** Random Piece -** Each time a new particle is born applies a random sub-mesh to the particle. Usually used to add mesh variation. - ** All Pieces -** Changes the rate at which particles are spawned so that each new particle gets a unique sub-mesh. Usually used for object destruction.
**Pieces Placement** | Allows feature's Meshes to act as [Location](Location.md) features. When paired with Pieces Mode and set to the All Pieces option, it allows the creation of object destruction effects. Under Pieces Placement, the following options are available: - **Standard -** Disables the placement of a piece. - ** Sub-Placement -** Offsets newborn particle position to the origin of the sub-piece assigned to the particle. Use in conjunction with ** Origin Mode** set to ** Origin**. - ** Centered Sub-Placement -** Offsets newborn particle to the center of the sub-piece assigned to the particle. Use in conjunction with ** Origin Mode** set to ** Center**.
**Cast Shadows** | When enabled, meshes start casting shadows. This option is set to **true** as default.

### Ribbon

This feature connects the particles together in a single line and with no gaps between them. For components without parents, it creates a single ribbon connecting all its particles whereas for components with parents, this feature ensures that each parent creates a separate ribbon. For more information about parent-child relationships, refer to [SecondGen](SecondGen.md).

All ribbons in a component are rendered together as a single primitive entity.

Properties | Description
--- | ---
**Ribbon Mode** | Specifies the method that will be used to generate ribbons. - **Camera -** Orients the ribbon towards the camera. The best outcome can be achieved when it's used for thin ribbons such as smoke trails or beams of light. - ** Free -** Uses free facing ribbons and Rotate3D to orient the ribbon. Ribbons using this mode can get twisted. The best outcome can be achieved when it's used for effects such as fabrics, paper rolls or whoosh effects of fast moving blades.
**Stream Source** | Specifies the source of the V axis for the diffuse map. - **Age -** Uses the age of the particle as a V axis. The best time to use this is when particles are continuously being spawned and immediately killed; for example, in rocket trails. - ** Spawn -** Uses the spawn order of the particle as a V axis. The best time to use it is when a predefined number of particles are spawned for each ribbon; for example lightning effects.
**Connect to Parent** | Usually, ribbons only connect particles that are available on the component. If the spawn rate of new particles is too low, the tip of the ribbons jumps towards the parent. When enabled, this setting adds an additional segment that is aligned to the parent particle or emitter of this component; meaning it will move along with the motion of the parent. This may not work in all cases; for example, when the ribbon particles are spawned with an offset relative to the parent
**Tessellated** | If set to true, ribbons will use hardware tessellation to smoothen the joints between segments. There are two CVars that affect this feature: - **r_ParticlesTessellation:** Enables particle tessellation and is set to 1 by default. - ** r_ParticlesTessellationTriSize:** Sets the particle tessellation screen-space triangle size in pixels and is set to 16 by default.
**Texture Frequency** | Specifies how often the V axis of the diffuse map repeats itself. Use this option with tiling textures along the V axis.
**Offset** | Adds an offset along the ribbon's spine. Can be used to generate spirals, twists or to avoid ribbons from self-intersecting when aligned to camera.
**Sort Bias** | Specifies the sorting order of components that are always based on distance to camera of the emitter to which they belong. This bias is added to that distance to reorder the component relative to other components. It can, for example, force rocket trails to always render on top of smoke trails.
**Fill Cost** | Weights the size of particles used for the filling feature controlled by the CVar **e_particleMaxScreenFill**. This feature computes the approximate total screen size of particles that are rendered, and gradually culls the largest particles if the total exceeds the limit. By default, all particles are weighted equally, but by setting ** Fill Cost** to a value ** above or below 1**, a component's particles can be made to cull more or less easily.

### Sprites

Renders all particles as simple flat planes. This is the standard way to render particles on the screen.

Properties | Description
--- | ---
**Sort Mode** | Determines the type of sorting to be used for particles; sorting is always applied in every frame. This is very important for semi-transparent particles since the order in which they render influences the final visual quality. If no sorting is applied, particles might start to randomly appear on top of each other. This is due to how particles are stored in memory. For components with fewer but larger particles, it is recommended to use sorting. However, sorting is not recommended for components with many small particles. - **None -** No sorting is applied to particles, and they will be rendered randomly. Use this method for the fastest rendering; but be aware that in some cases it can cause visual glitches. - ** Back to Front -** Starts with rendering the particles that are far away from the camera; then, it renders the ones that are the closest to the camera. This is the standard method to sort particles. - ** Front to Back -** Starts rendering with the particles which are closest to the camera. This will make the particles appear hollow. - ** Old to New -** Starts rendering with the oldest particles first, then it renders the more recent ones. - ** New to Old -** Starts rendering with the newest particles first and then it renders the oldest. If Appearance: Blending is to be used with the mode Additive, set this property to ** None**. Additive particles do not need sorting. Please refer to [Appearance](Appearance.md) for more details
**Facing Mode** | Specifies which way the particles should be facing. This method also considers rotated particles from the [Angles](Angles.md) feature. - **Screen -** Aligns sprites to face towards the screen. When the camera moves, i.e. looks around, it can make large particles that are in the distance affect different parts of the scene. This option can make things look unnatural. Therefore, it is best suited for small and close up particles. - ** Camera -** Makes sprites face towards the camera position. This option can make large close up particles flip around the camera as they move through the scene. Best suited for large particles in the distance. - ** Velocity -** Aligns sprites along its velocity vector while maintaining the face towards the camera. This method is fundamental for fast moving small particles. - ** Free -** Allows sprites to be free of any constraint and only uses Rotation3D to orient itself. Best used when particles are trying to simulate small solid objects instead of participating mediums; for example, objects such as falling leaves as opposed to smoke clouds.
**Aspect Ratio** | Specifies how larger the width should be than the height. By default, sprites are squares. This option can be used to avoid distortion when diffuse textures are not squares.
**Axis Scale** | Valid only when Facing Mode is set to Velocity and it specifies the dimensions of the particle along its velocity vector while the height of the particle is always constrained to its size. Recommended value for this property is 0.016 (which is 1/60) which makes sprite behave like motion blur.
**Spherical Projection** | Extends the size of the particle relative to the screen to encompass the shape of a sphere. A value of 0 means the sprite will always behave like a regular flat plane. A value of 1 will make the sprite fully encompass that sphere. This property is not valid for particles that use Free as facing mode.
**Sort Bias** | Specifies the sorting order of components which are always based on the distance to the camera of the emitter to which they belong. While Sort Mode specifies sorting of sprites within a component, sprites do not sort themselves with other components. This bias is added to that distance to reorder the component relative to other components. It can, for example, force fire particles to always render on top of smoke.
**Camera Offset** | Offsets the sprite location relative to the camera in meters. Positive values will move sprites away from the camera, while negative values will move sprites toward the camera. Usually used to better place sprites relative to other game objects and regardless of camera orientation.
**Offset** | Changes sprite's pivot point.
**Flip U and Flip V** | Flips the coordinates of the diffuse texture if needed. Activating both is equivalent to spinning the sprite by 180 degrees.
**Fill Cost** | Weights the size of particles used for the filling feature controlled by the CVar **e_particleMaxScreenFill**. This feature computes the approximate total screen size of particles that are rendered, and gradually culls the largest particles if the total exceeds the limit. By default, all particles are weighted equally, but by setting ** Fill Cost** to a value ** above or below 1**, a component's particles can be made to cull more or less easily.

[Decals](#decals)[Meshes](#meshes)[Ribbon](#ribbon)[Sprites](#sprites)
