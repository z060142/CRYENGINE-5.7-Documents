# FreeSDK 3.3.7

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963025
- Page ID: 44963025
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > FreeSDK Archive > FreeSDK 3.3.7
- Parent: FreeSDK Archive

## Content

### CryENGINE 3 Free SDK – Build 2572 Changelog

Released October 17th, 2011.

- Added ability to save levels to Projects for use with [CryDev Projects Database](http://www.crydev.net/project_db.php?action=teams)
- Added redundancy for logoff to prevent “Account Locked” errors
- Added more flexibility to login username/password allowed characters
- Added ability for any CryDev user to load any level within the Launcher
- Added support for building GameDLL using Visual C++ Express
- Added ability for player to switch seats in some vehicles
- Added Time:FrameDelay flownode to delay actions for just one frame
- Fixed several login and logoff crashes
- Fixed crash when creating new levels
- Fixed rare crash when deleting an Animation Graph Editor view, along with several other fixes and adjustments to Animation Graph Editor
- Fixed rare crash if sound system is disabled
- Fixed several warnings/issues specific to 64-bit
- Fixed issue relating to mouse and screen resolution in Launcher
- Fixed issue where AI wouldn’t enter vehicles
- Fixed issue with Material Editor jumping to different materials against users input
- Fixed issue with road tool not aligning correctly with edited terrain
- Fixed “Frozen” material layer
- Fixed HMMWV not loading in Vehicle Editor
- Fixed issue with water volume material not displaying water ripples
- Fixed a few misplaced objects in the Forest sample level
- Made several adjustments to particle system
- Made several fixes made to AI system
- Made several changes to weapon firemodes and other weapon tweaks
- Improved CryTif support (64-bit and newer versions of Photoshop)
- Adjustments made to Flowgraph editor
- Adjusted warning box on Sandbox startup related to NtfsDisableLastAccessUpdate error, users can now ignore this warning or have the registry adjusted to fix
- Fixed TimeofDayTrigger and looping ToD not working correctly
- Fix for 16-bit float image always generate DXT5 instead of DXT1
- Adjusted spawnpoint arrow/icon
- Fixed issue with overlapping water volumes
- Many fixes/improvements to Maya exporter
- Several updates to Abrams Tank & MH60 Blackhawk sample vehicles
- Adjusted motionBlur settings to provide nicer results
- Added several new asset additions to the Forest sample level, including things like water droplet sounds, sounds for falling debris, etc
- Made several beautification updates to Forest level including new textures, additional objects, new materials, etc
- Updated rock assets for improved collision
- Added rooster boid with animations
- Updated turtle boid animations
- Added LODs for several assets, chimneys, railroad tracks, drains, etc
- Improved several particle effects, including bullet/water impact
- Added 3ds Max files for railroad tracks
- Added new low detail texture for terrain
- Added several new destroyable props and replaced lamp post and power poles in Forest with destroyable versions
- Added new outdoor toilet asset for Forest
- Added pickup, pick and throw animations
- Made several adjustments to the Asset Browser
- Fixed: Potential crash if no filename is specified for a static vehicle part. Added proper warnings with references to the part and vehicle causing the problem
- Fixed crash on closing Vehicle Editor when the HMMWW is loaded
- Destroyable object pieces no longer always sink in water ("kwater" prop was applied even when unset)

### 3.3.6 Engine Build Changes

**Renderer and 3d Engine**

- Fix: Render error when using the check-box "Use Terrain Color" for vegetation
- Added: High resolution screenshot support
- Fix: Flickering shadows throughout level
- Fix: Issues with material reloading in engine
- Fix: ATI specific ocean surface aliasing artifact
- Fix: Water dripples
- Fix: Max particle pixel fill now clamped to proper screen size – moved m_Wdith / m_Height members to SParticleRenderContext.
- Fix: Small particle bug with animated textures
- Fix: Particle incorrect positioning with MoveRelEmitter on initial emission
- Fix: Particle sound durations: one-shots now always play to completion. Pulsed emitters don't kill sounds early
- Fix: Restored ability of invisible particles to spawn 2nd-gen visible particles, fixing semantics of IsActive.
- Fix: Simplified ParticleEmitter.GetMaterial, removed unneeded ParticleEffect.FirstActive.
- Fix: Allow serialization/pasting of particle effects without version number; pasting only renames effects with no previous name

**CryCommon**

- Fix: Potential crash with CryString.swap()

**CryPhysics**

- Fix: Scale on cloth entities
- Improve simulation parameters for the rope object
- Fix: Allow scale on ePT_Fixed constraints mode
- Fix: Issues with non-colliding (thickness 0) cloth
- Fix: Some issues with precomputed rope collider parts

**CrySoundSystem**

- Fix: Wrong position of the Sound Listener in the Sandbox Editor when not in-game
- Added: Additional information about which sound event was not found
- Removed obsolete CVars: pl_FootstepSoundsNormalized and pl_AnimationTriggeredFootstepSounds
- Fix: Not able to play sound events properly

**CryAISystem**

- Improved: car maneuvering
- Fix: Allow vehicles regenerate paths on the way
- Renamed CPipeUser::m_IsSteering to CPipeUser::IsSteeringAroundObstacle to prevent confusion when reverse-engineering vehicle maneuvering code
- Added: Possibility to switch AI Debug Renders at runtime
- Replaced: "typedef unsigned tNavCapMask;" with "typedef uint32 tNavCapMask;"
- Fix: Network AI Debug Draw: Switch from type size_t to uint32
- Fix: Network AI Debug Draw: Add support for big endian
- Fix: Don't use Network AI Debug Draw on Dedicated Servers in Release
- Fix: Comment out deprecated CScriptBind_AI::GetGroupTarget and CScriptBind_AI::GetGroupTargetCount
- Fix: Stop using unsupported goalop "usecover"
- Removed: Unused AI perception variables
- Fix: AI Actor should be handled as remote client
- Fix: AI vehicle turret guys not always shooting you after a cp load, due to their vehicle not being correctly ignored for their sight tests
- Fix: AI Debug Draw
- Fix: AI Debug Renderer not showing in the Editor before the game start
- Fix: Issue moving backwards in COPTrace::ExecuteManeuver
- Fix: After a checkpoint reload enemies would stop tracking their target much quicker than what they should
- Fix: An helicopter patrolling can have the improper AI
- Fix: PlayerSensor and WeaponSensor to work if input entity changes during runtime
- Fix: Crash in CTacticalPointSystem::BoolPropertyInternal
- Fix: Cover surface message error when the bai file is not present. It explicitly says the file should maybe be regenerated if needed.
- Fix: FlowNode to calculate screen position out of entity position
- Fix: Improve AI debug draw goal pipe display: now shows all active goal ops rather than just the last executed one each goal op can do custom text
- Fix: InsertSubPipe can re-execute completed GoalOp upon return
- Fix: ScriptBind Add constants "InsideRange" and "OutsideRange"
- Fix: Console spam CGoalPipe::PushGoal - Attempting to push goalop "usecover"
- Fix: Goalop COPWait
- Fix: Serialization of goalop "timeout"
- Fix: CGoalPipe::PeekPopGoalResult()
- Fix: Goalop Wait (even XML) should always be blocking and grouped
- Fix: Potential crash in DelayedPipeSelection::DelayedPipeSelection
- Fix: DelayedPipeSelection::DelayedPipeSelection

**Entity System**

- Improved: es_DrawProximityTriggers indicates enabled/disabled and entered/exited
- Fix: Entity:EntityInfo low-node can check if an entity is also an AI object
- Fix: Translucency problem with es_DrawProximityTriggers

**CryAction and GameDll**

- Fix: Weapon State driven serialization
- Improved: Some cosmetic changes about pAIVisualDebugRenderer in CCryAction::ConnectCmd and CCryAction::DisconnectCmd
- Fix: Improve FlowActorSensor Node
- Added: function to get ZoomModeName to IWeapon
- Added: UIManager (singleton access to all game code relevant UI classes)
- Fix: Change HUD UIAction to use FlowActorSensor node
- Fix: Change HUD to display proper death message (don't show in spectator mode)
- Added: Minimap Nodes to FlowMinimapNodes
- Added: OnZoomChanged callback to IWeaponListener
- Added: WeaponSensorNode
- Fix: AIActions also prompt if it has unsaved changes
- Added: Display of custom picture on level load
- Added: New flownode to help setting mc's in screen space (0-1)
- Fix: Disallow pause in MP
- Fix: UI FlowNodes to flush all events that are used in UIAction FlowGraphs that are on the event stack
- Fix: gfx_reload_all command
- Fix: AI Actors not using player prediction code
- Fix: Crash in FlowActorSensor Node
- Fix: FlowWeaponSensor Node to receive correct name for zoom mode
- Fix: Potential crash on opening a Flowgraph
- Fix: Unregister FlowWeaponSensor from IItemSystem on unload level
- Fix: UIActionEvents if no level xml exists
- Fix: Picking up breakage pieces
- Fix: Client can't reload in a MP session
- Fix: Wrong first person muzzle flash effect
- Fix: Unsafe way to flush UI events in FG
- Fix: LocalPlayer Node does not trigger output if local player id changes
- Fix: HUD UIAction for MP
- Fix: Client not visible on Server after first spawn
- Fix: Client health above 100 after first spawn
- Fix: Health value returned from FlowActorNode to be int rather then float
- Fix: Crash in CanPerformPickUp
- Fix: Network hot fixes
- Fix: Disable Layer activation in MP
- Fix: Call IGame:Shutdown even if "ExitOnQuit" is set to 1

**Scripts**

- Updated: DestroyableObject
- Added: DeadBody entity properties not available in Sandbox
- Fix: Foley and footstep system tweak
- Fix: Add character sounds to Grunt_x
- Improved: Weapons: Binoculars, RocketLauncher
- Updated: Game/Scripts/AI/Coordination/Coordination.lua
- Fix: Changes default model of Door entity to be a door rather than a sphere

**Sandbox Editor**

- Refactored: the file change notification system, now it also reports the change type and skips duplicate notifications
- Removed: "Browse for Layer Texture", it is no longer supported
- Fix: Change FileChangeMonitor to use 32bit tick count
- Fix: Add context menu to all objects in editor view-port. Following items are added: "Show in Asset Browser" and "Properties".
- Removed: Unused UI elements from asset browser
- Added: New system to handle files that are not linked to the level
- Improved: Solid system reliability by excluding invalid data before updating a rendering data
- Removed: 'Use Custom Terrain size' check-box from the "Create new level" dialog
- Removed: "X" button does not function correctly in the Asset Browser
- Fix: Several leak within the file change monitor, added also clear() to MTQueue
- Fix: resize of the PropertiesPanel
- Fix: Cloud sync in LiveCreate
- Fix: Console hot update for CGFs
- Fix: Crash when sandbox is open with material editor
- Fix: Invalidate a HyperGraphNode without changing the "modification" state
- Fix: Potential crash bug when updating solid brush
- Fix: Crash bug happening when hiding and undoing a solid box.
- Fix: Crash while setting material in Updating Mesh with Solids Editor
- Fix: MaterialEditor layout problem on SwitchingUI twice (The actual controls were destroyed but never recreated)
- Added: keyboard shortcuts for particle item Enable and Enable All
- Fix: Spline tool-tips now show values with 3 rather than 2 digits precision, accurate for 8-bit quantization
- Fix: Bug about surface type drop-down menu so as for the list to have all surface items in Particle Editor
- Fix: Saving library creates useless Libs/ folder in root dir

**3ds Max Exporter**

- Added: MaxScript interface to exporter log
- Fix: Overwrite message boxes disabled when called from MaxScript
- Fix: set_bone_list setting node list actually
- Fix: Crash after Reseting a scene
- Fix: Animation - Subrange window doesn't stay open when you move away from the utilities tab
- Fix: Animation - Subrange window being unable to be resized makes it difficult to work with large names
- Fix: CrySkin crashes max if copy/pasted to another object
- Fix: NamedRanges dialog not wrapped into CNamedRangesDialog
- Fix: Bone selection was always reset when you click on the bone in the bone list
- Fix: Some of the text labels in CrySkin were wrong because of the conflicting string resource identifiers. MaxCryExport resource IDs are bumped by 2000
