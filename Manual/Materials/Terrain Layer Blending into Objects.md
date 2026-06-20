# Terrain Layer Blending into Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36340007
- Page ID: 36340007
- Breadcrumb: Materials > Terrain Layer Blending into Objects
- Parent: Materials

## Content

##
Overview

This feature creates a soft transition between terrain materials and objects (e.g. rocks or tree trunks), which makes for a much more natural look. It hides the artificial looking hard edge between objects and the terrain.

[Image: /docs/static/attachments/36309128]

##
Implementation

-
Select the terrain material in the Material Editor

You can use the
**
Pick Material From Object
**
 button in the Material Editor to pick the material from the scene.

-
Enable
**
Soft Depth Test
**
 in the
**
Shader Generation Params
**
.

-
Tweak the amount of blending with
**
Soft Depth Test Distance Ratio
**
 and
**
Soft Depth Test Range
**
.

##
CVars

Cvar/Command

 |
Description

 |
Comment and examples

 |

e_TerrainBlendingDebug 0
 |
Only blend objects that have FOB_ALLOW_TERRAIN_LAYER_BLEND set
 |
default
 |

e_TerrainBlendingDebug 1
 |
Disable blending on all objects
 |

 |

e_TerrainBlendingDebug 2
 |
Enable blending on all objects
 |

 |
