# Environment Probe Entity

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869875
- Page ID: 36869875
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Misc Objects > Environment Probe Entity
- Parent: Misc Objects

## Content

## Overview

With Environment Probes you have the ability to place cubemaps easily throughout a level just as you would a light. It is very useful especially with reflective materials because it will automatically assign the cubemap to anything within its radius.

This tool can be useful when used with dynamic lighting as well; it just requires a minor Flow Graph setup so that the different probes used in different situations will transition smoothly.

With Physically Based Shading cubemaps control many things in the engine now. Everything from shadow colors, ambient diffuse values, particle diffuse, and reflections. They act as bounce light by taking the colors from the surroundings and applying them directly into the diffuse of materials inside their radius.

### Setup

Having loaded a level in Sandbox, select from the **Create Objects → Misc → Environment Probe**.

After selecting the Environment Probe, move your cursor into the viewport to position and place the 'Environment Probe' into your level. You can adjust the location the same as with any entity.

With the new tile shading in CRYENGINEall cubemaps must be at a resolution of 256. The image generated is a floating point HDR image and has a much higher fidelity than previously.

#### Cubemap Generation

The texture file name will always change to the name of the Environment Probe entity. So it is a good idea to name your probe right away before you start generating anything. When you generate you will get back 2 textures, one will be the diffuse bounce lighting information and the other is the reflection map.

On the Properties Panel, under the Cubemap option, click the **Generate Cubemap** button.

This will generate a Tif cubemap image in: `Textures\cubemaps\<LevelDirectory>\<EnvironmentProbeName_cm>.tif`

![Image](https://www.cryengine.com/docs/static/attachments/36849638)

Generally, the environment probe should be placed at head height to generate proper reflections.

#### Global Cubemap Probes

Every level should have a Global cubemap to start with. This is a special cubemap that acts as the default/fallback.Generally, you only need one Global cubemap per level.

Having a Global probe in your level ensures that you will always have an active cubemap available. Any "local" probes will automatically sort as a higher priority within its defined radius and blend in over the top of the "Global" probe.

Setting a cubemap to be a Global cubemap requires just a few special settings:

- Ensure that it covers the entire level by setting the BoxSizeXYZ values high enough.
- Set the SortPriority to 0.
- Set AttenuationFalloffMax to 0.
- Set IgnoreVisAreas to true.

![Image](https://www.cryengine.com/docs/static/attachments/44966509)

![Image](https://www.cryengine.com/docs/static/attachments/44966510)

### Environment Probe Properties

Cubemap Parameters |
--- | ---
**Cubemap Resolution** | This allows you to tweak the resolution of the generated cubemap to ensure a good balance between quality and memory usage. Note that since CRYENGINE 3.6, the Physically Based Shading model has been tuned for 256px cubemaps and this resolution is enforced. An additional option introduced here is "skip update" which sets this Probe to not update its cubemap texture.
**Preview Cubemap** | Toggle this checkbox to see the probe change to a default sphere with the cubemap applied and rendered.
**Generate Cubemap** | Generates a cubemap for the currently selected Environment Probe.
Environment Probe Properties |
**Active** | Turns the entity on/off.
**Box Size X,Y and Z** | Specifies the X, Y and Z dimensions of the Environment Probes area of effect. Probes are now projected in Box fashion rather than Spherical fashion for better flexibility with level setups.
Color |
**Color** | The diffuse color of the light can be specified here.
**Diffuse Multiplier** | To make the light brighter this diffuse multiplier can be used.
**Specular Multiplier** | Multiplies the specular color brighter, use to adjust brightness.
Options |
**Affects Only This Area** | Set this parameter to false to make lights other visarea.
**Affects Volumetric Fog Only** | Whether this probe will affect volumetric fog.
**Attenuation Falloff Max** | Controls the falloff amount (0 - 1) to create smoother transitions or hard-edges which can be useful in interior lighting.
**Deferred Clip Bounds** |
**Ignores Vis Areas** | Controls whether the light should respond to visareas.
**Link To Sky Color** |
**Sort Priority** | Gives control over which Probe should be a higher priority. With two probes in the same area, the probe with the higher sort priority will be rendered on top.
**Volumetric Fog** | This probe will only affect volumetric fog.
Options Advanced |
**Deferred Cubemap** | Specifies the location of the cubemap texture.
**Projection** |
**Box Height** | Adjusts the height of cubemap box.
**Box Length** | Adjusts the length ofcubemapbox.
**Box Active** | Needs to be checked in order to be enabled.
**Box Width** | Adjusts the width ofcubemapbox.

### Tweaking Environment Probes

High reflective materials are suggested to be used in conjunction with SSR (Screen Space Reflections) as it will provide localized real-time reflections.

No SSR and no Environment Probe.![Image](https://www.cryengine.com/docs/static/attachments/36849635)

The following example was put together using a box projection method SSR with Environment Probe. Notice how the grid is accurately aligned with the shapes. When modifying your box projection be aware that a boundinggreen bounding box appears and to tweak the size accordingly.![Image](https://www.cryengine.com/docs/static/attachments/36849641)

This screen has SSR with no Environment Probe enabled. Notice the localized reflections located around edges and corners.![Image](https://www.cryengine.com/docs/static/attachments/36849640)

No SSR with BoxProject enabled Environment Probe aligned with the size of the room.![Image](https://www.cryengine.com/docs/static/attachments/36849632)

SSR with spherical Environment Probe. This aspect is not as accurate but in less reflective areas this option may be easier to use.![Image](https://www.cryengine.com/docs/static/attachments/36849631)

[Setup](#setup)[Environment Probe Properties](#environment-probe-properties)[Tweaking Environment Probes](#tweaking-environment-probes)
