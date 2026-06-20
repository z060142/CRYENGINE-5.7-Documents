# General

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448507
- Page ID: 76448507
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > General
- Parent: GamePlatform Features (Discord/Steam)

## Content

## Overview

There are various service level interfaces to a platform that don't specifically fall into the other categories.

This includes getting service information (such as whether the service is available), as well as some platform level events such as service errors or shutdown events.

The GamePlatformPlugin also provides each service with "Environment Variables", which allow the implementation to provide data from a platform that doesn't have an abstracted interface.

### General Service Functions

#### GetApplicationId

Retrieves the Application ID of the game on the platform.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::GetApplicationId
Flow Graph Nodes | GamePlatform:General:ApplicationId
Schematyc Nodes | Function::GamePlatform::Service::General::GetApplicationId

#### GetBuildId

Retrieves the Build ID of the game on the platform.

Platform(s) | Steam
--- | ---
API | Cry::GamePlatform::IService::GetBuildId
Flow Graph Nodes | GamePlatform:General:BuildId
Schematyc Nodes | Function::GamePlatform::Service::General::GetBuildId

#### GetEnvironmentValue

Retrieves the Environment Variable of the platform.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::GetEnvironmentValue
Flow Graph Nodes | GamePlatform:General:GetEnvironmentVariable
Schematyc Nodes | Function::GamePlatform::Service::General::GetEnvironmentValue

#### GetService

Retrieves details of the registered game platform service.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IPlugin::GetService
Flow Graph Nodes | GamePlatform:General:GetService
Schematyc Nodes | Function::GamePlatform::Service::General::GetServiceName

#### MarkContentCorrupt

Tells the platform to verify the data files on next launch.

Platform(s) | Steam
--- | ---
API | Cry::GamePlatform::IService::MarkContentCorrupt
Flow Graph Nodes | GamePlatform:General:MarkContentCorrupt
Schematyc Nodes | Function::GamePlatform::Service::General::MarkContentCorrupt

#### OwnsApplication

Checks if the local user owns the specified application on the platform.

Platform(s) | Steam
--- | ---
API | Cry::GamePlatform::IService::OwnsApplication
Flow Graph Nodes | GamePlatform:General:OwnsApplication
Schematyc Nodes | Function::GamePlatform::Service::General::OwnsApplication

### General Service Events

#### OnEnvironmentVariableChanged

Fired when an Environment Variable is updated.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::IListener::OnEnvironmentVariableChanged
Flow Graph Nodes | GamePlatform:Listener:Service:OnEnvironmentVariableChanged
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Service::OnEnvironmentVariableChanged

#### OnOverlayActivated

Fired when an overlay (for example, the Steam overlay) has been activated by the user.

Platform(s) | Steam
--- | ---
API | Cry::GamePlatform::IService::IListener::OnOverlayActivated
Flow Graph Nodes | GamePlatform:Listener:Service:OnOverlayActivated
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Service::OnOverlayActivated

#### OnShutdown

Fired when the service is about to shut down.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::IListener::OnShutdown
Flow Graph Nodes | GamePlatform:Listener:Service:OnShutdown
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Service::OnShutdown

[General Service Functions](#general-service-functions)[GetApplicationId](#getapplicationid)[GetBuildId](#getbuildid)[GetEnvironmentValue](#getenvironmentvalue)[GetService](#getservice)[MarkContentCorrupt](#markcontentcorrupt)[OwnsApplication](#ownsapplication)[General Service Events](#general-service-events)[OnEnvironmentVariableChanged](#onenvironmentvariablechanged)[OnOverlayActivated](#onoverlayactivated)[OnShutdown](#onshutdown)
