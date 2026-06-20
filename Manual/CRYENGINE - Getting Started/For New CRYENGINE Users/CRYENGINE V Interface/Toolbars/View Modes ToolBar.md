# View Modes ToolBar

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308636
- Page ID: 23308636
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Interface > Toolbars > View Modes ToolBar
- Parent: Toolbars

## Child Pages

- [Texels Per Meter](View%20Modes%20ToolBar/Texels%20Per%20Meter.md)

## Content

##
Overview

The ViewModes toolbar helps save time when debugging issues in your scenes.

To activate the ViewModes toolbar in CRYENGINE Sandbox, right-click on an empty space in the toolbar area. This will open a menu that will allow you to add additional toolbars to the UI .

Select
**
ViewModes
**
 from the drop down menu and you will see that the ViewModes toolbar has been added to your Editor's UI.

![Image](https://www.cryengine.com/docs/static/attachments/28881127)

This toolbar has been introduced to save you time by not having to remember a large number of CVars and commands.

##
Toolbar Breakdown

![Image](https://www.cryengine.com/docs/static/attachments/28881128)

From left to right, all the buttons in the toolbar have been listed below along with a description of what they do. Additionally and for your reference the CVar being modified has also been included.

All but one of these buttons are toggles, on/off. Others, like the min_LOD will cycle between 6 options (0 -> 5) & back again to 0.

No.
 |
Icon
 |
What it does
 |
Cvar / command being used
 |

1
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881133)
 |
Default normal rendering mode
 |
r_DebugGBuffer = 0
 |

2
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881134)
 |
Normals PBS debugview
 |
r_DebugGBuffer = 1
 |

3
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881135)
 |
Smoothness PBS
debugview
 |
r_DebugGBuffer = 2
 |

4
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881136)
 |
Reflectance PBS
debugview
 |
r_DebugGBuffer = 3
 |

5
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881137)
 |
Albedo
PBS
debugview
 |
r_DebugGBuffer = 4
 |

6
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881138)
 |
Lighting Model
PBS
debugview
 |
r_DebugGBuffer = 5
 |

7
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881139)
 |
Translucency
PBS
debugview
 |
r_DebugGBuffer = 6
 |

8
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881140)
 |
Sun Self Shadowing
PBS
debugview
 |
r_DebugGBuffer = 7
 |

9
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881141)
 |
SubSurface Scattering
PBS
debugview
 |
r_DebugGBuffer = 8
 |

10
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881142)
 |
Specular Validation
PBS
debugview
 |
r_DebugGBuffer = 9
 |

11
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881143)
 |
Default Material
 |
e_DefaultMaterial = 1
 |

12
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881144)
 |
Default Material with Normalmaps
 |
r_TexBindMode = 6
 |

13
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881145)
 |
Overlay Collision Proxies
 |
p_Draw_Helpers = 1
 |

14
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881146)
 |
Shaded Wireframe
 |
r_ShowLines = 2
 |

15
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881147)
 |
Full Wireframe
 |
r_wireframe = 1
 |

16
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881148)
 |
Show Vertex Normals
 |
r_shownormals = 1
 |

17
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881149)
 |
Show Tangents
 |
r_ShowTangents = 1
 |

18
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881150)
 |
Texels Per Meter 256
 |
r_TexelsPerMeter = 256
 |

19
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881151)
 |
Texels Per Meter 512
 |
r_TexelsPerMeter = 512
 |

20
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881152)
 |
Texels Per Meter 1024
 |
r_TexelsPerMeter = 1024
 |

21
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881153)
 |
Colour coded LOD visualisation
 |
e_DebugDraw = 3, -3, 0
(3=color + debugtext, -3=color only, 0=off)
 |

22
 |
![Image](https://www.cryengine.com/docs/static/attachments/28881154)
 |
Minimum LOD cycle
 |
e_LodMin = 0, 1, 2, 3, 4, 5 (cycle through the LOD states 0 - 5 (if available))
 |

##
Further Reading

For more information about 1-10, see
**
[Debug GBuffer](../../../../Graphics%20%26%20Rendering/Shaders/Physically%20Based%20Shading%20(PBS)/Physically%20Based%20Shading%20-%20Debugging.md)
**
.

For more information about 18-20, see
**
[Texels Per meter](View%20Modes%20ToolBar/Texels%20Per%20Meter.md)
**
.

[Toolbar Breakdown](#toolbar-breakdown)
[Further Reading](#further-reading)
