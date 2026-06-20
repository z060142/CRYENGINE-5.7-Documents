# Preview Setup File (xxxPreview.xml)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308475
- Page ID: 23308475
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Files > Preview Setup File (xxxPreview.xml)
- Parent: Mannequin Files

## Content

##
Description

The Mannequin Editor needs a
*
Mannequin Preview Setup
*
 to configure itself. It is basically an XML file that tells
the editor which
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File (xxxControllerDefs.xml)
)
 to load and which characters and
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798743](
Animation Database File (ADB)
)
 files to use.

These preview setup files are only used by the editor, they are not used in the game. You can have as many of these setups as you want.

Do not confuse this file with the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308476](
sequences
)
 which you edit in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-previewer](
Mannequin Previewer
)
.

##
Loading a Preview Setup

To load a preview setup, use the "Load Preview Setup..." option in the Mannequin File Menu.

##
Default Preview Setup

When you open the mannequin editor, it will try to load the  default Mannequin Preview Setup file. You can change this default in the
Mannequin Editor Preferences, which you can find under Edit -> Preferences in the main UI of the Editor.
.

##
Creating a Preview Setup

To create a mannequin preview setup, you need to create the text file by hand
. See the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308475#PreviewSetupFile(xxxPreview.xml)-FileFormat](
FileFormat
)
 section below for an example.

All Preview Setup files must be stored in the folder Animations/Mannequin/Preview/.  They typically use a name ending with "Preview.xml", but this is not required.

##
Editing a Preview Setup

To edit a preview setup, you use the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308457](
Mannequin Context Editor
)
.

##
File Format

An example preview setup file looks like this:

```

`
<MannequinPreview>
 <controllerDef filename="Animations/Mannequin/ADB/playerControllerDefs.xml"/>
 <contexts>
  <contextData name="Player" enabled="1" database="Animations/Mannequin/ADB/playerAnims1P.adb" context="Char1P" model="objects/characters/human/sdk_player/sdk_player.cdf"/>
  <contextData name="PlayerSound" enabled="1" database="Animations/Mannequin/ADB/playerSounds.adb" context="Sound"/>
  <contextData name="Rifle" database="Animations/Mannequin/ADB/rifleWeaponAnims.adb" context="Weapon" tags="rifle" model="objects/weapons/rifle/rifle_fp.cdf" attachment="weapon"/>
  <contextData name="Pistol" database="Animations/Mannequin/ADB/pistolWeaponAnims.adb" context="Weapon" tags="pistol" model="objects/weapons/pistol/pistol_fp.cdf" attachment="weapon"/>
 </contexts>
 <History StartTime="0" EndTime="0">
  <FragmentID Time="0" FragmentID="idlePose"/>
 </History>
</MannequinPreview>
`

```

The
*
controllerDef
*
defines which
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File (xxxControllerDefs.xml)
)
 to use.

The
*
contexts
*
 section defines how to fill the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450870](
Scope Contexts
)
 in the editor. You can use the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308457](
Mannequin Context Editor
)
 to change this section.

The
*
history
*
 section defines the default fragmentIDs to layer on in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-FragmentEditor](
Mannequin Fragment Editor
)
. This is useful for example when editing fragments playing on secondary scopes that rely on another fragment playing on the first scope; you can define which fragments to sequence on the first scope here. It uses the same format as the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308476](
Sequence File (xml)
)
.
