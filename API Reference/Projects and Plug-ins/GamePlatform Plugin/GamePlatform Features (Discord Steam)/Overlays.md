# Overlays

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448627
- Page ID: 76448627
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > Overlays
- Parent: GamePlatform Features (Discord/Steam)

## Content

## Overview

The overlay interface of the GamePlatform plugin abstracts the various overlay options provided by the platform APIs.

Due to platforms providing various different overlays unique to them, some overlays are only available with specific services.

### Overlay Service Functions

#### OpenBrowser

Opens a platform browser on the platform with the specified target address.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IService::OpenBrowser
Flow Graph Nodes | GamePlatform:Overlay:OpenBrowser
Schematyc Nodes | Function::GamePlatform::Service::Overlay::OpenBrowser

#### OpenDialog

Opens the specified platform dialog (for example, Add Friend).

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IService::OpenDialog
Flow Graph Nodes | GamePlatform:Overlay:OpenDialog
Schematyc Nodes | Function::GamePlatform::Service::Overlay::OpenDialog

#### OpenDialogWithTargetUser

Opens the specified dialog with the specified user on the platform (for example, private message chat).

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IService::OpenDialogWithTargetUser
Flow Graph Nodes | GamePlatform:Overlay:OpenDialogWithTarget
Schematyc Nodes | Function::GamePlatform::Service::Overlay::OpenDialogWithTargetUser

#### OpenPurchaseOverlay

Tries to open the purchase overlay for the specified product.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IService::OpenPurchaseOverlay
Flow Graph Nodes | GamePlatform:Overlay:OpenPurchaseOverlay
Schematyc Nodes | Function::GamePlatform::Service::Overlay::OpenPurchaseOverlay

[Overlay Service Functions](#overlay-service-functions)[OpenBrowser](#openbrowser)[OpenDialog](#opendialog)[OpenDialogWithTargetUser](#opendialogwithtargetuser)[OpenPurchaseOverlay](#openpurchaseoverlay)
