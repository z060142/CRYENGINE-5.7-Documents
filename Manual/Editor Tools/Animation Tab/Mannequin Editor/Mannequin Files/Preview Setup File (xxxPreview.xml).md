# Preview Setup File (xxxPreview.xml)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308475
- Page ID: 23308475
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Files > Preview Setup File (xxxPreview.xml)
- Parent: Mannequin Files

## Content

### Description

The Mannequin Editor needs a *Mannequin Preview Setup* to configure itself. It is basically an XML file that tells the editor which [Controller Definition File (xxxControllerDefs.xml)](Controller%20Definition%20File%20(xxxControllerDefs.xml).md) to load and which characters and [Animation Database File (ADB)](Animation%20Database%20(ADB).md) files to use.

These preview setup files are only used by the editor, they are not used in the game. You can have as many of these setups as you want.

Do not confuse this file with the [sequences](Sequence%20File%20(xml).md) which you edit in the [Mannequin Previewer](../../Mannequin%20Editor.md#MannequinEditor-previewer).

### Loading a Preview Setup

To load a preview setup, use the "Load Preview Setup..." option in the Mannequin File Menu.

### Default Preview Setup

When you open the mannequin editor, it will try to load the default Mannequin Preview Setup file. You can change this default in the Mannequin Editor Preferences, which you can find under Edit -> Preferences in the main UI of the Editor..

### Creating a Preview Setup

To create a mannequin preview setup, you need to create the text file by hand. See the [FileFormat](Preview%20Setup%20File%20(xxxPreview.xml).md#PreviewSetupFile%28xxxPreview.xml)-FileFormat) section below for an example.

All Preview Setup files must be stored in the folder Animations/Mannequin/Preview/. They typically use a name ending with "Preview.xml", but this is not required.

### Editing a Preview Setup

To edit a preview setup, you use the [Mannequin Context Editor](../Mannequin%20Context%20Editor.md).

### File Format

An example preview setup file looks like this:

```
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
```

The *controllerDef* defines which [Controller Definition File (xxxControllerDefs.xml)](Controller%20Definition%20File%20(xxxControllerDefs.xml).md) to use.

The *contexts* section defines how to fill the [Scope Contexts](../Mannequin%20Concepts/Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md) in the editor. You can use the [Mannequin Context Editor](../Mannequin%20Context%20Editor.md) to change this section.

The *history* section defines the default fragmentIDs to layer on in the [Mannequin Fragment Editor](../../Mannequin%20Editor.md#MannequinEditor-FragmentEditor). This is useful for example when editing fragments playing on secondary scopes that rely on another fragment playing on the first scope; you can define which fragments to sequence on the first scope here. It uses the same format as the [Sequence File (xml)](Sequence%20File%20(xml).md).
