# ADX2 & Reverb

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44967871
- Page ID: 44967871
- Breadcrumb: Audio > Audio Middleware > ADX2 Workflow > ADX2 & Reverb
- Parent: ADX2 Workflow

## Content

##
Overview

The following describes how to set up reverbs in levels using ADX2.

Refer to
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964924](
Audio & Reverbs*
)
 for more information on audio Environments.

##
Setting up Reverbs in AtomCraft

Inside AtomCraft's
**
Project/Global
**
 tree, navigate to
**
Global Settings → DspBusSettings → DspBusSetting_0
**
and create a DSP Bus with a name of your choice.

Select the created DSP Bus and add a reverb effect to its
**
Effects
**
 section in the DSP Bus Setting Info. window by clicking the
[Image: /docs/static/attachments/44967880]
 icon and selecting
**
Atom Sound Renderer (ASR) → Reverb
**
. Similarly, click the
[Image: /docs/static/attachments/44967880]
 icon in the DSP Bus'
**
Sends
**
 section and add a
**
MasterOut.
**

[Image: /docs/static/attachments/44967876]

*
Reverb effect
*

*
[Image: /docs/static/attachments/44967877]
*

*
Master Out
*

The reverb values can then be tweaked to match your environment.

To control which Cue is affected by the reverb and to also allow fading of the reverb, a BusSend per reverb effect is required for each Cue. Therefore select the Cue, open the
**
FX1
**
 tab inside the
**
FX/AISAC
**
 window, and add a BusSend as shown in the image below.

[Image: /docs/static/attachments/44967884]

*
Adding a BusSend called 'ReverbChurch'
*

Once the DSP Bus is connected to an audio system Environment in the ACE, the reverb will automatically fade in based on the value of the
**
EnvironmentDistance
**
 property set for the Audio Area Entity or Audio Area Ambience Entity.

When using reverbs Audio Trigger Spots, make sure to activate the
**
Trigger Areas on Move
**
 property from the Properties panel.
