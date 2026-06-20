# SDL Mixer & Localization

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964973
- Page ID: 44964973
- Breadcrumb: Audio > Audio Middleware > SDL Mixer Workflow > SDL Mixer & Localization
- Parent: SDL Mixer Workflow

## Content

##
Overview

CRYENGINE's SDL Mixer-based audio implementation provides a simple interface to import audio files in different languages through the use of its
[/docs/static/engines/cryengine-5/categories/23756816](/docs/static/engines/cryengine-5/categories/23756816)
[Audio Controls Editor](../../../Editor%20Tools/Audio%20Controls%20Editor.md)
 and command line editor,
[Console](../../../Editor%20Tools/Advanced%20Tab/Console.md)
.

While the ACE allows localized sound files to be imported from disk into a project's audio assets directory, the CVar
**
g_languageAudio
**
 helps specify the language a localized audio file corresponds to when imported into a project.

The CVar's default value is
**
English
**
, and it can accept any user-defined value corresponding to the language of localization, i.e.,
**
German
**
,
**
French
**
,
**
Finnish
**
 or such.

Switching between these values enables
 switching between the different language versions of localized audio files within the Editor, as explained on this page.

##
Importing Localized Audio Files

Audio files are imported into CRYENGINE's audio system using the Audio Controls Editor, which is accessed through the
**
Tools -> Audio Controls Editor
**
option of the Main Menu Bar.

In the Audio Controls Editor, clicking the
**
Import Files
**
button at the top of the Middleware Data panel opens the
**
Import Audio Files
**
 window, allowing users to locate and import audio files from disk.

Audio files can also be imported by dragging and dropping them into the Middleware Data panel from disk, or by right-clicking within the Middleware Data panel and selecting the
**
Import Files
**
 option.

![Image](https://www.cryengine.com/docs/static/attachments/44964977)

*
Import Files
*

File types supported by the
**
Import Files
**
option include MP3 Audio (
**
.mp3
**
), Ogg Vorbis (
**
.ogg
**
) and Microsoft Wave (
**
.wav
**
) only.

##
Specifying the Language of Imported Audio Files

Selecting the desired audio files from disk subsequently opens the Audio File Importer
**

**
window, with the option to specify if the imported files are localized or not.

Check the
**
Localized
**
box besides the
**
Target Folder
**
 field if the imported audio file is localized/available in other languages.

![Image](https://www.cryengine.com/docs/static/attachments/44964976)

*
Localized checkbox
*

Based on the language setting specified by the
**
g_languageAudio
**
CVar, the Audio File Importer attempts to save the imported file in the
*
localization
*
 directory of a project, under a folder of the same name as the CVar's value.

For example since the value of
**
g_languageAudio
**
has been set to
**
German
**
, the Audio File Importer attempts to save the imported
**
.wav
**
file under
*
localization/
German
/audio/sdlmixer/assets
*
within the project directory in the above image.

If a folder corresponding to the language value of the
**
g_languageAudio
**
 CVar doesn't exist, a new one will be created by the Audio File Importer.

In any case. the save destination of the imported audio files can be changed, or a new folder created by clicking the icon beside the
**
Target Folder
**
field. The
![Image](https://www.cryengine.com/docs/static/attachments/44964978)
 icon beside a folder's listing in the Middleware Data panel indicates that it contains localized files.

The imported file can then be linked to a new or previously created audio trigger through the Audio System Controls and Properties panels.

##
Connecting Imported Audio Files to an Audio Trigger

Once imported, an audio file can be linked to a previously created Audio Trigger in the Audio System Controls panel.

To connect an imported audio file to a previously created Audio Trigger, select the Trigger in the Audio System Controls panel, and then drag/drop the audio file from the Middleware Data panel into the Connections section of the Properties panel.

![Image](https://www.cryengine.com/docs/static/attachments/44964975)

*
Connections
*

Audio Triggers can then be associated to Audio Trigger Components, and to
[audio entities](/docs/static/engines/cryengine-5/categories/23756816)
 such as Audio Area Entity, Audio Area Random and Audio Trigger Spot within the Viewport.

##
Importing Different Language Versions of the Same Audio File

Once an audio file has been imported, its alternate language versions can be imported by changing the value of
**
g_languageAudio.
**

In the case of the example provided in the previous section, changing the value of
**
g_languageAudio
**
 from
**
German
**
to
**
English
**
 will cause the Import Audio Files window to attempt saving all subsequently imported files under
*
localization/
English
/audio/sdlmixer/assets
*
 within the project directory
*
 when the
*
**
Localized
**
box is checked.

Consequently, previously imported versions of the localized audio file in languages other than English will no longer be visible under the Middleware Data panel.

If the language of the audio file linked to a trigger doesn't correspond to the language value specified by
**
g_languageAudio
**
, a
![Image](https://www.cryengine.com/docs/static/attachments/44964980)
 icon beside the file's listing under the Connections section of the Properties panel will indicate that the linked audio file is no longer available.

![Image](https://www.cryengine.com/docs/static/attachments/52592755)

*
Unavailable audio file
*

Once imported, these alternate language versions of the same audio file can also be linked to triggers in the Audio Systems Control panel as explained above.

##
Switching Between Different Language Versions of an Audio File in the Viewport

When multiple language versions of the same audio file are connected to the same trigger, users can switch between the different languages within the Viewport by simply changing the value of the
**
g_languageAudio
**
CVar from the Console.

##
Use Case Example

Consider a German language audio file
*
GERMAN_dg_npc_generator_01.wav
*
(imported with
**
g_languageAudio=German
**
) and its English language version
*
ENGLISH_dg_npc_generator_01_001.wav
*
(imported with
**
g_languageAudio=English
**
), both of which are connected to an audio trigger
*
NPC_Trigger
*
.

When this
*
NPC_Trigger
*
is associated with an Audio Area Ambience or Audio Area Random audio entity that might be attached to an an
[Area Shape](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Shape.md)
 in the Viewport, users can specify which language of the
*
dg_npc_generator_01.wav
*
 audio file plays when a player walks into the Area Shape b
y changing the value of
**
g_languageAudio.
**

Setting
**
g_languageAudio
**
to
**
German
**
 via the Console, for instance, will cause only the
*
German_dg_npc_generator_01.wav
*
file to be triggered within the defined Area Shape.

[Importing Localized Audio Files](#importing-localized-audio-files)
[Connecting Imported Audio Files to an Audio Trigger](#connecting-imported-audio-files-to-an-audio-trigger)
[Importing Different Language Versions of the Same Audio File](#importing-different-language-versions-of-the-same-audio-file)
[Switching Between Different Language Versions of an Audio File in the Viewport](#switching-between-different-language-versions-of-an-audio-file-in-the-viewport)
[Use Case Example](#use-case-example)
