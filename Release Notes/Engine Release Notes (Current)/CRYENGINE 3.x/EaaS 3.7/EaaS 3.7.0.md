# EaaS 3.7.0

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962947
- Page ID: 44962947
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.7 > EaaS 3.7.0
- Parent: EaaS 3.7

## Child Pages

- [EaaS 3.7.0 Texture Format Changes](EaaS 3.7.0/EaaS 3.7.0 Texture Format Changes.md)

## Content

Released 28th April, 2015

If you're receiving AI errors on startup, make sure you delete or update the 3.6 AI scripts which you may have extracted.

If you're using Area Lights, make sure you set r_deferredShadingAreaLights=1 to enable them.

##
Overview

CRYENGINE 3.7.0 is here and it is BIG. There is a new Cross Platform build system, a new Character tool with unified toolset and a new UI. There are advanced lighting features including tiled-shading support for glass and SSDO color bleeding for better ambient occlusion.  The new Audio Translation Layer provides the industry's first abstraction layer to support audio middleware solutions. Sandbox has a slew of new features including Flowgraph and various editor improvements. The Sample Content includes the new "Woodland" level with high quality assets and PBR lighting. All of this and much more, including tons of minor improvements, bug fixes, and optimizations. See the Release Highlights below for more information and scroll down for all the details.

##
Release Highlights

##
Cross-Platform Build System

CRYENGINE 3.7 features a new cross-platform build system based on WAF. For detailed information see
[/docs/static/engines/cryengine-3/categories/1638401/pages/19380746](
WAF Build System
)
.

*
The new build system is fully replacing the build configurations from Code/Solutions. Complete removal of the old build system is planned for CRYENGINE 3.7.2.
*

##
Lighting on Transparent Objects

When tiled forward shading is enabled, glass will now receive direct lighting (including shadows) and probe-based ambient, making it look a lot more consistent with standard opaque objects.

[Image: /docs/static/attachments/44962967]

##
SSDO Color Bleeding

SSDO color bleeding is a simple and very efficient light scattering approximation which solves the problem of having overly dark ambient occlusion on bright surfaces.

The feature can be toggled with r_ssdoColorBleeding 0/1 and requires tiled deferred shading to be enabled.

[Image: /docs/static/attachments/44962991]

##
Improved LOD System

The LOD system now takes into account the average triangle size for deciding when to switch between LOD meshes. This gives greatly improved results (less polygons while having less LOD popping) when just using the default view distance ratio.

Use e_lodFaceArea 0/1 to switch between the previous and the new system.

[Image: /docs/static/attachments/44962952]

*
Shown above is e_debugdraw -3, the minus value still color codes assets but removes the text information overlay
*

##
Improved Temporal Anti-Aliasing

Our improved Temporal AA technique that shipped with Ryse PC is available now in CRYENGINE 3.7. With just a minimal performance overhead, it provides a greatly more stable image by applying projection matrix jittering.

Set r_AntialiasingMode 3 to enable.

[Image: /docs/static/attachments/44962993]

##
Clip Volumes

The new
[/docs/static/engines/cryengine-3/categories/1114113/pages/19379670](
Clip Volumes
)
 greatly simplify the workflow for setting up interior lighting by solving previous light leaking problems.

The volumes provide pixel-accurate clipping of light sources and probes and work with tiled deferred shading and forward-shaded objects like hair. Clip volumes can be setup in Sandbox using Designer or imported from a static mesh.

[Image: /docs/static/attachments/44962964]

*
Arbitrary clip volume shape containing 3 colored point lights and 1 additional blue light which only affects outside.
*

Due to the introduction of ClipVolumes, LightBoxes will soon be deprecated in a future version of CRYENGINE.

##
Character Tool

This new tool u
nifies the Character Editor, the Animation Importer, the Animation Compression Editor and the DBA Editor in one tool with a completely reworked UI (for more information see
[/docs/static/engines/cryengine-3/categories/1114113/pages/19380982](
Character Tool
)
).

[Image: /docs/static/attachments/44962950]

##
Audio Translation Layer

This brand new and industry's first system servers as an abstraction layer between CRYENGINE and an audio middle-ware. Due to full audio source code availability and detailed interface documentation it is possible to hook any audio middle-ware into CRYENGINE's ATL.

Current implementations include Wwise for a professional and SDL_mixer for a simple and cost free audio solution. It has never been easier implementing audio into CRYENGINE using its as well brand new
[/docs/static/engines/cryengine-3/categories/1114113/pages/17826178](
Audio Controls Browser
)
.

This release fully substitutes and replaces the former FMOD based audio solution. For more details see
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048650](
ATL Docs
)
.

[Image: /docs/static/attachments/44962969]

##
Sample Content

For CRYENGINE 3.7 we introduce a new sample level called "Woodland". This level is roughly twice the size of Forest and features a proper PBR lighting setup and high quality assets to better showcase the rendering capabilities of CRYENGINE.

Other features include several trackview examples, geomcache, a showcase area where we show some of our face rendering/animation tech. We will be adding more content to this level as we go as well as more sample showcases.

We've retired the old faithful Forest level so we can fully concentrate on the new showcase content of much higher quality.

[Image: /docs/static/attachments/44963001]

[Image: /docs/static/attachments/44962999]

[Image: /docs/static/attachments/44962997]

[Image: /docs/static/attachments/44962996]

[Image: /docs/static/attachments/44962995]

[Image: /docs/static/attachments/44962994]

##
Editor

[Image: /docs/static/attachments/44962968]

*
The latest CRYENGINE 3.7 Sandbox interface
*

-
**
New
**
: (CE-1497) (Flowgraph) Add Environment:SkyMaterialSwitch FlowNode.

-
**
New
**
: (CE-4995) (Flowgraph) Added IsInWater and IsHeadUnderWater ouput for FG ActorSensor node.

-
**
New
**
: (Flowgraph) Add input to force update on Time:RealTime node.

-
**
New
**
: (Material Editor) Increased maximum exposure value for distance clouds.

-
**
New
**
: (Prefab) When extracting single object from a prefab, the object is now selected properly which improves the workflow.

-
**
New
**
: (Prefab) Prefab-Panel automatically updates object list when changed.

-
**
New
**
: (Vegetation) Adding Elevation Min & Max values and Slope Min & Max values to Vegetation Panel in Database View.

-
**
New
**
: (CE-4874) Added (Editor) tag for displayInfo when in Editor.

-
**
New
**
: (CE-594) UI: Smart Open tabs will not order the shown items from path / modified date and size.

-
**
New
**
: Added support to load .hdr files as source image for light probes, with automatic conversion from longitudinal/latitudinal and cross maps.

-
**
New
**
: Editor now has a regular update hook in the game DLL that can be used to update and render all sorts of helper information.

-
**
New
**
: It is not possible to change the prefab properties of multiple prefabs at the same time.

-
**
New
**
: Added "Clear Registry Data" to Tools menu.

-
**
New
**
: List selection dialog show previously selected item.

-
**
New
**
: Added additional FOV presets.

-
**
New
**
: Refresh entity scripts and panel tree browser when new entity classes are registered at run-time.

-
**
Fixed
**
: (CE-2992) (LODGen) Editor crashes when Generate Textures is clicked.

-
**
Fixed
**
: (CE-2573) (Material Editor) Create material in correct folder.

-
**
Fixed
**
: (CE-5348) (Editor, Export) No longer export all vegetation-object's static-object-groups to all surface-types that have at least one vegetation-object using the same static-object applied to it.

-
**
Fixed
**
: (CE-5410) (Input) Mouse becomes active outside of viewport when in game mode.

-
**
Fixed
**
: (CE-5036) (TOD) Changing from the default 'dark skin' to 'no skinning' will result in the start and end time in TOD to appear blank.

-
**
Fixed
**
: (CE-5209) (TOD) Remove OnChanged message to prevent sending TIMEOFDAYN_CHANGE twice.

-
**
Fixed
**
: (CE-5038) (Trackview) Disallow creating TV sequences if no level is loaded.

-
**
Fixed
**
: (CE-5256) (Flowgraph) Modules only trigger one instance.

-
**
Fixed
**
: (CE-5212) (Flowgraph) Inventory:EquipPackAdd doesn't work correctly.

-
**
Fixed
**
: (CE-5180) (Flowgraph) Basic Entity's removed via flowgraph do not reset on exiting game mode.

-
**
Fixed
**
: (CE-4608) (Flowgraph) Comment box moving down on undo and import.

-
**
Fixed
**
: (CE-5568) (LensFlare) Crash when undoing right after creating a new Library will crash the Editor.

-
**
Fixed
**
: (CE-1737) (LensFlare) Editor UI broken on first use.

-
**
Fixed
**
: (CE-5003) Prefab-Undo does not work correctly.

-
**
Fixed
**
: (CE-4980) Flowgraph input key doesn't work immediately with AI/Physics enabled.

-
**
Fixed
**
: (CE-5440) Unchecking "Vegetation" rendering in rollupbar w/o Level loaded crashes Sandbox.

-
**
Fixed
**
: (CE-5416) GameVolume's loads two extra properties after reloading script.

-
**
Fixed
**
: (CE-5162) Adding two brushes to a level gives a sandbox error message.

-
**
Fixed
**
: (CE-5431) Python Script Pane: Fix functionality for 'Edit' right-click menu.

-
**
Fixed
**
: (CE-4423) Hide/unhide layers from toolbar: Update render view.

-
**
Fixed
**
: (CE-4256) Selecting a material makes it show up in the Used In Level list.

-
**
Fixed
**
: (CE-5094) Changing game rules to MP in the editor causes a crash.

-
**
Fixed
**
: (CE-4752) Perforce Plugin: Crash while saving material outside of working folder.

-
**
Fixed
**
: (CE-5485) Toggling in-game mode is now done outside the actual update call to prevent remaining updates when already exited the game.

-
**
Fixed
**
: (CE-5082) Jumping in-game marks layers as modified.

-
**
Fixed
**
: (CE-4916) Toggling helpers or changing to wireframe unhides/activates all vegetation.

-
**
Fixed
**
: (CE-1819) Flare Editor: Reload Library 'detects' changes, when there are none.

-
**
Fixed
**
: (CE-3709) Removed detail spec from shadow casting list.

-
**
Fixed
**
: (CE-4637) ERROR: Console error on creating a new level "Failed to get level info for level .....".

-
**
Fixed
**
: (Flowgraph) Unregister module root graphs from flowsystem by default.

-
**
Fixed
**
: (Prefab) Editing Prefab crashes game.

-
**
Fixed
**
: (Prefab) Removed unnecessary rotation around Z when creating a prefab from selection.

-
**
Fixed
**
: (Prefab) Often unable to select objects within a prefabs bounding box.

-
**
Fixed
**
: (Prefab) Deleting a prefab from a library requires an editor reset before it is recognized as deleted.

-
**
Fixed
**
: (Trackview) Initialize depth of field in animation node.

-
**
Fixed
**
: (Trackview) TrackView node ordering.

-
**
Fixed
**
: (Vehicle) Closing and reopening the structure tab in Vehicle Editor crashes the editor.

-
**
Fixed
**
: Crash in debug when jumping into game in editor.

-
**
Fixed
**
: Sandbox Plugins: enabled NOT_USE_CRY_MEMORY_MANAGER by default.

-
**
Fixed
**
: Sandbox plugins: prevent loading of the plugins built in different configurations.

-
**
Fixed
**
: Update static shadow map whenever an object is changed in editor.

-
**
Fixed
**
: Top/Front and Left view grid is rendered over useful information.

-
**
Fixed
**
: Crash in CryGame::CProjectileExtension::Finalize.

-
**
Fixed
**
: Grouping and un-grouping results in random objects being unselected.

-
**
Fixed
**
: Clear registry data also resets shortcuts during run-time.

-
**
Fixed
**
: Broken hot reloading.

-
**
Fixed
**
: Undefined NOT_USE_CRY_MEMORY_MANAGER and _USRDLL to resolve mismatch of allocation/deallocation calls.

-
**
Fixed
**
: Now we save empty sub-materials again (empty MaterialRef node) to prevent breaking (shifting) sub-material IDs.

-
**
Fixed
**
: Cloning a group containing a light you can't see causes the editor to hang.

-
**
Fixed
**
: Editor crashing on quit in Debug configuration.

-
**
Fixed
**
: Possible infinite recursion in asset resolver.

-
**
Fixed
**
: Crash when creating a level without GameDll.

-
**
Fixed
**
: CRASH: GHashSetBase<GHashNode<GASString,GASMember,GASStringHashFunctor>,GHashNode<GASSt[...]

-
**
Fixed
**
: CRASH: GHashSetBase<GHashNode<GASString,GASMember,GASStringHashFunctor>,GHashNode<GASSt[...]

-
**
Fixed
**
: CRASH: GASExecutionContext::Function2OpCode.

-
**
Fixed
**
: CRASH: GFxMovieDefImpl::CreateMemoryContext" -> All bugs were caused by out of memory in the flash allocator - GFX AMP must be ticked each frame, else data is only allocated but never freed.

-
**
Fixed
**
: PluginManager prints wrong plugin name (always last enumerated one).

-
**
Fixed
**
: PluginManager also prints the name of the plugin it failed to load if it doesn't export the "CreatePluginInstance" method.

-
**
Fixed
**
: No longer CRY_ASSERT on non-plugin DLL's (ie, Audio plugins).

-
**
Fixed
**
: Draw area light helpers only when area light is selected.

-
**
Fixed
**
: Problem with multiple water area deletion.

-
**
Fixed
**
: Undo crash bug when undoing of area solid.

-
**
Fixed
**
: Position of the camera that was not serialized and restored correctly when saving/loading a level in Sandbox.

-
**
Fixed
**
: Bug about having PostNcDestroy() method not called when a dialog on a rollup with autodestory variable disabled.

-
**
Fixed
**
: SPyWrappedProperty is registered as pointer only, so pass as pSPyWrappedProperty in PySetCVar.

-
**
Optimized
**
: (CE-5059) (Material Editor) Removed obsolete generate cubemap button from material editor. Cubemaps should be generated with probes to fully decouple materials and lighting.

-
**
Optimized
**
: (CE-3602) (Material Editor) Hide non-functional UI elements in the Material Editor.

-
**
Optimized
**
: (CE-5005) (TOD) Tooltip on Recording button always displays "Start Recording".

-
**
Optimized
**
: (Material Editor) Remove unsupported tex gen modes.

-
**
Optimized
**
: Remove LightShapes. Replaced by
[/docs/static/engines/cryengine-3/categories/1114113/pages/19379670](
Clip Volumes
)
.

-
**
Optimized
**
: Removed Animation Import, Animation Compression Editor and Character Editor - Replaced by Character Tool.

-
**
Optimized
**
: Removed deprecated Voxel Painter button from Terrain Panel.

##
CryDesigner

[Image: /docs/static/attachments/44962953]

*
Designer object using new Subdivision technique.
*

*
*
[Image: /docs/static/attachments/44962990]

Subdivision Tool With Semi Sharp Creases.

*
*

*
[Image: /docs/static/attachments/44962978]

Cube Editor
*

*
*
*
If you want see more pictures click this link
[/docs/static/engines/cryengine-3/categories/1114113/pages/19381622](
Gallery [Zen Garden]
)
*
*
*

-
**
New
**
: Added the Subdivision Tool with Semi Sharp Crease and Treatment of Boundaries. -
[/docs/static/engines/cryengine-3/categories/1114113/pages/19379888](
Subdivision Manual
)

-
**
New
**
: Developed the Cube Editor with Axis Placement function. -
[/docs/static/engines/cryengine-3/categories/1114113/pages/18383153](
Cube Editor Manual
)

-
**
New
**
: Added CryDesigner PlugIn project and moved all files related to Designer, AreaSolid and ClipVolumeObject to here.

-
**
New
**
: Added a function for merging the selected faces in the existing Merge tool in addition to merging the selected designer objects.

-
**
New
**
: Added the boundary check in the Bevel tool as expanding edges.

-
**
New
**
: Exposed the seamless enable button to the designer panel.

-
**
New
**
: Added a selection option holding SPACE so that only faces can be selected by only selecting the small cubes.

-
**
New
**
: Bevel Tool - Implemented the first and second subdivision of a face at which three points meet.

-
**
New
**
: Added an "Exclude Collision" flag in Geometry Flags Panel in CryDesigner.

-
**
Fixed
**
: (AreaSolid) (CE-4527) Bug caused by a wrong boundbox of an empty area solid when clicking an error message and directing the camera toward the area solid.

-
**
Fixed
**
: (AreaSolid) Crash bug occurring when entering AreaSolid mode.

-
**
Fixed
**
: (CE-4357) Bug about disappearing a previous created designer object after creating a box object.

-
**
Fixed
**
: (CE-4453) Bug on an expected behavior as ESC pressed continually.

-
**
Fixed
**
: (CE-4457) Made a pivot point kept in the middle of the boundbox every time a new primitive shape is created.

-
**
Fixed
**
: (CE-4455) Crash bug in the Stair Tool caused by consecutive clicks of a mouse button in the view port.

-
**
Fixed
**
: (CE-5101) Got the "Snap To Grid" and "Export" button on the Designer Panel to reappear.

-
**
Fixed
**
: (CE-5102) Made Environment probes invisible on Exclude mode.

-
**
Fixed
**
: (CE-5250) Changed the default directory of exporting designer object as obj, cgf and grp to ../GameSDK.

-
**
Fixed
**
: (CE-5484) Bug about not raising a height of Cone and Cylinder when a cursor is on nothing.

-
**
Fixed
**
: (CE-5469) Bug about shifting a designer object with "Keep Pivot Center" on after transforming faces or edges or vertices.

-
**
Fixed
**
: Creating wrong bottom and top face as creating a box on a terrain.

-
**
Fixed
**
: Loop selection bug about excluding a selected edge when selecting edges around a border.

-
**
Fixed
**
: Bug about not updating backfaces of faces with a smoothing group.

-
**
Fixed
**
: Bug about drawing a rectangle or a box on a plane which is not parallel with the main axis.

-
**
Fixed
**
: Made it possible to edit them with the seamless editing as more than two designer object are selected.

-
**
Fixed
**
: Crash bug caused by exiting the drawing line tool after undoing.

-
**
Fixed
**
: Bug about an object, which was highlighted in the object mode tool, being kept highlighted after exiting the object mode tool.

-
**
Fixed
**
: Bug about going into the infinite loop when loading a designer object having lots of polygons.

-
**
Fixed
**
: Got mesh node in serialization not remained when undoing of a designer object.

-
**
Fixed
**
: Made a brush mesh of a designer object updated when a texture info has changed.

-
**
Fixed
**
: Expanded offset, scale and rotate ranges from 1000 to 100000 in the designer texture panel.

-
**
Fixed
**
: Enabled rearrangement of index order as creating a triangles out of a convex in the polygon decomposer.

-
**
Fixed
**
: Gave a polygon limitation as saving a designer object so that a designer object won't create the mesh node if it has polygons beyond the maximum count.

-
**
Fixed
**
: Crash bug as undoing of a designer object after moving vertices/edges/faces.

-
**
Fixed
**
: Can edit designer objects in a Prefab, even when the prefab is closed.

-
**
Fixed
**
: Bug about not being able to select an object after entering AI/Physics Simulation mode.

-
**
Fixed
**
: Made the highlight more transparent so that the face below can been seen more clearly.

-
**
Fixed
**
: Crash bug as the stair is created with the steprise which is same as or n times of the snapping grid size.

-
**
Optimized
**
: (AreaSolid) When an area solid is selected and it is empty, designer mode will be the default mode.

-
**
Optimized
**
: Refactored CBrushDesignerMoveTool class.

-
**
Optimized
**
: Calculation of triangulation by having triangles created from only modified regions. All regions used to be triangulated before every time.

-
**
Optimized
**
: Removed the SBrushPlaneEx and the function in it has been merged into the SBrushPlane.

-
**
Optimized
**
: Renamed "Split" to "Clip" in the codes.

-
**
Optimized
**
: Renamed "Faceter" to "PolygonDecomposer" in the codes.

-
**
Optimized
**
: Renamed Pivot2Center 2 Pivot2Bottom.

-
**
Optimized
**
: Refactored designer codes by separating routine about the selection of elements into the CBrushDesignerElementManager class (vertices,edges and faces).

-
**
Optimized
**
: Modified CBaseBrush::Update() function so that the function gets responsible to the whole update of mesh and other UpdateXXX() function will move to private part.

-
**
Optimized
**
: Removed all things about the old solid system in the codes.

-
**
Optimized
**
: Detached all MFC UI codes from the tools code of CryDesigner.

##
Renderer

[Image: /docs/static/attachments/44962967]

*
Tiled-Shading for Glass brings physically accurate point-light interaction, ambient lighting and shadows to glass objects.
*

-
**
New
**
: Tiled-shading support for Glass.

-
**
New
**
: Physical based BRDF for Glass.

-
**
New
**
: Sun shadow receiving for glass.

-
**
New
**
: Added SSDO color bleeding (requires tiled deferred shading).

-
**
New
**
: Added support for using a spec map on vegetation.

-
**
New
**
: Apply dithering to reduce banding in dark scenes.

-
**
New
**
: Added signed 8bit texture format (for render-targets).

-
**
New
**
: Improved quality of SMAA 2TX (plus additional WIP changes for accurate reprojection).

-
**
New
**
: Shader parser support for Texture3D and RWTexture3D.

-
**
New
**
: UAV support for Texture3D.

-
**
New
**
: Introduced common material attribute structure and corresponding functions for encoding/decoding gbuffer.

-
**
Fixed
**
: (CE-5046) Refresh shader constants on spec change.

-
**
Fixed
**
: (CE-5387) Fixed shader compile error in wireframe mode.

-
**
Fixed
**
: (CE-4871) Fixed sun specular multiplier in standard shading path.

-
**
Fixed
**
: (CE-5154) Removed obsolete beam modes; r_beams 0/1 toggles beam rendering now.

-
**
Fixed
**
: (CE-5299) Fixed 2-sided glass normal computation.

-
**
Fixed
**
: (CE-5053) Check for nullpointer before accessing CRenderObject::m_pRenderNode.

-
**
Fixed
**
: (CE-3436) Fix Shadow casting frustum issue.

-
**
Fixed
**
: (CE-4932) Use cubemap for translucency in standard deferred shading (behavior consistent with tiled shading now).

-
**
Fixed
**
: (CE-5293) Fixed shader parser error message (USE_DEPTH_MASK).

-
**
Fixed
**
: (CE-248) Sample shadow mask for area lights in tiled shading.

-
**
Fixed
**
: (CE-5164) Removed assert in CDeferredShading::ReleaseData which triggers on shutdown (Renderer shutdown gets executed on RT). The function should be safe to be called from the render thread when assuring synchronization.

-
**
Fixed
**
: (CE-5135) Prevent Flash-RT being treated as EnvMap-RT.

-
**
Fixed
**
: (CE-5265) Disable shadow casting based on 'e_ObjShadowCastSpec' CVar instead of sys spec.

-
**
Fixed
**
: (CE-3335) Fixed gbuffer velocity generation when tessellation is enabled.

-
**
Fixed
**
: (CE-5386) Increased size of SHDataBuffer to avoid warning about reallocation.

-
**
Fixed
**
: (CE-5403) Use m_TempMatrices[0][2] for shadow cascade blending instead of m_TempMatrices[2][0], as m_TempMatrices[2][0] is used for forward shadows.

-
**
Fixed
**
: (CE-5706) Visareasperpixel 0/1 is broken.

-
**
Fixed
**
: Visarea stencil markup when r_VisAreasClipLightsPerPixel=0.

-
**
Fixed
**
: Area lights with tiled shading.

-
**
Fixed
**
: Floating point exception due to driver bug when switching to fullscreen.

-
**
Fixed
**
: Re-added NULL Renderer and Dedicated Server.

-
**
Fixed
**
: Fixed inconsistent usage of m_nGPUs and querying if MGPU is active; always use GetActiveGPUCount now to retrieve the number of GPUs.

-
**
Fixed
**
: Use full SSDO intensity when generating probes.

-
**
Fixed
**
: SS Reflections when MGPU support is disabled on an MGPU system.

-
**
Fixed
**
: Set default value for cascade blend var to avoid console error message.

-
**
Fixed
**
: Shadow blending artifacts in extremely dark environments: Make sure blending values add up to one at minimum even under quantization to 8 bit.

-
**
Fixed
**
: Initial refresh rate at device creation not properly stored. Could cause problems for "lock fps" feature if window setup doesn't go through res change code path before playing. Essentially, it'd then just be regular vsync.

-
**
Fixed
**
: Detail map behavior.

-
**
Fixed
**
: Skip drawcalls when activation of any shader stage fails due to shaders still being compiled. This should avoid various D3D errors and driver crashes.

-
**
Fixed
**
: Crash in shadercachegen if ps3 or xenon CVars are not created.

-
**
Fixed
**
: PostEffects.cpp static Vec2/Vec4 are initialized to NaNs in debug.

-
**
Fixed
**
: Motion blur broken on some objects in low & medium spec.

-
**
Fixed
**
: Ambient in forward passes (_RT_AMBIENT flag is not getting set from engine any longer and is obsolete).

-
**
Fixed
**
: Update static shadow map whenever an object is modified. Has some false positives but nothing major performance critical.

-
**
Fixed
**
: Small forward shading fixes (terrain, detail mapping).

-
**
Fixed
**
: Cache unused material constants for later as they might be used by other shader permutations.

-
**
Fixed
**
: Use renderNode material in CDeferredCollisionEventOnPhysCollision.

-
**
Fixed
**
: Color-datatype not updated in shader from material dialog.

-
**
Fixed
**
: Cleared constant-buffers, refill with texture's scales and biases on refresh.

-
**
Fixed
**
: Swapped enum positions of Auto2D and Dyn2D, so that material files automatically use the correct new enum-member.

-
**
Fixed
**
: "CRASH: DeviceInfo::ProcessSystemEvent" - Applied same FPE workaround as for other DXGI functions.

-
**
Fixed
**
: Depth mask generation in tiled shading.

-
**
Fixed
**
: Cleanup of material parameter naming, passing and configuration.

-
**
Fixed
**
: Another source for asserts in LookupTexPriority.

-
**
Fixed
**
: Deferred decals now work with non-orthogonal transforms (e.g. stretched particles). Simplified and optimized transformations, fixed confusing axis labels.

-
**
Fixed
**
: SSS ghosting Temp irradiance buffer did not get cleared and contained MB data.

-
**
Optimized
**
: (CE-5181) Removed BMP from supported capture file formats, use 24 bit TGA instead.

-
**
Optimized
**
: Marked MSAA as deprecated.

-
**
Optimized
**
: Separate texture-types for water rendertargets (Auto-Cube and Auto-2D) and dynamic flash rendertargets (Dyn-2D).

-
**
Optimized
**
: Removed obsolete SSAO and cleaned up voxel terrain leftovers.

-
**
Optimized
**
: Remove LOD calculations from render code path.

-
**
Optimized
**
: Remove SPU specific render objects cache code.

-
**
Optimized
**
: Removed obsolete nightvision and visarea ambient passes.

-
**
Optimized
**
: Removed rendering pipeline support for obsolete forward lighting.

-
**
Optimized
**
: Removed obsolete rendering techniques/passes : Forward caustics, ShadowPass, ShadowGenPS.

-
**
Optimized
**
: A few changes to reduce frame latency on PC (measured response to gamepad input in game using high speed camera).

-
**
Optimized
**
: Support for Lock FPS mode to properly vsync. Syncs to closes available refresh rate (via presentation interval in rage 1..4) based on monitor refresh rate and sys_maxfps setting.

-
**
Optimized
**
: Removed nVidia-specific and outdated TXAA.

-
**
Optimized
**
: Removed obsolete forward lighting from shaders (the sun gets handled explicitly now, for point lights we will rely on tiled shading).

-
**
Optimized
**
: Added defines for LDR/HDR range renormalization points.

-
**
Optimized
**
: Forward shadow sampling based on dynamic branching.

-
**
Optimized
**
: Removed obsolete shaders.

-
**
Optimized
**
: Removed obsolete non-gbuffer rain pass.

-
**
Optimized
**
: Dropped support for SMAA being applied to two MSAA samples.

-
**
Optimized
**
: Removed obsolete camera motion blur technique.

-
**
Optimized
**
: Cleanups in HDR post processing, removed obsolete code paths.

-
**
Optimized
**
: Missing IRenderNode::Clone() functions are now always available.

-
**
Optimized
**
: CWaterVolumeRenderNode::OffsetPosition now also affects physics all the time.

-
**
Optimized
**
: Remove SRenderObjectModifier.

-
**
Optimized
**
: Use aligned data structures for tiled shading.

-
**
Optimized
**
: Remove unused shader permutations.

-
**
Optimized
**
: Tiled shading light culler.

-
**
Optimized
**
: Removed obsolete files from Renderer: DXUT, CTileRaster, RendererMeshDataHeap, TangentSpaceCalculation.

-
**
Optimized
**
: Slight adjustments to sys specs.

-
**
Optimized
**
: Remove some old DXSDK, some stuff is still missing. Had to rename some types, which seems to have changed. Removed CD3D9Renderer::D3DError and CD3D9Renderer::Error as those were unused but depended on DXErr which is no longer supported. Replaced linked libs in CryInput with Microsoft SDK headers.

-
**
Optimized
**
: Move texture modification matrices to PB instead of PI (fixes instancing with texture tiling).

-
**
Optimized
**
: Fix and re-enable skin draw call batching.

-
**
Optimized
**
: Use GPA_2014_R2 lib instead of GPA_2012_R15.

-
**
Optimized
**
: Removed "SetMaterialFloat" from engine.

-
**
Optimized
**
: Removed CryD3DCompiler Stub as we can use the D3DCompile function now directly as we switched to VS 2012.

-
**
Optimized
**
: Unified material-parser and translator.

-
**
Optimized
**
: Prefixed enum names in IStereoRenderer.h according to coding guidelines.

-
**
Optimized
**
: Split console configurations into a general and a platform-specific section; platform-specific CVar settings are ignored when switching sys specs on PC.

-
**
Optimized
**
: Made ShaderEnum queries independent of CString.

##
3dEngine

[Image: /docs/static/attachments/44962964]

[Image: /docs/static/attachments/44962963]

*
ClipVolumes support arbitrary shape creation with the power of Designer to give full control over light clipping.
*

-
**
New
**
:
[/docs/static/engines/cryengine-3/categories/1114113/pages/19379670](
Clip Volume
)
 supports arbitrary shape creation for light culling. Can also load CGFs for mimicking the shape of existing meshes.

-
**
New
**
: (GeomCache) Support for geom cache physics interactions.

-
**
New
**
: (CryPak) Added CryFatalError for empty zip names (malformed zip files).

-
**
New
**
: Auto-select texture streaming pool size based on available VRAM when sys_spec_TextureResolution is not explicitly set.

-
**
New
**
: Create game object entity proxies from game code.

-
**
New
**
: Added CPU requirements check. Check for SSE1,2,3 support and enforce it to be present (otherwise don't start the engine).

-
**
New
**
: Added serialization functions for CryFixedStringT<size_t> and CryStackStringT<class, size_t>

-
**
New
**
: Added the HalfEdgeStructure class.

-
**
New
**
: Add Point_Sphere check to GeomOverlap utils.

-
**
New
**
: Multi-threaded mip-map filtering.

-
**
New
**
: Occlusion culling: New cvar to set a polygon limit (e_CoverageBufferRastPolyLimit)

-
**
New
**
: Occlusion culling: New cvar to delay abort of rasterization when main thread is ready to consume data (e_CoverageBufferEarlyOutDelay)

-
**
Fixed
**
: (CE-5382) (MergedMeshes) Crash during pool resize in pure game.

-
**
Fixed
**
: (CE-5073) (GeomCache) Fix known problem where very short caches would cause stream aborts when looping.

-
**
Fixed
**
: (CE-5742) (GeomCache) Geom cache hang in woodland: clear fill thread job state when FillFrameAsync returns early.

-
**
Fixed
**
: (CE-4548) DisableRuntimeFileAccess: now always allow access in editing mode; moved calls to more closely match gameplay start/end; allow checking access without warning message; more consistent usage of CDebugAllowFileAccess; disabled run-time loading of particle files, controlled by CVar.

-
**
Fixed
**
: (CE-4667) Multi-threading issue with area containment check.

-
**
Fixed
**
: (CE-5107) Take CGA character attachment LOD into account in texture streaming.

-
**
Fixed
**
: (CE-4965) Calls to script function OnPropertyChange now check if this function exists in the entity's script table beforehand.

-
**
Fixed
**
: (CE-5621) Crash in reading chunk files *without* chunks.

-
**
Fixed
**
: (Physics) Issue with quadratic polynomial solver.

-
**
Fixed
**
: (Physics) Physicalization issue with multi-part brushes.

-
**
Fixed
**
: (GeomCache) Crash with e_geomCacheDebugDrawMode == 3 because of non thread safe aux rendering from render job. Fix is to move debug rendering to main thread.

-
**
Fixed
**
: (GeomCache) Speed scale not working in AnimGeomCacheNode.

-
**
Fixed
**
: (CrySystem) Fixed potential buffer overflow when using profiler.

-
**
Fixed
**
: (CrySystem) introduced the system event ESYSTEM_EVENT_FAST_SHUTDOWN which is issued when the system quits instead of the ESYSTEM_EVENT_SHUTDOWN event which was renamed to ESYSTEM_EVENT_FULL_SHUTDOWN and is now issued when the system does a full shut down.

-
**
Fixed
**
: Using garbage character when setting long name of a thread.

-
**
Fixed
**
: fpe in breakability.

-
**
Fixed
**
: Potential crash during shutdown.

-
**
Fixed
**
: Position of to be deleted mergedmeshrendernode not matching the position it was inserted into the node grid.

-
**
Fixed
**
: Rope cutting uninitialized pMesh in event.

-
**
Fixed
**
: int overflow fix in boolean2d.

-
**
Fixed
**
: Stricter bounds checks in pre-cg solver. More range checks in rigidbody pre-cg solver.

-
**
Fixed
**
: Issue with player collision impulse.

-
**
Fixed
**
: Use area light for sun just when area light support is enabled.

-
**
Fixed
**
: More fixes to run-time file access permission, to more closely match gameplay start/end, for single and multiplayer. e_ParticlesAllowRuntimeAccess now = 1 by default; only logs when disallowed.

-
**
Fixed
**
: Use after free in CGeomCache::Release.

-
**
Fixed
**
: Use after free in CEntity::~CEntity (m_szName deallocated before m_proxy).

-
**
Fixed
**
: Uninitialized SMMRMInstanceContext::rotationOrigin.

-
**
Fixed
**
: Use after free in CFileIndexingThread.

-
**
Fixed
**
: WaitForSingleObject cannot be used with _beginthread in CTaskManager::CThread.

-
**
Fixed
**
: Use after free in destruction of static TActionHandler<CUIInput> (CryName pool used is already destroyed).

-
**
Fixed
**
: Remove assert in CTCPStreamSocket::~CTCPStreamSocket (m_socket is never 0).

-
**
Fixed
**
: Issue with advanced water volumes.

-
**
Fixed
**
: Added post renormalization clamp.

-
**
Fixed
**
: Crash in debug for wrong casting of a Value type that should contain a string but it tries to assign it and cast it to a const char.

-
**
Fixed
**
: Removing Virtual call in Destructor.

-
**
Fixed
**
: Changed CreateResources() behavior to not load textures on-creation, the loading is deferred to RefreshResources().

-
**
Fixed
**
: Restore default behavior for entity pool (config file is empty, and pools are always disabled in MP and editor, so it should not be used anyway).

-
**
Fixed
**
: Ensure automatically selected streaming pool size does not get overwritten when changing specs.

-
**
Fixed
**
: Assert ((Source->m_Flags & DLF_LIGHTTYPE_MASK) != 0) for light in editor preview window.

-
**
Fixed
**
: Protection against dangling entity ptr in GetPhysForeignName.

-
**
Fixed
**
: Wrong size check and alignment for interlocked single linked list on 32 bit.

-
**
Fixed
**
: Make CBaseLibraryManager header not rely on known CBaseLibrary class.

-
**
Fixed
**
: Made CFileUtil functions independent of CString.

-
**
Fixed
**
: Adjusting calls to string Format function to avoid possible unsafe usage of passing the same string we are formatting as a parameter of the function.

-
**
Fixed
**
: Bug about the incorrect use of vec3 in IsIncludePointsInConvexHull() method in BaseObject.cpp.

-
**
Optimized
**
: (CE-2756) Cleaned up e_mergedmeshesdebug view.

-
**
Optimized
**
: (Vegetation) Bending vegetation tweak.

-
**
Optimized
**
: Improved consistency of character rope environment collision flags.

-
**
Optimized
**
: Reworked system spec auto detection.

-
**
Optimized
**
: Avoid constructing clip volume bsp tree at game runtime - serialize as special chunk into mesh cgf instead.

-
**
Optimized
**
: Refactor of deferred light clip volume system: Works with tiled and deferred shading. Clip volumes are created either directly with CryDesigner or imported from cgfs. Works with forward objects and particles (based on their pivot position). Vis areas are treated as instances of Clip Volumes, previous behaviour (per object instead of per pixel clipping can be restored via cvar). Mode for blending lights and cubemaps in portals.

-
**
Optimized
**
: Removing AlwaysDrawOutdoors vis area flag as it doesn't seem to be used anywhere and looks more like a hack fix for some bug than an actual feature.

-
**
Optimized
**
: Remove 'cheap light' option.

-
**
Optimized
**
: C3DEngine::GetObjectsByFlags is now always available.

-
**
Optimized
**
: Change the default of e_LightVolumesDefault to 1.

-
**
Optimized
**
: Restored terrain code which utilized decalnode::clone().

-
**
Optimized
**
: CRenderObject::m_nLod -> union for specific use.

-
**
Optimized
**
: Split geomcache fill job in high priority transform update and mesh update jobs.

-
**
Optimized
**
: Removed redundant turnaround of texture load request and function parameters.

-
**
Optimized
**
: Removed -specific ISkeletonAnim::GetRootTransform.

-
**
Optimized
**
: Adjusted texture streaming pool sizes based on RysePC requirements.

-
**
Optimized
**
: Use VectorMap instead of std::map.

-
**
Optimized
**
: DynArray improvements and refactoring: Default allocator now stores pointer to original allocator in memory, for compatibility across modules. Refactored allocator templates to use one multipurpose alloc() function. Refactored template components to be more independent: SmallDynStorage instead of SmallDynStorage<T, I>. Faster capacity storage scheme in SmallDynStorage. FixedDynArray and StaticDynArray now work correctly with non-POD types, constructing and destructing elements only on use. Removed FixedDynStorage, RawStorage, InitStorage classes. Various small fixes and optimizations. Moved code for clarity.

-
**
Optimized
**
: Changed engine and sandbox to boost 1.55.

-
**
Optimized
**
: Removed "GetTextureName" from decalnode.

-
**
Optimized
**
: Removed unused MAT_ENTITY type; inlining code of CLoaderCGF::ProcessMaterials() to get rid of the confusing function name.

##
Particles

-
**
New
**
: Reimplemented PlaneAlignBlendDistance for particles.

-
**
New
**
: Moving soft particle scale parameter from material into particle editor.

-
**
New
**
: Particle scale parameter can make particles both softer or harder (not only harder).

-
**
New
**
: Added particle reduce size and reduce life time based on keep density param.

-
**
New
**
: Added spherical approximation parameter to particles to choose between standard and spherical tangent calculations.

-
**
New
**
: Added glow map to particle shader.

-
**
Fixed
**
: (CE-4267) Broken bump-map normals (bad #if placement). Fixed issues with curvature: now affects only lighting normals, not expansion of near geometry.

-
**
Fixed
**
: (CE-5103) FPE in particle vortex rotation.

-
**
Fixed
**
: (CE-5514) Memory overwrite when out of particle vertex memory.

-
**
Fixed
**
: (CE-5456) Collision and timing issues, that prevented child decals from spawning or sticking; fixed infinite look-ahead on particle collisions.

-
**
Fixed
**
: (CE-5327) Spherical rendering expansion now based on shortest axis, fixing stretch & aspect errors.

-
**
Fixed
**
: Emitters now update when e_ParticlesThread = 0.

-
**
Fixed
**
: Using first 3 GSM for particle shadows.

-
**
Fixed
**
: Crash during phys area update callback.

-
**
Fixed
**
: Make sure particle vertices never end up exactly on the z=0 plane when 'Spherical Approximation' is used.

-
**
Fixed
**
: Don't overwrite particle alpha on refractive particles.

-
**
Fixed
**
: Changed soft particles from linear to inverse quadratic exponent.

-
**
Fixed
**
: Soft particles are also affected by camera approximation and not just surface. makes transitions into soft particles much smoother.

-
**
Fixed
**
: Depth fix up and glow map options had the same mask on shader extensions.

-
**
Fixed
**
: Errors in reading library versions <= 20: Facing conversion, Color splines.

-
**
Fixed
**
: Restored Horizontal facing behavior (aligns particles regardless of forces or turbulence). Correctly align particles for all combinations of Facing / OrientToVelocity.

-
**
Fixed
**
: Half-res CVars now properly obeyed. Half-res rendering fix.

-
**
Optimized
**
: Removed cube map caching logic from particle system and using now the 3dEngine cache instead.

-
**
Optimized
**
: Uninitialized m_II.m_Matrix in particle rendering.

##
RC/Tools

-
**
New
**
: Introduced
[/docs/static/engines/cryengine-3/categories/1638401/pages/19380746](
WAF build system
)
.

-
**
New
**
: Brand new Universal Remote Console, featuring new UI, filters and MIDI support.

-
**
New
**
: Added signed pixel-formats.

-
**
New
**
: Added "minTextureSize" key for upscaling.

-
**
New
**
: Added "mipgenop" key for min/max filtering.

-
**
New
**
: Added support for bias/scale for samplers.

-
**
New
**
: (RC) Added greyscale preset to crytiff.

-
**
New
**
: (RC) Changed formats for DisplacementMaps to BC4.

-
**
New
**
: (RC) Changed formats for NormalMaps to BC5S (signed).

-
**
New
**
: (RC ImageCompiler) Added analyze switch to ImageCompiler, creating in-depth debugging of compiled textures in a CSV.

-
**
New
**
: (RC ImageCompiler) Added DDS loading to ImageCompiler.

-
**
New
**
: (RC ImageCompiler) Added more sRGB/Linear to sRGB/Linear transform options to RCImage.

-
**
New
**
: Allow remote console to use alternative ports if default one is already used (for example by other instance of the game).

-
**
New
**
: Added cryAlembic.py tools for preparing and exporting for GeomCaches in Sandbox.

-
**
New
**
: Added cryAlembic.mel wrapper to the python scripts.

-
**
New
**
: Added cryDecorators.py, used by cryAlembic.py to assure AbcExport.mll is loaded.

-
**
New
**
: Re-added CppCheck. Enable Remote Execution for CppCheck. Add cppcheck translation files, configs and GUI tool.

-
**
New
**
: Added unknown exception parsing support to make errors clickable in visual studio.

-
**
New
**
: Added Maya cryAlembic buttons and icon bitmaps for shelf_Crytek.mel

-
**
Fixed
**
: (CE-5268) (RC ImageCompiler) Checking of code returned by sce::GpuAddress::computeSurfaceTileMode().

-
**
Fixed
**
: (CE-5064) (RC ColladaCompiler) Now using temporary .$tmp$ file when saving .cgf to prevent Editor's file monitor from reading half-written file.

-
**
Fixed
**
: (CE-5166) (RC Collada) fixed : Maya exporter: freeze transformations required.

-
**
Fixed
**
: (CE-5439) (LuaRemoteDebugger) Window Z-fighting between main window and child dialogs causes the child dialog to become unresponsive.

-
**
Fixed
**
: (CE-4969) (Statoscope) Unable to save captured logs.

-
**
Fixed
**
: (CE-5133) Fixed LightProjector texture format and TiledShading resource format to be identical.

-
**
Fixed
**
: (RC AnimationCompiler) CAF files that were put into DBA were still written to the disk.

-
**
Fixed
**
: (RC AnimationCompiler) Aimposes were stored in DBA.

-
**
Fixed
**
: (RC AnimationCompiler) Aimpose animations were compressed, now they always have zero compression.

-
**
Fixed
**
: (RC AnimationCompiler) Using proper input filename for RC's AddInputOutputPair() - DBATable.json or DBATable.xml.

-
**
Fixed
**
: (RC) Fixed bug in removal of duplicate morph vertices.

-
**
Fixed
**
: (RC) Disable RC's own timestamp checks for processing.

-
**
Fixed
**
: (ChunkExplore) Improved printing of material's physicalizations types.

-
**
Fixed
**
: (MayaCryExport) Bug when using addPoseFrame that the time range is not properly set in the animation clip.

-
**
Fixed
**
: BytesperBlock to BytesPerPixel for non-block formats.

-
**
Fixed
**
: File race-condition in texture compiler.

-
**
Fixed
**
: Prevent ImageCompiler accessing uninitialized memory from partial decompression.

-
**
Fixed
**
: Sigma-six filtering clamp of support region.

-
**
Fixed
**
: Bug in the attached alpha flag conversion.

-
**
Fixed
**
: Crash in case a submaterial has no name.

-
**
Fixed
**
: Alpha-weight flag set twice.

-
**
Fixed
**
: Autoselectpreset filename mismatch.

-
**
Fixed
**
: Preview of signed compressed textures.

-
**
Fixed
**
: Checking alpha of textures without alpha.

-
**
Fixed
**
: Missing alpha-channel awareness for Bitmaptooltip.

-
**
Fixed
**
: Need to force NOT_USE_CRY_MEMORY_MANAGER on all RC modules.

-
**
Fixed
**
: Possible random timestamp assignment to dummy textures.

-
**
Fixed
**
: Prevent a possible race-condition in the texture-queue submission.

-
**
Fixed
**
: Changed order of normalization of pixel ranges.

-
**
Fixed
**
: Generalized alpha-coverage API.

-
**
Fixed
**
: Allow all formats being previewed as 3x2 cubemaps.

-
**
Fixed
**
: Stop faulting texture-requests to trigger again.

-
**
Fixed
**
: Allow old texture-checkouts being queued for compilation as well.

-
**
Fixed
**
: Lower decompress & decode job priority to eStreamPriority.

-
**
Optimized
**
: (MaxCryExport) Renamed/removed functions called ProcessXXX in favor of SaveXXX functions; added const.

-
**
Optimized
**
: (MaxCryExport) Removed OpenMP.

-
**
Optimized
**
: Changed lightprojector to greyscale-only, higher precision BC4.

-
**
Optimized
**
: Removed CryCP icon bitmap file and shelf_button connection in shelf_Crytek.mel.

-
**
Optimized
**
: Pixel-format unification.

-
**
Optimized
**
: Removed redundant code/variable from SRFCompiler.

##
Audio

[Image: /docs/static/attachments/44962970]
*

ACB UI when running with the Wwise implementation
*

[Image: /docs/static/attachments/44962949]
*

ACB UI when running with the SDL Mixer implementation
*

-
**
New
**
: Introduced SDL Mixer audio implementation.

-
**
New
**
: (ACB) Wwise controls are also loaded from subfolders.

-
**
New
**
: (ACB) Execute control with the space bar.

-
**
New
**
: Support for stopping events in the SDL Mixer implementation.

-
**
New
**
: Serialization: resource selectors for audio types.

-
**
Fixed
**
: (CE-5495) Preventing crash on shut down where the audio logger accessed an invalid cvar pointer.

-
**
Fixed
**
: (CE-4313) Now all audio triggers are stopped on vehicles that get released without a reset call beforehand.

-
**
Fixed
**
: (CE-4385) GameAudio class does not try to parse obsolete audio xmls anymore.

-
**
Fixed
**
: (CE-4570) Now resetting environments on AAAs once they get disabled.

-
**
Fixed
**
: (CE-4452) prevent audio trigger execution on hidden entities.

-
**
Fixed
**
: (EntitySystem) Check if we are using an audio implementation before creating the audio proxy by default.

-
**
Fixed
**
: Communication Handler can now be notified when a sound stops his playing so that it can notify all the listeners about the sound stop event.

-
**
Fixed
**
: Ref counting of AFCM entries, blocking load requests now cause a blocking stream as well.

-
**
Fixed
**
: ATS now updates its environment once it moves.

-
**
Fixed
**
: Audio module is now shut down last and with that does not cause dangling audio proxy pointers.

-
**
Fixed
**
: Crash when entering game mode in editor.

-
**
Fixed
**
: Particle effects retrigger audio even if they have not been disabled before.

-
**
Fixed
**
: SDL Mixer events are set to "start" by default.

-
**
Fixed
**
: Let the Audio System sleep some time to prevent busy waiting.

-
**
Fixed
**
: Ignore sleep time in function profiler during internal update.

-
**
Fixed
**
: Increased stack size of WWise Thread to allow using stack heavy log functions of CryEngine.

-
**
Optimized
**
: Push audio object position update requests only if they moved by a given delta for that introduced new CVar: s_PositionUpdateThreshold.

-
**
Optimized
**
: Removed deprecated audio tools.

##
Animation

##
Animation System

[Image: /docs/static/attachments/44963002]

*
Secondary Animation showing Lozenges in action for character attachments.
*

-
Characters always reset to their bind pose at the beginning of the animation update. As a result you will notice bind poses when you are not playing animation, which should help detecting those kinds of bugs.

-
Improved or removed various warnings, errors, asserts, fatalerrors and pop-up boxes.

-
Blend-spaces:

-
Blend-spaces can now be played on any animation layer (not restricted to layer 0 anymore). A blend-space can now contain additive or override animation, though you are not allowed to mix different types within one blend-space.

-
Splice animations (aka MotionCombinations) within blend-spaces are not supported anymore. You can still use dedicated animation layers to achieve the same result. (as an example: in GameSDK the "weaponpose" animations which used to be splice animations are now implemented using additional layers within Mannequin fragments).

-
Allow virtual example grid precomputation for any number of dimensions, and generate the data in the BSPACE files directly from within character editor (right-click on a BSPACE, select 'Save VGrid').

-
Debugging:

-
es_debuganim now also displays the animationqueue for attachments of the entity.

-
es_debuganim (and ca_debugtext) now also show the name of the model before showing the layers (to make it easier to tell them apart when multiple queues are shown).

-
Secondary Animation:

-
Activated proxies and collision response for normal face and bone attachments (which are not re-directed). This can only be edited in character editor (soon also in character tool).

-
Introduced new Lozenges tech which simplifies character attachment physics down to 4 numbers and 8 shapes.

-
Pose Modifiers:

-
OperatorQueue Modifier: Added operation that allows for overriding the world space location of a joint.

-
Experimental: Initial implementation for data driven 'Pose modifer components' were added. Code is wrapped in ENABLE_RUNTIME_POSE_MODIFIERS and marked as 'experimental' in the editor, indicating that this feature is likely to change in the future.

-
CHRPARAMS:

-
Deprecated the undocumented BBoxExcludeList feature of CHRPARAMS. To specify the bounding box w
e recommend using a combination of BBoxIncludeList (listing a
 minimal amount of joints to get a reasonable bounding box) and BBoxExtension (to extend the box a bit). In order to re-enable the old feature, you can enable the #define ENABLE_BBOX_EXCLUDE_LIST in ICryAnimation.h, but we will remove this code in a later SDK version.

-
The dysfunctional #ParseSubFolders directive from CHRPARAMS is now ignored (to parse sub folders, use the '*/' syntax as described in the documentation).

##
Animation Pipeline (Editor, RC, ...)

*
[Image: /docs/static/attachments/44962971]

Streamlined animation event editing with user defined presets.
*

[Image: /docs/static/attachments/44962972]

*
ChrParams editing; here for example we add a prefix to the animation names of all .comb files
*

[Image: /docs/static/attachments/44962974]

*
Rule-based compression presets; for example apply settings based on animation tags as in this example
*

-
Introduction of Character Tool (for more information see
[/docs/static/engines/cryengine-3/categories/1114113/pages/19380982](
Character Tool
)
).

-
Unifies Character Editor, Animation Importer, Animation Compression Editor and DBA Editor in one tool with reworked UI.

-
It acts as asset browser for animation related files.

-
Allows editing of CHRPARAMS, though not all properties are exposed yet in this release, those will be added in a subsequent version.

-
Can be used to inspect content of existing BSPACE and COMB files.

-
Allows to define flexible rules for DBA grouping.

-
Adds an editor for compression presets.

-
Allows editing of experimental
Pose Modifier
 Components.

-
Animation Compression Editor, Animation Import and DBA Editor are removed in favor of Character Tool.

-
Character Editor is deprecated in favor of Character Tool and will be removed in future releases.

-
AnimSettings format changed (
**
format can be updated by simply resaving in Character Tool: File->Resave AnimSettings...
**
).

-
New way to define DBA files. Use of dbatable.xml is deprecated and replaced by DBA presets saved in dbatable.json. Support for DBATable.xml will be removed in a future version, so
**
users are advised to manually convert DBATable.xml
**
(see below:
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962947#EaaS3.7.0-DBATableConversion](
DBATable Conversion
)
).

-
New way to define animation compression presets (CompressionPresets.json, working hand in hand with the settings in the animsettings).

-
We now allow animations to be placed and processed by the editor outside of the animations folder.

-
Display status of background task manager in Sandbox status bar (along with texture compilation status). Change in behavior: we now also display the failures when no tasks are running.

-
RC: When CHR files contain controller names, we now use them to improve error messages during compression. The Collada->CHR converter has been changed so it also exports these controller names.

##
Animation Fixes

-
ResourceCompiler:

-
Fix bug with random animations failing to be processed because of bug in PakSystem GetLength() function.

-
Fixed unitialized variable in background task, which could have caused error messages not to appear.

-
Blend-spaces:

-
COMB blend-spaces will now pick the closest BSPACE in the case where no parameters match directly. The parameters will then be clamped to the chosen blend-space limits internally. Previously the parameteriser would bail without an exact match causing the first example animation to receive 100% of the weight.

-
Fixed out of bounds array access in various places when a COMB contains an unknown or invalid BSPACE.

-
Small fix for AABB being oversized on small characters (minimum size of the bounding box has been reduced to 10 cm).

-
SkeletonEffectManager::IsPlayingAnimation now checks all animation layers instead of only the first 4.

-
CHRPARAMS:

-
Fixed a couple of bugs during reloading of chrparams (including uninitialized error state in PoseBlenderAim/LookDesc).

-
Facial Animation (Facial Instance):

-
Skeleton extension now works in combination with FacialInstance.

-
Fix for bone effector rotations not being applied correctly. Previously one effector with weight of 1 would only end up rotating half as much as expected, it now rotates the full amount. Concatenated transforms are still applied correctly and translation is still kept separate to rotation so order of effectors doesn't effect the result.

-
CModelAnimationSet::GetAnimationDCCWorldSpaceLocation: Fixed undefined behavior when the animation that is passed in is not a CAF, now always returns false in that case.

-
Look & Aim IK:

-
Fix for Look & Aim IK not playing nicely with scrubbing time etc. (now uses the time delta that is passed in, not an average over time).

-
Bugfix in PoseBlenderAim and -Look to Synchronize when Prepare fails.

-
Fixed inconsistencies in checks for number of supported poses for aim and look poses.

-
Aim or look poses can now use skeletons with more than 255 joints.

-
Fixed floating point exception when bone has zero length.

-
Animation:

-
The system now plays additive animations on upper layers if there's no base animation currently playing.

-
Fix for animations started with the CA_FORCE_TRANSITION_TO_ANIM flag sometimes failing to play.

-
Fix for exploding character during overwrite blending mode.

-
Fix for multilayer animation blending.

-
Fix for faces folding themselves inside out; if an anim is missing all channels then it should use the bind pose.

-
Animation events path was incorrectly reset when using skeleton extensions.

-
Removed support for animevent with name "segment4". (since it always had to be at time 1 anyway).

-
Feet locking: Unified the check that enabled/disabled feet locking, solving some corner cases where feet locking was not properly enabled.

-
Streaming: Fixed broken defrag heap stats for fixed allocs.

-
Pose Modifiers:

-
Now clearing pose modifier queues when characters are off-screen to avoid pose modifier queue overflow.

-
DBA Files:

-
Fix for crash when a DBA contains animations with more than 255 controllers.

-
Fix for crash when loading DBA files containing more than 8192 animations.

-
Debugging:

-
Fix for crash when using ca_debugAnimUsage with missing DBA files.

##
Animation API Changes

-
Made it easier to use CryAnimation's interfaces in 'const correct' code: Functions in CryAnimation's interfaces that can be const are now const; also added const variations where possible.

-
IAnimationSet:

-
GetDuration_sec() now never returns negative values.

-
Added SampleAnimation(), a basic function to sample any controller in a CAF animation.

-
Editor Only: Added new functions like GetSubAnimations(), IsCombinedBlendSpace(), etc. so the editor can find out more about animations at run-time.

-
ICharacterInstance:

-
Renamed GetOjectType() to GetObjectType().

-
Removed IgnoreScaleForJoint()/CustomScaleForJoint() and SetUniformScale(). The first two are incomplete features, the last is unneeded: you can use the scale in the locationAnimation parameter to StartAnimationProcessing.

-
ISkeletonPose:

-
Removed SetPostProcessQuat().

-
ISkeletonAnim:

-
Exposed skeleton animation layer count as ISkeletonAnim::LayerCount. Removed all the hardcoded layer count values we could find.

##
Mannequin

[Image: /docs/static/attachments/44962965]

[Image: /docs/static/attachments/44962959]

-
New procedural clip format:

-
Stronger typing of clip properties.

-
Scripts/Mannequin/ProcDefs.xml is no longer needed, everything is now exposed through the serialization framework.

-
Conversion is done automatically using the
`
 Scripts/Mannequin/ProcClipConversion.xml
`
 file.

-
**
In case you have custom made procedural clips you will need to edit the ProcClipConversion file for them to be automatically converted too.
**
 More details here:
[/docs/static/engines/cryengine-3/categories/1114113/pages/19381016](
Procedural Clip Parameters using Serialization Framework
)
.

-
Mannequin editor:

-
Various usability tweaks and fixes (tab navigation, browsing using arrow keys, copy-pasting tracks, etc).

-
Right-clicking on an animation clip, the user can edit the source asset, be it a blend-space or Maya file. (see
[/docs/static/engines/cryengine-3/categories/1114113/pages/15012282](
Mannequin Animation Clip Properties
)
)

-
Right-clicking on an animation clip, the user can find all transitions referring to the same clip. (see
[/docs/static/engines/cryengine-3/categories/1114113/pages/15012282](
Mannequin Animation Clip Properties
)
)

-
Transition browser can now filter transitions based on animation names.

-
Middle-click + mouse move on the timeline will now always scrub through time.

-
Showing time in frames by default.

-
Scopes or individual layers can be 'muted'. In other words they can be temporarily disabled. (see
[/docs/static/engines/cryengine-3/categories/1114113/pages/19381800](
Mannequin Track Properties
)
)

-
Addition of a
[/docs/static/engines/cryengine-3/categories/1114113/pages/19381020](
List Used Animations
)
 tool.

-
Editor now only saves files related to the project currently being edited.

-
Added a "Re-export" all feature. This will load all the mannequin files and try to save them.

-
Fixed previewing of additive animations on upper layers if there's no base animation currently playing (CE-4754
).

-
Fragment Browser: Support for copy pasting of sets of fragments, as well as addition of special paste feature to change tags while pasting (Ctrl+Shift+V). (see
[/docs/static/engines/cryengine-3/categories/1114113/pages/15011340](
Mannequin Fragment Browser
)
)

-
Fixed crash when updating Perforce with the editor open but without a Mannequin editor instance.

-
Flow nodes:

-
Moved Mannequin nodes from GameSDK to CryAction. (see
[/docs/static/engines/cryengine-3/categories/1114113/pages/15733635](
Mannequin Flowgraph
)
)

-
Added a flow node to listen for events triggered by a dedicated procedural clip. See Actor:ProcClipEventListener and the "FlowGraphEvent" proc clip.

-
Procedural clip changes: (see
[/docs/static/engines/cryengine-3/categories/1114113/pages/15011327](
List of Procedural Clip Types
)
)

-
ParticleEffect procedural clip can now explicitly reference an attachment interface or a joint ID.

-
ParticleEffect procedural clip has now a 'Keep Emitter Active' boolean field in order to trigger effects with a life longer than the clip. The procedural clip is controlling a procedural context.

-
SoundMood procedural clip has been removed (is unneeded with the new audio system).

-
ForceFeedback procedural clip now has a flag to trigger force feedback only locally.

-
Fixed missing procedural clip CompromiseCover.

-
Audio procclip introduced to go along with the introduction of the audio translation layer. This procclip at the moment is the same as the deprecated PlaySound procclip.

-
System:

-
SCA fixes in the mannequin code.

-
API change: public interfaces dealing with IActions now take references instead of smart pointers to make it clear that they do not accept NULL pointers.

-
Experimental: Added a new OnActionFinished virtual method in IAction to let the client know when a fragment reaches a user-defined completion point. This can be used by client code to make decisions on which action to play next without waiting for the Exit() callback, thus providing a convenient way of eliminating "frozen" transitions. Editing for this is not enabled yet in this build, but some initial code can be enabled by enabling MANNEQUIN_BLENDOUT_EDITING in code in FragmentTrack.cpp in the editor

-
IAction::ComparePriority (see
[/docs/static/engines/cryengine-3/categories/1114113/pages/15011601](
Mannequin Actions
)
) )is now also called during CActionController::PushOntoQueue() to make it consistent with CActionController::TryInstalling(). If you override IAction::ComparePriority() in an action, make sure the order is well defined (a.ComparePriority(b) should return the opposite of b.ComparePriority(a)). If you previously simply returned "Higher", and you push multiple equal priority actions within the same frame, you can use something like the following to make sure the queue still behaves as a FIFO:

```

`
virtual EPriorityComparison ComparePriority(const IAction& actionCurrent) const
{
  return (IAction::Installed == actionCurrent.GetStatus() && IAction::Installing & ~actionCurrent.GetFlags()) ? Higher : IAction::ComparePriority(actionCurrent);
}
`

```

##
DbaTable Conversion

See below to read information on how to transition the DBATable file from XML to the new JSON format.

Initially DbaTable.xml file contained a list of CAF-files that are grouped per DBA.

This proved itself to be error-prone and requiring regular intervention of a technical person to update it with newly added animations.

To reduce maintenance overhead a new way to define DBA was introduced in SDK 3.7. It differs in following:

-
Instead of listing individual animation files a filtering condition can be defined for each DBA. It selects animations based on certain criteria. For example on file location, name substring, or certain tags assigned.

-
Conditions can be combined with logical expression into a complex conditions.

-
Filename that is used to store the table changed from DBATable.xml to DBATable.json (internally it is converted into JSON as well).

-
No need for manual editing anymore: DBATable.json can be edited and debugged through Character Tool.
As previous format didn't contain any high-level information, conversion should be performed manually.

An example of such conversion is provided below based on SDK assets.

```

`
<DBAs>
  <DBA Path="Animations\human\male\hits_1p.dba">
    <Animation Path="Animations\human\male\hits\1p\stand_tac_hit_generic_add_1p_01.caf"/>
    <Animation Path="Animations\human\male\hits\1p\stand_tac_hit_knockDown_1p_01.caf"/>
    <Animation Path="Animations\human\male\hits\1p\stand_tac_idle_reactExplosion_3p_01.caf"/>
  </DBA>
  <DBA Path="Animations\human\male\hits_3p.dba">
    <Animation Path="Animations\human\male\hits\3p\coverHigh_idleBasic_com_lft_hit_back_01.caf"/>
    <Animation Path="Animations\human\male\hits\3p\coverHigh_idleBasic_com_lft_hit_front_01.caf"/>
    <Animation Path="Animations\human\male\hits\3p\coverHigh_idleBasic_com_rgt_hit_back_01.caf"/>
    <!-- ... -->
  </DBA>
  <DBA Path="Animations\human\male\locomotion.dba">
    <Animation Path="Animations\human\male\locomotion\kneel\kneel_tac_AimPoses_idle_01.caf"/>
    <Animation Path="Animations\human\male\locomotion\kneel\kneel_tac_death_01.caf"/>
    <Animation Path="Animations\human\male\locomotion\kneel\kneel_tac_idle_01.caf"/>
  <!-- ... -->
  </DBA>
  <!-- ... -->
</DBA>
`

```

Similar setup with a new system will look as following:

[Image: /docs/static/attachments/44962961]

You may refer to
[/docs/static/engines/cryengine-3/categories/1114113/pages/19380982](
Character Tool
)
 documentation to see how to define animation filter in details.

In case you would like to perform automated conversion yourself, files saved by the Character Tool will look as follows:

```

`
{
  "entries": [
    {
      "path": "Animations/human/male/hits_1p.dba",
      "condition": { "inFolder": { "path": "Animations/human/male/hits/1p/" } }
    },
    {
      "path": "Animations/human/male/hits_3p.dba",
      "condition": { "inFolder": { "path": "Animations/human/male/hits/3p/" } }
    },
    {
      "path": "Animations/human/male/locomotion.dba",
      "condition": { "inFolder": { "path": "Animations/human/male/locomotion/" } }
    }
}
`

```

Due to ResourceCompiler limitation, incremental builds can not be performed after removing old DBATable.xml. Make sure to delete previous build state (specifically rc_createdfiles.txt, by default created in the folder of RC executable Bin64/rc/), otherwise CAF files may not be produced as expected.

What if you need some more complex logic in animation selection?

For example, here we are excluding /poses/ folder from locomotion.dba, as well as all animations that have word "kick" in their name:

[Image: /docs/static/attachments/44962960]

##
AI System

[Image: /docs/static/attachments/44962966]

*
Multi-threaded NavMesh processing can significantly speed up time to process MNM areas.
*

-
**
New
**
: Multi-threaded AI systems: Added ai_NavGenThreadJobs CVar to allow control over how many threads to allow Navigation system to use for processing meshes.

-
**
New
**
: First iteration of the refactoring of the MovementSystem to detach the PipeUser from the system. Now a MovementActor needs to be provided of an implementation of an adapter that must provide the implementation of the needed functionality to use the AISystem features.

-
**
New
**
: The associated entity id of both observer and observable parameters can now be changed.

-
**
Fixed
**
: (CE-5313) The debug draw mode for the modular behavior tree variables is now bound to the ai debug target instead of the cvar ai_DebugBehaviorVariables (which is now removed).

-
**
Fixed
**
: (CE-4958) Fixing the OnPropertyChanged callback setup for SmartObjects when selecting multiple ones at the same time.

-
**
Fixed
**
: (CE-5023) NavigationSystem: bumped BAI_NAVIGATION_FILE_VERSION since struct MNM::Tile::Triangle is no longer compatible with older versions.

-
**
Fixed
**
: (CE-5251) Removing only addition if a smart object is deleted. Removal of the link should still be executed since we need to notify the navigation system.

-
**
Fixed
**
: (CE-5356) MBT SDK_Grunt_07.xml: weapon is no longer holstered in the Idle subtree itself, but rather just before transitioning to that tree.

-
**
Fixed
**
: (CE-5300) CollisionAvoidanceSystem: Removed a heuristic to minimize the case where an agent would get stuck at a side of a corridor when avoiding a standing agent (the constraint line no longer changes suddenly).

-
**
Fixed
**
: (CE-5108) Fix OffMeshNavigationManager crash with Smart Objects.

-
**
Fixed
**
: (CE-5183) Fix the SetSwitchState calls in the CommunicationHandler. Now the calls happen only if there is a value to switch and so we should only get valid warnings. Also fixed the warning to communicate the not existance of the "switch state" and not of the "switch".

-
**
Fixed
**
: (CE-5482) Fixed the IPhysicalEntity reference managing by the vision map.

-
**
Fixed
**
: Crash when moving a river during MNM generation.

-
**
Fixed
**
: SDK_Grunt_07.xml: removed some StopMovement nodes to get rid of unnecessary abrupt stops before going to Combat and fixed animation twitching when in Idle.

-
**
Fixed
**
: Engine changes to allow to the AISystem to create and return a default PathFollower. Users can specify the PathFollowerParams and the IPathObstacles that should be used with the created pathfollower.

-
**
Fixed
**
: AIMoveSimulation is now using directly the Movement System instead of passing through the goalpipes.

-
**
Fixed
**
: Exposing the AI system's AgentDebugTarget to its interface.

-
**
Fixed
**
: Adding an input action to trigger the debug visualization of an AI agent (will be mapped to the / key).

-
**
Fixed
**
: Adding a base AI extension for the actor, which will serve as the base for the AI specific actor game object extensions.

-
**
Fixed
**
: Adding the modular behavior tree actor extension which will enable the execution of behaviors by actors.

-
**
Fixed
**
: The modular behavior tree extension now registers and handles actor events.

-
**
Fixed
**
: Fixed selection behavior so you can select parent groups that are not mesh shapes.

-
**
Fixed
**
: Load behavior tree from xml node.

-
**
Fixed
**
: The modular behavior tree can now also load files from the libs/ai/behavior_trees/ folder.

-
**
Fixed
**
: VisionMap: Added customizable raycast flags.

-
**
Fixed
**
: Adding a vision map helper for adding entities to the observer or observable params skip list.

-
**
Fixed
**
: Removing unnecessary includes from the tactical points component header file.

-
**
Fixed
**
: Adding the 'pure grid' generator to the TPS system.

-
**
Fixed
**
: Adding the 'entity' object to the TPS system.

-
**
Fixed
**
: Deprecating a node specific to the Crysis 3 'stalker' character which was still being defined in the AI System.

-
**
Fixed
**
: TPS queries are now reloaded on RESET_ENTER_GAME in editor mode or on RESET_LOAD_LEVEL.

-
**
Fixed
**
: Adding the concept of blackboard to the modular behavior tree, which the nodes can use to share information between each other.

-
**
Fixed
**
: Added native support for dispatching events to the behavior trees.

-
**
Fixed
**
: Made the modular behavior tree debugging to work with any entity, and not only AI actors. You can now look at an entity running a behavior tree and hit the numpad "slash" key to start debugging.

-
**
Fixed
**
: TacticalPointSystem: result of the "reachable" property wasn't returned to the calling code.

-
**
Fixed
**
: Crash in CSmartObjectsManager when unticking all classes of a SmartObject.

-
**
Fixed
**
: MNM::MeshGrid::SetTile() was guarding against bad input parameters in only 1 out of 3 cases.

-
**
Fixed
**
: TPS queries are now required to have entries in their Weights and Generation tables to guard against undefined behavior.

-
**
Fixed
**
: The exit point of an off mesh link should be stored as a NAV_UNSET inthe NavPath and not with the same type as the entry point.

-
**
Fixed
**
: Increased the AI interaction query result container from 32 to 48 to stop bogus warnings.

-
**
Fixed
**
: Pass the lowerPrecision parameter instead of using the hardcoded false value inside PipeUserMovementActorAdapter::RequestExactPosition.

-
**
Fixed
**
: Reset function of the modular behavior tree extension.

-
**
Fixed
**
: Obstruction position not being updated when the raycasts are complete.

-
**
Fixed
**
: Registration of observable objects in the vision map now correctly stores all the information from the parameters (before the associated entity param was not correctly added).

-
**
Fixed
**
: Navigation system code can now handle correctly cases in which the exported data contains references to actors that are not correctly setup or meshes that cannot be created.

-
**
Fixed
**
: Reset the pathfollower when attaching a new path because the last version of the path store and the internal values may still refer to the old path that is no longer valid.

-
**
Fixed
**
: Always set flag ENTITY_FLAG_TRIGGER_AREAS to Actors, so AreaManager can process Actors in Multiplayer. Note that the logic that does the actual triggering of the Area Trigger is done in AreaTrigger.lua. The lua file checks whether the Actor is a client or not and other properties set in the editor.

-
**
Fixed
**
: State machine node from the modular behavior tree now verifies that it has the minimum amount of states, preventing it being used to in a way that could lead to a crash: BehaviorTree::StateMachine::Update.

-
**
Fixed
**
: SDK_Grunt_07 now uses "Relaxed" stance throughout the Idle state.

-
**
Fixed
**
: CVisionMap::IsInFoV() was considering not all observable positions.

-
**
Fixed
**
: Collision Avoidance was not taking CAIPlayers into consideration (CE-5523).

-
**
Fixed
**
: SDK_Grunt_07: in DefendArea assignment AIs move now to a more random position around the center of that area.

-
**
Optimized
**
: Tweaked the position of the variable collection debug draw.

-
**
Optimized
**
: Removed the dependency with the AI System's IAISignalExtraData interface from the events.

-
**
Optimized
**
: Removed the concept of event dispatcher from the modular behavior tree, as its its functionality is deprecated and its use had a different behavior from the manager's handle event functions (time stamps and the behavior variables were not updated).

-
**
Optimized
**
: First step of the refactoring CMNMPathfinder code to expose some of the structures that will be needed to multi-thread the code. Moving the m_processingRequestData into the m_processingRequest. Split the NavigationSystem update into three consecutive stages: 1-Write => 2-Read => 3-Dispatch. Remove wrong release called on the smart object containing the path in the PathAgentExtension. When an agent cancel a MNMPathfinder request we also need to clear the events that may be already ready to be sent to the agents. Removing pathCount parameter from the Triangle structure.

-
**
Optimized
**
: Move the MovementRequestID to his own header file to avoid to have to include the whole MovementRequest when only the id definition is required.

-
**
Optimized
**
: Corrected typo in the communication system. Rephrased a few of comments on the MBT nodes.

-
**
Optimized
**
: Typedeffed boost::shared_ptr<BehaviorTreeInstance> to BehaviorTreeInstancePtr.

-
**
Optimized
**
: Exposed functionality to start and stop behavior trees via the interface of the behavior tree manager.

-
**
Optimized
**
: Removed some redundancy in the modular behavior tree event code. Also added an extra private for better readability.

-
**
Optimized
**
: Changed the communication manager's ID's to use CRCs as the current hashing function was poor, in terms of crashing with a set of communications we were trying to add due to the length of the string causing it to skip unchanged characters and result in a hash clash. AI Debug renderer now draws text in monospace mode. Integrating the VisionMap system. Integrating the tree visualizer.

-
**
Optimized
**
: The functions IsPointReachableFromPosition now gets a IEntity pointer instead of an IAIPathAgent. Also renaming the variable name to make it clear the purpose of the usage of that pointer.

-
**
Optimized
**
: GetSmartObjectLinkCostFactorForMNM function allowing to pass to FindSmartObjectLinks a list of states to exclude from the match of the smart object states instead of passing a filtered list that requires a vector copy (for multiple calls in the same frame is very expensive).

##
Game

-
**
New
**
: (Network) [NetMessageDistpatcher] New system to send simple messages from client to server and vice versa, including flow graph nodes for designers.

-
**
New
**
: Added logic and CVars to control players breathing capability / drowning (CE-5061).

-
**
New
**
: Expose entities in area via entity area proxy.

-
**
New
**
: Bind one or more independent listeners to an action map.

-
**
New
**
: Restored USM_Player.fla.

-
**
Fixed
**
: (CE-5171) "Too many silhouettes active" warning message appearing when it shouldn't.

-
**
Fixed
**
: (CE-5034,4155,5113) (Nework) No longer assume a HUD is always present to prevent floating HUD during killcam playback.

-
**
Fixed
**
: (CE-5342) (Vehicle) Custom animated joint part geometry can't use vehicle paint material. Added new 'usePaintMaterial' script parameter.

-
**
Fixed
**
: (CE-5354) (CryAction) Vehicle: Tank tread won't oscillate.

-
**
Fixed
**
: (CE-5270) (EntitySystem) CScriptBind_Entity::SetLinkTarget() was inspecting the wrong parameter

-
**
Fixed
**
: (CE-5146) (UI) Clients can only join the server at the top of the server list.

-
**
Fixed
**
: (CE-5279) (UI) Flash wants "loop" flag set for USM_Player.gfx.

-
**
Fixed
**
: (CE-5188) (UI) MP Chat functionality broken.

-
**
Fixed
**
: (CE-5426) (UI) Mission text typing speed too slow.

-
**
Fixed
**
: (CE-5409) (UI) Mission objectives - hold down tab to prolong the mission details only 1/2 times out. Fixed bug where a new mission detail would close when the old mission was solved right before that.

-
**
Fixed
**
: (CE-5467) (UI) Added calculation to take varying frametimings into account when displaying mission messages.

-
**
Fixed
**
: (CE-5236/5223) (UI) If you fail a set mission, the UI portion that deals with Mission text will no longer work. If no following mission is set the prev misson details stay active. Various small fixes and improvements to Objectives flowgraph.

-
**
Fixed
**
: (CE-4386) Weapon reload does not work when a use message is on screen.

-
**
Fixed
**
: (CryAction) GameObjects update state is stuck on "FarAway".

-
**
Fixed
**
: (Network) CRASH: GFxAmpServer::SetState on dedicated server.

-
**
Fixed
**
: (Network) Crash in CSimpleHttpServer when failing to bind to an address.

-
**
Fixed
**
: (Network) Added missing NULL ptr checks to prevent crashes on Dedicated Server.

-
**
Fixed
**
: (Network) Crash when quitting dedicated server.

-
**
Fixed
**
: (Network) Crash on dedicated server shutdown.

-
**
Fixed
**
: (Network) Potential FPE on server when all clients disconnect.

-
**
Fixed
**
: (EntitySystem) Wrong/duplicated assert in entityloader.

-
**
Fixed
**
: (Input) ForceFeedback: Check for DeviceType instead of DeviceId.

-
**
Fixed
**
: (UI) HUD not visible after trackview sequence gets aborted (CE-5481).

-
**
Fixed
**
: Remove 'ActorEntity' hard-coded dependency in EntitySystem.

-
**
Fixed
**
: Avoid to ragdollize the players if god mode is enabled.

-
**
Fixed
**
: Crash in IGameObject::SetGameObject.

-
**
Fixed
**
: Crash on character respawn.

-
**
Fixed
**
: Spawn Groups Enable/Disable not updating the spawnpoint list.

-
**
Fixed
**
: LUA error when AreaTrigger:Event_Enter is called directly (e.g. by TrackView) as opposed to being generated by an actual entity entering in the area.

-
**
Fixed
**
: Use after free in CVehicleSeat::StandUp.

-
**
Fixed
**
: Use after free in ~CFlashUI (CryName pool used is already destroyed).

-
**
Optimized
**
: (CE-5270) (EntitySystem) Several script-bind functions related to entity-links.

-
**
Optimized
**
: (Network) Changed from #if !defined(DEDICATED_SERVER) ifdefs into runtime checks.

-
**
Optimized
**
: Simplify changes to action map system.

##
Assets

[Image: /docs/static/attachments/44962957]

[Image: /docs/static/attachments/44962956]

[Image: /docs/static/attachments/44962955]

[Image: /docs/static/attachments/44962954]

-
**
New
**
: Added new Rifle weapon and accessories.

-
**
New
**
: Added new Swat Van vehicle and accessories.

-
**
New
**
: Added new Hmmwv vehicle and accessories.

-
**
New
**
: Added new Abrams vehicle and accessories.

-
**
New
**
: Added new Blackhawk vehicle and accessories.

-
**
New
**
: Updated Abrams script to suit new assets.

-
**
New
**
: Added HMG Mannequin setup and some additional anims.

-
**
New
**
: Added pistol+flag Mannequin aimpose.

-
**
New
**
: Added default friendly_leave setup. Set nw idlepose to nw animation instead of rifle.

-
**
New
**
: Added some new trees and rocks.

-
**
New
**
: Added various new road texture/materials and source files for new/old textures.

-
**
New
**
: Added several example terrain materials and textures.

-
**
New
**
: Added MergedMeshSurfaceType.xml used to configure the merged mesh collision audio.

-
**
New
**
: Added many new generic PBR texture and material setups, concrete, brick, metal, wood, etc.

-
**
New
**
: Added buxus hedges assets.

-
**
New
**
: Added Damaged version of speedboat. Deleted unused CGF. Started on Anims version for propellers/steeringwheel.

-
**
Fixed
**
: (CE-5063) Removed <MotionCombination> code from bspace/comb files (deprecated method) into Mannequin fragments as animlayers.

-
**
Fixed
**
: (CE-5237) HUD is invisible. Changed the HUD material Texture-Type of Flash-textures to "Dynamic 2D" instead of "Auto-2D" to not conflict with water reflections.

-
**
Fixed
**
: (CE-4933) Grenade does not explode if you throw it straight up in the air. Also fixed case of in-water. Missing exp entries in the mat_default column.

-
**
Fixed
**
: (CE-4420) Greenhouse: Split some glass pieces which shouldn't have been connected. Separated proxy mesh back out (doesn't need to be merged). Removed unnecessary proxy sections. Set Proxy material surface type to Metal (Glass surface type was causing errors).

-
**
Fixed
**
: (CE-5436) Wall_decal material on Hangar asset, changed to brick texture.

-
**
Fixed
**
: (CE-5503) Deleted cloth_2 assets. Redid material for main Cloth asset. Exported low and high quality versions (tessellated 2x/0.5x). Deleted ugly old textures.

-
**
Fixed
**
: (CE-5600) Increased resolution to 1k and re-created dirt_bullet sprite textures using slightly modified blood alpha textures and layered dirt diffuse textures.

-
**
Fixed
**
: (CE-4310) Added RPG and HMG events to AI Mannequin setup for audio.

-
**
Fixed
**
: (CE-5660) Added MotionMove fragment setup for AI RPG.

-
**
Fixed
**
: (GeomCache) Make stone_toad playback from memory.

-
**
Fixed
**
: Added general blend_out+standup event (removed shotgun event which used Rifle anims). Added RocketLauncher events select/deselect/melee.

-
**
Fixed
**
: Updated skeleton_player_generic.chrparams for 3.7 release: removed unsupported defaultlookpose, and replaced bboxexcludelist by a bboxincludelist and bboxextension.

-
**
Fixed
**
: Smoothed canyon_path_a proxy so player doesn't get stuck.

-
**
Fixed
**
: Character flipping out when sliding with grenade in 3P.

-
**
Fixed
**
: Character using rifle pose when turning with grenade in 3P.

-
**
Fixed
**
: Tweaked existing terrain materials and textures. Deleted DDNs, created DDNAs. Renamed several assets for clarity/matching.

-
**
Fixed
**
: Converted DBATable into new format (with animation filter conditions).

-
**
Fixed
**
: Updated all the enemy & friendly AI characters in the archetypes list to use the CommConfig = Human.

-
**
Fixed
**
: Updated ammo crate asset with better textures, added multiple color variants and materials. Simplified materials with no unused submats.

-
**
Fixed
**
: Updated Greenhouse material and textures. Re-exported meshes without unneeded extra submat, merged proxies into main rendermesh. Increased resolution on textures. Resaved Tint map as _Tint, not _Spec.

-
**
Fixed
**
: Incorrect surface type on sand terrain materials.

-
**
Fixed
**
: Updated ground_cover_nofern diff/ddna textures to 1024 from 512.

-
**
Fixed
**
: human.adb was missing tags for "Alerted" stance in some fragment IDs.

-
**
Optimized
**
: (CE-5295) (Assets) Exported all CGFs from editor_helpers Max scene and pointing to helper.mtl to keep it uniform and allows removal of unwanted unique materials . Deleted duplicate Max files (already exist in editor_helpers Max). Deleted Objects which seem useless/broken (still exist in editor_helpers Max) and not used in code/scripts. Renamed alienenergypoint to energypoint for generic-ness. Fixed typos in some filenames. Added .tif versions of the gradient textures in as .dds. Requires build scripts update to process Editor folder, so leaving .dds in for now. Made filenames lowercase. Re-exported c2/c3 SOs and added Max source file. Re-saved several materials with up-to-date settings. Re-exported mtlobjects all referencing mtlobjects material, added Box to max scene.

-
**
Optimized
**
: Airfield: Added small planes as physicalized RigidBodies. Rounded off values in TOD. Optimized some Decals and brushes. Removed fairly pointless lights inside Jets.

-
**
Optimized
**
: Updated SkeletonList: Reorganized into groups in alphabetical order. Removed obsolete entries. Added rocketlauncher and HMG entries.

-
**
Optimized
**
: Deleted "gun_mounted" assets, resetup as "mounted_gun" to match folder name. Exported FP and TP models. Setup CDF/CHR/CHRPARAMS. Added handle for ripoff animation sensibility. Cleaned up HMG weapon script.

-
**
Optimized
**
: Updated Hmmwv script to account for new asset changes. Tweaked handling and damages. Removed obsolete additional 3P views. Added "NoBullBar" mod and paints for variations.

-
**
Optimized
**
: Renamed HMMWV mannequin setups from "Vehicle" to "hmmwv". Using underscores instead of camelCase for filenames.

-
**
Optimized
**
: Renamed "forrest" road textures. Tweaked numerous road textures. Added DDNA road textures.

-
**
Optimized
**
: Delete orphaned rock_large01 asset with no proxy and no source file (CE-4142).

-
**
Optimized
**
: Moved several animal character assets into more specific subfolders.

-
**
Optimized
**
: Guardhouse: Removed double proxy setup. Removed unused submats. Tweaked material.
[#release-highlights](
Release Highlights
)
[#editor](
Editor
)
[#crydesigner](
CryDesigner
)
[#renderer](
Renderer
)
[#3dengine](
3dEngine
)
[#particles](
Particles
)
[#rctools](
RC/Tools
)
[#audio](
Audio
)
[#animation](
Animation
)
[#ai-system](
AI System
)
[#game](
Game
)
[#assets](
Assets
)
