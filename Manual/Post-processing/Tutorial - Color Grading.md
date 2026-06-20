# Tutorial - Color Grading

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26872965
- Page ID: 26872965
- Breadcrumb: Post-processing > Tutorial - Color Grading
- Parent: Post-processing

## Child Pages

- [Enabling Charts in Sandbox](Tutorial%20-%20Color%20Grading/Enabling%20Charts%20in%20Sandbox.md)

## Content

##
Overview

Color correction is a post processing effect that takes a frame rendered by the Engine and changes the appearance of colors in various ways.

These typically include effects like Hue & Saturation, Contrast & Brightness, Luminance & Color Curves, Sepia, etc.

##
Chapters:

[Chapters:](#chapters)
[Using Reference Images](#using-reference-images)
[Troubleshooting](#troubleshooting)
[Video Tutorial](#video-tutorial)

##
Using Reference Images

##
1 - Taking the image

Color correction by example takes a reference image that gets color corrected by an artist. The image includes a color chart so all transformation steps applied to the image can later be reconstructed by the engine in real-time.

Take an arbitrary reference image that hasn't been color corrected yet and (ideally) shows a wide range of colors. It should have reasonable size.

Avoid using insanely high resolution images as they won't improve color correction quality and only waste space and processing time in the resource compiler.

##
2 - Add color chart

Copy/paste the attached
[RGBChart.bmp](/docs/static/attachments/1212829)
 into the reference image. It is important to use the color chart supplied with this document, as otherwise the resource compiler later on won't be able to detect and extract the chart.

Flatten all layers, and save the file.

##
3 - Color correcting

Color correct the reference image. While doing so always pay attention to how the colors inside the chart react.

Avoid extreme levels of saturation (usually a result of color correcting desaturated images) or abrupt changes between similar colors as otherwise these will result in banding artifacts when later applying the chart during post processing inside the engine.

It is also recommended to use reference images that initially show a wide range of colors.

##
4 - Exporting

Save the reference image as a CryTIF file using the following naming convention:
*
filename
*
 +
_cch.tif
. For example:
sample_cch.tif

If you follow this naming convention the resource compiler should automatically pick "ColorChart" as the preset to be used. If for any reason this preset was not chosen, please do so manually.

Make sure that the image is not tiled in the Resource Compiler. Then click
Generate Output
 in order to create a file with a .dds extension. Please be aware that the name of the file may change.

##
5 - Save location

The .dds color chart must now be copied to the textures.pak file. Before copying the file, the Sandbox Editor must be closed, as this is a compressed folder. You will need to create a new folder inside of the texture pack called
colorcharts
.

Your sample color chart in its correct location should look like this:
`
Textures.pak\Textures\colorcharts\sample_cch.dds
`

##
Troubleshooting

If you encounter visual glitches on the PC, please ensure that you haven't overwritten 3D settings for either the editor or game launcher in the control panel of your video driver. This is a major source of visual artifacts.

Especially enforcing multi-sampling or anisotropic texture filtering can break post processing effects, deferred shading, and other things. Ideally, in such case a message box would be shown to alert the user.

However, there's currently no way to detect that the video driver is overwriting settings the application assumes to be in control of.

##
Video Tutorial

See also
[this](http://youtube.com/watch?v=Ecq2YTlJM-8)
 video tutorial on our YouTube channel.

*
Pic: Resetting 3D settings in the video driver's control panel.
*
