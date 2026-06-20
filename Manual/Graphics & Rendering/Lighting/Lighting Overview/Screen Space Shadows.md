# Screen Space Shadows

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26872870
- Page ID: 26872870
- Breadcrumb: Graphics & Rendering > Lighting > Lighting Overview > Screen Space Shadows
- Parent: Lighting Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933281)

##
Overview

This functionality can be used in combination with the shadow maps to prevent bias and low resolution effects in the objects. It improves the quality of usual shadow maps without increasing CPU and GPU overhead. This effect can be implemented for objects within the 3 meters range from the camera.

##
Implementation

To activate this functionality, enable the cvar
**
r_ShadowsScreenSpace
**
 from the console.

*
Pic1: A sample Detailed Screen Space Shadows utilized in a scene.
*

*
![Image](https://www.cryengine.com/docs/static/attachments/44970779)
*
