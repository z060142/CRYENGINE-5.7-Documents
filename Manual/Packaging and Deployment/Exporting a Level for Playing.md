# Exporting a Level for Playing

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535306
- Page ID: 25535306
- Breadcrumb: Packaging and Deployment > Exporting a Level for Playing
- Parent: Packaging and Deployment

## Content

##
Overview

In order to play a map in
[Game Executable Launcher](Game%20Executable%20Launcher.md)
 using the game launcher application, the level needs to be prepared by generating and exporting some data.

##
Exporting the Level to the Engine

On the
**
File
**
 menu, click
**
Export to engine
**
:

This will write the level data into the
`
level.pak
`
 file that is read by the engine in the pure game mode via the Launcher.

Evaluation SDK
For the Evaluation SDK, exported levels are encrypted for security reasons. In order for the Launcher to be able to read encrypted levels, it is necessary to provide the decryption key, which is shown by Sandbox after
*
"Export to engine"
*
 has been used. The key is copied into the clipboard and can easily be used. The Launcher application expects the decryption key in file system.cfg. To set the key, write following line into the file:

**
*
level_decryption_key = key
*
**

Where
**
*
key
*
**
 is to be replaced by the key in the clipboard.

Only the PC Launcher is able to read encrypted levels this way. On console, no encryption is necessary. Therefore, export levels for console specifically, by using menu option
*
"File / Export to engine for console"
*
. If you are moving along from an evaluation to a full license, levels which have been created in the evaluation phase cannot be read by the full license initially, as the full license cannot handle encrypted files. Therefore, if you want to transfer levels from evaluation to full license, please send those levels to Crytek, in order to have them decrypted.

##
Generating Navigation Areas and Cover Surfaces

-
In the menu, go to Game → AI → Regenerate Navigation -> Regenerate All Layers

-
Game -> AI -> Generate Cover Surfaces

This second step is only necessary if you have placed Cover Surface objects in your level.

##
Generating the Level Surface Texture

On the
**
File
**
 menu, click
**
Generate surface texture
**
:

This will write the painted ground textures to the
`
terraintexture.pak
`
 file.

For final quality, select the
**
16384 x 16384
**
 option, and also select the
**
High Quality
**
and
**
Calculate Terrain Sky Accessibility
**
 check boxes.

For testing, the default 4096 x 4096 will do.
