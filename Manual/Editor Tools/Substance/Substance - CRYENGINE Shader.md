# Substance - CRYENGINE Shader

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450470
- Page ID: 29450470
- Breadcrumb: Editor Tools > Substance > Substance - CRYENGINE Shader
- Parent: Substance

## Content

##
Overview

This is a stand-alone tool in the Tools/Substance folder in your Engine installation folder. It cannot be found in the Sandbox Editor.
This tool is a shader that tries to match the viewport shading of Allegorithmic's Substance Designer and Painter software, more that is, toward the shading found in CRYENGINE.

[Image: /docs/static/attachments/28900914]

##
Installation

##
Substance Designer

Download
**
[/docs/static/attachments/28900920](
Designer_shaders.zip
)

**
and unzip it to
**
c:\Program Files\Allegorithmic\Substance Designer\5\resources\view3d\shaders
**
or the respective folder where your Designer is installed.

Restart the Designer. After this, the new shader should appear in the shader list named
**
ce_physically_specular_glossiness.
**

##
Substance Painter

Download
**
[/docs/static/attachments/28900919](
CryEngine.glsl
)
**
 and when your project is open, drag&drop it to the Shaders shelf in the Painter:

[Image: /docs/static/attachments/28900913]

In Painter you should use the same channels CRYENGINE is using:

-
**
Base Color
**

-
**
Glossiness
**

-
**
Displacement
**

-
**
Specular
**

-
**
Transmissive
**

##
Usage

This shader tries to mimic CRYENGINE shading. It supports default Physically Based Rendering (PBR) shading, together with Parallax Occlusion Mapping (POM) with selfshadow and also supports translucency.

Most of the settings from the Designer or Painter software should be straightforward and mean exactly the same as in CRYENGINE.

[Image: /docs/static/attachments/28900916]

[Image: /docs/static/attachments/28900915]

##
Parallax Occlusion Mapping (POM)

Substance Designer: As a target map for a heightmap use "
**
Height"
**

Substance Painter: As a source channel for POM use "
**
Displacement"
**

Since Substance doesn't support small step changes in values, the depth for POM is displayed as being in the 0-1 range, but it is the same as a CRYENGINE range of 0-0.05.

##
Light Setup

The only
difference in
setup is in light handling, since
**
Substance Designer
**
 only allows having light intensity defined by color, while
**
Substance Painter
**
 doesn't have any light in the scene at all.

Therefore, for
**
Substance Painter
**
, Sun-related parameters were introduced to mimic the sun in the scene. In
**
Substance Designer
**
,
**
Sun Multiplier Intensity
**
 was added as a shader parameter to allow increasing the sun intensity in the scene.

By default, using the cubemap together with the sun intensity set to 1 means the sun has almost the same intensity as brightness coming from the image based lighting setup. It might look as if selfshadows on POM are not working, but they do; you need to actually boost
**
Sun Intensity
**
. It is also recommended to lower
**
Environment Exposure
**
 to
**
below 0.
**
This is not a bug, it is the result of differences between Substance and CRYENGINE. See below.
[Image: /docs/static/attachments/28900911]

##
Using CryEngine Cubemap in a Viewport

It is also possible to use CRYENGINE cubemaps as a Panorama image in Substance:

-
Open a cryengine tif cubemap in Photoshop. (found in the cubemaps folder, with _cm suffix). Don't be scared by strange colors.

[Image: /docs/static/attachments/28900912]

-
Run this
[/docs/static/attachments/28900918](
vertical_cubemap.jsx
)
 Photoshop script to transform the image to a vertical cross cubemap.

[Image: /docs/static/attachments/28900910]

-
You can now expand the border of the cubemap so there are less seams.

-
Save the image as an
**
HDR
**
 image format.

-
Open the image in
[/docs/static/attachments/28900917](
HDRShop.zip
)
.

-
Go to menu
**
Image/Panorama/PanoramaticTranform
**
.

-
Make sure the settings are as below, and potentially raise resolution.

[Image: /docs/static/attachments/28900909]

-
Save as a new
**
HDR
**
 image.

-
In
**
Substance Designer
**
, change the panorama image in the scene options.

-
Done.

##
Substance Render vs CRYENGINE Render Differences

Apart from using a different cubemap format where Substance uses a latitude-longitude environment map and CRYENGINE uses a 6-sided cubemap, there is also a difference in the sampling. Whereas in
CRYENGINE
 cubemap importance sampling is done during dds generation in the Resource Compiler, in Substance it is done directly in the shader. Also,
CRYENGINE
 uses a secondary low res diffuse cubemap, whereas Substance uses SphericalHarmonics coefficients calculated from the environmental map. However, results should be similar.

##
ToneMapping

The biggest difference is in tonemapping.
CRYENGINE
 lights the scene with raw values that it gets from light and cubemaps (see the very top right in the cubemap example above) and then applies tonemapping to the final scene to compensate.

Substance, however doesn't compensate too much or use too lower light in postprocessing, but it allows changing the exposure of the Environmental map. This is almost the same as lowering the Diffuse and Specular multiplier for an Environmental probe in the Sandbox Editor.

This is why it's highly recommended to lower Environmental map exposure in Substance and higher sun intensity to get more similar results to that produced in
CRYENGINE
.

[#installation](
Installation
)
[#usage](
Usage
)
[#parallax-occlusion-mapping-pom](
Parallax Occlusion Mapping (POM)
)
[#light-setup](
Light Setup
)
[#using-cryengine-cubemap-in-a-viewport](
Using CryEngine Cubemap in a Viewport
)
[#substance-render-vs-cryengine-render-differences](
Substance Render vs CRYENGINE Render Differences
)
