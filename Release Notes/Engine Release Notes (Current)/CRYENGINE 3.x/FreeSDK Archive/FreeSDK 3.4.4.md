# FreeSDK 3.4.4

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963029
- Page ID: 44963029
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > FreeSDK Archive > FreeSDK 3.4.4
- Parent: FreeSDK Archive

## Content

### CryENGINE 3 Free SDK – Build 6289 Changelog

Released February 1st, 2013

**Fixed**

- PlayerRotation WriteLockCond
- Selecting objects behind a frozen Group is buggy
- Fixed crash when HMMWV blows up
- Problem with cylinder-box unprojection with certain alignments
- Fixed particles orientation
- Potential crash if SmartObjectManager is already deleted (VehicleSeatActionWeapons)
- Misc fixes: printf errors, divide by 0
- Fixed bitmask overflows
- Fixed Save Game Warning
- CryLight skin: Menu check marks do not show
- Crash on levelreload if Model3DHud was still active
- UI: Don't block input if element is fading
- Fixed crash on exit by preventing duplicate D3DSurface frees. Fixed a couple of other on-exit errors
- Incorrect lod choosing for multi-mesh static objects
- Fixed and greatly improved particle target motion: no longer applies velocity twice; target orbit fraction computed from particle start age; radial motion properly separated from orbital motion; faster average radius for angular velocity computation
- MaxCryExport: disabling skin/skel extensions, integrated solution configurations for Max2013
- ShapeDeformations not existing were causing a crash on loading an object with morphs
- Always reset empty and alloc chunks if we remove the last one in FixedAllocator
- Fixed invalid packet structure when there are no joints
- Fixed bug with Material Editor and TOD dialog being resizable to almost nothing, minimum now 400x300
- Fixed physics debug draw checkbox in rendering panel not enabling
- EntityObject now sets correct world-space SRendParams.fDistance (using BB radius for size)
- Qhull 64bit issue
- Decals on characters (changed decal bbox debug color to red, proper decal spawning on skinned attachments, cleaned up CreateDecalsOnInstance code)
- Box-cylinder unprojection issue
- Much better precision on MoveRelative feature, prevents particle drift
- Force state change to FallAndPlay when an actor falls
- Dedicated Server support for custom GameDLL names (would crash otherwise)
- Adding entityClass name to the NavigationAreaObject (It also appears as type in the list of the objets available in the level)
- Fixed Normalize-0 error for vertical camera angles
- If gamerules don't exist default to DeathMatch
- Wrong cloning of LogicOnce nodes
- Fixed rocketlauncher not spawning impact decal material. Commented out decal/pfx code in ammo scripts
- The sphere physics primitive is now correctly voxelized. Added support for the capsule voxelization
- Wrong deallocation if it is the last chunk in FixedAllocator
- BST Editor wouldn't reload properly due to missing registration
- Potential crash if the SmartObjectManager doesn't exist anymore (VehicleDamageBehaviorBurn)
- Wrong use of decal texture on Mine Entity (deprecated feature)
- Cylinder-cylinder contact normal issue
- Wrongly setting entity slot when setting the particle emitter (breaks spawning at random render geometry locations if particle emitter is not linked to another entity)
- Pain sounds not working with new localization system
- Cheat protected sound CVars error
- Don't fill UI stack on disabled and invalid UI actions
- Sanity check in UIActions

**Optimization**

- Particle stats gathering optimisation and consolidation, 200 lines less code. No longer allocate stats in CParticleEffect; collect dynamically in map
- Removed some obsolete negative-age particle code
- Brush object no collision switching
- Accurate frustum culling for particles, 60% more particles culled than cone culling, approx same speed
- Change the default Editor helpers icon size from 1 -> 0.5
- Removed complex XML cache in CParticleEffect; now load all effects in lib, and delete unused on level start, saves even more memory
- Small buoyancy tweaks for rigid entities

**Tweak**

- Disabled force feedback in system.cfg, not needed during development
- Removed wrong assert in CreateSound
- Refactored stereoscopic window to fit properly in the rollupbar
- Increased default min fall angle to 70 degrees
- Removed disabling of geometry instancing in system cfg
- Added warning for levels with spaces in name. Added warning for heightmaps larger than 4096. Fixed fault with tools configuration dialog cutting off text
- Default LAN port is now 64090
- Move change texture sector resolution button from Terrain texture painter to Import/Export terrain texture dialog
- Lowered min aniso filter to 4, added min aniso 8 to sys_spec 4, added max aniso 16 to all spec
- Updated Splashscreen
- Unique names for prefabs based on the library name and not the typename only
- Tweaked Texture Generation Tool to give cleaner, less cluttered interface. High quality checked by default

**New Feature**

- Glowpass: Add Tessellation support
- Added option to render params FG that entities in slot 0 can be rendered nearest
- Deferred snow entity (with deferred snow blending and snow fall effects)
- Added menu entry to character editor for reloading the animation list manually if desired
- Vehicles now respond to friction of surface
- Persistent debug draw of OBB's and AABB's
- Added particle fill stat and sort mode to PerfHud ParticleWidget
- Added plane restrictions to character ropes
- Bending support for entities and brushes
- Define lobby port from command line for multiple server instances
- New snowfall texture sheet for snow entities and falling snow
- Ropes aren't assigned to a category
- Material Editor: Reset material to read-only defaults
- Refactored and generalised particle emission offsets, replacing PosRandomOffset scalar with Roundness fraction. Can now spawn in line, rect, box, ellipse, capsule, ellipsoid shapes
- Added bEmitOffsetDir option
- Mousewheel supported for scaleform
- Added flownode to launch projectiles in the world
- Changed flownode to check for whitespaces
- Screen-space displacement for snow + sprite/particle based snow fall
- Added the new sdk_player to the lua to use him as a player chr.
- Added RainDropSpeed variable and fucntion to rain entity and exposed said function to flow graph
