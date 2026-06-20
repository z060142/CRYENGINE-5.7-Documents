# Camera Settings

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966443
- Page ID: 44966443
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Interface > Viewport Window > Camera Settings
- Parent: Viewport Window

## Content

##
Overview

The Perspective Viewport is the only Viewport that is adjustable. On this page, we'll discuss the
**
Camera Settings
**
.

##
Camera Settings for the Perspective Viewport

You can find the Camera settings for the Perspective Viewport in the top-left corner of the Viewport window:

[Image: /docs/static/attachments/44967974]

Setting
 |
Description
 |

**
Speed
**
 |
Changes the speed within that Viewport. (Can also be changed by scrolling the mouse wheel while moving around in the Viewport, see also
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308616](
Viewport Navigation
)
**
.)
 |

**
Camera Speed Height-relative
**
 |
When enabled, adjusts the speed of camera movement based on the height of the camera above terrain or objects. The camera speed is multiplied by the height in meters (clamped to a range of 1-1000). This lets you move precisely when close to the ground, or quickly to different parts of the level, without constantly adjusting the camera speed slider.
 |

**
Camera Terrain Collisions
**
 |
Toggles terrain collision on and off. When turned on, the camera does not go through the terrain when hitting it, but will always move along it. This option also affects
**
Speed Height-Relative
**
: when on, camera height is measured above terrain
*
or
*
 objects; when off, terrain only.
 |

**
Camera Object Collisions
**
 |
Toggles object collision on and off. When turned on, the camera does not go through objects on the terrain when hitting them, but will always move along them.
 |

**
FOV
**
 |
Sets the Field of View.
 |

**
Resolution
**
 |
Sets the resolution for this Viewport.

-
**
 Window Resolution -
**
Game framebuffer has the exact same size as the viewport window. If you need a set/static resolution that does not change with window size, use a preset or custom resolution.

-
**
Preset resolutions -
**
Lets you choose a game framebuffer resolution from a list of commonly used resolutions.

-
**
Positioning
**

-
**
Stretch -
**
The contents of the game framebuffer are scaled to the boundaries of the editor window, preserving the aspect ratio of the internal resolution.

-
**
Center, Top Right, Top Left, Bottom Right, Bottom Left -
**
The contents of the game framebuffer are positioned to the relevant area of the editor window. The size of the framebuffer is preserved. You will need to increase the size of the window manually to see all the contents of the framebuffer if the framebuffer is bigger than the window.

**
NOTE:
**
 Selecting any of the positioning options will make the framebuffer resolution a set/static resolution, even if it was a window resolution before.

-
**
Custom -
**
Spawns a dialog that allows users to create and set a custom game framebuffer resolution for the viewport. The top numbers correspond to width and height of the framebuffer. If a certain aspect ratio is needed, The aspect ratio drop down can be used to enforce an aspect ratio according to the current width or height. The aspect ratio itself can be set using the two bottom fields. Any custom resolution added with this dialog will be added to a list below the preset resolutions for further use.

-
**
Clear Custom Resolutions
**
-
**
**
Clears the custom resolution set with the option above.
 |

**
Create Camera from Current View
**
 |
Creates a camera from the current view.
 |

**
Default
**
 |
Sets the view to the default camera.
 |

**
Trackview
**
 |
Sets the view to the Trackview Camera.
 |

**
Camera Entity
**
 |
Lets you jump between different cameras you have created with Create Camera from Current View.
 |

**
Create Viewport
**
 |
Opens another Viewport of your choice in a new window. (This can also be done by going to
**
Tools -> Viewport
**
 and choosing the Viewport you want to open.)
 |

[#camera-settings-for-the-perspective-viewport](
Camera Settings for the Perspective Viewport
)
