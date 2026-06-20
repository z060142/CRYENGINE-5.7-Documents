# Reference Picture

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869877
- Page ID: 36869877
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Misc Objects > Reference Picture
- Parent: Misc Objects

## Content

## Overview

The main purpose of the ReferenceImage setup is that the ReferenceImage shader does not receive light or other shader information from within the level. It keeps the image at its pure source:

*Illum Shader on the left, ReferenceImage Shader on the right*![Image](https://www.cryengine.com/docs/static/attachments/36849645)

This tutorial shows how to add raw reference pictures in a level.

### Saving the reference picture

- Make sure you have the CryTiff plugin [installed](../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20CryTIF%20Plugin%20for%20Photoshop.md).
- Open the original reference picture in Photoshop.
- Set the size of the canvas or resize the picture to a power of 2 and use alpha channel to hide the black stripe if needed.
![Image](https://www.cryengine.com/docs/static/attachments/36849643)
- Save the picture as CryTiff, use **Diffuse_lowQ** or **highQ** preset. If needed, disable the streaming of the texture.
![Image](https://www.cryengine.com/docs/static/attachments/36849647)

### Inserting the reference picture in the level

- Place a brush that will contain the picture in the level. Usually, something like a flat billboard asset would be best suited.
- Create a new material with the ReferenceImage shader and add the previously created texture in the **diffuse** slot. Increase AlphaTest parameter when needed.
![Image](https://www.cryengine.com/docs/static/attachments/36849642)

### Result

This picture shows the difference between the standard Illum shader (left panel) and the ReferenceImage shader (right panel), unaffected by the noise/grain shading.

![Image](https://www.cryengine.com/docs/static/attachments/36849646)

[Saving the reference picture](#saving-the-reference-picture)[Inserting the reference picture in the level](#inserting-the-reference-picture-in-the-level)[Result](#result)
