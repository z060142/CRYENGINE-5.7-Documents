# UI Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450638
- Page ID: 29450638
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > UI Nodes
- Parent: Flow Graph Node Reference

## Content

##
Action

##
Control

Controls an UI Action.

[Image: /docs/static/attachments/29688049]

##
End

End node for UI Action.

[Image: /docs/static/attachments/29688048]

##
Start

Start node for UI Action.

[Image: /docs/static/attachments/29688047]

##
Display

##
Advance

Node to advance a UIElement.
**

**

[Image: /docs/static/attachments/29688046]

##
Config

Node to setup flags for UIElements.

[Image: /docs/static/attachments/29688045]

##
Constraints

Node to setup constraints for UIElements.

[Image: /docs/static/attachments/29688044]

##
Display

Node to display/hide/reload UIElements.

[Image: /docs/static/attachments/29688043]

##
Layer

Node to setup layer of UIElements.

[Image: /docs/static/attachments/29688042]

##
RayToFlashSpace

Casts a ray, finds the hitposition in flash space and calls a function.

[Image: /docs/static/attachments/29688041]

##
ScreenPos

Node to convert a screen position (Value 0-1) to a actual X,Y position in the flash asset.

[Image: /docs/static/attachments/29688040]

##
UIElementInstance

Node to delete instances of UIElements and receive notifications about new/destroyed instances of an UIElements.

[Image: /docs/static/attachments/29688039]

##
UIElementListener

Node receive notifications about display/hide/load/unload of an UIElements

[Image: /docs/static/attachments/29688038]

##
WorldScreenPos

Node to convert a world position to a actual X,Y,Z and Scale value in the flash asset.

[Image: /docs/static/attachments/29688037]

##
Events

##
OnConnect

Triggered if connect to a server (Not in Editor!).

[Image: /docs/static/attachments/29688029]

##
OnDisconnect

Triggered if disconnect to a server (Not in Editor!).

[Image: /docs/static/attachments/29688028]

##
OnGamePause

Triggered if game is paused (Not in Editor!).

[Image: /docs/static/attachments/29688027]

##
OnGameResume

Triggered if game is resumed (Not in Editor!).

[Image: /docs/static/attachments/29688026]

##
OnGameplayEnded

Triggered if gameplay ends (Not in Editor!).

[Image: /docs/static/attachments/29688025]

##
OnGamePlayStarted

Triggered if gameplay starts (Not in Editor!).

[Image: /docs/static/attachments/29688024]

##
OnLoadingComplete

Triggered if loading is complete (Not in Editor!)

[Image: /docs/static/attachments/29688023]

##
OnLoadingError

Triggered if an error occurred during loading (Not in Editor!).

[Image: /docs/static/attachments/29688022]

##
OnLoadingProgress

Triggered during loading progress (Not in Editor!)

[Image: /docs/static/attachments/29688021]

##
OnLoadingStart

Triggered if level is loading (Not in Editor!).

[Image: /docs/static/attachments/29688020]

##
OnReload

Triggered if UI is reloaded (Not in Editor!).

[Image: /docs/static/attachments/29688019]

##
OnSystemShutDown

Triggered if system shuts down (Not in Editor!).

[Image: /docs/static/attachments/29688018]

##
OnSystemStarted

Triggered if system is started (Not in Editor!).

[Image: /docs/static/attachments/29688017]

##
OnUnloadComplete

Triggered if level unload is completed (Not in Editor!).

[Image: /docs/static/attachments/29688016]

##
OnUnloadStart

Triggered if level unload starts (Not in Editor!).

[Image: /docs/static/attachments/29688015]

##
Functions

##
UnloadAllElements

Unloads all UI Elements (Skip Elements that are defined in the Array input).

[Image: /docs/static/attachments/29688035]

##
MovieClip

##
GotoAndPlay

Provides Access to MovieClips.

[Image: /docs/static/attachments/29688032]

##
PosRotScale

Provides Pos/Rot/Scale access to MovieClips.

[Image: /docs/static/attachments/29688031]

##
Visible

Provides Visible/Alpha access to MovieClips.

[Image: /docs/static/attachments/29688030]

##
Template

##
CreateMovieClip

Create a MovieClip and attaches it to the given Parent MovieClip.

[Image: /docs/static/attachments/29688034]

##
RemoveMovieCLip

Removes a MovieClip.

[Image: /docs/static/attachments/29688033]

##
Util

##
FromArray

Gets Values from an UI Array.

[Image: /docs/static/attachments/29688014]

##
FromArrayByIndex

used to get specific Value from UI Array.

[Image: /docs/static/attachments/29688013]

##
MergeArrays

Used to merge two Arrays.

[Image: /docs/static/attachments/29688012]

##
Platform

Node to get current platform, works also with selected platform of UIEmulator.

[Image: /docs/static/attachments/29688011]

##
ToArray

Used to Create an UI Array.

[Image: /docs/static/attachments/29688010]

##
UIDelay

This node will delay passing the signal from [In] to [Out] for the specified number of seconds in [Delay].

[Image: /docs/static/attachments/29688009]

##
Variable

##
Array

Used to provide access to Arrays.

[Image: /docs/static/attachments/29688008]

##
Var

Used to provide access to variables.

[Image: /docs/static/attachments/29688007]

[#action](
Action
)
[#display](
Display
)
[#events](
Events
)
[#functions](
Functions
)
[#movieclip](
MovieClip
)
[#template](
Template
)
[#util](
Util
)
[#variable](
Variable
)
