# System Setup for PBS

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959242
- Page ID: 44959242
- Breadcrumb: Graphics & Rendering > Shaders > Physically Based Shading (PBS) > System Setup for PBS
- Parent: Physically Based Shading (PBS)

## Content

In order to attain the best results when setting up your materials for physical based shading, you need to set up your monitor and graphics software to display your work files properly.

This also includes all monitors & systems you would like to review the materials on.

### Monitor Setup: sRGB Color Space

Make sure that you are working in sRGB color space on your monitor when painting a texture. In sRGB space, a 50% mid-gray is not 0.5 or 127 but rather 0.5 raised by the inverse of gamma 2.2 which is equal to 187 in Photoshop. In a nutshell, the reason that sRGB is used is to avoid banding artifacts. In sRGB space you get more precision for darker colors to which the human eye is more sensitive. Before working on colors, please make sure that your screen is calibrated properly.

### Photoshop Setup:

Verify that your Photoshop color management is set up properly. You can access the **Color Settings** from the menu via ** Edit → Color Settings...**

**RGB** should be set to ** sRGB** and ** Gray** to ** Gray Gamma 2.2**

By default, Gray is often set to **Dot Gain 20%** which will result in a color transformation in the alpha channel. A value of **127** will come into the engine as ** 104** in that case which can cause inconsistencies, so please make sure ** Gamma 2.2** is used instead.
