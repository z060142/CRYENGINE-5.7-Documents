# ADX2 & Localization

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44967886
- Page ID: 44967886
- Breadcrumb: Audio > Audio Middleware > ADX2 Workflow > ADX2 & Localization
- Parent: ADX2 Workflow

## Content

##
Overview

The following explains how to set up localized CueSheet Binaries in ADX2 and CRYENGINE.

CRYENGINE loads localized CueSheet Binaries from your project's localization folder (where English CueSheet Binaries, for example, may be stored under
*
localization/english/audio/adx2
*
). This allows having multiple languages of audio completely separated from each other, making it easier to swap them out during runtime and to also distribute region-specific content.

##
Information About Localized Soundbanks

ADX2 builds localized CueSheet Binaries into a subfolder of the primary CueSheet Binary storage location (i.e.,
*
<ProjectFolder>/audio/adx2/assets
*
).

Since this sub-folder cannot be manually specified in AtomCraft, it is necessary to move the Binaries after they're generated. The CRYENGINE SDK contains post-process scripts that can be used to automate the process of moving CueSheet Binaries to the correct folder; these scripts have been attached below.

[crytek_audio_scripts.zip](/docs/static/attachments/44967888)

The above scripts only work when the ADX2 project is stored under the
*
audio/adx2_project
*
folder of your CRYENGINE project.  Otherwise, the scripts need to be edited to match the ADX2's true storage location.

Currently only English and German are supported by these scripts, but you can also easily add other languages to the
*
languages.txt
*
 file located in the
*
/audio/adx2_project/crytekscripts
*
 folder of your CRYENGINE project.

##
Setting Up Localized Soundbanks in ADX2

##
Executing Post-process Scripts in an AtomCraft Project

Copy the CRYENGINE SDK post-process scripts into the
*
/audio/adx2_project/crytekscripts
*
 folder of your AtomCraft project, and open the Build Atom CueSheet Binary window in AtomCraft.

-
Activate the
**
Setting Post Process
**
 option.

-
Set the
**
Execute Path
**
 field to
**
./crytekscripts/move_binaries_pc.bat.
**

-
Click the
**
Default Path
**
 button next to the
**
Output Path
**
 field to ensure that it is set to the default path; leave the
**
Output File Path
**
 and
**
Option
**
 fields empty. You can use the following picture for reference.
![Image](https://www.cryengine.com/docs/static/attachments/44967891)

*
Build Atom CueSheet Binary window
*

You could also enable the
**
Show Tool Window
**
 option to receive feedback when the batch file containing the post process scripts is executed.

Click the
**
Build
**
 button to build the CueSheet Binaries. This opens the Complete Building window which displays a list of successfully updated Binaries; the batch file is executed after clicking the
**
OK
**
 button in this window.

![Image](https://www.cryengine.com/docs/static/attachments/44967906)

*
Complete Building
*

The code lines for PC are part of the batch file attached above. Other platforms can be easily added by copying the script and adjusting its content.

This batch file not only moves the localized CueSheet Binaries to the correct folder path, but also moves the non-localized Binaries to their intended position within the CRYENGINE project.

It is important that the localization languages and their Reference/Output Folder names, as defined in the AtomCraft project, match the names in the
*
languages.txt
*
 file located in the
*
/audio/adx2_project/crytekscripts
*
 folder of your CRYENGINE project.
