# EaaS 3.8.1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962898
- Page ID: 44962898
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.8 > EaaS 3.8.1
- Parent: EaaS 3.8

## Child Pages

- [Important 3.8.1 EaaS Code and Data Changes](EaaS%203.8.1/Important%203.8.1%20EaaS%20Code%20and%20Data%20Changes.md)
- [VR_Demo Level](EaaS%203.8.1/VR_Demo%20Level.md)

## Content

Released 19th June, 2015

### Overview

CRYENGINE 3.8.1 is here and it is packed with features that we know many of you have been extremely eager to get your hands on for quite some time. A culmination of all the work we've been doing since the CRYENGINE 3.7.0 release, this is one of our biggest releases yet.

You'll find the top level features highlighted below, including our brand new OpenGL renderer which we use on Linux and Android platforms. We've added support for Oculus VR which has been a joint effort between the CRYENGINE team and the VR team working on our newly announced [Robinson: The Journey game](http://robinsonthegame.com/), and you can expect much more to come in this area over the next few releases! We've got Voxel-based rendering updates including Volumetric Fog with support for point lights, shadows, probes and more. GameZero is our brand new, stripped down, lean & mean GameCode sample package which makes creating a game on CRYENGINE much cleaner and simpler without all of the additional Crysis-related game code which you may not need for your title. This and a ton of other great improvements are [available for download](http://store.steampowered.com/app/220980/) right now!

### Release Highlights

#### OpenGL Renderer

Our brand new OpenGL Renderer running on Linux:

![Image](https://www.cryengine.com/docs/static/attachments/44962905)![Image](https://www.cryengine.com/docs/static/attachments/44962904)

#### VR Support

Support for [Oculus Rift](/docs/static/engines/cryengine-3/categories/1638401/pages/21267378) has been integrated and we're rapidly adding more features and functions to help you get the most out of your Virtual worlds. We've included a small demonstration level, aptly titled the ["VR_Demo"](EaaS%203.8.1/VR_Demo%20Level.md) level. This showcases some information on how you can approach setting up your levels for VR, some of the implications and the immersive benefits of using VR.

![Image](https://www.cryengine.com/docs/static/attachments/44962911)

#### Voxel Based Volumetric Fog

With CRYENGINE 3.8 we introduce an all new [voxel-based volumetric fog](/docs/static/engines/cryengine-3/categories/1114113) system. The system supports illumination from deferred lights, respects clip volume boundaries and works consistently with transparent objects including particles. It is also possible to inject particles directly into the fog volume to simulate some turbulence.

![Image](https://www.cryengine.com/docs/static/attachments/44962902) *Correct ordering / sorting of transparent objects, particles & lights all within the Volumetric Fog Volume*

![Image](https://www.cryengine.com/docs/static/attachments/44962901) *Shadows Casting Lights within a Volumetric Fog Volume*

![Image](https://www.cryengine.com/docs/static/attachments/44962900)![Image](https://www.cryengine.com/docs/static/attachments/44962899) *Comparison of Light Entities, contributing into the Volumetric fog On / Off*

#### Cascaded Shadow Cache

[Cached shadows](/docs/static/engines/cryengine-3/categories/1114113/pages/21267738) (formerly: static shadow map) have been extended to multiple cascades, covering several kilometers view distance out of the box. Cache updates are now handled under the hood but can still be manually tweaked via flow graph.

![Image](https://www.cryengine.com/docs/static/attachments/44962909)

#### Reverse Depth for Increased Z-Buffer Precision

CRYENGINE stores depth values in a reversed range now. In combination with a floating point depth buffer, this helps to greatly increase depth precision and allows users to put the near clipping plane a lot closer than before without running into z-fighting problems.

![Image](https://www.cryengine.com/docs/static/attachments/44962913)![Image](https://www.cryengine.com/docs/static/attachments/44962912) *Left shows an exaggerated setup with near plane distance set to 0.1cm to showcase Z-fighting. Right is the exact same setup with Reverse Depth enabled.*

#### Efficient POM Self-Shadowing

POM self-shadowing is back now and working efficiently with deferred shading, allowing the sun to cast shadows from the heightmap used for POM.

![Image](https://www.cryengine.com/docs/static/attachments/44962903)![Image](https://www.cryengine.com/docs/static/attachments/44962907)

#### 8-Weight GPU Vertex Skinning

Skinning of complex animated meshes that use more than 4 vertex weights (up to 8 weights) can be performed directly on the GPU now which can significantly reduce the CPU load.

#### Voxel Based Global Illumination (Experimental)

The latest Release adds the prototype of a [voxel-based global illumination](/docs/static/engines/cryengine-3/categories/1114113/pages/19377157) system that can be used to render large-scale ambient occlusion with an optional indirect light bounce. Please note, the feature is highly experimental and not ready for production, it is just provided for testing and early feedback at that point.

#### Many Rendering Quality Improvements

- Bloom is more stable now and shows less flickering fireflies.
- Half- and quarter-resolution particle upsampling produces cleaner edges.
- The overall SSDO quality got improved, especially the quality of the specular occlusion.
- Deferred decals are more consistent with standard decals and don't suffer from excessive aliasing any longer.
- Caustics got some quality upgrades and are working with tiled deferred shading now.
- Auxiliary viewports like for the character tool have greatly improved shading quality.
- Smoothness is authored using a more perceptually linear distribution.
- Normal-variance filtering produces cleaner results.

![Image](https://www.cryengine.com/docs/static/attachments/44962908)![Image](https://www.cryengine.com/docs/static/attachments/44962914)

#### 3ds Max 2016, Maya 2016, MotionBuilder 2016

Added support of 3ds Max 2016, Maya 2016, MotionBuilder 2016.

#### GameZero

The GameSDK project is a full blown game example. It demonstrates how most of the CRYENGINE features can be utilized. Based on Crysis 3, its size and complexity can be overwhelming for first time users. Furthermore prototyping games other than first person shooters can be tedious as the game project would have to be simplified to its core functionality first.

[GameZero](/docs/static/engines/cryengine-3/categories/1638401/pages/21266931) offers a minimalist approach to CRYENGINE. It allows first time users to get a quick overview of using the engine’s core functionality. It can be used as starting point for creating several types of games.

![Image](https://www.cryengine.com/docs/static/attachments/44962910)

#### Road Tool

The Road Tool now comes with the ability to erase vegetation along the road which can rapidly speed up and simplify your level creation.

Some new parameters have been exposed, such as EraseVegWidth which lets you define how far from the road edges to cut vegetation.

There is also EraseVegWidthVar which gives a variation multiplier for the EraseVegWidth value. This allows you to create a more natural look with some sections being more overgrown than others.

#### SceneRoot in Maya

Maya scripts for creating SceneRoot were added (the scripts are accessible through Maya's Crytek toolbar). See [Character Authoring in Maya](/docs/static/engines/cryengine-3/categories/1114113/pages/1310815),

"Y-up/Z-Up, SceneRoot node, root bone".

### Important Code and Data Changes

See the [Important 3.8.1 EaaS Code and Data Changes](EaaS%203.8.1/Important%203.8.1%20EaaS%20Code%20and%20Data%20Changes.md) article for more information.

### Editor

#### Sandbox General

- **New**: (CE-4998) Added environment panel parameter to shift sun shadow clip range towards shadow far plane.
- **New**: (CE-2154) Added "VR Headset" to stereo output drop down list in rendering panel.
- **New**: (CE-5874) Added context menu to prefab editor with an option to inherit the pivot from an object inside the prefab.
- **New**: (CE-5462) SelectObjectsDialog: Select objects in closed prefab is now selecting the actual prefab.
- **New**: (CE-3962) Layers: Add key combo of ALT + LMB to isolate a layer.
- **New**: (CE-3970) Layers: Add layer modifications to the undo / redo list.
- **New**: (CE-5067) Added support of r_Vsync in the Editor.
- **New**: (CE-6101) Enable custom size and transparency scaling of Ruler tool's locator spheres in Editor Preferences. Added wire cube to center point for more accurate measurement. Removed useless "Ruler Marker" text.
- **New**: (CE-6102) Added specific size scaling of TagPoint spheres in Editor Preferences, still multiplies based off global "Helpers" scale function. Removed unnecessary (single use) define. Set default Tagpoint scale to 0.5 as a result of removed define and cleaner code. Helperscale also now comes from EntityObject parent. Removed unused SetHelperScale function. Fixed some typos.
- **New**: (CE-6231) Write to the console the CVar name + value when triggered by a python script.
- **New**: (CE-5458) Can now search for sub-material names in the Material Editor.
- **New**: (CE-6227) Added hidemask controls to Editor python scripts.
- **New**: (CE-5531) DBview dropdown list only lists 30 objects, added scrollbar.
- **New**: (CE-6106) HardwareMouseEvent now supports right and middle mouse button inputs in Editor gamemode.
- **New**: (Material) Added Objects folder shortcut to Texture file dialog.
- **New**: Added camera restraints such as move, rotation and panning to QViewport.
- **New**: Added new quick-access toolbars to the editor.
- **New**: Added new icon files for editor shelves toolbars. Added toolbar icons.
- **New**: Added offset display for TerrainMoveToolPanel.
- **Fixed**: (CE-5891) CBaseObject notifies the affected area also before its transformation now.
- **Fixed**: (CE-5653) Vehicle Editor is not saving changes.
- **Fixed**: (CE-5696) Terrain generation: Fixed bugs with various generation values.
- **Fixed**: (CE-5211) Enabling proxy debug in game mode result in the menu bar becoming active while in game.
- **Fixed**: (CE-4943) DataBase dialog: Avoid to create library if exists another library with the same name.
- **Fixed**: (CE-4872) Roads disappear when set too wide (NB: Limitation is still there but can increase width about 5x more over previous).
- **Fixed**: (CE-5453) Correct scale selection from InfoBar when scaling multiple brushes at the same time.
- **Fixed**: (CE-5700) Object Layers: Save objects of internal layer if it has external parent.
- **Fixed**: (CE-5009) Avoid freezing Viewport after Pressing cancel on the warning box about a level being read-only.
- **Fixed**: (CE-3072) Terrain Texture Layer window: ESC for Picking layer texture.
- **Fixed**: (CE-5941) Reload Scripts doesn't reload BodyDamage files.
- **Fixed**: (CE-4944) Return move gizmo after editing the shape.
- **Fixed**: (CE-5822) Crash when Sandbox is closed and there is an open Qt dialog modal to viewpane.
- **Fixed**: (CE-3666) Sizing terrain to a larger size creates the new terrain with a height of 0.
- **Fixed**: (CE-5655) Fixed formatting (Lowercase + spaces) in params/cvars, etc.
- **Fixed**: (CE-5006) (Road/River) Points don't need to be double selected in edit mode before they can be moved.
- **Fixed**: (CE-5461) Added functionality to open multiple libraries at once.
- **Fixed**: (CE-5276) Remove Export to Engine prompt. (CE-5841) Success message is logged to the console.
- **Fixed**: (CE-5897) Level successfully saved message now highlighted in green / error message red.
- **Fixed**: (CE-5666) Avoid saving materials in time when another level is loading.
- **Fixed**: (CE-6104) Cloning an archetype in the editor's Entity Library leaves the library in an invalid state.
- **Fixed**: (CE-6265) Iterate over all display info modes, adds r_DisplayInfo=3 to the cycle.
- **Fixed**: (CE-6021) "Go to position" dialog not closing with Escape.
- **Fixed**: (CE-5704) Multi-selecting MNM shapes removed basic rollupbar functions.
- **Fixed**: (CE-6032) Undo has no effect after modifying an object's location with the handle at the bottom of the view port.
- **Fixed**: (CE-5896) Added conditional compilation to simplify AITerritoryShapes to a single point (USE_SIMPLIFIED_AI_TERRITORY_SHAPE).
- **Fixed**: Create Quick Access control before Main Window gets a focus, to keep correct focus.
- **Fixed**: Fixed spurious calls to IRenderer::ChangeViewport on every frame (prevented RenderDoc hotkeys from functioning properly).
- **Fixed**: Vehicle Editor won't save added/removed parts.
- **Fixed**: Possible crash in Vehicle Editor when you're trying to re-open a vehicle that is already loaded.
- **Fixed**: Crash on clicking "Align To Heightmap" on yet empty road.
- **Fixed**: Fix problems with hiding when object is linked.
- **Fixed**: Don't send ENTITY_EVENT_EDITOR_PROPERTY_CHANGED event multiple times / certain entities don't load.
- **Fixed**: Old style property control: you were able to toggle boolean values using space even if the property control was read only.
- **Fixed**: Hide close button from dockable windows with closing disabled.
- **Fixed**: Warnings for vehicle editor.
- **Fixed**: Vehicle editor structure tab won't recognize parenting of parts that got newly created through the editor.
- **Fixed**: Displaying more info about background tasks in the RC tooltip (separate counts for texture compilations and other tasks, last tasks added).
- **Fixed**: Made data members of CBackgroundTasksListener private.
- **Fixed**: Undo suspend issue.
- **Fixed**: HandleAttachmentChange needs to ignore detach/attach that doesn't want to keep the world position.
- **Fixed**: Wrong position getting serialized.
- **Fixed**: ai_MNMDebugAccessibility not being correctly set on Editor start.
- **Fixed**: Bug where a shape object is force reset to "closed" shape when reloading level/reloading scripts.
- **Fixed**: Search for texture names in the Material Editor.
- **Fixed**: Made AreaBoxes not scalable with Sandbox UI scale tools (can cause broken functionality), use Entity params instead. Renamed "Filled" param to "DisplayFilled" for consistency with other entities.
- **Fixed**: Tweaked PanelDisplayHide behavior to work more consistently and better with lua signals.
- **Optimized**: (CE-6112) Increased opacity of ProximityTrigger fill color as it could be too difficult to see in some situations.
- **Optimized**: (CE-5652) Equipment Pack dialog selects "Player_Default" equipment pack by default when opening.
- **Optimized**: (CE-1167) Removing unused PAK Manager from Sandbox.
- **Optimized**: Changed "glossiness" naming to "smoothness" in the Material Editor UI.
- **Optimized**: Updated Editor environmentModes and viewModes toolbars.
- **Optimized**: Set New Level Dialog to use 1m units instead of 2m units by default.
- **Optimized**: Delete unused configs/scripts from Editor folder.
- **Optimized**: Removing Qt4 code from QtIntegration.cpp.
- **Optimized**: Removed XYZ input limits from TerrainMoveToolPanel.

#### Flowgraph

- **New**: (CE-4312) Implemented new Weapon:Ammo FG node to merge functionality and clean up weapon and inventory nodes.
- **New**: (CE-5322) New FlowGraph nodes to specify the faction of all AIs in an AIWave.
- **New**: (CE-4250) Added new FlowGraph node to allow Tank turrets to get rotated by AIs.
- **New**: (CE-2722) Added destroy input on the vehicle script FG node.
- **New**: (CE-3413) Added Logic:Any to FG context menu.
- **New**: Added a FindEntityByName FG node.
- **New**: Added FG nodes to add constraints + estimate player rotational speed (for constraints). Physics:Constraint and Physics:CameraProxy.
- **New**: Add an input to let the designer choose which axis of the entity should point to the target when using the EntityFaceAt flowgraph node.
- **New**: Added phys id to raycast camera node.
- **New**: Added ActionMapManager flownode to enable/disable specific action maps.
- **Fixed**: (CE-6368) (Trackview) Play state of Animations:PlaySequence node now gets updated when the sequence is stopped.
- **Fixed**: (CE-1130) Removed duplicated + deprecated FG ammo nodes.
- **Fixed**: (CE-6287) Allow multiple connections on each output of a RandomTrigger node to prevent crash.
- **Fixed**: (CE-4976) WeaponSensor node outputting Firemode name in the AmmoName output. Re-ordered outputs to match. Removed unused/broken "Ammo Type" output. Updated description text for some outputs. Renamed "Ammo" to "AmmoCount" and renamed "MaxAmmo" to "ClipSize" for better readability and matching of weapon scripts params.
- **Fixed**: (CE-6288) Removing a node from a RandomTrigger node no longer breaks the functionality of the Randomtrigger node.
- **Fixed**: (CE-5142) Refactored entity iterator Flowgraph nodes.
- **Fixed**: To prevent confusion, functions ToString(SFlowSystemVoid&) and ToString(TFlowInputData&) were changed so they return "unknown" as it was in the past, instead of returning "SFlowSystemVoid" and "TFlowInputData".
- **Fixed**: Fixed memory leak involving not releasing a FlowNodes enumerator.
- **Fixed**: EntityFaceAt node: Fixed undesired roll added to the transformation and bad initial state requiring designers to activate all inputs manually. Note: An input was renamed on the EntityFaceAt flowgraph node.
- **Fixed**: Possible crash in GetInputActor flownode routine.
- **Fixed**: Fixed MoveEntityTo node (its handling of various coordinate systems was broken).
- **Fixed**: Bug where entity cannot be moved with Flownode "MoveEntityTo" when entity has no proxy.
- **Fixed**: Bug in "MoveEntityTo" Flow Node, where physical entity is not stopped on "Stop".
- **Fixed**: Crash in CFlowNode_AILookAt::OnUpdate on level unload.
- **Fixed**: Problem with world-attached constraint Flowgraph nodes.
- **Fixed**: Vehicle "Enter" FlowNode crash when using an invalid seat ID.
- **Optimized**: (CE-2341) Removed duplicated SimulatePlayerInput flownode
- **Optimized**: Renamed Input:Action flownode to Input:ActionListener for better understanding of its use.

#### Prefabs

- **New**: (CE-5501) Add level instance count information to selected Prefab rollupbar and database view.
- **New**: Added custom pivot points for prefabs. Can be manually moved with mouse or aligned to prefab objects.
- **Fixed**: Panels delete didn't work properly on multiple selection.
- **Fixed**: Optimization in the way objects update their properties when their inside prefabs. Now only the changes are reflected, which hugely speeds up working with prefabs.
- **Fixed**: Copying/Deleting/moving 10+ flowgraph nodes within a prefab causes it to lag.
- **Fixed**: Editing large numbers of objects inside a prefab cause it to lock up.
- **Fixed**: When the user changes an object, which is part of a prefab only the object and its changes gets propagated to all the other prefabs of the same type (previously all the prefabs of this type were getting destroyed and recreated from scratch).
- **Fixed**: Crash with dynamic prefabs.
- **Fixed**: Setting custom pivot points wasn't working properly in some cases.
- **Fixed**: Extracting a prefab will cause all prefabs of that type to be removed from a level.
- **Fixed**: Prefabs placed into a level will trigger the perforce handler dialogue box always.
- **Fixed**: Entities assigned to FG nodes will become unassigned when the nodes are copy and pasted.
- **Fixed**: Prefab lib is being modified, when the user deletes an external layer. Deleting layers in the level should not modify the prefab lib.
- **Fixed**: The ReloadAll scripts function was not working optimally with prefabs. It was triggering unnecessary modify operations on the prefab libs, when all we want is to reload the entities.
- **Fixed**: Objects in Prefabs are still selectable when hidden or frozen.
- **Fixed**: Flowgraph nodes inside prefabs were working in the editor but not in game. This exports the proper entity guids when the prefabs get expanded.

#### Vegetation

- **New**: Erase Vegetation button for Editor's Road Tool.
- **New**: Transfer Elevation and Slope from Terrain Layer to Vegetation Group with the click of a button.
- **New**: Rotate vegetation objects on Z axis towards terrain slope: Feature adds a new property in the Vegetation Panel: "RotationAngleToTerrainNormal".
- **New**: Vegetation's AlignToTerrain changed from checkbox to value Changes bAlignToTerrain (bool) to fAlignToTerrain (float) in vegetation panel.

#### Trackview

- **New**: Spacebar now triggers playback when curve editor is focused.
- **Fixed**: (CE-4106) File format is not reset anymore when selecting different render items in Batch Render Dialog.
- **Fixed**: (CE-6082) Infinite recursion when overlapping sub-sequences are controlling the same camera.
- **Fixed**: (CE-6082) Infinite recursion when overlapping sub-sequences are controlling the same camera. Fixed uninitialized variable.
- **Fixed**: Slow scrubbing when using multiple sub-sequences controlling same entity.
- **Fixed**: Uninitialized variable.
- **Fixed**: Consistent default tracks for entity node.
- **Fixed**: Fix TrackView node ordering.

#### CryDesigner

- **New**: Added the Shortcut tool in Misc group.
- **New**: Added a new item in DC setting, "ESC to object mode instantly".
- **New**: Added erasing selection by dragging a mouse holding ALT.
- **New**: Added support of non-planar quad.
- **New**: Implemented Loop Face Selection.
- **New**: Implemented Ring Face Selection.
- **New**: Implemented LoopCut Tool.
- **New**: Implemented Collapse Tool.
- **New**: Added a function of erasing "Vertex" and Edge" shared with several polygons to "Remove" tool.
- **New**: Replaced the existing MFC UIs with Qt UIs.
- **New**: Added a path about python in wscript again.
- **New**: Added the smoothing surface in the subdivided mesh.
- **New**: Added "Apply" button in panels of RemoveDoubles and Hide tools so that you can use the tool's functionality within them.
- **New**: Added the UV field to a vertex in Polygon. Introduced UV parameter per vertex in Polygon class.
- **New**: Improved a way of giving offset in Offset Tool.
- **Fixed**: (CE-5788) Solved the incorrect cache data problems caused after moving vertices or edges with "Keep Pivot Center" enabled.
- **Fixed**: (CE-6038) A bug about empty designer object not being removed has been fixed. And Routine to delete all empty designer objects just before saving and exporting a level has been added.
- **Fixed**: (CE-6013) Bug about tiling snaps back has been fixed in TextureMapping Tool.
- **Fixed**: (CE-6042) Crash bug caused randomly in TextureMapping Tool has been fixed.
- **Fixed**: (CE-6041) Made Sub Mat ID combo kept up to date.
- **Fixed**: (CE-6014) Corrected typo of Hide Face tool.
- **Fixed**: (CE-6007) Broken textures on a designer object.
- **Fixed**: (CE-6023) Enabled to draw stair profile on the ground.
- **Fixed**: (CE-5217) (CE-6017) Improved Clone/Array tool so that it works well and any crash doesn't happen.
- **Fixed**: (CE-6018) Added an undo for Subdivision level adjustment.
- **Fixed**: (CE-6015) Fixed a crash bug caused in the Bevel Tool.
- **Fixed**: (CE-6153) Fixed a crash bug causing after boolean operation
- **Fixed**: (CE-3674) Displaying the number of selected objects in designer tool has been restored.
- **Fixed**: (CE-6038) Bug about incomplete designer objects being exported.
- **Fixed**: Bug about not loading a designer object with "Region" tag in xml.
- **Fixed**: Bug about falling into the invalid designer mode and getting stuck in designer mode after undoing.
- **Fixed**: Enabled displaying hidden cubes for vertices, edges and faces by holding Spacebar.
- **Fixed**: Dealt with non-planar faces in the Weld tool and Exclude Tool, etc.
- **Fixed**: Enabled frozen objects to be picked in the Designer Tool.
- **Fixed**: Bug about not loading a shortcut list as the CShortcutManager object is created.
- **Fixed**: Crash which have happened as undoing has been solved.
- **Fixed**: Expanded "Setting" area so that all items can be displayed without being scrolled.
- **Fixed**: Bug about UI of CryDesigner not disappearing when switching to an object.
- **Fixed**: Incorrect loop edge selection.
- **Fixed**: Incorrect ring edge selection.
- **Fixed**: Drawing line bugs across multiple regions.
- **Fixed**: Bug of adjusting stair height in Stair Tool.
- **Fixed**: Areasoild has been available again.
- **Fixed**: Crash when exiting the designer tool when the model is empty.
- **Fixed**: Rare crash during level loading.
- **Fixed**: Bug related to BackFaceFlag of model.
- **Fixed**: Enabled to align height in Extrude tool without pressing Shift key.
- **Fixed**: Bug on drawing line in an empty object on ground.
- **Fixed**: Improved a way of giving an offset to a polygon by considering holes.
- **Fixed**: UVs of a brush object has been preserved after converted to a designer object.
- **Optimized**: Three items in Settings (ESC to Object Mode, Enable Seamless Edit and Nonplanar Quad) have been removed.
- **Optimized**: The tool names saved to JSON has been changed from tool class name to tool name.
- **Optimized**: Changed external settings for the Exclusive Mode.
- **Optimized**: Renamed Group Names to the First letter to make tabs look better.
- **Optimized**: Cleaned up codes related to updating entire states of CryDesigner.
- **Optimized**: Renamed namespace BUtil:: to CD::
- **Optimized**: The whole project has been refactored so that duplicated codes has been least and long file and class names have been shorten etc.
- **Optimized**: Unified QT panels using QPropertyTree to one representative template panel class.
- **Optimized**: Removed duplicated codes on creating a panel of each tool by putting them to the abstract tool class.
- **Optimized**: Codes on DesignerTool class have been refactored so that duplicated codes can't be run and removed unnecessary parts.
- **Optimized**: Codes about Texturemapping tool have been refactored.
- **Optimized**: ElementManager::GetSize() has been renamed to ElementManager::GetCount()
- **Optimized**: 'Region' has been renamed 'Polygon'
- **Optimized**: 'CBrushRegion::RegionPtr' has been replaced with 'CD::PolygonPtr'
- **Optimized**: 'GetRegionSize()' has been renamed 'GetPolygonCount()'
- **Optimized**: Reduced as many number of using kDesignerEpsilon as possible.
- **Optimized**: Moved enumerations in CBrushPolygon and CBrushDesigner to CD:: namespace.
- **Optimized**: Removed CBrushArgumentEx class and the methods there got in the CBrushArgument.
- **Optimized**: Cleaned up codes on cache data in CBrushDesigner class.
- **Optimized**: Renamed CBrushRegion::GetVertexListSize() to CBrushRegion::GetVertexCount()
- **Optimized**: Renamed CBrushRegion::GetEdgeSize() to CBrushRegion::GetEdgeCount()
- **Optimized**: Codes about registering tools/UIs have been refactored by gathering those such codes into ToolRegister.h/cpp.
- **Optimized**: Codes related to creating the main panel have been refactored.
- **Optimized**: Refactored UI codes.
- **Optimized**: Removed Qt UI specific codes from UIFactory.h.
- **Optimized**: Tweaked the camera position for Exclusive mode so that the target object can be viewed better.
- **Optimized**: ExcludeMaterialPicking object param has been removed because it wasn't used at all.
- **Optimized**: MFC File Dialog box used for Exporting as Group has been replaced with Qt File Dialog box.
- **Optimized**: SMeshInfo and Triangles have been replaced with FlexibleMesh.
- **Optimized**: Brush has been renamed to ModelCompiler.
- **Optimized**: Codes related to selection mesh have been refactored.
- **Optimized**: Removed all polygon debugging codes.
- **Optimized**: "Mode" and "tool" has been renamed to "Tool" and "tool".
- **Optimized**: Some functions in BaseTool has been moved to DrawTool/DesignerTool etc to make BaseTool lighter.
- **Optimized**: Brush::DeleteRenderAllNodes() has been renamed to Brush::DeleteAllRenderNodes().
- **Optimized**: DesignerBaseObject<T>::GetDesigner() has been renamed to DesignerBaseObject<T>::GetModel().
- **Optimized**: Distributes tool files into several sub folders.
- **Optimized**: Some source files in Core has been moved to "Util" folder.
- **Optimized**: 'Create' has been renamed to 'Shape".
- **Optimized**: Every tool name in Create group has been reduced.
- **Optimized**: SOutputParameterForStairCreation has been renamed to SOutputParameterForStair.
- **Optimized**: Codes regarding Tool and UI has been refactored so that codes for registering tool and UI are scattered over Tool Codes.
- **Optimized**: A redundant method for triangulation has been removed.
- **Optimized**: Duplicated codes on initializing variables in constructors of Polygon have been removed.
- **Optimized**: CD:: has been removed as much as possible in Polygon class.
- **Optimized**: Refactored codes of MFC resources by remove unused ones.

#### QT System

- **New**: (CE-5691) (QPropertyTree) Cross-dll registration of PropertyRow-s.
- **New**: (QPropertyTree) Checkboxes are packed in two columns by default (can be turned off for each property tree).
- **New**: (QPropertyTree) Added shift-selection.
- **Fixed**: (QPropertyTree) Fixed '+' control character expanding properties after every change.
- **Fixed**: (QPropertyTree) Fixed tooltips for ranged values and vectors (and other inlined properties).
- **Fixed**: (QPropertyTree) Proper handling of read only control character '!' in buttons, clear read-only state for checkboxes.

### Renderer

- **New**: Revived POM self-shadowing.
- **New**: Added voxel-based Volumetric Fog feature. Can be enabled with e_VolumetricFog=1. See [Voxel-Based Volumetric Fog_old](/docs/static/engines/cryengine-3/categories/1114113) for more information.
- **New**: Improved depth precision for scene rendering with reverse clip space depth range (Limited OpenGL support for now).
- **New**: Reduced bloom flickering by performing higher quality down-sampling.
- **New**: (CE-2187) Added r_statsMinDrawcalls CVar to set minimum value to be displayed for use with r_stats 6.
- **New**: (CE-6149) Make maximum number of shadow casting lights tweakable via CVar: r_ShadowCastingLightsMaxCount. Each 4 lights consumes an additional 8MB of memory @ 1080p, so increase only as needed.
- **New**: Adds IRenderAuxGeom::Draw2dlabel() functionality.
- **New**: Tweaked Water shader to take Sun Specular Color into account which can be useful in low light (night time) situations to boost specular reflections.
- **New**: Switched to perceptually more linear roughness distribution (existing gloss maps get converted to new distribution by RC).
- **New**: Made streaming cbuffer compatible with compute.
- **New**: SamplerState and Textures semantics support in code and shaders.
- **New**: Enabled anisotropic filtering for blend layer diffuse and normal.
- **New**: Added basic range rescaling support for TVs (applied after PostAA, will not affect other post effects or UI right now).
- **New**: Introduced bloom quality CVar and lowered quality in mobile.cfg.
- **New**: (OpenGL) Add OpenGL render type and display 'GL' in displayinfo.
- **New**: Added the fog density noise functionality for FogVolume.
- **New**: Improved specular occlusion and how SSDO gets incorporated into shading.
- **New**: Can now dynamically set the icon to display on the window and taskbar from a DDS texture.
- **New**: Added IRB colorspace for reflectance encoding. Added all color-spaces for output.
- **New**: Enabled mip-map generation for dynamic flash textures used in material slots.
- **New**: Compute mip level for deferred decals to reduce aliasing.
- **New**: Allow switching to anisotropy level 1.
- **New**: Apply decal material parameters (Alpha Multiplier, Falloff, Diffuse Opacity) for deferred decals (more consistency with forward decals).
- **Fixed**: (CE-5767) Extend shadow cast min spec flags in terrain data to support all specs.
- **Fixed**: (CE-5401) Compile error in water volume shader.
- **Fixed**: (CE-4458) Terrain Shadowmap problem. e_GsmCastFromTerrain=1 should now provide better results.
- **Fixed**: (CE-6194) Crash on debug rendering of normals and tangents when number of vertices is large.
- **Fixed**: (CE-5402) Water caustics when tiled deferred shading is enabled. Improved caustics blending.
- **Fixed**: (CE-4458) Terrain Shadowmap Problem. This should fix most shadow issues when using e_gsmCastFromTerrain=1.
- **Fixed**: (CE-5402) Fixed water caustics when tiled deferred shading is enabled. Improved caustics blending.
- **Fixed**: (CE-6194) Crash on debug rendering of normals and tangents when # of vertices is big.
- **Fixed**: (CE-2948) (CE-2978) Output conservative depth when SilPOM is used.
- **Fixed**: (CE-1263) Changed post-processing parameter blending to not average with the param default value any longer which caused issues for the saturation parameter; for debugging r_PostProcessParamsBlending 2 can be used to restore previous behavior.
- **Fixed**: (CE-6058) Improved vfx rendering on Mannequin viewport - using default environment cubemap and flushing auxgeom after forcing grid to render before opaque instead after transparent pass.
- **Fixed**: (CE-6085) Call SetStopped on the compute vertices job in CRenderer::PrepareParticleRenderObjects rather than after the last job. The previous implementation can cause the main thread to wait indefinitely if no job is started within CRenderer::PrepareParticleRenderObjects but m_ComputeVerticesJobState[threadList] has been set as running. SetStarted and SetStopped already use a counter and AddJob increases this counter so there is no need for the previous job tracking code.
- **Fixed**: (CE-6157) DeferredRain: Renamed surface_flow.tif to surface_flow_ddn.tif to prevent Normals warning message.
- **Fixed**: (CE-5492) Fixed lag and broken HDR/Bloom after changing e_sketch_mode to 0.
- **Fixed**: (CE-6410) Use the actual current viewport size when scaling 2D geometry.
- **Fixed**: (CE-6429) Fixed crash in FX_DrawTangents().
- **Fixed**: (CE-6427) Fixed tiled shading crash when invalid texture is specified and added warning in displayinfo section.
- **Fixed**: (CE-6226) Replaced broken r_UseAlphaBlend by r_TransparentPasses to skip rendering of transparent objects.
- **Fixed**: Rectangular area lights in tiled shading and fixed intensity on very smooth materials.
- **Fixed**: For resource view creation in CTexture::GetSurface for 3d textures and cube maps.
- **Fixed**: Volumetric fog shadow.
- **Fixed**: Shading in secondary viewports like character tool and material editor (apply output gamma correction, apply default probe, more consistent skin shading).
- **Fixed**: Normal computation in Glass shader.
- **Fixed**: Made usage of diffuse and specular material colors in Glass shader more consistent with other shaders.
- **Fixed**: Add override for forcing single tap forward shadow filtering. Fixes usage from compute and vs/ds.
- **Fixed**: Disabled anisotropic filtering for smoothness maps to make mip transitions of prefiltered maps less noticeable.
- **Fixed**: Use shape parameters instead of AttenuationBulbSize for spherical Area lights (r_DeferredShadingAreaLights without "PlanarLight" enabled).
- **Fixed**: Added a query to toggle mesh tessellation.
- **Fixed**: Changing rasterization resolution to what was used on consoles in 720p.
- **Fixed**: TextureFlushFix for anti-aliasing and shadows.
- **Fixed**: Crash in CImageDDSFile::AdjustFirstFileName when texture does not exist.
- **Fixed**: Multi-threaded compression/decompression.
- **Fixed**: UAV creation in texture3d case.
- **Fixed**: Crash in pipeline profiler due to out of bounds access of static namelist array.
- **Fixed**: Crash in CImageDDSFile::AdjustFirstFileName when texture does not exist.
- **Fixed**: Broken reloading of attached alpha with split textures.
- **Fixed**: Updated list of buffers for r_debugGBuffer.
- **Fixed**: Don't use Concurrency run-time for DXT compress/decompress.
- **Fixed**: MSAA crash and shader compile errors.
- **Fixed**: Missing shadows from vegetation backfaces - Remove cull mode override for shadow gen from sun: cull mode is set up in shader and applied during FX_DrawBatch*
- **Fixed**: Replaced r_ShaderCompilerFolder by a suffix which is appended to sys_game_folder to reduce duplication.
- **Fixed**: WaterVolume Shader: Set minimum values of 0.01 for Tiling, Detail Tiling and Rain Ripples Tiling to prevent visual artifacts when set to 0.
- **Fixed**: Improved image sharpness when TAA jittering is enabled.
- **Fixed**: Properly handle rain receivers below rain occluder bounding box.
- **Fixed**: Loading BGRA8 textures from file: typo in PixFormat initialization.
- **Fixed**: MSAA and shader compile error fixes.
- **Fixed**: Assert in VolumeLighting.cfi: Add float3 to list of supported tokens for texture declarations.
- **Fixed**: Only use alpha channel min blending in forward transparent pass.
- **Fixed**: Always use min blending for the alpha channel of forward rendered objects to make sure depth fixup values are not affected.
- **Fixed**: Clear temp depth surfaces upon creation to avoid rendering errors due to uninitialized content.
- **Fixed**: Only enable tiled shading runtime flag when CVar is set.
- **Fixed**: Improved numerical stability when generating view matrix; this reduces re-projection inaccuracies of TAA when being very close to surfaces.
- **Fixed**: Hair rendering to use stable_sort for transparent objects.
- **Fixed**: Enhanced precision for inverse view projection matrix in renderer.
- **Fixed**: Flickering when using tiled forward shading on nVidia hardware.
- **Fixed**: RTVs and mip map generation for cubemaps.
- **Fixed**: Loading of attached alpha for cubemaps.
- **Optimized**: (CE-2830) Deprecate e_DebugDraw 10. Replaced by r_ShowLines=2.
- **Optimized**: Removed R2VB from LPV-shader.
- **Optimized**: Move 3rdParty code from Renderer into Code/SDKs.
- **Optimized**: Do not link d3d9.lib when using OpenGL for frame profiler labels.
- **Optimized**: Removed nvDXT and old squish from renderer.
- **Optimized**: Removed tiledshading 0 from sys_spec_shading (gets set via system.cfg).
- **Optimized**: Refactor static shadows: Multiple cascades and better automated placement. Removed now unused CVars e_GsmExtendLastLod, e_GsmExtendLastLodIncludeObjects, e_GsmCache, e_GsmCacheLodOffset, e_GsmCacheLodOffsetExtended, e_GsmRangeStepExtended, e_GsmScatterLodDist
- **Optimized**: Remove shadow cascade lod from SRenderingPassInfo::EShadowMapType.
- **Optimized**: Removed unreferenced binaries.
- **Optimized**: Dropped non-PBR compatible diffuse alpha to specular option and did small shading adjustments.
- **Optimized**: Use fullscreen triangles for post effects instead of fullscreen quads.
- **Optimized**: Smaller tiled shading optimizations.
- **Optimized**: Removed light clip box support from tiled shading (superseded by [Clip Volumes](/docs/static/engines/cryengine-3/categories/1114113/pages/19379670)).

#### OpenGL

- **New**: (HLSLcc) Added depth clamping emulation performed in vertex and fragment shader for application compatibility with OpenGL ES.
- **New**: Added generation of GLSL headers for run-time linking of shaders depending on the pipeline configuration.
- **New**: Added depth clamp emulation for OpenGL ES.
- **New**: Support for timestamp queries in GL.
- **New**: Added support for binding of constant buffer ranges through a set of extension functions (DXGL* SetConstantBuffers).
- **New**: Added optional per-slot linear streaming constant buffers mode (currently experimental, can be enabled by setting DXGL_STREAMING_CONSTANT_BUFFER to 1).
- **New**: Added an option (enabled with DXGL_MERGE_CONSTANT_BUFFER_SLOTS, on by default) to merge the mapping of constant buffer slots to uniform block locations for different stages when they are compatible.
- **New**: Added loader for GL_EXT_shader_image_load_store.
- **New**: Added some GL extensions for future use.
- **New**: Enabled dxgl_streaming_constant_buffer_persistent_map by default as it works on Foster too; added dxgl_streaming_constant_buffers_sorting mode to reduce overhead of CContext::FlushConstantBuffers in the average case.
- **New**: Enabled constant buffer streaming by default (persistent mapping still off); disabled only for specific constant buffers (SPI and indirect SPI buffers).
- **Fixed**: (CE-6048) Disable use of vertex array binding until further investigation since it causes driver crashes inside glDraw* on NVIDIA 331.113 Linux x64 driver.
- **Fixed**: (HLSLcc) Replaced cross-dependency compilation with a preprocessor-based symbols that are dynamically resolved by the application; this allows to translate offline single shaders without knowledge of parameters such as attribute interpolation in the vertex shader or tessellator partitioning and output primitive in domain shader, or other pipeline state such as depth clamp emulation.
- **Fixed**: (HLSLcc) Changed binary format for offline shaders to an extension of DXBC. Moved format parsing and writing code to hlslcc_bin.hpp so that it can be shared with the application.
- **Fixed**: (HLSLcc) Fixes #version header position problem with strict drivers which require it to be as the first line in the shader.
- **Fixed**: Disable scissor test when clearing render target/depth stencil and when blitting frame buffer.
- **Fixed**: Temporarily disable tessellation support as domain shaders produced by HLSLcc currently have compilation errors.
- **Fixed**: Compilation error in CD3D9Renderer::FX_SetTessellationShaders when TESSELLATION_RENDERER is disabled.
- **Fixed**: Disable SUPPORTS_INPLACE_TEXTURE_STREAMING code path when using OpenGL.
- **Fixed**: Missing attribute divisor state setting and caching, which was causing wrong attributes being sampled with instanced geometry.
- **Fixed**: Compile error when DXGL_MERGE_CONSTANT_BUFFER_SLOTS is 0.
- **Fixed**: Compile error on GLES.
- **Fixed**: Build fixes for combinations of DXGL_MERGE_CONSTANT_BUFFER_SLOTS and DXGL_STREAMING_CONSTANT_BUFFERS.
- **Fixed**: Creation of shader resource views, unordered access views and render target views of entire texture arrays (undocumented ArraySize set to (UINT)-1).
- **Fixed**: Shadercachegen project spec does not build CryRenderOpenGL, which breaks shader cache generation.
- **Optimized**: Refactoring and clean up of DXGL_STREAMING_CONSTANT_BUFFERS and DXGL_MERGE_CONSTANT_BUFFER_SLOTS - they can now be used together.
- **Optimized**: Streaming constant buffers improvements - still disabled; speculative format fix for RGBA16F.

### Engine

#### Engine General

- **New**: (CE-5677) Visarea max number. Added new CVar e_PortalsMaxRecursion for portals recursion depth control.
- **New**: (CE-6277) (3DEngine) Added AffectsThisAreaOnly and IgnoreVisAreas checkbox to FogVolume. AffectsThisAreaOnly works only with e_VolumetricFog=1.
- **New**: (CE-5625) (Localization) sys_languages CVar removed, supported languages now detected from available localization files.
- **New**: (SDKs) Updated to version r128 of lz4.
- **New**: (SDKs) Added lzss, lzma, Lua and FreeType static libraries.
- **New**: (Unicode) General move towards UTF-8 encoded strings everywhere.
- **New**: (CrySystem) Added sys_FilesystemCaseSensitivity CVar. Set this to 1 to show warnings when a file is loaded with incorrect letter casing. Set to 2 to show errors.
- **New**: (CrySystem) Alpha blending support for hardware cursor.
- **New**: (CryAction) Added a small interface ITimeDemoRecorder along with a listener for CTimeDemoRecorder (needed for game related tweaks for timedemo in gamedll).
- **Fixed**: (CE-5830) (CrySystem) Profiling in release is not possible.
- **Fixed**: (CE-5621) Crash when reading chunk files without chunks.
- **Fixed**: (CE-5537) Unchecking Roads is disabling the Environment Probes.
- **Fixed**: (CE-5468) Fixed sys_job_system_enable in Editor.
- **Fixed**: (CE-2767) Improved 'sys_job_system_profiler' layout.
- **Fixed**: (CE-6224) e_entities 0/1 turns off merged mesh vegetation.
- **Fixed**: (CE-605) (CE-518) Improved 'Profile' debug view layout.
- **Fixed**: (CrySystem) Fixes unresolved symbol due to missing inclusion in ArchiveHost.cpp.
- **Fixed**: (CrySystem) Solving compilation problems when including zlib's zutil.h.
- **Fixed**: (CrySystem) Move quit console command to system so games don't have to implement it.
- **Fixed**: (CryCommon) Adding a const to a reference argument in AngleAxis constructor (so that we can pass a temporary to that constructor).
- **Fixed**: (HttpWebServer) Disable it by default.
- **Fixed**: (RemoteConsole) Once again builds and runs on Mono.
- **Fixed**: (Flash) Fixed FPE.
- **Fixed**: (CrySystem) Timer bug, t_FixedStep didn't work. RealFrameTime now set correctly.
- **Fixed**: (CrySystem) Wrong standard deviation calculation for profile 8.
- **Fixed**: (CrySystem) Added missing platform identifiers to CSystem::LogVersion.
- **Fixed**: (CryString).compare(NoCase) with null-terminated string did not take into account the length of the null-terminated string when comparing.
- **Fixed**: (CryEntity) Removed the living entity rotation check on the physics proxy.
- **Fixed**: (Serialization) Fixed Range<> decorator always to clip value to hard limits.
- **Fixed**: Provide a vtable free implementation of the reference counting class for smart pointers.
- **Fixed**: Silence zero-length printf parameter warning in 3dEngine.cpp.
- **Fixed**: Crash during server connection (e_StatObjBufferRenderTasks=1).
- **Fixed**: Add missing check for NULL objects tree while gathering shadow casters from vis areas.
- **Fixed**: Proprietary G16R16 DDS-header identification (rotrandom.dds only).
- **Fixed**: Bug where GetTerrainSurfaceNormal returns inaccurate result.
- **Fixed**: Intersect::Lineseg_Triangle wasn't filling the optional parameters properly in case of overlap between the two primitives.
- **Fixed**: Shutdown via exit - IMemReplay was destroyed but still being used in atexit() procedure.
- **Fixed**: Report the fatal error in the lua panic handler. Report lua out of memory.
- **Fixed**: Bug in CRC32 computation (text strings with byte values exceeding 127).
- **Fixed**: Possible crash when ending game context gets called without proper engine initialization.
- **Fixed**: Various scriptbind description and parameter formats.
- **Fixed**: Enabled C++11: enabled c++11 for gcc and clang, deleted 'register', replaced deprecated auto_ptr by unique_ptr.
- **Optimized**: (CE-373) (Console) Refactored VF_CONST_CVAR error, allowing change message.
- **Optimized**: (CE-2988) Pad number of shadow frustums with spaces to avoid flickering text in displayinfo.
- **Optimized**: (CE-6302) Added game token scriptbind description to the documentation.
- **Optimized**: (CryFont) Refactored to compile from vanilla FreeType redist (v2.5.5) with custom options.
- **Optimized**: (Lua, ScriptSystem, RC) Moved Lua into SDKs folder.
- **Optimized**: (CryAction) Minor changes to exposure of functions in CTimeDemoRecorder.
- **Optimized**: (CryAction) Changed PerfHUD to trigger only if CVar sys_perfhud was turned on (to avoid collision with TimeDemo keys).
- **Optimized**: (Serialization) Cleaning up class factories, removed unused "inplace" code.
- **Optimized**: (Serialization) Proper support for CryExtension classes.
- **Optimized**: (Serialization) Changes factories to use strings instead of TypeID for derived types (needed for CryExtension integration).
- **Optimized**: Using cry_strcpy() and cry_strcat() instead of strcpy*(), strncpy*(), strcat*().
- **Optimized**: Skip culling and render jobs for octree nodes that would not contribute to a pass.
- **Optimized**: Replaced multiple versions/files computing crc32 by single CryEngine/CryCommon/CryCrc32.h.
- **Optimized**: Remove PS3 and Xenon related functionality from the CRYENGINE.
- **Optimized**: Only consoles should use PlatformSavingAPI by default.
- **Optimized**: Deleted obsolete commented-out code and cleaned Windows-related #defines.
- **Optimized**: Cleaned CryGetCurrentDirectory().
- **Optimized**: Scan the Code/GameSDK/GameDll directory for script bindings as well as Code/CryEngine.
- **Optimized**: Removed de-virtualizer stuff (changed VIRTUAL with virtual, FINAL with final etc).
- **Optimized**: Cleaned CryCreateDirectory().
- **Optimized**: Random numbers generation: refactored/cleaned/fixed.
- **Optimized**: Refactored responsibility for window message pumping and handling to CrySystem (instead of split between game, renderer and system), exposing interface for notification if so desired.
- **Optimized**: Refactored Win32 window handling so IME and Unicode events are properly handled, this change does not take effect in Editor (because it's not compatible with ANSI MFC/XT dependencies).

#### CryPhysics

- **New**: (CE-5732) Added phys geometry planar rasterizer.
- **New**: (CE-3785) Implemented Road physicalization.
- **New**: PWI tests with custom intersection params can still use a user defined un-projection direction.
- **New**: PWI tests now store the primitive index in the contact info if applicable.
- **New**: Support horizontal wave sim to water volumes.
- **New**: Exposed rope stiffness and hardness to LUA script.
- **Fixed**: (CE-5570) Fixed issue with asymmetrical box gravity areas.
- **Fixed**: (CE-6162) Fixed bone remapping in engine's AnalyzeFoliage.
- **Fixed**: (CE-6011) Check for non-physicalized skeletons in SyncFromImpacts.
- **Fixed**: Div by 0 in rope code.
- **Fixed**: Proper forced bbox update for ropes.
- **Fixed**: Physics Proxy performing netserializing even when the serialization is disabled.
- **Fixed**: Rope sleep speed serialization.
- **Fixed**: Ignore setting 0 mass to cloth.
- **Fixed**: Crash from Constraints Physics Helper in Pure Game. The change will also make the debug look same as the helper drawn in Editor.
- **Fixed**: Issue with aligned cylinders/capsules intersection.
- **Fixed**: Account for suspension in energy estimation.
- **Fixed**: Another fpe in pre-cg solver.
- **Fixed**: RayCastIntersection doesn't work without valid physics proxy in the world.
- **Fixed**: Water volume memory corruption issue.
- **Fixed**: Rope's twist damping (friction pull) was applied the second time as a general damping.
- **Fixed**: Some slot matrix fixes for breakable objects.
- **Fixed**: Boolean deformables issue caused by tangent frame cleanup.
- **Optimized**: Rope and player constraints tweaks.
- **Optimized**: Rope tweaks.

#### CryInput

- **New**: Added exclusiveinput listener functionality to the hardware mouse module.
- **New**: Added Mouse sensitivity CVar: i_mouse_sensitivity.
- **New**: CTRL+V will now paste text from the Windows clipboard.
- **Fixed**: Mouse sends also the 0 event when stopping to keep consistency with controller inputs.
- **Fixed**: Don't use left thumb for d-pad events and correctly send release d-pad button events.
- **Optimized**: (CE-5622) Implement IInput::GetDevice on CBaseInput.
- **Optimized**: Delete xinput1_3.dll, it cannot be redist like this since it has an DX9 OS-side dependency. Only installation with end-user runtime for DX 9.0c is supported (or DXSDK), since COM registration is required.

#### CryEntitySystem

- **New**: Allow querying rope length via ScriptBind.
- **Fixed**: Out of memory crash during BspTree creation: Fix for infinite loop and made creation non-recursive.
- **Optimized**: Updated es_LayerX CVar description text with line breaks so information fits in console view.
- **Optimized**: Removed the GetWorldTM_fast method and replaced the GetWorldTM with it.

#### CryNetwork

- **Fixed**: (CE-5624) Rare null pointer exception in CryNetwork which can cause server crashes in Multiplayer.
- **Fixed**: Assert on shutdown due to socket reference staying alive due to static duration object.
- **Fixed**: Potential context corruption.
- **Fixed**: Stack overflow in getaddrinfo from the CNetAddressResolver by using the default stack size rather than 16KB.
- **Fixed**: Wrong matchmaking sessionID handling.

### Particles

- **New**: (CE-5860) Add control over light clipping to lights spawned from particles.
- **Fixed**: (CE-5864) Changed 2nd DrawIndexedPrimitive call to fix render errors.
- **Fixed**: (CE-6282) Disappearing emitters, caused by incorrect 3DEngine.GetRenderer pointer. Now compute angular density and max distance from PassInfo.Camera whenever needed.
- **Fixed**: (CE-6373) Fixed Facing=Velocity behavior. Restored Stretch.OffsetRatio behavior.
- **Fixed**: Particle soft intersection when no depth test is used.
- **Fixed**: Improved up-sampling for half and quarter res particles.
- **Fixed**: Out of range array access fix; don't add a refractive particle render item if refraction is disabled.
- **Fixed**: Particles aren't rendered by a shader for alpha blend when the blend mode is set to alpha blend.
- **Optimized**: Removed obsolete HDR Dynamic parameter from particle lights.
- **Optimized**: Base particle indices relative to first vertex of draw call instead of begin of vertex buffer.

### RC/Tools

#### Tools General

- **New**: (CE-5807) (Statoscope) Added text filter for the function profiler.
- **New**: (MemReplay) Support multiple debug symbols resolving for Linux non-static build.
- **New**: (MemReplay) Support Memreplay for Linux.
- **New**: (ChunkExplore) Added chunk table visualization, added type to DataStream and Mesh chunk name visualization.
- **New**: (LuaDbg) Allow stack-frame switching from the UI, will correctly populate the locals of only the selected frame.
- **New**: (LuaRemoteDebugger) Updated to match new LuaDbg.
- **New**: (MayaCryExport) Added mesh validation for degenerate triangles (NaNs for positions/normals).
- **New**: Update CrySCompileServer.sln to use VS2012.
- **New**: Added support for 3ds Max 2016, Maya 2016, Motion Builder 2016.
- **Fixed**: (CE-5676) (Memory) Compile Fix - Engine does not compile without USE_GLOBAL_BUCKET_ALLOCATOR.
- **Fixed**: (CE-5837) (Memreplay) Hangs on level load.
- **Fixed**: (CE-6105) (Statoscope) Fixed crash when saving the capture to file after the launcher is terminated.
- **Fixed**: (CE-1468) (Statoscope) Fixed left part of the hover over label going off screen.
- **Fixed**: (MemReplay) Fixed crash caused by unused module book keeping code.
- **Fixed**: (LuaDbg) Now shows locals of the current frame only (no longer conflict with identical named locals from parent frames hiding actual locals).
- **Fixed**: (CryTIF) Incorrect type used (was using uint32 instead of required Photoshop SDK's unsigned32).
- **Fixed**: (CryTIF) Solving problem of int32 and uint32 typedef'ed differently in the TIFF Library and in the Photoshop SDK.
- **Fixed**: (Legacy MSBuild) Fix MaxCryExport to match expat location.
- **Fixed**: Remove Sandbox/SDKs directory from Editor includes and cppcheck.
- **Fixed**: P4.exe only exists on Windows. Use 'p4' when referring to the executable as this works on all platforms.
- **Fixed**: Move RemoteShaderCompiler binaries to Tools/ folder.
- **Optimized**: (MaxCryExport) Deleted obsolete/unused crc32computer.*
- **Optimized**: (nvDXTLibrary) Removed binaries and dependencies after usage from code was removed.
- **Optimized**: (RemoteShaderCompiler) Moved PCGL compilers to /Tools/RemoteShaderCompiler/Compiler/PCGL where compilers now reside.
- **Optimized**: Remove deprecated RSASigner.
- **Optimized**: Remove obsolete Photopbump and Polybump content from Tools.
- **Optimized**: Deleted obsolete/unused Code/Tools/MayaCryExport and Code/Tools/MaxSDKSamples.
- **Optimized**: Remove Jenkins folder (now maintained in //depot/Tools/BuildTools/Jenkins).
- **Optimized**: (Pipeline) Now using original tifflib and zlib (located in 3rdParty folder) instead of using multiple versions of source files (sometimes modified) and precompiled libraries scattered in Code; removed some unused PS3 code.

#### Resource Compiler

- **New**: (RC) Added importance-sampled GGX-based specular probe convolution (enabled by default now).
- **New**: (RC) Removed neighborhood smoothing from normal variance filter and replaced Toksvig algorithm (does not require conversion to Phong exponent any longer).
- **New**: (RC) Added quality-settings to RCImage format conversion.
- **New**: (RC Image Compiler) Multi-threaded cubemap generation/integration, 2.5x to 4x speedup for Environment Probes generation.
- **New**: (RC ImageCompiler) Added support of aliases for preset names (section _presetAliases in rc.ini).
- **New**: (RC ImageCompiler) Added 2 channel formats.
- **New**: (RC ImageCompiler) Added configurable mapping of preset names.
- **New**: (RC Alembic) Now uses shared lz4 SDK
- **New**: (CryTIF plugin) added possibility to skip RC dialog by request.
- **New**: Added MSE-based sRGB vs. Linear auto-conversion (higher quality).
- **Fixed**: (RC) fixed error reporting for missing or invalid xml files.
- **Fixed**: (RC ImageCompiler) Updated block-compressor to support BC1-BC7.
- **Fixed**: (RC ImageCompiler) 4-channel 16 bit format.
- **Fixed**: (RC Animation Compiler) Fixed compilation of DEBUG configuration.
- **Fixed**: (CE-6123) (MaxCryExport) Handle animation range that is not a multiple of frame duration.
- **Fixed**: (CE-3613) Texture Streaming breaks skyboxes.
- **Fixed**: (MaxCryExport) Now referencing morpher files from max SDK instead of local copy of them.
- **Optimized**: (RC) Deleted obsolete refs_scan option.
- **Optimized**: (RC) Removed and cleanup RCImage includes.
- **Optimized**: (RC) Removed references to bin32/rc.exe.
- **Optimized**: (RC) Deleted p4 support in RC (unrelated to Editor P4 plugin).
- **Optimized**: (RC) Deleted AssetInfo, ExcelReport, ExcelExport.
- **Optimized**: (RC) Deleted experimental/obsolete (CUDA-related) multi-process support.
- **Optimized**: (RC ImageCompiler) Remove redundant "_CRT_SECURE_NO_DEPRECATE" define.
- **Optimized**: (RC ImageCompiler) Deleted SRF data support, TextureMerger.
- **Optimized**: (RC SkinCompiler) Cleanup/fixes/renaming.
- **Optimized**: Now assert() is disabled in release version of RC.
- **Optimized**: Removed support of ps3, x360, wiiu; implemented [Delete platform] for list of resolutions in RC ImageCompiler dialog; removed Emulate3DC option.

#### WAF

- **New**: Use separate default output folders for clang and gcc on Linux.
- **New**: Add detection for installed SDK when configuring, building and generating projects. Strip unsupported platforms if not on system. e.g. won't show up in Visual Studio.
- **New**: (CE-6033) Output dedicated server binaries in xxx_dedicated folder to avoid dll clashes when building and running game and server from same folder.
- **New**: Recover FBXPlugin. Added to WAF.
- **New**: Enable bootstrap option - Validation failed when p4.exe returned a none-zero value... hence p4 is installed and we should not fail at this step.
- **New**: (VR) add Oculus to gamesdk_and_tools.json, gamezero.json, and gamezero_and_tools.json.
- **Fixed**: (Bootstrap) Generate 32-bit executables for compatibility.
- **Fixed**: (Bootstrap) More readable error output for "ClientFile dictionary error"... caused most likely by "file not in client view".
- **Fixed**: Added fallback for toolchain folder.
- **Fixed**: Linux Compiler. Define LINUX32 for x86 linux systems, was LINUX64.
- **Fixed**: Tiff integration into WAF. Was renamed from libtiff to tiff.
- **Fixed**: Don't rely on project-spec providing a game project, read it from the config file.
- **Fixed**: Reactivate Recode and Bootstrap by default.
- **Fixed**: Only include tiff library where needed.
- **Fixed**: copy_output task. Create folder structure if target folder does not exist.
- **Fixed**: CryAudioImplSDLMixer is missing from gamesdk.json and gamezero.json.
- **Fixed**: Shadercachegen project spec does not build CryRenderOpenGL, which breaks shader cache generation.
- **Fixed**: Now that bootstrap uses.bootstrap.digest.pickle, WAF should use the same filename (this avoids conflicts where an old.bootstrap.digest file is present).
- **Fixed**: CryAudioImplSDLMixer is missing from gamesdk.json and gamezero.json.
- **Fixed**: MSVC include and lib directories.
- **Fixed**: Removed hardcoded Code/SDK include and library paths.
- **Fixed**: Issue with ADMIN RIGHT required for GCC MSBUILD folder creation. Create MSBUILD platform folders if not exist and only for active platforms.
- **Optimized**: Improve error message when attempting to build without specifying spec.
- **Optimized**: Improve missing TADP error warning.
- **Optimized**: Use Qt tools from the SDKs directory, not Tools directory.

### Audio

#### Audio General

- **New**: Updated Wwise to version 2014.1.4.
- **New**: Updated Wwise run-time to version 2014.1.3.
- **New**: Implemented real-time audio capture via Wwise, for that introduced new CVar s_WwiseEnableOutputCapture.
- **New**: Added CVars to be able to set Wwise memory pool sizes, increased lower engine pool from 4 to 16 MiB to safely cover for expensive reverbs.
- **New**: Added warning when an invalid auxAudioProxyID is used to execute a audio trigger.
- **New**: RemoveRequestListener can be called with NULL as callback-function-parameter to remove all callbacks for the specified listener-object.
- **New**: ExecuteTrigger now returns a bool which tells if at least one execute-trigger request was send to the audio system.
- **New**: Added missing SDL, SDLMixer and ogg/vorbis files to Bin32.
- **New**: Added filtered display of debug strings showing audio objects and triggers, for that introduced new CVars: s_ShowActiveAudioObjectsOnly, s_AudioTriggersDebugFilter and s_AudioObjectsDebugFilter.
- **New**: Added ability to toggle audio functionality on all particles globally, for that introduced a new CVar: e_ParticlesAudio.
- **New**: Introduced code to the audio memory allocator to catch memory misalignments, by default disabled but to enable it introduced define INCLUDE_AUDIO_ALLOCATOR_PRODUCTION_CODE.
- **New**: Preventing constant updates to the "object_speed" RTPC even if an audio object's velocity didn't change, introduced CVar s_VelocityTrackingThreshold to have control over the update threshold.
- **Fixed**: (CE-5994) (CryAudioImplWwise) Linux undefined symbol.
- **Fixed**: (CE-5593) Environmental audio is gone after a save/load procedure.
- **Fixed**: (CE-5796) (CE-4721) AudioAreaAmbience entities kept executing the start trigger when properties were changed.
- **Fixed**: (CE-6191) Audio mix preserved after muting.
- **Fixed**: (CE-5000) Bug in AreaManager where entities that were near an area never left it upon teleportation.
- **Fixed**: Monolithic release builds - Audio - Selectively load SLDMixer and Wwise module at run-time.
- **Fixed**: Audio trigger ID was not reset if no TriggerName was provided on the AudioTrigger FlowGraph node.
- **Fixed**: Bootstrap retrieves 3Dception Wwise plugin.
- **Fixed**: Porting the old Dialog System to the new AudioSystem.
- **Fixed**: Using a free list for the channels to avoid SDL Mixer assigning channels that haven't been cleared.
- **Fixed**: AudioTriggerSpot did not restart a newly added trigger.
- **Fixed**: SDL Mixer cleans up properly when data is modified in the ACB.
- **Fixed**: Crash when trying to access an invalid cvar pointer for s_AudioLoggingOptions.
- **Fixed**: Only the first registered Listener for a event was called.
- **Fixed**: Vehicle Engine Audio position was incorrect.
- **Fixed**: Engine shutdown, also properly removing profilers now when unloading modules.
- **Fixed**: AudioTriggerFlowNode could crash, because of async-Callback.
- **Fixed**: Made the constructor of SAudioCallBackInfos explicit, otherwise every 'this' pointer could implicitly be cast to an CallBackInfo object.
- **Fixed**: AddRequestListener now not only checks fct-ptr and listener-object, but also RequestType and RequestMask before early out with listener-already-existing.
- **Fixed**: Handle the cases that a ExecuteTrigger is failing before reaching the audio system at all. Before the dialog system would have waited forever for the 'finished'-callback.
- **Fixed**: Crash at shutdown, when the Oculus audio SDK plugin was destroyed to early.
- **Fixed**: Not saving the state anymore on audio scripts during save/load.
- **Fixed**: Properly shutting down Wwise in case of Wwise initialization failure.
- **Fixed**: Audio debug data did not contain memory pool utilization.
- **Fixed**: Parent entities did not show their children again after being shown themselves (hiding worked fine).
- **Fixed**: Removed log spam for preloads in SDL Mixer.
- **Fixed**: We do not fall back to the NULL implementation anymore if Wwise could not load the Init.bnk.
- **Fixed**: Disabled audio port specific warning via new define (ENABLE_AUDIO_PORT_MESSAGES).
- **Optimized**: Removed old code in the audio Proxy for playing at head position.
- **Optimized**: Increased audio object pool size for PC (fixes dead lock when too many objects are created during level load).
- **Optimized**: SubtitleManager is now using the new audio callbacks.
- **Optimized**: The old dialog system does not pass along native pointers as user data for the audio callbacks, but IDs instead. This is probably the much safer variations if other systems (subtitles?) are interested in events from that system.
- **Optimized**: Removed 'velocity' from the ATLWorldPosition struct.
- **Optimized**: Direction of audio sources and listeners is normalized when needed, so that the user of the audio system does not take care of this.

#### ACB (Renamed to ACE: Audio Controls Editor)

- **New**: (CE-5787) Created common project for the interface between the ACB and the implementations.
- **New**: Support for localized soundbanks with the same name as global soundbanks.
- **New**: External controls are colored different when not connected, can also be filtered.
- **New**: Can remove connection with context menu now.
- **New**: Added new default controls.
- **New**: MSBuild project for the SDL Mixer Editor.
- **New**: Doc-o-matic documentation for the ACB dll interface.
- **New**: Trigger preview in the resource selector dialog.
- **New**: Added the ACB to the dialog toolbar.
- **New**: New preload panel.
- **New**: First pass at automatic updating of the wwise panel.
- **New**: Added function to retrieve middle-ware name.
- **New**: Changing name to Audio Controls Editor. More accurate for its functionality.
- **New**: ACB adapts to changing audio middleware.
- **Fixed**: (CE-5634) Bug with new states not being saved to file.
- **Fixed**: (CE-6190) Fixed bug with duplicate connection being added.
- **Fixed**: (CE-6174) When creating a folder it will check that the name is valid before creating.
- **Fixed**: (CE-6238) Fixed crash when exiting Sandbox.
- **Fixed**: (CE-6189) Fixed problem with UI layout for SDL Mixer connection properties.
- **Fixed**: (CE-6217) Switches and states are loaded properly now.
- **Fixed**: Sort middleware controls by type then name.
- **Fixed**: Fixes to undo/redo.
- **Fixed**: Moved panes to docking panes.
- **Fixed**: Only one connection is added when dragging in an external control.
- **Fixed**: Connected status of middleware controls is updated when connections are deleted.
- **Fixed**: UI spacing for SDL Mixer.
- **Fixed**: Connected control colours for SDL Mixer.
- **Fixed**: Don't create the default_controls folder if controls are already in the project.
- **Fixed**: Find localized controls when reading connections from XML.
- **Fixed**: Don't filter switches if its name matches, even if all their children don't.
- **Optimized**: Separation of the tree layout and the controls data for simplification.
- **Optimized**: Removed custom mime data.

### Animation

#### CryAnimation

- **New**: LimbIK handles can now be longer than 8 characters, and become case-insensitive (technically, the LimbIKDefinition Handle type now uses lowercase CRC32).
- **New**: Activated physical hit reactions and Fall&Play. Toggle it on/off using ca_physicsProcessImpact. This will work out of the box in the GameSDK sample, as the 'hit' handling passes along impulses to the animation system already.
- **New**: Blend Spaces: Added more generic blendspace parameters, eMotionParamID_BlendWeightX. If you are using AnimatedCharacter you can use the new function SetBlendWeightParam to set these parameters. (next to the usual low level function ISkeletonAnim::SetDesiredMotionParam)
- **New**: Blend Spaces: Added debugging for parametric blend spaces on layers other than 0. (part of regular debugging information, see [Animation Debugging](/docs/static/engines/cryengine-3/categories/1638401/pages/19377239))
- **New**: Secondary Animation: Added option to project joint out of lozenge.
- **New**: Secondary Animation: Added yaw and pitch rotation to the attachment ellipsoid.
- **New**: Secondary Animation: Improved debug information display for attachments, springs and pendula.
- **New**: Secondary Animation: Replaced simulation method (technically: the integrator changed from "Symplectic Euler" to "Velocity Verlet").
- **New**: Secondary Animation: Force-align all attachments with "Translational Projections" with the joint.
- **New**: Secondary Animation: Collision detection for springs.
- **New**: GPU skinning now supports 8 weights per vertex (previously only supported 4 weights per vertex).
- **Fixed**: "Blending from ragdolls" (also known as "fall and play") in GameSDK. It is triggered when you, for example, slide into a human AI, or give a human AI a lot of damage without killing it.
- **Fixed**: Problem in streaming system, which (among other things) caused DBAs not to be loaded on a dedicated server.
- **Fixed**: (CE-4974) Exporter doesn't error but engine does with certain unsupported bone setups. (fixed editor crash following 'this joint was physicalized in max and failed to load geometry for some reason' error)
- **Fixed**: Secondary Animation: Attached CGFs don't disappear when we enable the redirect flag.
- **Optimized**: Small performance improvement in the GetIndexByName method in the attachmentManager, assuming you have a lot of attachments.
- **Optimized**: Modifiers (experimental): Modifier IDs are now stored in CDF as names, rather than GUID-s.

#### Character Tool

##### Secondary Animation in Character Tool

- ****New****: Character Tool now fully supports editing for secondary animation, and drastically improved attachment editing in general. See the new accompanying documentation: [Attachment System Tutorial - Character Tool](/docs/static/engines/cryengine-3/categories/1114113/pages/21266709).
- **New**: Gizmo works better now when editing simulated attachments.
- **New**: Added creation and removal of collision proxies.
- **New**: Activated relative joint position/rotation for the proxies.
- **New**: Stiffness Target was never supported for Springs.
- **New**: Added yaw & pitch rotation to the ellipsoid.
- **New**: Experimental: Added interfaces for Pendula Cloth (i.e. translational projection, turbulence,velocity clamping, frame rate independent physics update).
- **Fixed**: Position of newly inserted attachments.
- **Fixed**: Removed flags that don't make sense with certain attachments.
- **Fixed**: Shortarc Rotation wasn't displayed for half-cones.
- **Fixed**: Hinge-constraints didn't show the projection direction for rotations.
- **Fixed**: Directional projections not activated after loading.
- **Optimized**: Reorganized simulation parameters in the attachment panel.

##### General

- **New**: "Save unsaved changes" dialog when closing character tool.
- **New**: "Save As" context menu action.
- **New**: Support for deletion of assets.
- **New**: Added "Edges" display option to render edges on top of the character.
- **New**: Added warning about missing animsettings file.
- **New**: Added abstract anim event player interface (IAnimEventPlayer) which is used to play anim events in character tool. You can implement and register your own IAnimEventPlayer in your game code to preview game specific events. Created separate anim event player implementations for ATL, MFX and Particles. Those also act as examples in case you want to implement your own. See AnimEventPlayers.cpp.
- **New**: Added "Reset Character" button to display options. It resets the character to the origin and stops playing animations.
- **Fixed**: (CE-5795) Selecting a wrong skeleton will make the Editor crash. (fatal error "ModelError: duplicated CRC32 in SKEL")
- **Fixed**: Slow loading of the character when filter in Asset panel is not empty.
- **Fixed**: Removed (wrong) display of gizmos in the uncompressed view.
- **Fixed**: 'Reset' action in context menu of attachment transform.
- **Fixed**: Make sure that unloaded character is removed from memory.
- **Fixed**: Rendering of transparent debug geometries in Character Tool.
- **Fixed**: Issue with drawing debug options on compressed and uncompressed character.
- **Fixed**: Playback scale in CharTool had no impact on the simulation time.
- **Fixed**: Skel-Extensions loaded only the geometry, but didn't extend the skeleton (crashed on some PCs).
- **Fixed**: Crash when entering invalid blend space annotation indices.
- **Fixed**: Playback option "first frame at the end of timeline".
- **Fixed**: Animation starting every time character is selected in scene parameters.
- **Fixed**: New animations disappearing with "on disk+new only" filter.
- **Fixed**: Game playing in Character Tool viewport.
- **Fixed**: Duplicated keys do not lose their properties anymore.
- **Fixed**: Duplicated animation event is now properly selected in the property panel.
- **Fixed**: Default type of animation event is now audio_trigger.
- **Fixed**: Disabled animation control when loading character.
- **Fixed**: Playback when clicking on already selected animation.
- **Fixed**: Animation events not playing when previewing compressed animations.
- **Fixed**: Hanging during loading of characters.
- **Fixed**: Fix for audio related log spam while scrubbing.
- **Fixed**: Cleanup of attachment management (to fix errors like this one: [Error] CryAnimation: Attachment name 'fullbodymesh' is already in use, attachment will not be created).
- **Fixed**: Slow loading of the character when filter in Asset panel is not empty.
- **Fixed**: Fix for exploding characters when using SaveAll.
- **Fixed**: Keep Debug-Settings activated when doing SaveAll.
- **Fixed**: Crash when changing filtering options.
- **Fixed**: Slow update when changing locomotion parameters.
- **Fixed**: Expansion of the whole browser tree when displaying filtering options.
- **Optimized**: Reorganized display options.
- **Optimized**: BindPose option now also disables simulations.
- **Optimized**: (CE-5829) Changed error into warning when extending skeletons.
- **Optimized**: Modifiers (experimental): UI is updated to use same code path as other polymorphic types.

#### Mannequin

##### Mannequin Editor

- **New**: (CE-5791) Added ** mn_override_preview_file** CVar to override the default preview file to be used by the editor. This overrides the Sandbox setting which is stored in the registry.
- **New**: (CE-5971) Made timeline zoom using mouse wheel adjustable. The option is "Timeline Wheel Zoom Speed" in Tools/Preferences/Mannequin/General.
- **New**: (CE-5973) Copy/Paste layers in clips.
- **New**: (CE-5974) Copy/Paste fragmentIDs.
- **New**: Added Copy/Paste commands into context menu in the fragment browser. (the commands where previously only available through keyboard shortcuts)
- **New**: Assignment of current animation from Character Tool.
- **Fixed**: (CE-5963) Sub-adb organization by tag from within Anim DB editor.
- **Fixed**: (CE-6024) Avoid generating an error "DUPLICATE CXConsole::AddCommand()".
- **Fixed**: (CE-5959) Error report not appearing when opening a preview file.
- **Fixed**: (CE-6165) Crash when closing Mannequin editor when having panes un-docked.
- **Fixed**: (CE-5965) Deletion of fragmentID reshuffling sub-adb files (related to sub-adbs using fragmentIDs to filter).
- **Fixed**: Opening of.comb files from the animclip context menu.
- **Fixed**: FragmentID editor only listing xml files ending exactly with tags.xml (case sensitive). Now we simply scan for all.xml files, ignoring the rest of the filename.
- **Fixed**: Issue with "Hold Ctrl to snap scrubbing" setting was not properly saved in the registry.
- **Fixed**: Context menu in fragment browser acts now on clicked item, rather than item selected last time.
- **Fixed**: Disabled hiding of panels in Mannequin to prevent UI glitch.
- **Fixed**: (CE-6031) Filtering in the Mannequin UI changes the displayed case of Fragment Tags. Fixes lowercase tags in preview tree after filtering by tag name.
- **Fixed**: (CE-6025) Audio Proc Layer which starts at zero will play when scrubbed to zero. Audio will not play when scrubbed to zero. Will play when played from zero.
- **Fixed**: (CE-6034) Right-click in Mannequin Fragment Editor opens an empty context menu.
- **Fixed**: Avoid assert in Debug mode while there is no separator in tool bar.
- **Fixed**: Crash while moving mouse over Sequence Dope Sheet.
- **Fixed**: (CE-5968) Within the Edit Context window, a FragmentID can now only appear once.
- **Fixed**: Missing time display on the toolbar.

##### Mannequin System

- ****New**:**[Mannequin Actions](/docs/static/engines/cryengine-3/categories/1114113/pages/15011601) documentation has been updated.
- **New**: (CE-5174) CActionController::PruneQueue() will now also print all the queued actions when the queue overflows.
- **Fixed**: (CE-5148) Fixed CryAction and GameSDK so the ComparePriority implementation in custom mannequin actions behaves similar to before 3.7. This impacts AI, item animation, replay actors, turrets and playback in the mannequin editor. As explained in [Mannequin Actions](/docs/static/engines/cryengine-3/categories/1114113/pages/15011601).
- **Fixed**: Recovered missing procedural clip LayerAnimSpeed.
- **Fixed**: Fixed default values for procedural clips AimSmoothing, CopyNormalizedTime, MovementControlMethod, Ragdoll, TurretAimPose, WeaponBump, WeaponPose, WeaponWiggle.
- **Fixed**: Audio procclip: removed properties that weren't working; renamed properties to make them a bit more clear to the user.
- **Improved** (CE-4311) Made it more visually clear that clip properties cannot be edited in the previewer, by changing colors a bit in the old property control.

### AI System

- **New**: TPS debug draw mode also works with the agent debug target.
- **New**: Modular Behavior Tree: history of the execution stack can now be logged to files.
- ****New**:** The MNM pathfinder now also restarts the movement request if the visited tile or its neighbor tiles are changed. Before it was not taking the neighbors into account.
- **New**: Adding a new generic parameter to the TPS queries, to be used by the TPS extensions.
- **New**: MovementSystem: Can now display the queued movement requests of actors.
- **New**: CryAction_AIActionSequenceFlowNodeBase now offers a convenient way to stop the FlowGraph node from updating once the sequence-action finishes or gets canceled.
- **New**: Adding the concept of the event log to the behavior tree which will be used by the behavior tree visualizer to show the recent event history.
- **Fixed**: (CE-4250) Now ensures that turrets will be aligned before allowing to shoot through an AI.
- **Fixed**: (CE-5854) AILogLoading() was appending to uninitialized memory.
- **Fixed**: (CE-5392) AIWave: Fixed recycling of AIs when the wave got disabled and then re-enabled and added an optional parameter to script function System.PrepareEntityFromPool().
- **Fixed**: (CE-5603) Changing an AI's faction during gameplay didn't reflect the change in its visual perception.
- **Fixed**: (CE-5500) VisionMap: Crash when loading a save game (dangling data in accidental leftovers of pending rays when observables had more than one hotspot).
- **Fixed**: (CE-5891) NavMesh updated itself unreliably when changing transforms of brush objects.
- **Fixed**: (CE-5683) BasicCommunications.xml: deprecated "AutoGenerateCommunication" removed.
- **Fixed**: Registration of the AI extensions is now done in the Game::Init funtion, instead of Game::InitGameType which was happening too early.
- **Fixed**: TPS: properties of the max-heap were violated, causing VC++ error message popups in debug builds.
- **Fixed**: AI Movement System is now reset on level unload event.
- **Fixed**: Don't execute ReloadTPS and don't try to load Factions.xml if they doesn't exist.
- **Fixed**: The min and max members of the SRangeExtenderParameters structure to avoid conflicts with min and max functions.
- **Fixed**: (CE-6122) AI characters were no longer present in the movement system after quickloading.
- **Fixed**: TPS generator for points inside Navigation Mesh is no longer dependent on AIActor (the Navigation Agent Type name can now be specified as a parameter to the generator).
- **Optimized**: Human_x.lua: removed some unused script properties.
- **Optimized**: (CE-6159) Registering erroneous TPS queries now gives better warning messages.
- **Optimized**: (CE-4888) Prepared deprecation of old AI Character system (#define USE_DEPRECATED_AI_CHARACTER_SYSTEM).
- **Optimized**: (Behavior Tree) renamed USING_BEHAVIOR_TREE_DEBUG_EVENTS -> USING_BEHAVIOR_TREE_EVENT_DEBUGGING and USING_BEHAVIOR_TREE_DEBUG_TIMESTAMPS -> USING_BEHAVIOR_TREE_TIMESTAMP_DEBUGGING to prevent confusion.
- **Optimized**: Old AI character scripts removed due to deprecation.

### Game

- **New:** Re-added CanStabilize function which allows players to "hold breath" (with Shift, while zoomed) for increased weapon stability.
- **New**: (CryAction) Added registration method to the scheduling profile for game object.
- **New**: (CE-5990) Unified cursor loading for all platforms. Windows hardware and software cursor is now loaded dynamically at runtime from.pak file; as.tif or.dds format, instead as windows executable resource; as.cur format.
- **New**: (Scaleform) Integrated IME support (from Scaleform 3.3.94).
- **New**: Adding an optional snap rotation mode for controller via cl_controllerYawSnap CVars.
- **New**: Added no_mouseX and no_mouseY filters.
- **New**: Added functionality to move character in HMD direction via cl_enableMoveInHMDDirection CVar.
- **Fixed**: (CryAction) Fixes crash on game shutdown when CAnimationBoneInfo_Node is updated while its cached entity ID is no longer valid
- **Fixed**: (CE-5511) (CryAction) Vehicle massbox is ignoring driving offset when the vehicle received any damage on the hull.
- **Fixed**: (CE-5487) (CryAction) Proxy for Undamaged wheel spawns on destroyed vehicle.
- **Fixed**: (CE-5446) (CryAction) Animated Vehicle parts rotation is reset on exit and reinstated on entry.
- **Fixed**: (CE-4921) (Dedicated) Calling map airfield twice crashes the server.
- **Fixed**: (CE-5467) HUD updating slowly in medium & low spec.
- **Fixed**: (CE-5515) Vehicles can't be damaged by explosives (grenade, rocket, etc).
- **Fixed**: (CE-3271) Player unable to move after stealth kill.
- **Fixed**: (CE-5227) AutoAimManager: no longer caches AI factions since it might prevent AIs from getting killed by shots when the faction changes during gameplay.
- **Fixed**: (CE-5923) Actors could no longer get killed by bullets after standing up from their ragdoll phase.
- **Fixed**: (CE-5414) Actors would not have physics properly restored after recovering from a grenade explosion.
- **Fixed**: (CE-5926) Weapons were piling up in the Editor when reloading scripts.
- **Fixed**: (CE-6209) Invalid GameCache state on level unload.
- **Fixed**: (CE-6178) Proximity trigger doesn't track state while disabled.
- **Fixed**: (CE-6285) ProximityTrigger's "IsInside" output renamed to "NrOfEntitiesInside" to match area trigger (and to more closely reflect what it does). This output is now always 0 when the trigger is disabled.
- **Fixed**: (CE-6426) USE_BLEND_FROM_RAGDOLL was not defined resulting in AI not getting up once knocked over.
- **Fixed**: Fixed fall-and-play not triggering when you slide into or jump onto an AI.
- **Fixed**: Path for Ironsight model in Precache lists.
- **Fixed**: Spread scale not working for hold breath function.
- **Fixed**: Updated weapon scripts for new rifle assets.
- **Fixed**: Formatting/alignment of some i_debug_ text.
- **Fixed**: Moved gametokens reset to the start of the loading game process (flowgraph were using it before it was initialized).
- **Optimized**: (CE-1495) Remove deprecated "Tweaks" system.
- **Optimized**: (CE-6130) Removed Diffuse/Spec/Radius flowgraph inputs from Light entity.lua script as they no longer work. Use Entity:PropertySet/Get instead.
- **Optimized**: (CE-4380) Removed unused pl_jump_quickPressTresh CVar and related code.
- **Optimized**: Cleaned up flashlight code and removed unused Crysis3:Flashlight flownode.
- **Optimized**: Speedboat script tweaks.
- **Optimized**: Cleaned up multiplayer config to lessen some log spam. Removed some unnecessary entries which are using default values from code. Removed whitespace between CVar and value. Removed audio entries which are no longer valid CVars.
- **Optimized**: Increased viewdist ratio on Chickens Boids from 30 to 50.
- **Optimized**: Removed "vehicle loops" log event from VehicleAct.lua.
- **Optimized**: Removed unused/obsolete Weapon Params: hint_loop_start, angular_impulse, back_impulse, spread_finalBreath_m, useLowAmmoWarning, lowAmmoWarningFraction, offset, stealthEnergyDrainMultiplier, hasEmptyReload, heavy_weapon, spin_down_time, hud_style, transitionAnimtation, recoilDamping, coverScale, coverScaleTime.

[Release Highlights](#release-highlights)[Important Code and Data Changes](#important-code-and-data-changes)[Editor](#editor)[Renderer](#renderer)[Engine](#engine)[Particles](#particles)[RC/Tools](#rctools)[Audio](#audio)[Animation](#animation)[AI System](#ai-system)[Game](#game)
