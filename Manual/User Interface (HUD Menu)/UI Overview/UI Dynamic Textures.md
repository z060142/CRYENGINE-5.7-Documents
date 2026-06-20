# UI Dynamic Textures

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535439
- Page ID: 25535439
- Breadcrumb: User Interface (HUD/Menu) > UI Overview > UI Dynamic Textures
- Parent: UI Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934088)

##
Overview

##
Sections

[Sections](#sections)
[Material Setup](#material-setup)
[Interaction on Dynamic Textures](#interaction-on-dynamic-textures)

##
Material Setup

It is possible to Display any UIElement as a dynamic texture on objects.

To do so you have to create a new material and setup the
Diffuse
 texture with the name of the UIElement and assign this material to your object.

The Diffuse texture name simply uses the name of the element plus the
.ui
 extension. You also have to change the TexType to
"Dynamic 2D-Map"
.

E.g. to Display the
USMPlayer
 (defined in
`
Libs/UI/UIElements/USMPlayer.xml
`
) use
USMPlayer.ui
.

You can also specify an InstanceID by using
*
UIElementName@InstanceID.ui
*
 (e.g.
*
USMPlayer@1.ui
*
).

Now you can use, for example, a proximity trigger to start the video playback on this object.

If you enter the trigger, the video is displayed on the object.

##
Interaction on Dynamic Textures

Since the assigned UIElement can be used in any UIAction, you can setup the interactive Flash like any other UIElement.
