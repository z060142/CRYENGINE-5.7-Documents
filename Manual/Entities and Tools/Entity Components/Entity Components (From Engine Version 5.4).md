# Entity Components (From Engine Version 5.4)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28180928
- Page ID: 28180928
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.4)
- Parent: Entity Components

## Content

## Overview

The Components panel contains all of the available Components that can be applied to an Entity. This article details the individual settings for each of the Components.

![Image](https://www.cryengine.com/docs/static/attachments/28248338)

### Transformation

![Image](https://www.cryengine.com/docs/static/attachments/28248339)

Many of the components have a Transform setting. This allows their position and orientation to be offset from the entity they are attached to, while still following it.

Setting | Description
--- | ---
**Translation** | The positional offset in relation to the entity - for example a value of 0,0,1 will mean an offset of one unit upwards (Z axis).
**Rotation** | The rotation offset in relation to the entity.
**Scale** | The scale offset in relation to the entity. The linking symbol locks the scaling so that the values are relative to each other. For e.g. a value of 1,2,3, scaled by 2x would result in 2,4,6. (if unlocked then the scaling cannot be guaranteed).

### AI - Pathfinder

![Image](https://www.cryengine.com/docs/static/attachments/28248340)

Setting | Description
--- | ---
**Maximum Acceleration** | Maximum possible physical acceleration that the AI entity can move at.

### Audio - Listener

![Image](https://www.cryengine.com/docs/static/attachments/28248341)

Setting | Description
--- | ---
**Translation** | The positional offset in relation to the entity - for example a value of 0,0,1 will mean an offset of one unit upwards (Z axis).
**Rotation** | The rotation offset in relation to the entity.
**Scale** | The scale offset in relation to the entity. The linking symbol locks the scaling so that the values are relative to each other. For e.g. a value of 1,2,3, scaled by 2x would result in 2,4,6. (if unlocked then the scaling cannot be guaranteed).

### Audio - Trigger

![Image](https://www.cryengine.com/docs/static/attachments/28248342)

**Setting** | **Description**
--- | ---
**PlayTrigger** | This trigger gets executed when Play is called.
**StopTrigger** | This trigger gets executed when Stop is called.
**Play** | Executes the PlayTrigger.
**Stop** | Stops the PlayTrigger if no StopTrigger assigned - otherwise executes the StopTrigger.

### Cameras - Camera

![Image](https://www.cryengine.com/docs/static/attachments/28248343)

Setting | Description
--- | ---
**Active** | Whether or not this camera should be activated on component creation.
**Near Plane** | Sets the distance from the camera that we will start rendering from (by default 0.25 meters).
**Field of View** | The field of view or angle that the camera will render.
**Translation** | The positional offset in relation to the entity - for example a value of 0,0,1 will mean an offset of one unit upwards (Z axis).
**Rotation** | The rotation offset in relation to the entity.
**Scale** | The scale offset in relation to the entity. The linking symbol locks the scaling so that the values are relative to each other. For e.g. a value of 1,2,3, scaled by 2x would result in 2,4,6. (if unlocked then the scaling cannot be guaranteed).

### Debug - Debug Draw

![Image](https://www.cryengine.com/docs/static/attachments/28248344)

Setting | Description
--- | ---
**Draw Persistent Text** | Whether persistent text will be drawn to the screen.
**Persistent Text** | The persistent text to draw to the screen.
**Persistent Text Color** | The color of the persistent text.
**Persistent View Distance** | The maximum view distance for the persistent text.
**Persistent Font Size** | The font size of the persistent text.

### Effects - Fog Volume

*![Image](https://www.cryengine.com/docs/static/attachments/28248345)*

Setting | Description
--- | ---
**Active** | Whether or not the fog volume is currently active.
**Type** | The type of shape to use for rendering the fog volume.
**Size** | Size of the fog volume.
**Color** | Color of the fog volume.
**Use Global Fog Color** | Whether or not to use the global fog color for this fog volume.
**Ignore VisAreas** | Whether the fog volume ignores the use of VisAreas in the level.
**Only Affect This Area** | Whether the fog volume can only affect the area it is currently in.
**Global Density** | Controls the density of the fog volume.
**Density Offset** | Additional controls to the density of the fog volume.
**Height Falloff Longitude** | Direction of the fall off (longitude). 0 = East (Positive X).
**Height Falloff Latitude** | Direction of the fall off (latitude). 90 = up.
**Height Falloff Shift** | Controls how much to shift the fog density along the fall off direction.
**Height Falloff Scale** | Scales the density distribution along the fall off direction. Higher values will make the fog fall off more rapidly.

### Effects - Decal

*![Image](https://www.cryengine.com/docs/static/attachments/28248346)*

Setting | Description
--- | ---
**Default Spawn** | Whether or not to automatically spawn the decal.
**Material** | The material we want to use on the decal.
**Follow Entity** | Whether or not the decal follows the entity.
**Projection Type** | The method of projection to be used.
**Projection Depth** | The depth at which the decal should be projected.
**Sort Priority** | Sorting priority - used to resolve depth issues with other decals.

### Effects - Particle Emitter

*![Image](https://www.cryengine.com/docs/static/attachments/28248347)*

Setting | Description
--- | ---
**Enabled** | Whether or not the particle should emit by default.
**Effect** | Determines the particle effect to load.
**Particle Spec** | Overrides Particle Spec for this emitter.
**Uniform Scale** | Emitter uniform scale.
**Count Scale** | Particle count multiplier.
**Speed Scale** | Particle emission speed multiplier.
**Time Scale** | Emitter time multiplier.
**Prime** | Advances emitter age to its equilibrium state.

### General - SensorVolume

*![Image](https://www.cryengine.com/docs/static/attachments/28248348)*

Setting | Description
--- | ---
**Shape** | Shape of the volume.
**Size** | Determines the size of the shape.
**Attribute** | Identifiers of this volume.
**Listener** | Determines to which attribute we want to listen. You will only receive signals for those specific attributes.

### Geometry - Animated Mesh

*![Image](https://www.cryengine.com/docs/static/attachments/28248349)*

Setting | Description
--- | ---
**Type** | Determines the behavior of the mesh.
**File** | Determines the animated mesh to load.
**Minimum Shadow Graphics** | Minimum graphical setting at which shadows will be cast.
**Ignore Visareas** | Whether this component will ignore vis areas placed in the level.
**View Distance** | View distance from 0 to 100 - where 100 = always visible.
**LOD Distance** | Level of Detail distance from 0 to 100 - where 100 = best LOD.
**Global Illumination** | Type of SVOGI to use.
**DefaultAnimation** | Specifies the animation to play by default.
**Loop Default** | Whether or not to loop the default animation.
**Mass** | Mass of the object in kg. Note: Mass cannot be set at the same time as density.
**Density** | Density of the object in Kg/m3. Note: Density cannot be set at the same time as mass.

### Geometry - Advanced Animations

*![Image](https://www.cryengine.com/docs/static/attachments/28248350)*

Setting | Description
--- | ---
**Type** | Determines the behavior of the static mesh.
**Character** | Determines the character to load.
**Minimum Shadow Graphics** | Minimum graphical setting at which shadows will be cast.
**Ignore Visareas** | Whether this component will ignore vis areas placed in the level.
**View Distance** | View distance from 0 to 100 - where 100 = always visible.
**LOD Distance** | Level of Detail distance from 0 to 100 0 - where 100 = best LOD.
**Global Illumination** | Type of SVOGI to use.
**Animation Database** | Path to the Mannequin.adb file.
**Controller Definition** | Path to the Mannequin controller definition file.
**Default Scope Context Name** | Name of the default Mannequin scope context to use.
**Default Fragment Name** | Name of the default Mannequin fragment to play.
**Animation Driven Motion** | Whether or not to use root motion in the animations for physical movement.
**Use Ground Alignment** | Enables adjustment of leg positions to align to the ground surface.
**Mass** | Mass of the object in kg. Note: Mass cannot be set at the same time as density.
**Density** | Density of the object in Kg/m3. Note: Density cannot be set at the same time as mass.

### Geometry - Alembic Mesh

*![Image](https://www.cryengine.com/docs/static/attachments/28248351)*

Setting | Description
--- | ---
**File** | The geom cache file (.abc or.cbc) to load.

### Mesh

*![Image](https://www.cryengine.com/docs/static/attachments/28248352)*

Setting | Description
--- | ---
**Type** | Determines the behavior of the mesh.
**File** | Determines the CGF to load.
**Minimum Shadow Graphics** | Minimum graphical setting at which shadows will be cast for this object.
**Ignore Visareas** | Whether this component will ignore vis areas.
**View Distance** | View distance from 0 to 100, 100 being always visible.
**LOD Distance** | Level of Detail distance from 0 to 100, 100 being always best LOD.
**Global Illumination** | Type of SVOGI to use.
**Mass** | Mass of the object in kg. Note: Mass cannot be set at the same time as density.
**Density** | Density of the object in Kg/m3. Note: Density cannot be set at the same time as mass.

### Lights - Environment Probe

*![Image](https://www.cryengine.com/docs/static/attachments/28248353)*

Setting | Description
--- | ---
**Active** | Determines whether the environment probe is enabled.
**Box Size** | Size of the area the probe affects.
**IgnoreVisAreas** | Whether to ignore vis areas placed in the level.
**Sort Priority** | Sorting priority, used to resolve depth issues with other light sources.
**Maximum Attenuation Falloff** | Maximum Attenuation Falloff.
**Affect Volumetric Fog** | Whether this probe will affect volumetric fog.
**Only Affect Volumetric Fog** | Whether this probe will **only** affect volumetric fog.
**Only Affect This Area** | Whether this probe will **only** affect the area it is currently in.
**Use Box Projection** | Whether to use box projection for this environment probe.
**Color** | Color for the probe.
**Diffuse Multiplier** | Diffuse color multiplier for the probe.
**Specular Multiplier** | Specular color multiplier for the probe.
**Cube Map Path** | Path to the cube map to load.
**Load Texture Automatically** | Whether to attempt loading a texture when the environment probe is created.
**Resolution** | Resolution of the probe (Editor only).
**Generate** | Generates a cube map with the specified resolution (Editor only).

### Lights - Point Light

*![Image](https://www.cryengine.com/docs/static/attachments/28248354)*

Setting | Description
--- | ---
**Active** | Determines whether the point light is enabled.
**Radius** | Determines the range of the point light.
**Color** | Color of the point light.
**Diffuse Multiplier** | Diffuse color multiplier for the point light.
**Specular Multiplier** | Specular color multiplier for the point light.
**Minimum Shadow Graphics** | Minimum graphical setting to cast shadows.
**Attenuation Bulb Size** | Controls the falloff exponentially from the origin. A value of 1 means that the light is at full intensity (within a 1 meter ball) before it begins to falloff. See Attenuation and Falloff for more information.
**Ignore VisAreas** | Whether the light source ignores VisAreas in the level.
**Affect Volumetric Fog** | Whether the light source should affect volumetric fog.
**Only Affect Volumetric Fog** | Whether the light source will **only** affect volumetric fog.
**Only Affect This Area** | Whether the light source will **only** affect the area it is currently in.
**Ambient** | Makes the light behave like an ambient light source, with no point of origin.
**Fog Radial Lobe** | Adjusts the blend ratio of the main radial lobe (parallel to the eye ray) and side radial lobe (perpendicular to the eye ray). The direction of the main radial lobe depends on the Anisotropic parameter value used (found in the Time of Day dialog window).
**Global Illumination** | Determines how this light interacts with Global Illumination.
**Style** | The animation style of the light.
**Speed** | The animation speed of the light.

### Lights - Projector Light

******![Image](https://www.cryengine.com/docs/static/attachments/28248355)******

Setting | Description
--- | ---
**Active** | Determines whether the projector light is enabled.
**Range** | Determines the range of the projector light.
**Angle** | Determines the angle/field of view of the projector light.
**Near Plane** | Determines the distance from the light itself and where it will start projecting.
**Projected Texture** | The texture to project.
**Material** | The material to project.
**Color** | Color of the projector light source.
**Diffuse Multiplier** | Diffuse color multiplier for the projector light source.
**Specular Multiplier** | Specular color multiplier of the projector light source.
**Minimum Shadow Graphics** | Minimum graphical setting to cast shadows.
**Attenuation Bulb Size** | Controls the falloff exponentially from the origin. A value of 1 means that the light is at full intensity (within a 1 meter ball) before it begins to falloff. See Attenuation and Falloff for more information.
**Ignore VisAreas** | Whether the light source ignores VisAreas in the level.
**Affect Volumetric Fog** | Whether the light source should affect volumetric fog.
**Only Affect Volumetric Fog** | Whether the light source will **only** affect volumetric fog.
**Only Affect This Area** | Whether the light source will **only** affect the area it is currently in.
**Ambient** | Makes the light behave like an ambient light source, with no point of origin.
**Fog Radial Lobe** | Adjusts the blend ratio of the main radial lobe (parallel to the eye ray) and side radial lobe (perpendicular to the eye ray). The direction of the main radial lobe depends on the Anisotropic parameter value used (found in the Time of Day dialog window).
**Global Illumination** | Determines how this light interacts with Global Illumination.
**Style** | The animation style of the light.
**Speed** | The animation speed of the light.

### Physics - Box Collider

*![Image](https://www.cryengine.com/docs/static/attachments/28248356)*

Setting | Description
--- | ---
**Size** | Size of the box.
**Mass** | Mass of the object in kg. Note: Mass cannot be set at the same time as density.
**Density** | Density of the object in Kg/m3. Note: Density cannot be set at the same time as mass.
**Surface Type** | Surface type assigned to this object - determines its physical properties.

### Physics - Character Controller

*![Image](https://www.cryengine.com/docs/static/attachments/28248358)*

Setting | Description
--- | ---
**Networked Synced** | Syncs the physical entity over the network and keeps it in sync with the server.
**Mass** | Mass of the character in kg.
**Collider Radius** | Radius of the default capsule or cylinder.
**Collider Height** | Height of the default capsule or cylinder.
**Use Capsule** | Whether to use a capsule for the default geometry, otherwise a cylinder.
**Send Collision Signal** | Whether or not this component should listen for collisions and report them.
**Air Control Ratio** | Indicates how much the character can move in the air, 0 = no movement, 1 = full control.
**Air Resistance** | Air resistance for the character.
**Inertia Coefficient** | A larger value gives a greater dampening effect, whereas a value of 0 gives no dampening effect.
**Inertia Acceleration Coefficient** | A larger value gives a greater dampening effect on acceleration, whereas a value of 0 gives no dampening effect.
**Maximum Climb Angle** | Maximum angle the character can climb.
**Maximum Jump Angle** | Maximum angle the character can jump at.
**Minimum Angle For Slide** | Minimum angle before the character starts sliding.
**Minimum Angle For Fall** | Minimum angle before the character starts falling.
**Maximum Surface Velocity** | Maximum velocity of the surface the character is on before they are considered airborne and slide off.

### Physics - Cylinder Collider

*![Image](https://www.cryengine.com/docs/static/attachments/28248359)*

Setting | Description
--- | ---
**Radius** | Radius of the cylinder.
**Height** | Height of the cylinder.
**Mass** | Mass of the object in kg. Note: Mass cannot be set at the same time as density.
**Density** | Density of the object in Kg/m3. Note: Density cannot be set at the same time as mass.
**Surface Type** | Surface type assigned to this object - determines its physical properties

### Physics - Capsule Collider

**![Image](https://www.cryengine.com/docs/static/attachments/28248360)**

Setting | Description
--- | ---
**Radius** | Radius of the capsule.
**Height** | Height of the capsule.
**Mass** | Mass of the object in kg. Note: Mass cannot be set at the same time as density.
**Density** | Density of the object in Kg/m3. Note: Density cannot be set at the same time as mass.
**Surface Type** | Surface type assigned to this object - determines its physical properties.

### Physics - RigidBody

***![Image](https://www.cryengine.com/docs/static/attachments/28248361)***

Setting | Description
--- | ---
**Networked Synced** | Syncs the physical entity over the network and keeps it in sync with the server.
**Enabled by Default** | Whether the physics of the entity will be enabled by default.
**Type** | Type of physicalized object to create.
**Send Collision Signal** | Whether or not this component should listen for collisions and report them to Schematyc.

### Physics - Sphere Collider

****![Image](https://www.cryengine.com/docs/static/attachments/28248362)****

Setting | Description
--- | ---
**Radius** | Radius of the sphere.
**Mass** | Mass of the object in kg. Note: Mass cannot be set at the same time as density.
**Density** | Density of the object in Kg/m3. Note: Density cannot be set at the same time as mass.
**Surface Type** | Surface type assigned to this object, determines its physical properties

### Physics Constraint - Point Constraint

****![Image](https://www.cryengine.com/docs/static/attachments/28248363)****

Setting | Description
--- | ---
**Active** | Whether or not the constraint should be added when the component is created.
**Axis** | Axis around which the physical entity is constrained.
**Minimum X Angle** | The minimum angle for the primary axis that the object will be constrained to.
**Maximum X Angle** | The maximum angle for the primary axis that the object will be constrained to.
**Minimum YZ Angle** | The minimum angle for the other axes that the object will be constrained to.
**Maximum YZ Angle** | The maximum angle for the other axes that the object will be constrained to.
**Damping** | Determines how much the object loses momentum (as it moves) while the constraint is active.

### Physics Constraint - Line Constraint

****![Image](https://www.cryengine.com/docs/static/attachments/28248364)****

Setting | Description
--- | ---
**Active** | Whether or not the constraint should be added when the component is created.
**Lock Rotation** | Whether the constrained object will be allowed to rotate.
**Axis** | Axis around which the physical entity is constrained.
**Minimum Limit** | Minimum position that the entity can be moved to form the constraint pivot. A unit of -1 indicates that the minimum position is one meter behind the entity.
**Maximum Limit** | Maximum position that the entity can be moved to form the constraint pivot. A unit of +1 indicates that the maximum position is one meter ahead of the entity.
**Damping** | Determines how much the object loses momentum (as it moves) while the constraint is active.

### Physics Constraint - Plane Constraint

****![Image](https://www.cryengine.com/docs/static/attachments/28248365)****

Setting | Description
--- | ---
**Active** | Whether or not the constraint should be added when the component is created.
**Axis** | Axis around which the physical entity is constrained.
**Minimum Limit X** | Determines how far the constrained object can move to the left.
**Maximum Limit X** | Determines how far the constrained object can move to the right.
**Minimum Limit Y** | Determines how far the constrained object can move to the top.
**Maximum Limit Y** | Determines how far the constrained object can move to the bottom.
**Damping** | Determines how much the object loses momentum (as it moves) while the constraint is active.

[Transformation](#transformation)[AI - Pathfinder](#ai-pathfinder)[Audio - Listener](#audio-listener)[Audio - Trigger](#audio-trigger)[Cameras - Camera](#cameras-camera)[Debug - Debug Draw](#debug-debug-draw)[Effects - Fog Volume](#effects-fog-volume)[Effects - Decal](#effects-decal)[Effects - Particle Emitter](#effects-particle-emitter)[General - SensorVolume](#general-sensorvolume)[Geometry - Animated Mesh](#geometry-animated-mesh)[Geometry - Advanced Animations](#geometry-advanced-animations)[Geometry - Alembic Mesh](#geometry-alembic-mesh)[Mesh](#mesh)[Lights - Environment Probe](#lights-environment-probe)[Lights - Point Light](#lights-point-light)[Lights - Projector Light](#lights-projector-light)[Physics - Box Collider](#physics-box-collider)[Physics - Character Controller](#physics-character-controller)[Physics - Cylinder Collider](#physics-cylinder-collider)[Physics - Capsule Collider](#physics-capsule-collider)[Physics - RigidBody](#physics-rigidbody)[Physics - Sphere Collider](#physics-sphere-collider)[Physics Constraint - Point Constraint](#physics-constraint-point-constraint)[Physics Constraint - Line Constraint](#physics-constraint-line-constraint)[Physics Constraint - Plane Constraint](#physics-constraint-plane-constraint)
