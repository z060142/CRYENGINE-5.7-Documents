# Character Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44961853
- Page ID: 44961853
- Breadcrumb: Editor Tools > Animation Tab > Character Tool
- Parent: Animation Tab

## Child Pages

- [Character Tool - Display Options](Character%20Tool/Character%20Tool%20-%20Display%20Options.md)
- [Character Tool - Properties Panel](Character%20Tool/Character%20Tool%20-%20Properties%20Panel.md)
- [Animation Compression - Character Tool](Character%20Tool/Animation%20Compression%20-%20Character%20Tool.md)
- [Animation Events - Character Tool](Character%20Tool/Animation%20Events%20-%20Character%20Tool.md)
- [Animation Import - Character Tool](Character%20Tool/Animation%20Import%20-%20Character%20Tool.md)
- [Attachment System Tutorial - Character Tool](Character%20Tool/Attachment%20System%20Tutorial%20-%20Character%20Tool.md)
- [Blend Spaces - Character Tool](Character%20Tool/Blend%20Spaces%20-%20Character%20Tool.md)
- [Character Attachments - Character Tool](Character%20Tool/Character%20Attachments%20-%20Character%20Tool.md)
- [Creating Character Definition - Character Tool](Character%20Tool/Creating%20Character%20Definition%20-%20Character%20Tool.md)

## Content

## Overview

The Character Tool is used for setting up character definitions by importing assets authored in third-party tools and making them available to be used within CRYENGINE. A fully authored character usually consists of models, skeleton, physical properties and an associated animation set. The tool also enables interactive control and adjustment of animations as well as the collider proxy setup. The latter is used for interaction with the physical world in the game.

The concept of the Character Tool is not only associated with characters (humans, animals etc.). Think of the tool in a way that handles all objects with animations associated with them. i.e. characters (*.cdf), weapons (*.cdf), vehicles (*.cga) etc.
To open the Character Tool, go to **Tools -> Animation -> Character Tool**.

![Image](https://www.cryengine.com/docs/static/attachments/44961857)

Here are four core UI components of the Character Tool:

### 1. Menu

The menu in the Character Tool has four sub-menus:

#### File

Option | Description
--- | ---
**New Character...** | Create a new character from scratch.
**Open Character...** | Open an already saved character.
**Recent Characters** | Shows a list of recently opened character files and their locations.
**Save All** | Saves all modified assets. (Assets which have been modified and not yet saved in this CT session).
**Import Animation Layers** | Import previously exported [animation layers](Character%20Tool.md#CharacterTool-animationlayers).
**Export Animation Layers** | Export existing [animation layers](Character%20Tool.md#CharacterTool-animationlayers).
**Clean Compiled Animations...** | Shows a window allowing to run a batch clear of i_caf compilation cache.
**Resave AnimSettings...** | Shows a window allowing to perform a batch force save of all animsettings files.
**Import FBX** | - **Skin -** Opens the Import Skin tool so you can import the skin of an asset separately. - ** Animation -** Opens the Import Animation tool so you can import the animations of an asset separately. - ** Skeleton -** Opens the Import Skeleton tool so you can import the skeleton of an asset separately. It is also possible to import the entire FBX, including skin, animation and skeleton, by dragging and dropping it into the Viewport of the Character Tool. However, when doing it this way, the skins will not automatically be attached to the character. It is recommended to drag and drop the FBX into the Asset Browser instead, and then open the character in the Character Tool.

#### View

Shows or hides the different panels within the Character Tool.

#### Layout

Option | Description
--- | ---
**Save Layout...** | Saves the layout of the Character Tool.
**Remove** | Removes a saved layout.
**Reset to Default** | Resets the layout of the Character tool.

#### Help

Opens the documentation page for this tool.

### 2. Assets

The **Assets** panel is the core of the Character Tool UI. It is placed on the left side of the window by default.

It gives an overview of all character-related assets.

As soon as you select an entry of your interest, its properties will appear in the **Properties** panel on the right side.

#### Context menu (right-click)

Each item within the tree has a context menu with available actions. Depending on what kind of asset you have selected, this context menu can consist of any number of the following options:

Option | Description
--- | ---
**Copy Name** | Copies name of the selected asset entry to the clipboard.
**Copy Path** | Copies file path of the selected asset entry to the clipboard.
**Paste Selection** | Selects an asset entry based on the file path currently contained in the clipboard.
**Revert** | Reverts a modified asset back to its last saved state.
**Save** | Saves a modified asset to its own file.
**Save As...** | Saves a modified asset to another file.
**Delete** | Deletes an asset (completely).
**Show in Explorer** | Shows the file or *.pak file containing the asset in the Windows Explorer.

For **Animations**, the following options are also available:

Option | Description
--- | ---
**Export HTR+I_CAF (Lossy)** | Exports a compressed animation asset (caf) back to the i_caf format. The generated i_caf file will contain compression artifacts introduced by the caf compilation process.
**Force Recompile** | Clears i_caf compilation cache for the selected animation asset and re-compresses it again.
**Generate Footsteps** | Shows up a windows allowing to automatically generate footstep animation events for the selected animation asset.

#### Filtering

There are two ways to filter the tree in the Assets panel:

- By using the **Search bar** and typing part of the name of the asset you're looking for (i.e. "strafe" for all assets/animations etc. containing "strafe")
- By using the **drop-down menu next to the Search bar** to show: All types, Animations, Characters, Compression and Skeletons.

#### Multiple Asset browser panes

You can have multiple instances of the **Assets** panel open. To create a new one use the ** Split Pane** button in the title of the ** Assets** panel:

![Image](https://www.cryengine.com/docs/static/attachments/44961863) *Split Pane button*

#### Columns

Note that right clicking on the tree header (where the **Name** string is shown) opens a context menu that allows you to show additional columns like ** Size**, ** Pak** and ** Audio** events.

### 3. Viewport

Here the loaded character will be shown.

The Viewport uses Sandbox standard navigation: **WASD** for movement, ** RMB** for camera rotation and ** Middle Mouse Button** to pan the camera.

In the top right you will see four buttons, **Display Options**, ** Edit Proxies**, ** Clear Proxies** and ** Test Ragdoll**.

#### Display Options

The Display Options determine how the scene is displayed in the Character Tool. These settings are not saved in the character files, they are purely for preview purposes.

[**See here**](Character%20Tool/Character%20Tool%20-%20Display%20Options.md) for descriptions of these options.

#### Edit Proxies

Here you can create and edit proxies for your character. **[See here](Character%20Tool/Character%20Attachments%20-%20Character%20Tool.md)** for more information.

#### Clear Proxies

Removes all proxies from the character.

#### Test Ragdoll

Launches a PhysDebugger instance with the current ragdoll.

It's possible to launch several instances of it to compare several iterations of the ragdoll.

### 4. Scene Parameters

A scene is set up only for previewing purposes and consists of:

![Image](https://www.cryengine.com/docs/static/attachments/44961854)

Parameter | Description
--- | ---
**Character** | You can use this entry to load a new character by clicking on the **Folder** button. (this is an alternative way to select a character as opposed to selecting from the Asset tree panel on the left side).
**Animation Layers** | Here the played animations are set up. Whenever you select an animation in the Assets panel, one will be assigned to the active animation layer (highlighted with a bold text and pressed button). You can add new animation layers by using the little button located next to it. You can remove animation layers through the context menu (RMB on the number left to the layer button). Blend spaces, aim- and look-poses expose additional settings.
**Blend Shapes** | Shows blend shape sliders, when the character contains blend shapes.

#### AnimEvent Players

The options in this section were created for use with a tool that was developed internally, but not released to the public. As such, these options will not be of use to users outside of Crytek.

### 5. Properties

There are many properties that can appear in the Properties panel, depending on what is selected. See [this page](Character%20Tool/Character%20Tool%20-%20Properties%20Panel.md) for details.

### 6. Playback

The **Playback** panel at the bottom can be used to scrub the timeline and provides playback options like looping of animations and playback speed. You can also change the timeline to be represented in seconds, frames or normalize the timeline from 0 - 1. The options gear offers further control on organizing how the timeline is represented.

[1. Menu](#1-menu)[2. Assets](#2-assets)[3. Viewport](#3-viewport)[4. Scene Parameters](#4-scene-parameters)[5. Properties](#5-properties)[6. Playback](#6-playback)
