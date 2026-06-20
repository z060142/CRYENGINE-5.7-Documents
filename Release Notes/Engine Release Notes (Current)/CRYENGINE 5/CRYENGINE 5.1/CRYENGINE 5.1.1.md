# CRYENGINE 5.1.1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962611
- Page ID: 44962611
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.1 > CRYENGINE 5.1.1
- Parent: CRYENGINE 5.1

## Content

### Release Highlights

CRYENGINE 5.1.1 brings fixes and improvements to the way users navigate the Sandbox Editor. With this release expect more efficient menus, smoother camera movement and much more!

**Editor Console Help Menu:** Users will now see a "Help" menu in the Console plug-in with "Console Variables" and "Console Commands" menu items.

![Image](https://www.cryengine.com/docs/static/attachments/44962614)

**More Camera Movement Options in the Sandbox** ** Editor:**More camera movement options have been added in Editor mode. These are located with the other options (standard UI toggles) in the Camera drop-down menu above the main Viewport.

- **Speed Height-Relative:** (new option) When enabled, adjusts the speed of camera movement based on the height of the camera above terrain or objects. The camera speed is multiplied by the height in meters (clamped to a range of 1-1000). Allows for precise movement when close to the ground, or to quickly move to different parts of a Level without the need to constantly adjust the camera Speed slider.
- **Terrain Collision:** (existing option) Camera collision with the terrain when moving.
- **Object Collision:** (new option) Camera collision with physicalized objects when moving - the camera will slide along the physics proxy, but without penetrating. This option also affects the ** Speed Height-Relative:** when set to on; camera height is measured above terrain or objects. When set to off; camera height is measured above terrain only.

**Terrain Editor Cleanup:** Improvements to Terrain Tool usability. "View" has been removed from the Tools Menu - the top down view wasn’t working as expected. In the future this will be configured to work as a standard "Top" view. The “Copy” and “Move” buttons have been fixed and the UI has been changed - there is now a checkbox "Move objects" - this does exactly what you’d expect and an “Undo” operation has also been implemented.

![Image](https://www.cryengine.com/docs/static/attachments/44962613)

**Optimized Viewport Resolution Control:** Previously,Viewports with custom resolutions could only have their contents stretched to the edges of the window to preserve aspect ratio. Now when setting a custom resolution for a Viewport widget some new options are available that allow users to position the contents of the game in the Viewport, but without stretching.

![Image](https://www.cryengine.com/docs/static/attachments/44962612)

### Editor

#### Editor General

- **New**: Added file Drag&Drop for resource selectors and Mesh Importer
- **New**: Terrain: Add Undo/Redo for all terrain operations that were missing it (Move, Flatten...)
- **New**: Added extra positioning options (without stretching) for custom resolutions. Allows render target pixels to correspond 1 to 1 with screen pixels
- **New**: Added Console Variables and Console Commands to the Console Help Menu
- **New**: Deprecated "Exclusive Mode" for Designer Tool (until further notice)
- **New**: UI will now not become unresponsive during Level loading
- **New**: Support for 3Dconnexion devices
- **New**: Level Settings now supports Undo/Redo
- **New**: Added a quick debug info button in the Viewport header - similar to SandboxLegacy
- **Fixed**: Full screen mode stability improved
- **Fixed**: Highlight breakable and highlight missing surface options not properly set after tweaking in properties
- **Fixed**: Property Tree's scrollbar size and display
- **Fixed**: Shape objects are correctly updated when invalidating their transforms
- **Fixed**: UI becoming unresponsive after Material Picker window is closed in SandboxLegacy
- **Fixed**: Added missing Material Picker
- **Fixed**: Slider color
- **Fixed**: Viewport: Display menu dropdown menus not working properly
- **Fixed**: Terrain: Jumping into Game Mode with Ctrl+G switches height settings of Raise/Lower Tool from positive to negative values
- **Fixed**: Stack overflow on changing active material when a UV Mapping window is open
- **Fixed**: A rare crash when deleting a parented object
- **Fixed**: Serialize Equipment type variables
- **Fixed**: Re-added missing Object Collisions Display Menu item
- **Fixed**: Environment Editor: Speed is now restricted
- **Fixed**: Invalid width computation resulting in timeline not showing the whole duration of an animation clip within the Character Tool
- **Fixed**: Crash when deleting Camera Objects with targets
- **Fixed**: Crash when Smart Objects fail to initialize their scripts
- **Fixed**: Crash when right clicking on 3D texture in the Material Editor when no terrain exists
- **Fixed**: PSD buttons in the Material Editor do not show an error when no PSD is found
- **Fixed**: Crash when using file dialogs in the Database View and Lens Flare Editor
- **Fixed**: Saving of cleared shortcuts relative to defaults. Added tooltips to shortcut edit buttons. Fixed removing of custom commands (through contextual menu and delete shortcut)
- **Fixed**: Directory select dialog - now accepts directories properly
- **Fixed**: Trackview: Trackview tab not cleaned up when exiting the Trackview Editor
- **Fixed**: Trackview: Record button sometimes stops working - although it's highlighted (breaks scene)
- **Fixed**: TrackView: Record button highlighted even though the mode is inactive or vice versa
- **Fixed**: TrackView: Rotate tracks not working properly when close to 90° on the Y-axis
- **Fixed**: TrackView: Multi-selection does not work
- **Fixed**: TrackView: Copy/Pasting of keys should be more reliable
- **Fixed**: TrackView: Disabling certain nodes does not work
- **Fixed**: Sandbox: Selected icon tint in all tree views. Now tinted according to the qproperty-selectedTreeViewTint in qss. Made it so QAdvancedItemDelegate removes any previous tinting from icons and pixmaps and applies the new custom tree view tint
- **Fixed**: Sometimes Particle Effects crashed the Editor while closing
- **Fixed**: Curve Editor: It is not possible to multi-select keyframes with shift or Ctrl
- **Tweaked**: Use icons for camera speed. Pressing them will also bring up the Speed Slider
- **Tweaked**: Naming of Camera Object in Camera Menu - from "Object" to "Camera Entity"

### Renderer

#### Renderer General

- **Fixed**: SVOGI crash in DX12
- **Fixed**: Wind areas interpolation (vegetation bending)
- **Fixed**: The Shadow Map for LightBeam is flipped
- **Fixed**: Crash when LightBeam shader is set to Light Entity
- **Fixed**: Crash in CRenderMesh::AddShadowPassMergedChunkIndicesAndVertices
- **Fixed**: Shader hash collision during offline shader cache generation
- **Fixed**: Improved quality of GI temporal filtering by using scene velocity vectors
- **Fixed**: LINUX: Shader error couldn't compile HW shader 'ShadowMaskGen@ReprojectShadowMap'

### Engine

#### Engine General

- **New**: Added LICENSE.md and README.md
- **New**: An assert message box no longer sends the ESYSTEM_EVENT_CHANGE_FOCUS but rather clears the input keys as originally intended
- **Fixed**: Workaround for Linux Level loading fail

#### WAF

**Fixed**: Relative path overrides

### 3D Engine

- **Fixed**: SVOGI analytical occluders prototype bug fixing and improvements
- **Fixed**: Missing shadow from merged grass
- **Fixed**: Hide/Unhide functionality of static meshes (when used with permanent RenderObjects)

### Particles

- **New**: Features without properties will display "No Properties" text

### Tools

- **Fixed:** Update Brofiler 1.1.2 to avoid false positive malware detection by some anti-virus scanners

### Action

#### Action General

- **Fixed**: Fixed client crash when connecting to servers that did not have an sv_pacifist CVar available

### Audio

#### Audio General

- **New**: Added PlayFile functionality to the FMOD impl
- **New**: Added parameter to the PlayFile method (allows specifying if the line is localized and which Audio Trigger should be used as a playback reference)
- **New**: Added PlayFile implementation for SDL_mixer
- **Refactored**: PlayFile now returns a boolean to indicate if a request was sent to the middleware
- **Optimized**: Have a central place to delete un-used AudioObjects instead of having separate checks in many places. As a side effect fixes a crash in FMOD when the AudioEventPool was of size 0
- **Optimized**: ResetAudioObject and ResetAudioEvent is called before Destroy is called on these objects
- **Optimized**: SDL_mixer now uses the new PlayFile parameters
- **Fixed**: No-uber configuration

#### DRS (Dynamic Response System)

- **New**: Every dialog line now has property "StandAloneFile" which can be used to directly reference voice-assets on the disc
- **Fixed**: Missing icons in Launcher version
- **Fixed**: Missing Icons in WebLauncher version

### AI System

- **Refactored**: GraphNodeManager::GetNode no longer returns a dummy node, but rather asserts that the desired node exists - thus gives the possibility to figure out what might be going wrong on the caller's side

### Game

- **Fixed**: Hardware mouse not respecting system cursor preference
- **Fixed**: Crash when using file dialogs using wildcard/all files filter
