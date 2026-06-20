# Height Map Based Ambient Occlusion

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215324
- Page ID: 26215324
- Breadcrumb: Graphics & Rendering > Lighting > Lighting Overview > Height Map Based Ambient Occlusion
- Parent: Lighting Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933285)

### Overview

CRYENGINE provides an extremely efficient, yet highly approximate large scale ambient occlusion solution for outdoor environments. In combination with Screen Space Directional Occlusion (SSDO) and Height Map Ambient Occlusion (Height Map AO), additional shading cues are provided to the eye that yield enhanced depth perception of a scene.

![Image](https://www.cryengine.com/docs/static/attachments/21868167)![Image](https://www.cryengine.com/docs/static/attachments/21868168)

*Click the images for an On/Off comparison*

### Usage

Height Map AO can be enabled via the **Level Settings → Settings** tab as shown in the image below.

![Image](https://www.cryengine.com/docs/static/attachments/52593436)

When active, occlusion is evaluated based on a height map representation of the scene. By default, the evaluation is performed at quarter display resolution, though the CVar **r_HeightMapAO** allows evaluation at half or even full resolution as well.

The influence of Height Map AO can be restricted via [Clip Volumes](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Clip%20Volume.md) and [Vis Areas](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md): Both object types provide a **IgnoreHeightMap AO** checkbox which will locally disable Height Map AO inside the volume.

### Related CVars

- **r_HeightMapAO**: 0=off, 1=quarter resolution, 2=half resolution, 3=full resolution
- **r_HeightMapAOAmount**: Strength of the occlusion effect when combined with the scene
- **r_HeightMapAORange**: Area around the viewer which is affected by Height Map AO
- **r_HeightMapAOResolution**: Texture resolution of the height map used for approximating the scene

[Usage](#usage)[Related CVars](#related-cvars)
