# FMOD & Time of Day

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964951
- Page ID: 44964951
- Breadcrumb: Audio > Audio Middleware > FMOD Studio Workflow > FMOD & Time of Day
- Parent: FMOD Studio Workflow

## Content

##
Overview

This tutorial explains on how to create a day and night cycle using FMOD Studio and CRYENGINE.

##
Setting up Time of Day in FMOD Studio and CRYENGINE

CRYENGINE automatically sends the
*
 Time of Day
*
 value (in 24hr format) to the audio system. However, in order for CRYENGINE to receive it a corresponding audio system RTPC has to be created in the Audio Controls Editor. Furthermore, this audio system RTPC must be named as
time_of_day
and needs to be connected to an FMOD Studio parameter.

##
Setting up the Time of Day in FMOD Studio

To setup the Time of Day in FMOD Studio, add a parameter called
time_of_day
to the sound event that should be affected by the time. The range should be 0 to 24 so that it matches the same range as the Time of Day inside CRYENGINE.

[Image: /docs/static/attachments/44968260]

##
Connecting the Time of Day in FMOD Studio and CRYENGINE

With the parameter created, you can now open the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481](
Audio Controls Editor
)
 in CRYENGINE and connect the FMOD Studio Control with an audio system Control.

[Image: /docs/static/attachments/44968261]

##
Create a Dynamic Ambience in FMOD Studio

Now, you need to create a setup in FMOD Studio that makes use of the newly connected
time_of_day
 parameter.

The image below shows an example setup where the birds and insects are audible only during the day using volume automation.

[Image: /docs/static/attachments/44968262]

After you have successfully created your Ambient setup in FMOD Studio make sure to regenerate your Soundbanks as explained
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964944](
here
)
.

[#setting-up-time-of-day-in-fmod-studio-and-cryengine](
Setting up Time of Day in FMOD Studio and CRYENGINE
)
[#setting-up-the-time-of-day-in-fmod-studio](
Setting up the Time of Day in FMOD Studio
)
[#connecting-the-time-of-day-in-fmod-studio-and-cryengine](
Connecting the Time of Day in FMOD Studio and CRYENGINE
)
[#create-a-dynamic-ambience-in-fmod-studio](
Create a Dynamic Ambience in FMOD Studio
)
