# Voxel-Based Global Illumination (SVOGI)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535599
- Page ID: 25535599
- Breadcrumb: Graphics & Rendering > Lighting > Lighting Overview > Voxel-Based Global Illumination (SVOGI)
- Parent: Lighting Overview

## Child Pages

- [Ray Traced Shadows](Voxel-Based%20Global%20Illumination%20(SVOGI)/Ray%20Traced%20Shadows.md)

## Content

## Overview

This GI solution is based on voxel ray tracing and provides the following effects:

- Dynamic indirect light bounce from static and most of dynamic objects.
- Large scale AO and indirect shadows from static geometry (vegetation, brushes and terrain).
- Works without pre-baking and does not require manual setup of many bounce lights or light volumes.

![Image](https://www.cryengine.com/docs/static/attachments/21239779)![Image](https://www.cryengine.com/docs/static/attachments/21239457)![Image](https://www.cryengine.com/docs/static/attachments/19335754)![Image](https://www.cryengine.com/docs/static/attachments/20349274)![Image](https://www.cryengine.com/docs/static/attachments/44964629)![Image](https://www.cryengine.com/docs/static/attachments/21240534)![Image](https://www.cryengine.com/docs/static/attachments/21235585) *Global Illumination examples*

How It Works

- First we prepare voxel representation of the scene geometry (at run-time, on CPU, asynchronously and incrementally).
- Every frame on GPU we trace thousands of rays through the voxels (and shadow maps) in order to gather occlusion and indirect lighting.

The current default configuration provides only **diffuse GI**. For **specular lighting** we still need light probes. This system can be used as an AO add-on to light probes or can completely replace diffuse contribution of light probes.

### Performance

The performance depends on which GI settings are used. Usually on Xbox One it takes 3-4 ms of GPU time and on an average PC it takes 2-3 ms (AO + Sun bounce, no point lights, low-spec mode). The fastest configuration is AO only mode; this provides large scale AO at a cost of less than 2 ms on Xbox One.

### User Interface

The Global Illumination settings are located in**Tools → Environment Editor → Constants → Total Illumination** and **Total Illumination Advanced**:![Image](https://www.cryengine.com/docs/static/attachments/52593394) * Global Illumination settings*

For more information about the Global Illumination parameters in this window, **[click here](../../../Editor%20Tools/Environment%20Editor.md)**.

### Debugging

- Use **e_svoDebug = 6** to visualize the voxels. Make sure all important objects in the scene are voxelized otherwise they will cast no occlusion and no secondary shadows. Also make sure all unwanted and unnecessary occluders are excluded from voxelization.
- Use **r_ShowRenderTarget svo_fin** to show the output of GI system.

![Image](https://www.cryengine.com/docs/static/attachments/44964633) *r_ShowRenderTarget svo_fin*

- Use **r_profiler 1** or **2** to get GPU profiling information.

### Current Limitations

- Large scale AO and indirect shadows may be cast properly only by static geometry.
- GI is not working on some forward rendering components like particles or water.
- Some artifacts like ghosting, aliasing, light leaking and noise may be noticeable in some cases.
- Procedural vegetation and merged vegetation do not cast occlusion or secondary shadows.
- If the camera is teleported to a completely new location it may take up to a few seconds until occlusion is working properly.
- Only objects and materials with enabled shadow map casting may produce proper bounced light.
- For dynamic objects indirect light bounce is working only in the areas near voxelized static geometry.
- Bounce light may have a noticeable delay of 1-2 frames.
- **r_Supersampling = 2** makes GI look strange but setting lower LowSpecMode (2X lower) pretty much restores the look and speed. Temporal AA (** r_AntialiasingMode 2/3**) works just fine.

### About Integration Modes

By default, when **Total Illumination Advanced → Integration Mode** set to** 0**, only opacity is voxelized. This allows very small memory allocations on GPU - about 16 MB. The bounced light is sampled directly from shadow maps (extended to RSM). Compute shaders are not used.

The advantages of mode 0 are:

- Small memory usage.
- Completely dynamic indirect lighting (moving sun does not cause any slowdown).
- Dynamic objects can bounce indirect lighting.

The disadvantages:

- Sometimes low quality of indirect lighting (more noise) especially for small point lights.
- Only single bounce is possible.
- Only diffuse GI is possible (environment probes are supposed to be used for specular).

**Integration Modes 1-2** use more memory for voxelization (at least 64 MB) - albedo, normals and several layers of radiance are voxelized together with opacity. The lighting gets injected into voxelization, then it may be propagated (within the voxelization) and is then sampled during ray tracing pass.

Below, you can see example of information stored in voxels: albedo colors, direct light injection and light propagation.![Image](https://www.cryengine.com/docs/static/attachments/44964634) *Albedo colors, direct light injection and light propagation*

The advantages of this mode:

- Support for multiple bounces (light source can be marked to be semi-static with multi-bounce support or to be fully dynamic but only with single bounce).
- Support for traced speculars (in mode 2).
- Better quality (smoother) indirect lighting.

The disadvantages:

- Higher memory usage.
- Large semi-static multi-bounce lights can not be moved freely (but slowly moving sun may work fine).
- Dynamic objects can not affect GI (but can receive it of course).

If you get the error message "Display driver stopped responding and has recovered", you can use **[this workaround from Microsoft](https://support.microsoft.com/en-us/kb/2665946)**. This fix is applicable to Windows 10 as well.

### Analytical Occluders Prototype

Hand-placed analytical occluders help get sharper and more detailed occlusion in some places where voxel resolution is not enough. Also analytical occluders can be moved or created in game dynamically (for example for opening doors or small house built by the player in the game).

Enable it using the **Analytical Occluders** checkbox in the ** Environment Editor**.

It activates support for hand-placed occlusion shapes and also enables soft indirect shadows from characters.

For a character setup example please see **ShadowCapsulesList** in **GameSDK\Objects\characters\human\generic\skeleton_player_generic.chrparams**.

#### How to Make a New Occluder:

- Create new Static Mesh Entity and set flowing **.cgf** as entity geometry:
- *GameSDK/objects/default/primitive_sphere.cgf* for capsule shapes.
- *GameSDK/objects/default/primitive_cube.cgf* for box shapes.
- *GameSDK/objects/default/primitive_cylinder.cgf* for cylinder shapes.

- Find the **GI and Usage Mode** setting in the entity properties and select ** Analytical Occluder** (it is an occluder applied in deferred way after all cone tracing is performed and average light direction is already computed). You can try also ** Analytical Proxy** ** Hard** or ** Analytical Proxy Soft** (occluders that are applied during cone tracing stage and used like true replacement of voxels allowing also light bouncing from them).
- Now you can use non-uniform scaling of entities to produce the shape your want:

- - For capsules normally the entity needs to be scaled down in X and Y dimensions for example to 0.1.
- Boxes and cylinders produce sharp contact shadows but capsules (on purpose) have no sharp contact shadows.

The direction of shadows depends on the average light direction in that location, it is calculated automatically as part of GI calculations. The actual mesh used in the entity is not important - only the CGF name is used to pick one of 3 shapes. Normally mesh can be hidden by setting NoDraw shader in material. The entity can be moved freely (ghosting may be removed completely in future versions).

For more information about SVOGI and how to it efficiently in your level, please refer to the following tutorials:

- [Tutorial - Creative Lighting Basics](../../../Tutorials/Graphics/Lighting%20Tutorials/Tutorial%20-%20Creative%20Lighting%20Basics.md)
- [Tutorial - Environment Editor part 3 - SVOGI and Ambient Light](../../../Tutorials/Graphics/Environment%20Tutorials/Environment%20Editor%20Tutorials/Tutorial%20-%20Environment%20Editor%20part%203%20-%20SVOGI%20and%20Ambient%20Light.md)

### External Links

[Crytek’s Artists Showcase CRYENGINE With New Beautiful Forest Maps](http://www.dsogaming.com/news/cryteks-artists-showcase-cryengine-with-new-beautiful-forest-maps/) [SVOTI in Kingdom Come: Deliverance Alpha 0.5 on/off comparison (with FPS)](https://www.youtube.com/watch?v=PEfqtOYjolE) [LIGHT & ART: USING SVOTI TO BUILD BETTER GAMES](http://80.lv/articles/light-art-using-svoti-to-build-better-games/) [SVOTI in Miscreated open world MMO](http://steamcommunity.com/app/299740)[GI on/off comparision](https://www.youtube.com/watch?v=JC5jIa5fvlk), [YouTube](https://www.youtube.com/watch?v=bnvmB9iztaM), [YouTube](https://www.youtube.com/watch?v=laZ97IAJ8Xo), [YouTube](https://www.youtube.com/watch?v=Jy-G5aopdi4),

[Performance](#performance)[User Interface](#user-interface)[Debugging](#debugging)[Current Limitations](#current-limitations)[About Integration Modes](#about-integration-modes)[Analytical Occluders Prototype](#analytical-occluders-prototype)[External Links](#external-links)
