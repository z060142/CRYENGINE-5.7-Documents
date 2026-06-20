# Water Caustics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26872962
- Page ID: 26872962
- Breadcrumb: Post-processing > Water Caustics
- Parent: Post-processing

## Content

##
Overview

##
Sections

Watervolumes and rivers support a unified caustics approach. These caustics capture 1:1 caustics of the water surface (when tilling and intensity are set to 1, see below). This includes water ripples generated from objects interacting with the water surface.

Make sure your Watervolume is at a world height of '1' or greater. If it's below '1' Z height in the level then the caustics will not display.

[Sections](#sections)
[Caustics Settings](#caustics-settings)
[Console Variables](#console-variables)

##
Caustics Settings

The water volume and river entities have been extended to allow these controls over the caustics (all settings per-entity):

Parameter

 |
Description

 |

**
Caustics
**

 |
Enables Caustics for this entity.

 |

**
Intensity
**

 |
Intensity of normals during caustics generation.

 |

**
Tiling
**

 |
Tilling of normals during caustics generation.

 |

**
Height
**

 |
Height above water surface caustics are visible.

 |

##
Intensity

Controls the intensity of the caustics (this scales the normals of the surface when rendering to the caustic map, producing stronger caustics).

 |
 |
 |

Intensity 1
 |
Intensity 4
 |
Intensity 8
 |

##
Tiling

This is a multiplier for the tiling applied to the surface normals during caustic generation. It allows you to scale the caustics generation independently from the surface material in cases of strong tiled normals or vice-versa.

 |
 |
 |

Tiling 1
 |
Tiling 4
 |
Tiling 8
 |

##
Height

Controls the height above the water entity in which caustics can be cast. This can be used to cause caustics on overhangs and other nearby objects.

 |
 |
 |

Height 1
 |
Height 3
 |
Height 6
 |

##
Console Variables

CVar

 |
Description

 |
Values

 |

**
r_WaterVolumeCaustics
**

 |
Enables or disables caustics for water volumes

 |
0 - 1 (default depends on system - currently 0 on all except PC high-spec).

 |

**
r_WaterVolumeCausticsDensity
**

 |
Sets the density of the grid mesh.

 |
16 - 256 (default is 128 for lower specs, 256 for high specs).

 |

**
r_WaterVolumeCausticsMaxDist
**

 |
Sets the maximum view distance caustics are visible.

 |
Anything. Default 25.

 |

**
r_WaterVolumeCausticsRes
**

 |
Sets the resolution of the caustics map/g-buffer.

 |
Texture resolution. Default 1024 for high specs, 512 for low specs.

 |

**
r_WaterCausticsSnapFactor
**

 |
Sets the snap factor of the caustic render, helps prevent aliasing during motion.

 |
Anything. Default: 0.1.

 |
