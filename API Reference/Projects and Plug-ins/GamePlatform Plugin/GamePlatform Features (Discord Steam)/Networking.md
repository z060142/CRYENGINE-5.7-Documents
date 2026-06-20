# Networking*

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448622
- Page ID: 76448622
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > Networking*
- Parent: GamePlatform Features (Discord/Steam)

## Content

## Overview

The Networking abstraction attempts to unify basic networking features between the different platforms. This includes sending and receiving files between users, marking users that are in multiplayer mode, as well as checking if a user is logged in and has access to multiplayer services on the platform.

Since functionality varies between different platforms, some platform specific functions are required to facilitate the abstraction.

### Networking Service Functions

#### CloseSession

Closes a network session opened with [SendPacket](Networking.md#Networking%2A-sendpacket)between the local user and the specified account.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::INetworking::CloseSession
Flow Graph Nodes | GamePlatform:Network:CloseSession
Schematyc Nodes | Function::GamePlatform::Service::Networking::CloseSession

#### FilterText

Censors/filters the specified text on the platform. The output is limited to once per frame.

This is useful for chat censoring; some platforms require you to censor chats depending on the region or rating of a game.

The output may not trigger on the same frame.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IService::FilterText
Flow Graph Nodes | GamePlatform:Network:FilterText
Schematyc Nodes | Function::GamePlatform::Service::Networking::FilterText

#### GetAuthToken

Retrieves the authorization token used for web services on the specified platform.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IService::GetAuthToken
Flow Graph Nodes | GamePlatform:Network:AuthToken
Schematyc Nodes | Function::GamePlatform::Service::Networking::GetAuthToken

#### IsLoggedIn

Checks if the platform is logged in and access to the backend is available.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IService::IsLoggedIn
Flow Graph Nodes | GamePlatform:Network:IsLoggedIn
Schematyc Nodes | Function::GamePlatform::Service::Networking::IsLoggedIn

#### IsPacketAvailable

Checks if there is a data packet available via the platform network and if so, returns the size of the data.

This data is also binary. This means that if you read the data as a string, you may miss part of the data (binary can contain a binary zero, which for strings just means the end of the string).

Platforms | Steam
--- | ---
API | Cry::GamePlatform::INetworking::IsPacketAvailable
Flow Graph Nodes | GamePlatform:Network:IsPacketAvailable
Schematyc Nodes | Function::GamePlatform::Service::Networking::IsPacketAvailable

#### ReadPacket

Tries to read the next packet payload. The output of this function would be the Source Account Identifier, the data that was read (can be a string or binary buffer, depending on if C++ API/Flow Graph or Schematyc is used), and the number of bytes that was read from the packet.

The whole packet might have to be read multiple times until the total number of bytes read is equal to the size of the packet (obtained via [IsPacketAvailable](Networking.md#Networking%2A-ispacketavailable)).

Platforms | Steam
--- | ---
API | Cry::GamePlatform::INetworking::ReadPacket
Flow Graph Nodes | GamePlatform:Network:ReadPacket
Schematyc Nodes | Function::GamePlatform::Service::Networking::ReadPacket

#### SendPacket

Sends the data packet to the specified account via the platform network.

This is the counter function to ReadPacket; only packets that are sent can be read. One user will send data via SendPacket to another, who can then check for IsPacketAvailable and then read data using ReadPacket.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::INetworking::SendPacket
Flow Graph Nodes | GamePlatform:Network:SendPacket
Schematyc Nodes | Function::GamePlatform::Service::Networking::SendPacket

### Networking Service Events

#### OnCheckMultiplayerAccess

Fired when aa multiplayer access check request receives a response.

Platforms | Steam
--- | ---
API | N/A (callback provided to Cry::GamePlatform::IService::CanAccessMultiplayer)
Flow Graph Nodes | N/A (uses provided callback to activate output directly)
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Networking::OnCheckMultiplayerAccess

#### OnGetSteamAuthTicketResponse

Fired when a Steam Authentication token request receives a response.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IService::IListener::OnGetSteamAuthTicketResponse
Flow Graph Nodes | GamePlatform:Listener:Networking:OnGetSteamAuthTicketResponse
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Networking::OnGetSteamAuthTicketResponse

[Networking Service Functions](#networking-service-functions)[CloseSession](#closesession)[FilterText](#filtertext)[GetAuthToken](#getauthtoken)[IsLoggedIn](#isloggedin)[IsPacketAvailable](#ispacketavailable)[ReadPacket](#readpacket)[SendPacket](#sendpacket)[Networking Service Events](#networking-service-events)[OnCheckMultiplayerAccess](#oncheckmultiplayeraccess)[OnGetSteamAuthTicketResponse](#ongetsteamauthticketresponse)
