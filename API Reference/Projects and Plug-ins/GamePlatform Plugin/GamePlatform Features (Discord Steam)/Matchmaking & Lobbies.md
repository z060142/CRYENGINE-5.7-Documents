# Matchmaking & Lobbies

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448584
- Page ID: 76448584
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > Matchmaking & Lobbies
- Parent: GamePlatform Features (Discord/Steam)

## Content

##
Overview

The Matchmaking module abstracts the matchmaking functionality of each platform into a more unified interface. It allows you to create and search for lobbies based on user defined lobby data or player counts. This allows an implementation of skill grouping or custom games with custom properties set by the game clients.

Each platform implements matchmaking in their own way, and you may need to setup additional properties of your game on your platform product manager to allow certain matchmaking functionalities.
This documentation also includes lobby specific functionality; while lobbies do not rely on matchmaking, they are usually used in tandem.

Lobbies provide an abstracted set of functionalities, such as setting lobby data (game type, for example), as well as user data (which team the user prefers, for instance) and text communication between each lobby member. On some platforms, a single user can be a part of multiple lobbies and each lobby will have its own functions and events (for example, to leave a specific lobby).

##
Matchmaking Service Functions

##
AddLobbyQueryFilterString

Adds a lobby query filter that will be used on the next
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584#Matchmaking&Lobbies-querylobbies](
 QueryLobbies
)
call.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking::AddLobbyQueryFilterString
 |

Flow Graph Nodes
 |
GamePlatform:Matchmaking:AddLobbyQueryFilterString
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Lobby::AddQueryLobbiesFilter
 |

##
CreateLobby

Attempts to create a new matchmaking lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking
::CreateLobby
 |

Flow Graph Nodes
 |
GamePlatform:Matchmaking:CreateLobby
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::CreateLobby
 |

##
GetQueriedLobbyIdByIndex

Returns the lobby at the specified index from the
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584#Matchmaking&Lobbies-querylobbies](
 QueryLobbies
)
result (after the
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584#Matchmaking&Lobbies-lobbyquerycomplet](
OnLobbyQueryComplete
)
event).

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking
::GetQueriedLobbyIdByIndex
 |

Flow Graph Nodes
 |
GamePlatform:Matchmaking:GetQueriedLobbyIdByIndex
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::GetQueriedLobbyIdByIndex
 |

##
GetUserLobby

Attempts to get the lobby identifier the specified user resides in (if any).

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking
::GetUserLobby
 |

Flow Graph Nodes
 |
GamePlatform:Matchmaking:GetUserLobby
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::GetUserLobby
 |

##
JoinLobby

Makes the local user join the specified lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking
::JoinLobby
 |

Flow Graph Nodes
 |
GamePlatform:Matchmaking:JoinLobby
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::JoinLobby
 |

##
QueryLobbies

Queries the backend for lobbies that match any and all filters added since the last QueryLobbies call.

Listen for the
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584#Matchmaking&Lobbies-lobbyquerycomplete](
 OnLobbyQueryComplete
)
event after querying the backend.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking
::QueryLobbies
 |

Flow Graph Nodes
 |
GamePlatform:Matchmaking:QueryLobbies
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::QueryLobbies
 |

##
Matchmaking Service Events

##
OnCreatedLobby

Fired when a lobby has been created by the local user.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking::IListener
::OnCreatedLobby
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Matchmaking:OnCreatedLobby
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Matchmaking::OnCreatedLobby
 |

##
OnJoinedLobby

Fired when the local user joins a lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking::IListener::OnJoinedLobby
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Matchmaking:OnJoinedLobby
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Matchmaking::OnJoinedLobby
 |

##
OnLobbyJoinFailed

Fired if a lobby join request fails.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking::IListener
::OnLobbyJoinFailed
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Matchmaking:OnLobbyJoinFailed
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::
Matchmaking
::OnLobbyJoinFailed
 |

##
OnLobbyQueryComplete

Fired on completion of a lobby query request.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking::IListener
::OnLobbyQueryComplete
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Matchmaking:OnLobbyQueryComplete
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Matchmaking::OnLobbyQueryComplete
 |

##
OnPreJoinLobby

Fired when the local user attempts to join a lobby before receiving a response from the platform.

When a user tries to join a lobby, the response is either going to be success or failure. The
**
OnPreJoinLobby
**
 is fired between the request to join and the response from the server that the request was a success.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IMatchmaking::IListener
::OnPreJoinLobby
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Matchmaking:OnPreJoinLobby
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Matchmaking::OnPreJoinLobby
 |

##
Lobby Functions

##
GetData

Retrieves lobby data of the specified key.

The data is made up of a key-value pair. The key corresponds to the name of the data, while the value is the data itself.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::GetData
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:GetData
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::GetData
 |

##
GetMemberAtIndex

Queries the lobby for the member at the specified index.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::GetMemberAtIndex
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:GetMemberAtIndex
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::GetMemberAtIndex
 |

##
GetMemberData

Gets the meta-data of the user in the lobby by key name.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::GetMemberData
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:GetMemberData
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::GetMemberData
 |

##
GetMemberLimit

Queries the specified lobby for the maximum number of users that can inhabit it.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::GetMemberLimit
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:GetMemberLimit
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::GetMemberLimit
 |

##
GetNumMembers

Queries the specified lobby for the current number of users that are inhabiting it.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::GetNumMembers
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:GetMemberCount
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::GetNumMembers
 |

##
GetOwnerId

Queries the lobby for the member that owns the lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::GetOwnerId
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:GetOwnerId
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::GetOwnerId
 |

##
Leave

Makes the local user leave the specified lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::Leave
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:Leave
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::Leave
 |

##
SendChatMessage

Sends a message to the specified lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::SendChatMessage
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:SendChatMessage
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Lobby::SendChatMessage
 |

##
SetData

Sets the lobby data of the key to the specified value.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::SetData
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:SetData
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::SetData
 |

##
SetMemberData

Sets the meta-data of the local user in the lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::SetMemberData
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:SetLocalMemberData
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::SetLocalMemberData
 |

##
ShowInviteDialog

Shows the platform-specific invite dialog to invite friends to the current lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby
::ShowInviteDialog
 |

Flow Graph Nodes
 |
GamePlatform:Lobby:ShowInviteDialog
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Lobby
::ShowInviteDialog
 |

##
Lobby Events

##
OnChatMessage

Fired for each message received in the lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::IListener
::OnChatMessage
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Lobby:OnChatMessage
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::
Lobby
::OnChatMessage
 |

##
OnLeave

Fired when the local user leaves the lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::IListener::OnLeave
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Lobby:OnLeave
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Lobby::OnLeave
 |

##
OnLobbyDataUpdate

Fired when the lobby data has been updated.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::IListener
::OnLobbyDataUpdate
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Lobby:OnLobbyDataUpdate
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::OnLobbyDataUpdate
 |

##
OnPlayerBanned

Fired when a lobby member is banned from the lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::IListener
::OnPlayerBanned
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Lobby:OnPlayerBanned
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::
Lobby
::OnPlayerBanned
 |

##
OnPlayerDisconnected

Fired when a lobby member loses connection to the lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::IListener
::OnPlayerDisconnected
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Lobby:OnPlayerDisconnected
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::
Lobby
::OnPlayerDisconnected
 |

##
OnPlayerEntered

Fired when a member enters the lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::IListener
::OnPlayerEntered
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Lobby:OnPlayerEntered
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::
Lobby
::OnPlayerEntered
 |

##
OnPlayerKicked

Fired when a lobby member is kicked from the lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::IListener
::OnPlayerKicked
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Lobby:OnPlayerKicked
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::
Lobby
::OnPlayerKicked
 |

##
OnPlayerLeft

Fired when a lobby member intentionally leaves the lobby.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::IListener::OnPlayerLeft
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Lobby:OnPlayerLeft
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Lobby::OnPlayerLeft
 |

##
OnUserDataUpdate

Fired when a lobby member updates their member data.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IUserLobby::IListener
::OnUserDataUpdate
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Lobby:OnUserDataUpdate
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::
Lobby
::OnUserDataUpdate
 |

##
Event Registration Functions

##
StartStopLobbyListener

Starts or stops lobby event listeners.

This function handles starting and stopping events for specific lobbies. A user can be connected to more than one lobby at a time, and so control is needed over which lobbies are being listened to (for instance, when the local user leaves a lobby).

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IPlatformEventManager::[Start|Stop]Listening
 |

Flow Graph Nodes
 |
GamePlatform:Listener:RemoteStorage:StartStopLobbyListener
 |

Schematyc Nodes
 |
Function::Components::PlatformSignalReceiver::StartStopRemoteFileListener
 |

If the local user leaves a lobby, you technically do not need to call StartStopLobbyListener as all listeners to that lobby will be unregistered when you leave the lobby

[#matchmaking-service-functions](
Matchmaking Service Functions
)
[#matchmaking-service-events](
Matchmaking Service Events
)
[#lobby-functions](
Lobby Functions
)
[#lobby-events](
Lobby Events
)
[#event-registration-functions](
Event Registration Functions
)
