# Measurement Reference - (DCC Unit Setup)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308289
- Page ID: 23308289
- Breadcrumb: Asset Prep (External) > Measurement Reference - (DCC Unit Setup)
- Parent: Asset Prep (External)

## Content

## Overview

The reference measurements referred to in this article were originally created for the game Crysis, however they are still relevant in regard to creating new assets.

### 3ds Max Unit Setup

1 meter = 1 Unit in CRYENGINE

The best way to work in 3ds Max is to set the unit to centimeters you can also adjust the grid and make it more readable while working on an Asset.

There is also a very useful way to get feedback directly from the Engine.

Simply set up a 1x1x1m Designer object and go to **Level -> Export Selected Objects**. Then in the ** Save As** dialog box, make sure to set the file type to ***.obj/*.fbx.**

Import this *.obj/*.fbx into the 3ds Max scene and use it as a size reference to configure the grid and unit scale. Adjust the grid accordingly to match your 1x1x1m cube. Re-export to test that the setting are correct.

#### Unit Setup

Inside 3ds Max, the unit setup can be found under the menu **Customize** **-> Units Setup**. Also don't forget to adjust the System Unit scale through the button at the top in the Units Setup window:

![Image](https://www.cryengine.com/docs/static/attachments/23996554) **![Image](https://www.cryengine.com/docs/static/attachments/25506757)**

What's important here is that you are using the **Metric system**!

#### Home Grid settings

Right-click the Snaps Toggle area under the menu bar and go to the 3rd **Home Grid** tab to adjust your grid size. The size and spacing of the grid that you're setting up is only relevant to the size of the object your making. Adjust accordingly to have a comfortable grid that's appropriate to the size of the model your creating. Creating a coin model vs a 2 story house model requires a vastly different grid setup!

![Image](https://www.cryengine.com/docs/static/attachments/23996548)

In this example, a grid spacing of 0.5m, with a major line every 5 units and a grid extension (view distance) of 10.

#### Check measurement settings

To confirm the size of the object you created, in the utilities section, you can use the measurement tool to verify the dimensions of the object you created.

*Using the measurement tool in 3dsMax (4 x 0.25m grid spacing = 1m)*![Image](https://www.cryengine.com/docs/static/attachments/25506765)

### Maya Unit Setup

1 meter = 1 Unit in CRYENGINE

The best way to work in Maya is to set the unit to centimeters. You can also adjust the grid and make it more readable while working on an asset.

There is also a very useful way to get the measurement feedback directly from the Engine.

Simply create a 1x1x1m designer object and go to **Level menu -> Export Selected Objects** and save the file type as either an ***.obj** or ***.fbx** file.

Import the created solid to your 3D scene and use it as a reference.

The unit setup can be found under **Window -> Settings/Preferences -> Preferences**:

![Image](https://www.cryengine.com/docs/static/attachments/23996549)

Then click on **Settings** in the left column. Here, you have to set the ** Working Units** to centimeter or the exporter will post a warning on export. Meter increments can be used but must be shifted back if you wish to have a warning and error free export process.

![Image](https://www.cryengine.com/docs/static/attachments/23996550)

### Centimeters or Meters

When you configure the unit scale of the DCC tool to match with CRYENGINE, setting the unit value scale to **cm** or ** m** is asset related.

- If you are working with smaller assets like rocks/pebbles/grass it would make your life easier in centimeters.
- If you are working with larger assets like houses/buildings etc., set the unit scale to meters.

### Size References

- Table Height (top of table) = 75cm.
- Seat height (top of chair, seat) = 46cm.
- Stair steps = 18.75cm (4 steps will sum up to 75cm).
- Boxes = 60cm x 40cm x 40 cm.

- Hide Objects (which AI lie prone to hide behind) = object that are smaller than 120cm.
- Hide Objects (which AI crouch to hide behind) = object that are bigger than 120cm.
- Hide Objects (which AI stand to hide behind and strafe left/right to leave cover) = object that are bigger than 180cm.

- Jump over Objects (standing, without hand) = 30 - 50cm high.
- Jump over Objects (running jumps) = 50 - 100cm high.
- Jump over Objects (sideways, with using hand) = 120 - 150cm high.

[3ds Max Unit Setup](#3ds-max-unit-setup)[Maya Unit Setup](#maya-unit-setup)[Centimeters or Meters](#centimeters-or-meters)[Size References](#size-references)
