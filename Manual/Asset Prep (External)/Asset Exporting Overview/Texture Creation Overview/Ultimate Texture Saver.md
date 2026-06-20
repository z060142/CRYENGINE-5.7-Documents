# Ultimate Texture Saver

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29799056
- Page ID: 29799056
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > Ultimate Texture Saver
- Parent: Texture Creation Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933576)

##
Overview

##
Sections

The UltimateTextureSaver is a Photoshop extension that has been developed to ease the life of a Texture Artist.

-
It creates a default folder layout in PSD files for desired textures

-
Saves desired textures and automatically shuffles all channels

-
Supports user defined keyboard shortcuts

-
Supported textures and channel(s) mapping are easily and quickly configurable

Currently it has only been tested on Photoshop CS6, but does support Photoshop CS5.5 and CC. Note: This support excludes Photoshop 2014 CC and above versions (includes the usage of the CC Extension Manager in the above versions).

[Sections](#sections)
[Installation](#installation)
[Technical Documentation](#technical-documentation)

##
Installation

-
It can be installed manually using the
[UltimateTextureSaver.zip](/docs/static/attachments/44970556)
 file. Adobe Extension Manager should then be opened and used to install the extension. After this, you should copy the contents of the folder
"{zip}UltimateTextureSaver\Install"
into
"
C:\Program Files\Adobe\"

Note:
 This installation only works for users who have
admin rights
 to their machines!

-
Restart Photoshop after installation

-
In Photoshop you can find the extension in the menu "Window/Extensions/UltimateTextureSaver"

##
Usage

Default View
 |
Change Destination Tab
 |
Edit Shortcuts Tab
 |

![Image](https://www.cryengine.com/docs/static/attachments/51347784)

 |
![Image](https://www.cryengine.com/docs/static/attachments/51347785)

 |
![Image](https://www.cryengine.com/docs/static/attachments/51347786)

 |

##
Create Texture Layout

To create the texture layout, hit the
"+"
 button next to the texture name.

If you hit
"Default Layout +"
, then

layouts for Albedo, NormalWithSmoothness and Reflectance will be created.

##
Saving Textures

To save a desired texture, hit the respective button or press the relevant keyboard shortcut.

If the target texture does not exist, the RC dialog pops up and the user can change the texture presets. However, if the target texture already exists, then the RC dialog is skipped to speed up the save process. If the user wants to display the RC dialog again, then the texture save button has to be pressed with the
Middle Mouse Button
.

##
Changing Destination

The Texture is by default saved
Two Folders Up
from the location where the PSD is located.

This is configuration specific and can be changed for each project - if there is a need for different folder structures.

To change a destination, click on the "
Change Destination
" button. You are then allowed to choose a new target location for *.tif files. Don't forget to hit "
Save
" to save any changes.

The target location is
always
 relative to PSD location, so when another artist opens the PSD in a different location, the *.tiff file will be saved relative to this one.

##
Edit Shortcuts

The only way to support keyboard shortcuts in Photoshop extensions, is to generate Photoshop Actions. Due to Photoshop limitations you always have to restart Photoshop if you want to edit UltimateTextureSaver shortcuts - this includes the same session where you have already changed some shortcuts for other Photoshop actions.

The keyboard shortcut Editor respects all shortcuts in Photoshop. So if you encounter a situation where it is impossible to configure a shortcut as you you want it, then it is almost always because it is already in use in another Photoshop action.

Always remember to
"Save"
any changes. Actually saved shortcuts are displayed next to texture button name.

Keyboard shortcuts will work even without extension active/visible.

##
Technical Documentation

Texture buttons are configured using the xml file
"{zip}\UltimateTextureSaver\UltimateTextureSaver.xml"
and are dynamic.

UltimateTextureSaver.xml

`
<
`
`
UltimateTextureSaver
`

`
path
`
`
=
`
`
"..\.."
`
`
>
`
`

`
`
<
`
`
Texture
`

`
name
`
`
=
`
`
"Albedo"
`

`
suffix
`
`
=
`
`
"_diff"
`

`
FKey
`
`
=
`
`
"F2"
`

`
Shift
`
`
=
`
`
"false"
`

`
Ctrl
`
`
=
`
`
"false"
`

`
Default
`
`
=
`
`
"true"
`

`
>
`
`

`
`
<
`
`
Components
`
`
>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"diff"
`

`
target
`
`
=
`
`
"color"
`

`
alias
`
`
=
`
`
"DIFF"
`

`
color
`
`
=
`
`
"red"
`
`
/>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"alpha"
`

`
target
`
`
=
`
`
"a"
`

`
alias
`
`
=
`
`
"ALPHA"
`

`
color
`
`
=
`
`
"gray"
`
`
/>
`
`

`
`
</
`
`
Components
`
`
>
`
`

`
`
</
`
`
Texture
`
`
>
`
`

`
`
<
`
`
Texture
`

`
name
`
`
=
`
`
"Reflectance"
`

`
suffix
`
`
=
`
`
"_spec"
`

`
FKey
`
`
=
`
`
"F2"
`

`
Shift
`
`
=
`
`
"false"
`

`
Ctrl
`
`
=
`
`
"true"
`

`
Default
`
`
=
`
`
"true"
`
`
>
`
`

`
`
<
`
`
Components
`
`
>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"spec"
`

`
target
`
`
=
`
`
"color"
`

`
alias
`
`
=
`
`
"SPEC"
`

`
color
`
`
=
`
`
"yellow"
`
`
/>
`
`

`
`
</
`
`
Components
`
`
>
`
`

`
`
</
`
`
Texture
`
`
>
`
`

`
`
<
`
`
Texture
`

`
name
`
`
=
`
`
"Normals"
`

`
suffix
`
`
=
`
`
"_ddn"
`

`
FKey
`
`
=
`
`
"F3"
`

`
Shift
`
`
=
`
`
"true"
`

`
Ctrl
`
`
=
`
`
"false"
`
`
>
`
`

`
`
<
`
`
Components
`
`
>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"normal"
`

`
target
`
`
=
`
`
"color"
`

`
alias
`
`
=
`
`
"DDN"
`

`
color
`
`
=
`
`
"blue"
`
`
/>
`
`

`
`
</
`
`
Components
`
`
>
`
`

`
`
</
`
`
Texture
`
`
>
`
`

`
`
<
`
`
Texture
`

`
name
`
`
=
`
`
"Displacement"
`

`
suffix
`
`
=
`
`
"_displ"
`

`
FKey
`
`
=
`
`
"F3"
`

`
Shift
`
`
=
`
`
"true"
`

`
Ctrl
`
`
=
`
`
"true"
`
`
>
`
`

`
`
<
`
`
Components
`
`
>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"displ"
`

`
target
`
`
=
`
`
"a"
`

`
alias
`
`
=
`
`
"HEIGHT"
`

`
color
`
`
=
`
`
"orange"
`
`
/>
`
`

`
`
</
`
`
Components
`
`
>
`
`

`
`
</
`
`
Texture
`
`
>
`
`

`
`
<
`
`
Texture
`

`
name
`
`
=
`
`
"DetailMerged"
`

`
suffix
`
`
=
`
`
"_dt"
`

`
FKey
`
`
=
`
`
"F4"
`

`
Shift
`
`
=
`
`
"false"
`

`
Ctrl
`
`
=
`
`
"true"
`
`
>
`
`

`
`
<
`
`
Components
`
`
>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"detail_diff"
`

`
target
`
`
=
`
`
"r"
`
`
/>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"detail_gloss"
`

`
target
`
`
=
`
`
"b"
`
`
/>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"detail_normal"
`

`
target
`
`
=
`
`
"ga"
`

`
mapping
`
`
=
`
`
"rg"
`

`
/>
`
`

`
`
</
`
`
Components
`
`
>
`
`

`
`
</
`
`
Texture
`
`
>
`
`

`
`
<
`
`
Texture
`

`
name
`
`
=
`
`
"Blend"
`

`
suffix
`
`
=
`
`
"_mask"
`

`
FKey
`
`
=
`
`
"F5"
`

`
Shift
`
`
=
`
`
"false"
`

`
Ctrl
`
`
=
`
`
"false"
`
`
>
`
`

`
`
<
`
`
Components
`
`
>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"blend"
`

`
target
`
`
=
`
`
"color"
`
`
/>
`
`

`
`
</
`
`
Components
`
`
>
`
`

`
`
</
`
`
Texture
`
`
>
`
`

`
`
<
`
`
Texture
`

`
name
`
`
=
`
`
"NormalWithSmoothness"
`

`
suffix
`
`
=
`
`
"_ddna"
`

`
FKey
`
`
=
`
`
"F3"
`

`
Shift
`
`
=
`
`
"false"
`

`
Ctrl
`
`
=
`
`
"false"
`

`
Default
`
`
=
`
`
"true"
`
`
>
`
`

`
`
<
`
`
Components
`
`
>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"normal"
`

`
target
`
`
=
`
`
"color"
`

`
alias
`
`
=
`
`
"DDN"
`

`
color
`
`
=
`
`
"blue"
`
`
/>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"gloss"
`

`
target
`
`
=
`
`
"a"
`

`
alias
`
`
=
`
`
"GLOSS"
`

`
color
`
`
=
`
`
"violet"
`
`
/>
`
`

`
`
</
`
`
Components
`
`
>
`
`

`
`
</
`
`
Texture
`
`
>
`
`

`
`
<
`
`
Texture
`

`
name
`
`
=
`
`
"SSS"
`

`
suffix
`
`
=
`
`
"_sss"
`

`
FKey
`
`
=
`
`
"F6"
`

`
Shift
`
`
=
`
`
"false"
`

`
Ctrl
`
`
=
`
`
"false"
`
`
>
`
`

`
`
<
`
`
Components
`
`
>
`
`

`
`
<
`
`
Component
`

`
name
`
`
=
`
`
"sss_translucency"
`

`
target
`
`
=
`
`
"r"
`
`
/>
`
`

`
`
</
`
`
Components
`
`
>
`
`

`
`
</
`
`
Texture
`
`
>
`
`
</
`
`
UltimateTextureSaver
`
`
>
`
 |

Node
 |
Attribute
 |
Explnation
 |

<UltimateTextureSaver>
 |

 |
Root xml node.
 |

 |
path
 |
Default relative path where textures are saved in Photoshop.
 |

<Texture>
 |

 |
Main node defining known texture for the system.
 |

 |
name
 |
Name of the button in the UltimateTextureSaver extension.
 |

 |
suffix
 |
Suffix for target *.tif file.
 |

 |
FKey
 |
Default Fkey for shortcut Editor. Can be overridden and has to be uppercase.
 |

 |
Shift
 |
False/true. Defines if shortcut also uses Shift key.
 |

 |
Ctrl
 |
False/true. Defines if shortcut also uses Ctrl key.
 |

 |
Default
 |
If true, texture components are created when "Default Layout" button is pressed in the UltimateTextureSaver.
 |

<Components>
 |

 |
List of components that texture can consist of.
 |

<Component>
 |

 |
Particular component definition.
 |

 |
name
 |
Name of layer set that will be created and used for saving.
 |

 |
target
 |
Defines target channels where content of a particular component will be placed. Values are color/r/g/b/a. Color has to be standalone, whereas rgb can be in combination.

target="rg"
 means that r and g channels from the source layers set are going to be placed to respective channels for the resulting texture.
 |

 |
mapping
 |
If channel shuffling is desired, then this defines channel mapping. Defining
target="ga" mapping="rg"
means r channel from source layer set will be copied to

g channel of target texture and g channel to alpha.
 |

 |
alias
 |
Alternative, semicolon separated names of layer set - to preserve backward compatibility.
 |

 |
color
 |
Color of texture layer set when created through the UltimateTextureSaver extension. Possible values are: red, orange, yellow, blue, violet, gray, none.
 |
