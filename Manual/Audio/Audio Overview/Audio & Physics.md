# Audio & Physics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964923
- Page ID: 44964923
- Breadcrumb: Audio > Audio Overview > Audio & Physics
- Parent: Audio Overview

## Content

##
Overview

In CRYENGINE the environment is very interactive - things move, collisions occur and things break. Furthermore, when two materials touch, a sound is often generated.

##
Sounds and Physics

The interaction between two materials is described in a file called
*
MaterialEffects.xml
*
 (located in
`
<
`
`
Game folder>\Assets\gamedata.pak, and w
`
ithin this *.pak file, in
`

`
`
Libs\MaterialEffects
`
). Opening this file with spreadsheet software will show a matrix, with surface types in the first column/row.

From this file the Engine looks up actions to be taken on any given interaction and each entry in the table contains text pointing to a description of the effect to be taken. The effects are described in the
*
FXLibs
*
 subfolder.

The example below shows how the description is composed for collisions.

Example: When an Entity with an assigned surface type of
*
mat_wood
*
 collides with the surface_type
*
mat_metal
*
the corresponding cell in the spreadsheet contains the text:
*
collisions:wood_metal.
*
This text indicates that the effect is called
*
wood_metal
*
- this is situated in the
`
FXLibs\collisions.xml
`
 file and the audio system Trigger to be played is described therein.

*
Pic2: Collisions.xml

*

##
Special Cases

##
Special Table Entries

In some cases the material of an object is not enough to describe its sound probabilities. For example, a barrel (made out of sheet metal) dropped to the ground sounds very different from a sheet metal roof being hit by something.

Therefore, the first column of the table described above may contain special names used by archetype classes.

The image below lists various names for the barrel object class and describes the different interaction sounds.

Destructibles also have a special mapping:

-
**
Breakage:Breakage
**
: When an object of said surface type breaks; can be a partial destruction.

-
**
Breakage:Destroy
**
: When an object of said surface type is completely destroyed.

-
**
Breakage:Joint_Break
**
: When the joint of an object breaks.

-
**
Breakage:Freeze_Vapor:
**
 Points to the sound made when frozen articles vanish upon destruction.

-
**
Breakage:Freeze_Shatter
**
: Points to the sound made when frozen articles shatter.

##
Bullet Impacts

A separate file called
`
FXLibs\projectiles.xml
`
 is used to reference bullet effects.

**
NOTE:
**
 A delay can be put into the effect so that the player can hear the sound of the bullet impacting even while still shooting. Also, a bullet hitting a special object, such as a barrel, will create a sound according to the object's assigned material (for example, sheet metal).

*
Delay in projectiles.xml

*

##
Bypassing the Table for Vegetation Objects

Entries in the
`
FXLibs\vegetation.xml
`
 file bypass the table in the
*
MaterialEffects.xml
*
 file and result in audio system Triggers based on the name of the vegetation.

##
Console Variables

-
**
mfx_Debug
**
: Turns on MaterialEffects debug messages (1=Collisions, 2=Breakage, 3=Both).

-
**
mfx_Enable
**
: Enables MaterialEffects.

-
**
mfx_EnableFGEffects
**
: Enables Flow Graph based MaterialEffects (Default: On).

-
**
mfx_ReloadFGEffects
**
: Reloads MaterialEffect's Flow Graphs.

-
**
mfx_Reload
**
: Reloads the MFX Spreadsheet.
[Sounds and Physics](#sounds-and-physics)
[Special Cases](#special-cases)
[Console Variables](#console-variables)
