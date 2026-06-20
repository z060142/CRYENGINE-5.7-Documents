# CRYENGINE 5.6.1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44969342
- Page ID: 44969342
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.6 > CRYENGINE 5.6.1
- Parent: CRYENGINE 5.6

## Content

Known Issues
**
Compilation Errors with GitHub Source
**

Currently, by default, the option "
*
Schematyc
*
" is checked in the CMake GUI when generating the engine solution. This option should be unchecked for successful compilation.

PakTools currently cannot be compiled without modifications to the source code.

##
AI

-
**
Fixed:
**
 Crash when changing the faction of an AI while Physics/AI is enabled. (CryAISystem.dllehaviorTree::Shoot::OnTerminate).

##
Audio

-
**
Tweaked:
**
 Updated to Wwise SDK v2019.1.3.

##
Core/System

-
**
New:
**
 (Console) Allow commands from console batch files to run through the exec command.

-
**
New:
**
 (Console) Warning about config entries that cannot be resolved and commands in config files.

-
**
New:
**
 Added qpOASES SDK version 3.0 and Detours SDK version 4.0.1.

-
**
New:
**
(Asserts) Added CVar sys_assert_dialogues.

-
**
Fixed:
**
VS2019 not showing as an option when generating the Engine solution via the cryengine.cryengine file.

-
**
 Fixed:
**
 ThreadSafePushContainer could over commit on its virtual memory.

-
**
Refactored:
**
 (Asserts) Change sys_asserts and sys_log_asserts back to being CVars.

-
**
Refactored:
**
 (Asserts) 'Ignore all' setting for asserts removed (in favor of 'Disable Asserts' to avoid ambiguities).

-
**
Tweaked:
**
 Changed ThreadSafePushContainer iterator to forward only.

-
**
Tweaked:
**
 Changed ThreadSafePushContainer's maximum capacity to a soft limit.

##
CMake/Build

-
**
New:
**
 Added project command to root CMakeLists.txt.

-
**
Fixed:
**
 Error if Xbox One XDK environment variable doesn't exist.

-
**
Fixed:
**
 (PS4) Adjusted platform name to not all be uppercase.

-
**
Refactored:
**
 Fixing CMake setup behavior.

-
**
Tweaked:
**
 Print out compiler location during the Xbox One configuration step.

-
**
Tweaked:
**
 Minor cleanup of the Xbox One toolchain file.

-
**
Tweaked:
**
 Minor cleanup in the Xbox One Ninja toolchain file.

-
**
Tweaked:
**
 Resource Compiler option is now enabled by default (in the CMake options) when
generating
 the Engine solution.

##
Entity System

-
**
Fixed:
**
 Position, Rotation and Scale cannot be undone or redone when using components in an Empty Entity.

##
Graphics and Rendering

-
**
Fixed:
**
 Increased light radius threshold for tiled light volume check (if we are inside the volume).

-
**
Fixed:
**
 EndFrame without BeginFrame assert edge cases.

-
**
Fixed:
**
 Freeze when changing pipeline after cubemap generation.

-
**
Fixed:
**
(Shaders) Added area light contribution to multi-layered materials.

-
**
Fixed:
**
(Shaders) Eye shader appearing black under some light conditions.

-
**
Fixed:
**
 Permanent render object invalidation in RenderSectorUpdate_Finish.

##
Particles

-
**
Fixed:
**
 GPU static bounds now updated on emitter movement or state change. Added CBoundsMerger static bounds list manager.

-
**
Fixed:
**
Crash in GPU particles when spawn count = 0.

##
Project System

-
**
Fixed:
**
 Reversion of previous submissions that check for special characters in the Engine path when generating project solutions.

##
Sandbox

-
**
Fixed:
**
 (UV) Flipping Designer Objects UV islands crashes the Editor. CryDesigner.dll!Designer::UVMapping::UVMappingEditor::SetTool.

-
**
Fixed:
**
 Issue where notifications were not rendered when drawn on top of the Viewport and MFC tools. Also fixed an issue with notifications not spawning in the right place when the window was not maximized.

-
**
Fixed:
**
 (Designer) Freeze - Sphere subdivision count is choppy, causes crashes, triggers assert and doesn't render the whole sphere if a high subdiv amount is entered.

-
**
Fixed:
**
 Adjusted the broadness of a column in material settings (will also affect the headlines in the material's properties).

-
**
Fixed:
**
 Opening a new Editor instance with the CryEngine Exporter and the Create Material Tool eliminates layout.

-
**
Fixed:
**
 (Python Scripts) Additional columns appear after using the search field.

-
**
Fixed:
**
 Aligning the Height Map to a road when the MPU of a level is below 1 does not create a smooth fall-off.

-
**
Fixed:
**
 Clicking the 'Edit Outputs' button will open a black Editor window.

-
**
Fixed:
**
 The Asset Browser's hamburger menu -> Edit -> "Rename" option doesn't work.

-
**
Fixed:
**
 Paste allows to copy to read-only folders - which ultimately fails.

-
**
Fixed:
**
LOD Generator should not be enabled in release.

##
VR

-
**
Fixed:
**
 Late camera injection race condition.
