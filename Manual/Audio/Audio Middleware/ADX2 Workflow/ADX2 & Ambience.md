# ADX2 & Ambience

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966369
- Page ID: 44966369
- Breadcrumb: Audio > Audio Middleware > ADX2 Workflow > ADX2 & Ambience
- Parent: ADX2 Workflow

## Content

##
Overview

The following explains how to set up Ambient sounds in CRYENGINE using ADX2.

##
Setting up Ambient Sounds in ADX2 and CRYENGINE

##
Setting up Ambient Sounds in ADX2

In CRYENGINE, the Audio Area Entity and Audio Area Ambience Entities can be used to set up ambient sounds in a level. These Entities need to be attached to an Area Shape which defines the region within which the sound is played. Since the Audio Area Entity and Audio Area Ambience Entities don't use ADX2's standard attenuation, their setup in Atom Craft differs from that of an Audio Trigger Spot.

##
Setting up a Basic Ambient Sound Object

First, import a
**
.wav
**
file containing your ambient sounds into Atom Craft's Material Tree. With this audio material file selected in the Material Tree, set the
**
Override loop information Flag
**
 property to
**
True
**
 to ensure that it loops.

Create a new Cue and drag/drop the audio material file on to a new track of the Cue.

![Image](https://www.cryengine.com/docs/static/attachments/44967817)

*
Cue tracks
*

Next, create a new AISAC control by right-clicking the
**
AISAC-Controls
**
 folder within the Project Tree and selecting the
**
New Object → Create AISAC Control
**
option from the context menu; name it
*
area_fade_distance.
*
This parameter will later attenuate the volume of the ambience as the listener moves away from the Shape that the Audio Area Ambience/Audio Area Entity is linked to.

Go back to the Cuesheet and right-click the Cue you created earlier for the ambience. Select the
**
New Object → Create AISAC...
**
 option. This opens the
**
Add AISAC
**
 window that lets you specify the details of the new AISAC, as shown in the image below.

![Image](https://www.cryengine.com/docs/static/attachments/44966409)

*
Add Aisac
*

Make sure to set the
**
AISAC Control
**
 field to
**
area_fade_distance,
**
and the
**
AISAC Graph Type
**
 to
**
Volume.
**
Click the
**
Add
**
 button when finished.

Since the sound of the ambience should be inaudible when the AISAC Control's value is 0, create a graph for the AISAC in the AISAC window similar to the one shown in the picture below. The AISAC window can be opened by clicking the
**
AISAC
**
 button at the bottom of the Atom Craft main window.

![Image](https://www.cryengine.com/docs/static/attachments/44966412)

*
AISAC graph
*

Add the newly created
**
 AISAC Control
**
to the ACE so that its value can later be altered by Entities in CRYENGINE. You can now build the CueSheet Binaries that contain the ambience Cue.

For more information on setting up and using your created ADX2 ambience Cue inside CRYENGINE, please refer to the
[Audio & Ambience](../../Audio%20Overview/Audio%20%26%20Ambience.md)
 documentation.
