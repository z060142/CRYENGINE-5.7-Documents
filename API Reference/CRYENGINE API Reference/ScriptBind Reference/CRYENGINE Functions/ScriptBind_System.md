# ScriptBind_System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306605
- Page ID: 23306605
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CRYENGINE Functions > ScriptBind_System
- Parent: CRYENGINE Functions

## Content

### CreateDownload

```
System.CreateDownload()
```

### LoadFont

Loads a font.

```
System.LoadFont(pszName)
```

Parameter | Description
--- | ---
pszName | Font name.

### ExecuteCommand

Executes a command.

```
System.ExecuteCommand(szCmd)
```

Parameter | Description
--- | ---
szCmd | Command string.

### LogToConsole

Logs a message to the console.

```
System.LogToConsole(sText)
```

Parameter | Description
--- | ---
sText | Text to be logged.

### ClearConsole

Clears the console.

```
System.ClearConsole()
```

### Log

Logs a message.

```
System.Log(sText)
```

Parameter | Description
--- | ---
sText | Text to be logged.

### LogAlways

Logs important data that must be printed regardless verbosity.

```
System.LogAlways(sText)
```

Parameter | Description
--- | ---
sText | Text to be logged.

### Warning

Shows a message text with the warning severity.

```
System.Warning(sText)
```

Parameter | Description
--- | ---
sText | Text to be logged.

### Error

Shows a message text with the error severity.

```
System.Error(sText)
```

Parameter | Description
--- | ---
sText | Text to be logged.

### IsEditor

Checks if the system is the editor.

```
System.IsEditor()
```

### IsEditing

Checks if the system is in pure editor mode, i.e. not editor game mode.

```
System.IsEditing()
```

### GetCurrTime

Gets the current time.

```
System.GetCurrTime()
```

### GetCurrAsyncTime

Gets the current asynchronous time.

```
System.GetCurrAsyncTime()
```

### GetFrameTime

Gets the frame time.

```
System.GetFrameTime()
```

### GetLocalOSTime

Gets the local operating system time.

```
System.GetLocalOSTime()
```

### GetUserName

Gets the username on this machine.

```
System.GetUserName()
```

### ShowConsole

Shows/hides the console.

```
System.ShowConsole(nParam)
```

Parameter | Description
--- | ---
nParam | 1 to show the console, 0 to hide.

### CheckHeapValid

Checks the heap validity.

```
System.CheckHeapValid(name)
```

Parameter | Description
--- | ---
name | Name string.

### GetConfigSpec

Gets the config specification.

```
System.GetConfigSpec()
```

### IsMultiplayer

Checks if the game is multiplayer.

```
System.IsMultiplayer()
```

### GetEntity

Gets an entity from its ID.

```
System.GetEntity(entityId)
```

Parameter | Description
--- | ---
entityId | Entity identifier.

### GetEntityClass

Gets an entity class from its ID.

```
System.GetEntityClass(entityId)
```

Parameter | Description
--- | ---
entityId | Entity identifier.

### PrepareEntityFromPool

Prepares the given bookmarked entity from the pool, bringing it into existence.

```
System.PrepareEntityFromPool(entityId)
```

Parameter | Description
--- | ---
entityId | Entity identifier.
bPrepareNow | (optional) Specifies whether the pooled entity shall be prepared immediately rather than queuing a request in case there is a preparation already in progress.

### ReturnEntityToPool

```
System.ReturnEntityToPool(entityId)
```

**Returns:** the bookmarked entity to the pool, destroying it.
Parameter | Description
--- | ---
entityId | Entity identifier.

### ResetPoolEntity

Resets the entity's bookmarked, which frees memory.

```
System.ResetPoolEntity(entityId)
```

Parameter | Description
--- | ---
entityId | Entity identifier.

### GetEntities

Gets all the entities contained in the specific area of the level.

```
System.GetEntities(center, radius)
```

Parameter | Description
--- | ---
center | Center position vector for the area where to get entities.
radius | Radius of the area.

### GetEntitiesByClass

Gets all the entities of the specified class.

```
System.GetEntitiesByClass(EntityClass)
```

Parameter | Description
--- | ---
EntityClass | Entity class name.

### GetEntitiesInSphere

Gets all the entities contained into the specified sphere.

```
System.GetEntitiesInSphere( centre, radius )
```

Parameter | Description
--- | ---
centre | Centre position vector for the sphere where to look at entities.
radius | Radius of the sphere.

### GetEntitiesInSphereByClass

Gets all the entities contained into the specified sphere for the specific class name.

```
System.GetEntitiesInSphereByClass( centre, radius, EntityClass )
```

Parameter | Description
--- | ---
centre | Centre position vector for the sphere where to look at entities.
radius | Radius of the sphere.
EntityClass | Entity class name.

### GetPhysicalEntitiesInBox

Gets all the entities contained into the specified area.

```
System.GetPhysicalEntitiesInBox( centre, radius )
```

Parameter | Description
--- | ---
centre | Centre position vector for the area where to look at entities.
radius | Radius of the sphere.

### GetPhysicalEntitiesInBoxByClass

Gets all the entities contained into the specified area for the specific class name.

```
System.GetPhysicalEntitiesInBoxByClass( centre, radius, className )
```

Parameter | Description
--- | ---
centre | Centre position vector for the area where to look at entities.
radius | Radius of the sphere.
className | Entity class name.

### GetNearestEntityByClass

Gets the nearest entity with the specified class.

```
System.GetNearestEntityByClass( centre, radius, className )
```

Parameter | Description
--- | ---
centre | Centre position vector for the area where to look at entities.
radius | Radius of the sphere.
className | Entity class name.

### GetEntityByName

Retrieve entity table for the first entity with specified name. If multiple entities with same name exist, first one found is returned.

```
System.GetEntityByName( sEntityName )
```

Parameter | Description
--- | ---
sEntityName | Name of the entity to search.

### GetEntityIdByName

Retrieve entity Id for the first entity with specified name. If multiple entities with same name exist, first one found is returned.

```
System.GetEntityIdByName( sEntityName )
```

Parameter | Description
--- | ---
sEntityName | Name of the entity to search.

### DrawLabel

Draws a label with the specified parameter.

```
System.DrawLabel( vPos, fSize, text [, r [, g [, b [, alpha]]]] )
```

Parameter | Description
--- | ---
vPos | Position vector.
fSize | Size for the label.
text | Text of the label.
r | Red component for the label colour. Default is 1.
g | Green component for the label colour. Default is 1.
b | Blue component for the label colour. Default is 1.
alpha | Alpha component for the label colour. Default is 1.

### DeformTerrain

Deforms the terrain.

```
System.DeformTerrain()
```

### DeformTerrainUsingMat

Deforms the terrain using material.

```
System.DeformTerrainUsingMat()
```

### ApplyForceToEnvironment

Applies a force to the environment.

```
System.ApplyForceToEnvironment( pos, force, radius)
```

Parameter | Description
--- | ---
pos | Position of the force.
force | Strength of the force.
radius | Area where the force has effects.

### ScreenToTexture

```
System.ScreenToTexture()
```

### DrawTriStrip

Draws a triangle strip.

```
System.DrawTriStrip(handle, nMode, vtxs, r, g, b, alpha )
```

Parameter | Description
--- | ---
handle | .
nMode | .
vtx | .
r | Red component for the label color. Default is 1.
g | Green component for the label color. Default is 1.
b | Blue component for the label color. Default is 1.
alpha | Alpha component for the label color. Default is 1.

### DrawLine

Draws a line.

```
System.DrawLine( p1, p2, r, g, b, alpha )
```

Parameter | Description
--- | ---
p1 | Start position of the line.
p2 | End position of the line.
r | Red component for the label color. Default is 1.
g | Green component for the label color. Default is 1.
b | Blue component for the label color. Default is 1.
alpha | Alpha component for the label color. Default is 1.

### Draw2DLine

Draws a 2D line.

```
System.Draw2DLine(p1x, p1y, p2x, p2y, r, g, b, alpha )
```

Parameter | Description
--- | ---
p1x | X value of the start point of the line.
p1y | Y value of the start point of the line.
p2x | X value of the end point of the line.
p2y | Y value of the end point of the line.
r | Red component for the label color. Default is 1.
g | Green component for the label color. Default is 1.
b | Blue component for the label color. Default is 1.
alpha | Alpha component for the label color. Default is 1.

### DrawText

Draws text.

```
System.DrawText( x, y, text, font, size, p2y, r, g, b, alpha )
```

Parameter | Description
--- | ---
x | X position for the text.
y | Y position for the text.
text | Text to be displayed.
font | Font name.
size | Text size.
r | Red component for the label color. Default is 1.
g | Green component for the label color. Default is 1.
b | Blue component for the label color. Default is 1.
alpha | Alpha component for the label color. Default is 1.

### SetGammaDelta

Sets the gamma/delta value.

```
System.SetGammaDelta( fDelta )
```

Parameter | Description
--- | ---
fDelta | Delta value.

### SetPostProcessFxParam

Sets a post processing effect parameter value.

```
System.SetPostProcessFxParam( pszEffectParam, value )
```

Parameter | Description
--- | ---
pszEffectParam | Parameter for the post processing effect.
value | Value for the parameter.

### GetPostProcessFxParam

Gets a post processing effect parameter value.

```
System.GetPostProcessFxParam( pszEffectParam, value )
```

Parameter | Description
--- | ---
pszEffectParam | Parameter for the post processing effect.
value | Value for the parameter.

### SetScreenFx

Sets a post processing effect parameter value.

```
System.SetScreenFx( pszEffectParam, value )
```

Parameter | Description
--- | ---
pszEffectParam | Parameter for the post processing effect.
value | Value for the parameter.

### GetScreenFx

Gets a post processing effect parameter value.

```
System.GetScreenFx( pszEffectParam, value )
```

Parameter | Description
--- | ---
pszEffectParam | Parameter for the post processing effect.
value | Value for the parameter.

### SetCVar

Sets the value of a CVariable.

```
System.SetCVar( sCVarName, value )
```

Parameter | Description
--- | ---
sCVarName | Name of the variable.
value | Value of the variable.

### GetCVar

Gets the value of a CVariable.

```
System.GetCVar( sCVarName)
```

Parameter | Description
--- | ---
sCVarName | Name of the variable.

### AddCCommand

Adds a C command to the system.

```
System.AddCCommand( sCCommandName, sCommand, sHelp)
```

Parameter | Description
--- | ---
sCCommandName | C command name.
sCommand | Command string.
sHelp | Help for the command usage.

### SetScissor

Sets scissor info.

```
System.SetScissor( x, y, w, h )
```

Parameter | Description
--- | ---
x | X position.

### GetSystemMem

Gets the amount of the memory for the system.

```
System.GetSystemMem()
```

### IsPS20Supported

Checks if the PS20 is supported.

```
System.IsPS20Supported()
```

### IsHDRSupported

Checks if the HDR is supported.

```
System.IsHDRSupported()
```

### SetBudget

Sets system budget.

```
System.SetBudget(sysMemLimitInMB, videoMemLimitInMB, frameTimeLimitInMS, soundChannelsPlayingLimit, soundMemLimitInMB, numDrawCallsLimit )
```

Parameter | Description
--- | ---
sysMemLimitInMB | Limit of the system memory in MB.
videoMemLimitInMB | Limit of the video memory in MB.
frameTimeLimitInMS | Limit in the frame time in MS.
soundChannelsPlayingLimit | Limit of the sound channels playing.
soundMemLimitInMB | Limit of the sound memory in MB.
numDrawCallsLimit | Limit of the draw calls.

### SetVolumetricFogModifiers

Sets the volumetric fog modifiers.

```
System.SetVolumetricFogModifiers( gobalDensityModifier, atmosphereHeightModifier )
```

Parameter | Description
--- | ---
gobalDensityModifier | Modifier for the global density.
atmosphereHeightModifier | Modifier for the atmosphere height.

### SetWind

Sets the wind direction.

```
System.SetWind( vWind )
```

Parameter | Description
--- | ---
vWind | Wind direction.

### GetWind

Gets the wind direction.

```
System.SetWind()
```

### GetSurfaceTypeIdByName

Gets the surface type identifier by its name.

```
System.GetSurfaceTypeIdByName( surfaceName )
```

Parameter | Description
--- | ---
surfaceName | Surface name.

### GetSurfaceTypeNameById

Gets the surface type name by its identifier.

```
System.GetSurfaceTypeNameById( surfaceId )
```

Parameter | Description
--- | ---
surfaceId | Surface identifier.

### RemoveEntity

Removes the specified entity.

```
System.RemoveEntity( entityId )
```

Parameter | Description
--- | ---
entityId | Entity identifier.

### SpawnEntity

Spawns an entity.

```
System.SpawnEntity( params )
```

Parameter | Description
--- | ---
params | Entity parameters.

### ActivateLight

NOT SUPPORTED ANYMORE.

```
System.ActivateLight(name, activate)
```

### SetWaterVolumeOffset

SetWaterLevel is not supported by 3dengine for now.

```
System.SetWaterVolumeOffset()
```

### IsValidMapPos

Checks if the position is a valid map position.

```
System.IsValidMapPos( v )
```

Parameter | Description
--- | ---
v | Position vector.

### EnableMainView

Feature unimplemented.

```
System.EnableMainView()
```

### EnableOceanRendering

Enables/disables ocean rendering.

```
System.EnableOceanRendering()
```

Parameter | Description
--- | ---
bOcean | True to activate the ocean rendering, false to deactivate it.

### ScanDirectory

Scans a directory.

```
System.ScanDirectory( pszFolderName, nScanMode )
```

Parameter | Description
--- | ---
pszFolderName | Folder name.
nScanMode | Scan mode for the folder. Can be: SCANDIR_ALL SCANDIR_FILES SCANDIR_SUBDIRS

### DebugStats

```
System.DebugStats( cp )
```

### ViewDistanceSet

Sets the view distance.

```
System.ViewDistanceSet( fViewDist )
```

Parameter | Description
--- | ---
fViewDist | View distance.

### ViewDistanceGet

Gets the view distance.

```
System.ViewDistanceSet()
```

### GetOutdoorAmbientColor

Gets the outdoor ambient color.

```
System.GetOutdoorAmbientColor()
```

### SetOutdoorAmbientColor

Sets the outdoor ambient color.

```
System.GetOutdoorAmbientColor( v3Color )
```

Parameter | Description
--- | ---
v3Color | Outdoor ambient color value.

### GetTerrainElevation

Gets the terrain elevation of the specified position.

```
System.GetTerrainElevation( v3Pos )
```

Parameter | Description
--- | ---
v3Pos | Position of the terraint to be checked.

### ActivatePortal

Activates/deactivates a portal.

```
System.ActivatePortal( vPos, bActivate, nID )
```

Parameter | Description
--- | ---
vPos | Position vector.
bActivate | True to activate the portal, false to deactivate.
nID | Entity identifier.

### DumpMMStats

Dumps the MM statistics.

```
System.DumpMMStats()
```

### EnumAAFormats

Enumerates the AA formats.

```
System.EnumAAFormats( m_Width, m_Height, m_BPP )
```

### EnumDisplayFormats

Enumerates display formats.

```
System.EnumDisplayFormats()
```

### IsPointIndoors

Checks if a point is indoors.

```
System.IsPointIndoors( vPos )
```

Parameter | Description
--- | ---
vPos | Position vector.

### SetConsoleImage

Sets the console image.

```
System.SetConsoleImage( pszName, bRemoveCurrent )
```

Parameter | Description
--- | ---
pszName | Texture image.
bRemoveCurrent | True to remove the current image, false otherwise.

### ProjectToScreen

Projects to the screen (not guaranteed to work if used outside Renderer).

```
System.ProjectToScreen( vec )
```

Parameter | Description
--- | ---
vec | Position vector.

### EnableHeatVision

Is not supported anymore.

```
System.EnableHeatVision()
```

### ShowDebugger

Shows the debugger.

```
System.ShowDebugger()
```

### DumpMemStats

Dumps memory statistics.

```
System.DumpMemStats( bUseKB )
```

Parameter | Description
--- | ---
bUseKB | True to use KB, false otherwise.

### DumpMemoryCoverage

Dumps memory coverage.

```
System.DumpMemoryCoverage( bUseKB )
```

### ApplicationTest

Test the application with the specified parameters.

```
System.ApplicationTest( pszParam )
```

Parameter | Description
--- | ---
pszParam | Parameters.

### QuitInNSeconds

Quits the application in the specified number of seconds.

```
System.QuitInNSeconds( fInNSeconds )
```

Parameter | Description
--- | ---
fInNSeconds | Number of seconds before quitting.

### DumpWinHeaps

Dumps windows heaps.

```
System.DumpWinHeaps()
```

### Break

Breaks the application with a fatal error message.

```
System.Break()
```

### SetViewCameraFov

Sets the view camera fov.

```
System.SetViewCameraFov( fov )
```

### GetViewCameraFov

Gets the view camera fov.

```
System.GetViewCameraFov()
```

### IsPointVisible

Checks if the specified point is visible.

```
System.IsPointVisible( point )
```

Parameter | Description
--- | ---
point | Point vector.

### GetViewCameraPos

Gets the view camera position.

```
System.GetViewCameraPos()
```

### GetViewCameraDir

Gets the view camera direction.

```
System.GetViewCameraDir()
```

### GetViewCameraUpDir

Gets the view camera up-direction.

```
System.GetViewCameraUpDir()
```

### GetViewCameraAngles

Gets the view camera angles.

```
System.GetViewCameraAngles()
```

### RayWorldIntersection

Shots rays into the world.

```
System.RayWorldIntersection(vPos, vDir, nMaxHits, iEntTypes)
```

Parameter | Description
--- | ---
vPos | Position vector.
vDir | Direction vector.
nMaxHits | Maximum number of hits.
iEntTypes | .

### RayTraceCheck

```
System.RayTraceCheck(src, dst, skipId1, skipId2)
```

### BrowseURL

Browses a URL address.

```
System.BrowseURL(szURL)
```

Parameter | Description
--- | ---
szURL | URL string.

### IsDevModeEnable

Checks if game is running in dev mode (cheat mode) to check if we are allowed to enable certain scripts function facilities (god mode, fly mode etc.).

```
System.IsDevModeEnable()
```

### SaveConfiguration

Saves the configuration.

```
System.SaveConfiguration()
```

### Quit

Quits the program.

```
System.Quit()
```

### GetHDRDynamicMultiplier

Gets the HDR dynamic multiplier.

```
System.GetHDRDynamicMultiplier()
```

### SetHDRDynamicMultiplier

Sets the HDR dynamic multiplier.

```
System.SetHDRDynamicMultiplier( fMul )
```

Parameter | Description
--- | ---
fMul | Dynamic multiplier value.

### GetFrameID

Gets the frame identifier.

```
System.GetFrameID()
```

### ClearKeyState

Clear the key state.

```
System.ClearKeyState()
```

### SetSunColor

Set color of the sun, only relevant outdoors.

```
System.SetSunColor( vColor )
```

Parameter | Description
--- | ---
vColor | Sun Color as an {x,y,z} vector (x=r,y=g,z=b).

### GetSunColor

Retrieve color of the sun outdoors.

```
Vec3 System.GetSunColor()
```

**Returns:** Sun Color as an {x,y,z} vector (x=r,y=g,z=b).

### SetSkyColor

Set color of the sky (outdoors ambient color).

```
System.SetSkyColor( vColor )
```

Parameter | Description
--- | ---
vColor | Sky Color as an {x,y,z} vector (x=r,y=g,z=b).

### GetSkyColor

Retrieve color of the sky (outdoor ambient color).

```
Vec3 System.GetSkyColor()
```

**Returns:** Sky Color as an {x,y,z} vector (x=r,y=g,z=b).

### SetSkyHighlight

Set Sky highlighing parameters. Highligh Params Meaning <hruler /> size Sky highlight scale. color Sky highlight color. direction Direction of the sky highlight in world space. pod Position of the sky highlight in world space.

```
System.SetSkyHighlight( params )
```

Parameter | Description
--- | ---
params | Table with Sky highlighing parameters.

### GetSkyHighlight

Retrieves Sky highlighing parameters. see SetSkyHighlight for parameters description.

```
System.SetSkyHighlight( params )
```

### LoadLocalizationXml

Loads Excel exported xml file with text and dialog localization data.

```
System.LoadLocalizationXml( filename )
```
