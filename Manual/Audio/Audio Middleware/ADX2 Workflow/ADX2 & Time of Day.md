# ADX2 & Time of Day

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966418
- Page ID: 44966418
- Breadcrumb: Audio > Audio Middleware > ADX2 Workflow > ADX2 & Time of Day
- Parent: ADX2 Workflow

## Content

## Overview

The following explains how to create a day and night cycle in CRYENGINE using ADX2.

### Setting up Time of Day in ADX2 and CRYENGINE

CRYENGINE automatically sends the Time of Day value (in 24H format) to the Audio System. However for ADX2 to receive a Time of Day value, a corresponding Parameter has to be created in the Audio Controls Editor and connected to an ADX2 AISAC Control. Name this audio system Parameter *time_of_day.*

#### Setting Up the Time of Day in CRI Atom Craft

Create a new AISAC Control called *time_of_day* in Atom Craft's Project Tree.

Assign this AISAC Control to an AISAC by right-clicking the Cue or track that might, for example, contain the day layer of an ambience;.

- Select the **New Object → Create AISAC...** option from the context menu.
- In the Add Aisac window, set **AISAC Control (ID: Name)** to * time_of_day* and **AISAC Graph Type** to **Volume***.*

The volume automation for this *time_of_day* AISAC could resemble the graph in the picture below.

![Image](https://www.cryengine.com/docs/static/attachments/44966423) *AISAC graph for time_of_day*

The curve type can be changed by right-clicking on a point in the AISAC window and selecting **Curve Type**. You can also listen to the resulting fade by moving the locator in the AISAC window from 0 to 1.

#### Connecting the Time of Day in ADX2 and CRYENGINE

With the *time_of_day* AISAC Control created and assigned to a Cue or track in ADX2, you can now open the ACE in CRYENGINE and connect the ADX2 AISAC Control with the *time_of_day* audio system Parameter created at the beginning of this page.

Since AISAC Controls only have a range between 0 and 1, the maximum value of the *time_of_day* Parameter (i.e. 24) in the ACE needs to be normalized. To do so after the *time_of_day* AISAC Control has been connected to the *time_of_day* Parameter in the ACE, activate the **Advanced** checkbox in the ACE's Properties panel and set the value of the ** Max Value** field to 24.

![Image](https://www.cryengine.com/docs/static/attachments/44966424) *Multiply*
