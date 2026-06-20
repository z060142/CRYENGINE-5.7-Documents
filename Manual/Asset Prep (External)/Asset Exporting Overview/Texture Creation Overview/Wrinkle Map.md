# Wrinkle Map

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23307984
- Page ID: 23307984
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > Wrinkle Map
- Parent: Texture Creation Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934011)

##
Overview

##
Sections

The texture being used to define the areas and ranges to be influenced for wrinkles is a normal 32-Bit .tif file, including the alpha channel.

The different channels, red, green, blue and the alpha channel have been split into ranges so that more than 3 or 4 channels can be addressed independently and drive different areas on the face.

At the moment this is "hardcoded". Using more than these 3 Channels per map channel would make code changes necessary.

The different Ranges are evenly distributed on the channels from 0 to 255, with a gap of 20 between the first and second ranges and a gap of 10 between the second and third ranges to prevent the channels from mixing into each other.

[Sections](#sections)
[Connection Between Color Ranges and Rig](#connection-between-color-ranges-and-rig)
[Driven Bone Setup in Maya](#driven-bone-setup-in-maya)
[Shader Setup](#shader-setup)
Below is the resulting texture without the alpha channel and the right is the red converted to grayscale:

![Image](https://www.cryengine.com/docs/static/attachments/23994286)

![Image](https://www.cryengine.com/docs/static/attachments/23994288)

##
Connection Between Color Ranges and Rig

The table below shows how the different nodes and properties connect to each other from the texture through the rig into the engine.

Note that these connections are completely arbitrary and can be changed to adapt to specific needs.

Joint Name

Code

 |
Joint Name

Model/Rig

 |
Joint Parameter

Engine Range 0 - 1

Maya Range 0 - 100

 |
Color Channel

driven by Parameter

 |
Level-Ranges

In

Color Channels

 |
Influenced Area

On Wrinkle Map

(current setup)

Character Point-of-View

 |
Rig-Control

driving Parameter/Range

 |

joint0

 |
blend_control_01

 |
translation x

translation y

translation z

 |
red 0

red 1

red 2

 |
0 - 75

95 - 170

180 - 255

 |
Right Mouth and Nasolabialfold

Right Eye

Right Forehead

 |
def_r_lipCorner (z trans)

def_r_upperCheek (trans z)

def_r_brow_B (z trans)

 |

joint1

 |
blend_control_02

 |
translation x

translation y

translation z

 |
green 0

green 1

green 2

 |
0 - 75

95 - 170

180 - 255

 |
Left Forehead

Left Eye

Left Mouth and Nasolabialfold

 |
def_l_brow_B (z trans)

def_l_upperCheek (trans z)

def_l_lipCorner(z trans)

 |

joint2

 |
blend_control_03

 |
translation x

translation y

translation z

 |
blue 0

blue 1

blue 2

 |
0 - 75

95 - 170

180 - 255

 |
Glabella

Veins/Neck

Lips

 |
def_midbrows (y trans)

Jaw_control (x Rot); lip-press/jaw close

def_/rl_lipCorner(z trans), each of them 60

 |

joint3

 |
blend_control_04

 |
translation x

translation y

translation z

 |
alpha 0

alpha 1

alpha 2

 |
0 - 75

95 - 170

180 - 255

 |
Under Jaw

Chin/Lower Lip crease; eye-lid crease on claire

Masked areas (teeth, tounge, innermouth etc.

 |
Jaw_control (x Rot)

def_chin; blink on claire

Jaw_control (x Rot); 100 when closed, 0 when open

 |

##
Driven Bone Setup in Maya

The connections from the Table in the preceding chapter have been implemented through a driven key setup in Maya.

Based on the different existing animations certain bones from the rig have been selected to drive each specific property by mapping the motion of these to a 0 to 100 Unit range of the corresponding blend_bone.

Following a brief description of the Driven Key setup in Maya:

To open the Dialog use the menu in the picture below:

![Image](https://www.cryengine.com/docs/static/attachments/23994284)

This opens the Driven Key Setup Dialog, where connections between driving and driven nodes are set up, and also keyed at the desired values.

![Image](https://www.cryengine.com/docs/static/attachments/23994289)

In this example, according to the table in the preceding chapter, the connection has been set between def_r_upperCheek's local x translation value and is mapped to the 0 to 100 range of blend_control_01's y-translation.

Below is an example of one connection and its correlated curve by which the movement of the driving bone is mapped.

![Image](https://www.cryengine.com/docs/static/attachments/23994285)

##
Shader Setup

In the picture below you can see an overview of how each map needs to be applied in the material.

![Image](https://www.cryengine.com/docs/static/attachments/23994290)

Note that on the right side of the picture where the properties of the anim object are, the "WrinkleMap"-flag under the "Rendering" section needs to be set, in order for the wrinkle shading to work.

Also, on the "Shader Generation Params" section inside the material, "Wrinkle Blending" has to be checked:

![Image](https://www.cryengine.com/docs/static/attachments/23994291)

Here is a 2 frame example (animated gif) which shows the blend_bone driving the "crows feet" without deforming its surroundings to make the effect more visible.

![Image](https://www.cryengine.com/docs/static/attachments/23994287)
