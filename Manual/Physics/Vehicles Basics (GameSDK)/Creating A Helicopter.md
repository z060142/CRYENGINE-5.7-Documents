# Creating A Helicopter

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26870699
- Page ID: 26870699
- Breadcrumb: Physics > Vehicles Basics (GameSDK) > Creating A Helicopter
- Parent: Vehicles Basics (GameSDK)

## Content

##
Overview

##
Sections

Helicopters and their special functions are covered in this topic.

[#sections](
Sections
)
[#sample-files](
Sample Files
)
[#fading-rotors](
Fading Rotors
)
[#ordnance](
Ordnance
)
[#landing-gears-and-other-animated-elements](
Landing Gears and Other Animated Elements
)
[#in-sandbox](
In Sandbox
)

##
Sample Files

-
[/docs/static/attachments/1441817](
max_MH60.rar
)

-
[/docs/static/attachments/1441831](
ma_MH80.rar
)

##
Fading Rotors

There are two different rotors that are modeled to represent motion blur when the rotor is running. There is a full geometry one and a second one that has the motion blurred texture applied to it. These all are attached to one object, but with 2 different material IDs. Code blends them into each other, as needed.

The same technique is applied to both the main and tail rotors. The rotors also have simple collision proxies. The rotation comes from the animation. Therefore, the rotor contains the normal, the motion blurred versions, and the proxy in one object.

##
Ordnance

Rocket pod firing positions can be added in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/26214869](
Vehicle Editor
)
 in Sandbox, or with helpers in 3ds Max. In the SDK sample asset, it's placed in the Editor.

##
Landing Gears and Other Animated Elements

Landing gears are animated in the DCC package and the whole sequence is exported as .anm animation file. There is one file for the opening sequence and one for closing. You can have different numbers of animated elements, like they are represented in the SDK asset.

For example, for exporting the landing gear opening sequence, you have to select only the objects that are involved in this sequence and add them to the export list. Then, you can export this sequence as an .anm file.

##
In Sandbox

Please refer to
[/docs/static/engines/cryengine-5/categories/23756816/pages/26214869](
this
)
 section for information on the vehicle editor.
