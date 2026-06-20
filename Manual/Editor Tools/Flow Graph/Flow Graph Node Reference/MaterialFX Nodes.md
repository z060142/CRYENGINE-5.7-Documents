# MaterialFX Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450609
- Page ID: 29450609
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > MaterialFX Nodes
- Parent: Flow Graph Node Reference

## Content

### FlashGoTOAndPlayOnObject

Handles Material Flash GotoAndPlay.

![Image](https://www.cryengine.com/docs/static/attachments/29687863)

### FlashHandleFSCommand

Handles flash FS command.

![Image](https://www.cryengine.com/docs/static/attachments/29687862)

### FlashInvokeOnObject

Used for Material Flash Invoke.

![Image](https://www.cryengine.com/docs/static/attachments/29687861)

### HUDEndFX

The MaterialFX end node for an HUD.

![Image](https://www.cryengine.com/docs/static/attachments/29687860)

**Inputs**

Port | Type | Description
--- | --- | ---
**Trigger** | Any | MaterialFX end node

### HUDStartFX

The MaterialFX start node for an HUD.

![Image](https://www.cryengine.com/docs/static/attachments/29687859)

**Inputs**

Port | Type | Description
--- | --- | ---
**Start** | Any | Triggered automatically by the material effect

**Outputs**

Port | Type | Description
--- | --- | ---
**Started** | Any | Triggered when the material effect has started
**Distance** | Float | Outputs the distance to the player
**Param1** | Float | Custom parameter 1
**Param2** | Float | Custom parameter 2
**Intensity** | Float | Dynamic value set by game code
**BlendOutTime** | Float | Outputs the material effect blend out time in seconds

[FlashGoTOAndPlayOnObject](#flashgotoandplayonobject)[FlashHandleFSCommand](#flashhandlefscommand)[FlashInvokeOnObject](#flashinvokeonobject)[HUDEndFX](#hudendfx)[HUDStartFX](#hudstartfx)
