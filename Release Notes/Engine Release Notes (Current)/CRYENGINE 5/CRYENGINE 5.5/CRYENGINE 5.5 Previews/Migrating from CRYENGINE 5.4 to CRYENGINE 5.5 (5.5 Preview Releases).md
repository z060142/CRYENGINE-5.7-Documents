# Migrating from CRYENGINE 5.4 to CRYENGINE 5.5 (5.5 Preview Releases)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962795
- Page ID: 44962795
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.5 > CRYENGINE 5.5 Previews > Migrating from CRYENGINE 5.4 to CRYENGINE 5.5 (5.5 Preview Releases)
- Parent: CRYENGINE 5.5 Previews

## Content

##
Migration Notes CRYENGINE 5.4 to CRYENGINE 5.5

##
Creating a Backup of Your Project

When upgrading your project from CRYENGINE 5.4 to 5.5, it is a good idea to make a backup of your project.

If you use the Launcher to access your project, you will be prompted automatically.

If not backing up through the Launcher, then follow steps below:

-
Right click your .cryproject file

-
Choose
**
Backup project
**

-
Choose a backup location (if you want this to be different than the default)

-
Click
**
Confirm
**

##
Upgrading a Template Project (Assets only)

-
Create a new project, using the same template you used before.

-
Delete the new template projects'
**
Assets
**
directory.

-
Copy your
**
Assets
**
directory and your
**
Game.cryproject
**
 file to the new template project folder.

-
Right-click on your
**
Game.cryproject
**
 file and select
**
Change Engine Version
**
 and choose
**
CRYENGINE 5.5
**
.
**

**

-
Start the Sandbox Editor with the new template project and follow any prompts to upgrade your level files to the new format.

##
Upgrading a Template Project (Assets and Game Code)

**
Updating your game code is only necessary if you have made edits to the source code of your game. In this case, you should refer your assigned programmer to the
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962794](
Important CRYENGINE 5.5 Data and Code Changes (5.5 Preview Releases)
)
.
**

-
Right-click your
**
Game.cryproject
**
 file and select
**
Switch engine version
**
 and choose
**
CRYENGINE 5.5
**
.

-
Then regenerate your source code solution files by right-clicking
**
Game.cryproject
**
 and choosing
**
Generate Solution
**
.
You should now be able to follow the interface changes guide mentioned above to make edits to your source code and rebuild your project file.

##
Upgrading the GameSDK Project (Assets only)

-
Right-click your
**
GameSDK.cryproject
**
 file and select
**
Switch engine version
**
 and choose
**
CRYENGINE 5.5
**
.

-
Update/Verify your
**
GameSDK Sample Project
**
 asset via the Launcher.

-
Copy the
**
bin/win_x64/GameSDK.dll
**
 file from the Launcher project to your own project into the respective directory.

-
Start the Sandbox Editor with the new template project and follow any prompts to upgrade your level files to the new format.

##
Upgrading the GameSDK project (Assets and Game Code)

**
Updating your game code is only necessary if you have made edits to the source code of your game. In this case, you should refer your assigned programmer to the
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962794](
Important CRYENGINE 5.5 Data and Code Changes (5.5 Preview Releases)
)
. Since the GameSDK code is only contained within the Engine source code, building the Engine is outside the scope of this guide, but details can be found on our documentation pages
[/docs](
here
)
.
**

-
Right-click your
**
GameSDK.cryproject
**
 file and select
**
Switch engine version
**
 and choose
**
CRYENGINE 5.5
**
.

-
Rebuild the GameSDK project making changes in accordance with the above documentation and copy the new
**
GameSDK.dll
**
 to your project.

-
Start the Sandbox Editor with the new template project and follow any prompts to upgrade your level files to the new format.

##
Migrating Your Audio Controls Editor (ACE) Files

From release 5.5 onwards, ACE files will be saved in their middleware specific folder, so each middleware implementation is completely separated from each other.

-
Create a folder called "assets" inside the current
`
audio/<middleware>
`
 folder.

-
Move all soundbanks and audio files from the middleware folder to the new "assets" subfolder. For instance:

-
`
audio/wwise
`
 to
`
audio/wwise/assets
`

-
`
audio/fmod
`
 to
`
audio/fmod/assets
`

-
`
audio/sdlmixer
`
 to
`
audio/sdlmixer/assets
`

-
Backup all *.xml files in the
`
audio/ace
`
 folder.

-
Remove the write protection on all .xml files inside the
`
audio/ace
`
 folder.

-
Remove all .xml files from .pak files (usually inside the audio.pak).

-
Launch the Sandbox Editor and open the
**
Audio Controls Editor
**
 from the
**
Tools
**
menu.

-
All audio libraries should now be marked as modified. Click the
**
Save All
**
button inside the
**
Audio Controls Editor
**
.

-
If the project contains preload requests, a dialog will appear that asks for reloading the audio system. Click
**
Yes
**
.
