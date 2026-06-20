# Texture Localization

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535435
- Page ID: 25535435
- Breadcrumb: User Interface (HUD/Menu) > UI Overview > Texture Localization
- Parent: UI Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934090)

##
Overview

##
Sections

CRYENGINE handles localization by using separate folders for each language, each of which has the exact same structure. The game automatically chooses the folder and textures based on the language setting in the configuration.

[Sections](#sections)
[General Setup](#general-setup)
[Test Localization Settings](#test-localization-settings)

##
General Setup

-
Identify the textures that need to be translated and localized.

-
Copy all textures to be localized into an appropriate file structure within the
`
<root>\Localization
`
folder. i.e;
`
<root>\Localization\Textures
`
 or in case you need to localize a lot of textures, mimic the same structure they were in before. i.e;
`
<root>\Localization\Objects\Library\Props\sign
`
. This folder is used for the default language.

-
Copy this folder structure with all included textures to the other languages folders your game will support. They should be located outside the normal Game folder and included only during a build procedure via a build script.

-
Update the material files of the objects that use the localized textures by changing the texture path to the location in the
`
<root>\Localization
`
folder.

-
Remove the original files from the
`
\Game
`
 sub-folders (only needed if you decide to localize textures after creating the asset).

-
Create .psd Files with separate layers, containing the text in the localized versions, and update the .tif files in the separate folders accordingly.

-
Test localization from within the game.

##
Test Localization Settings

In order to test localized versions of the game, you need to update the system.cfg within the root folder of your build. You also need to copy the localized .pak into the appropriate location.

-
Copy additional language .paks from your special PAK folder (the location depends on the build process) into the local
`
<root>\Localization
`
folder. By default there should be an English.pak already.

-
add
g_language="english"
 to the system.cfg - replace "English" with the name of the localized .pak file, i.e; "Turkish" for using the turkish.pak file.
