# Wwise & Time of Day

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964992
- Page ID: 44964992
- Breadcrumb: Audio > Audio Middleware > Wwise Workflow > Wwise & Time of Day
- Parent: Wwise Workflow

## Content

![Image](https://www.cryengine.com/docs/static/attachments/44964993)

## Overview

## Sections

This article explains how to create a day and night cycle with Wwise and CRYENGINE. CRYENGINE automatically sends the*Time of Day* value (in 24hr format) to the audio system. However, in order for CRYENGINE to receive it, a corresponding audio system RTPC has to be created in the Audio Controls Editor. Furthermore, this RTPC must be named as time_of_day and needs to be connected to an Wwise Game Parameter.

![Image](https://www.cryengine.com/docs/static/attachments/44968373)

[Sections](#sections)[Setting up the Time of Day in Wwise](#setting-up-the-time-of-day-in-wwise)[Connecting the Time of Day in Wwise and CRYENGINE](#connecting-the-time-of-day-in-wwise-and-cryengine)[Creating a Dynamic Ambience in Wwise using the Blend Container](#creating-a-dynamic-ambience-in-wwise-using-the-blend-container)

### Setting up the Time of Day in Wwise

To setup the Time of Day in Wwise, open the Game Syncs tab in the Project Explorer, and then create a new game parameter called time_of_day in Wwise.

![Image](https://www.cryengine.com/docs/static/attachments/44968378)

Now, you must edit the Game Parameter properties in Wwise to ensure that it uses the same range as the Time of Day in CRYENGINE.

![Image](https://www.cryengine.com/docs/static/attachments/44968380)

#### Connecting the Time of Day in Wwise and CRYENGINE

With the Game Parameter created, you can now open the [Audio Controls Editor](../../../Editor%20Tools/Audio%20Controls%20Editor.md) in CRYENGINE and connect the Wwise Control with an audio system Control.

![Image](https://www.cryengine.com/docs/static/attachments/44968382)

#### Creating a Dynamic Ambience in Wwise using the Blend Container

You need to create a setup in Wwise that makes use of the newly connected time_of_day Game Parameter. You need to open Wwise and import your audio files into the Actor-Mixer Hierarchy, and then create a Blend Container and move your files to it.

![Image](https://www.cryengine.com/docs/static/attachments/44968391)

You need to press Shift key and select the sound objects, to enable the Create new Parent Blend Container button below the Audio tab.

To open the Blend Track Editor, right-click the Blend Container and select Edit, and then click the Blend Track's Edit button in its General Setting tab. You need to click the New Blend Track button in order to create a new Blend Track setup within the Blend Track Editor.

*![Image](https://www.cryengine.com/docs/static/attachments/44968393)*

You also need to enable the Crossfade checkbox and select the time_of_day Game Parameter on your newly created Blend Track.

![Image](https://www.cryengine.com/docs/static/attachments/44968397)

To setup your sound objects on the Blend Track, go to the Contents Editor and drag the objects into the Blend Track field based on the order on which they need to appear in the Blend Track (From left to right).

![Image](https://www.cryengine.com/docs/static/attachments/44968399)

Open the Blend Track Editor again and move your files accordingly. You can also setup Crossfades to have a smooth transition over time from your day to night ambience.

![Image](https://www.cryengine.com/docs/static/attachments/52592686)

After you have successfully created your Ambient setup in Wwise make sure to regenerate your SoundBanks in Wwise as explained [here](Wwise%20Initial%20Setup.md).
