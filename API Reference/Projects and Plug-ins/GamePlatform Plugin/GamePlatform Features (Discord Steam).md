# GamePlatform Features (Discord/Steam)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448424
- Page ID: 76448424
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam)
- Parent: GamePlatform Plugin

## Child Pages

- [Accounts](GamePlatform Features (Discord Steam)/Accounts.md)
- [Achievements](GamePlatform Features (Discord Steam)/Achievements.md)
- [Catalog](GamePlatform Features (Discord Steam)/Catalog.md)
- [General](GamePlatform Features (Discord Steam)/General.md)
- [Leaderboard](GamePlatform Features (Discord Steam)/Leaderboard.md)
- [Matchmaking & Lobbies](GamePlatform Features (Discord Steam)/Matchmaking & Lobbies.md)
- [Networking*](GamePlatform Features (Discord Steam)/Networking.md)
- [Overlays](GamePlatform Features (Discord Steam)/Overlays.md)
- [Remote Storage](GamePlatform Features (Discord Steam)/Remote Storage.md)
- [Rich Presence](GamePlatform Features (Discord Steam)/Rich Presence.md)

## Content

The following pages provide details on each GamePlatform plugin feature (matchmaking, rich presence, etc.) from an abstracted point of view. Certain implementations may have nuances involved that will require extra steps to achieve the same goal, while a few of them may not even be supported by a specific platform service (for example,
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
Remote Storage
)
 only works on Steam). Not every service matches one-to-one with each other, and therefore some discrepancies will be noticed between different implementations.

Each feature that the GamePlatform plugin abstracts is categorized in code, and in nodes provided by Flow Graph and Schematyc (Experimental). That said, there are variations between the code categorization, and the designer level nodes categorization.

##
In This Section

The following is a list of GamePlatform plugin features (plus corresponding functions and events) available to the Steam and/or Discord platforms:

Feature
 |
Type
 |
Name
 |
Platform(s)
 |

##
Accounts

 |
Functions
 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
IsFriendWith
)

 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
GetAccountInfo
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
GetAvatar
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
GetBlockedAccounts
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
GetFriendAccounts
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
GetLocalAccount
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
RequestUserInformation
)
 |
Steam
 |

Events

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
OnAccountAdded
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
OnAccountRemoved
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
OnAvatarImageLoaded
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448430](
OnPersonaStateChanged
)
 |
Steam
 |

##
Achievements

 |
Service Functions

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
Download
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
Get
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
GetAchievement
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
ResetAchievements
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
ResetStatistics
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
Set
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
Upload
)
 |
Steam
 |

Specific Functions
 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
Achieve
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
GetName
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
GetProgress
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
Iscompleted
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
Reset
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448466](
SetProgress
)
 |
Steam
 |

##
Catalog

 |
Service Functions

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448503](
BrowseCatalog
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448503](
GetLicenses
)
 |
Steam
 |

Service Events

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448503](
OnCatalogReceived
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448503](
OnMicroTransactionAuthorizationResponse
)
 |
Steam
 |

##
General

 |
Service Functions

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448507](
GetApplicationId
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448507](
GetBuildId
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448507](
GetEnvironmentValue
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448507](
GetService
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448507](
MarkContentCorrupt
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448507](
OwnsApplication
)
 |
Steam
 |

Service Events

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448507](
OnEnvironmentVariableChanged
)
 |
Discord, Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448507](
OnOverlayActivated
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448507](
OnShutdown
)
 |
Discord, Steam
 |

##
Leaderboard

 |
Service Functions
 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448580](
GetLeaderboardData
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448580](
UpdateLeaderboardScore
)
 |
Steam
 |

Service Events
 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448580](
OnLeaderboardEntryDownloaded
)
 |
Steam
 |

##
Matchmaking & Lobbies

 |
Matchmaking Service Functions
 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
AddLobbyQueryFilterString
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
CreateLobby
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
GetQueriedLobbyIdByIndex
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
GetUserLobby
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
JoinLobby
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
QueryLobbies
)
 |
Steam
 |

Matchmaking Service Events

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnCreatedLobby
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnJoinedLobby
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnLobbyJoinFailed
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnLobbyQueryComplete
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnPreJoinLobby
)
 |
Steam
 |

Lobby Functions

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
GetData
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
GetMemberAtIndex
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
GetMemberData
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
GetMemberLimit
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
GetNumMembers
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
GetOwnerId
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
Leave
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
SendChatMessage
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
SetData
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
SetMemberData
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
ShowInviteDialog
)
 |
Steam
 |

Lobby Events

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnChatMessage
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnLeave
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnLobbyDataUpdate
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnPlayerBanned
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnPlayerDisconnected
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnPlayerEntered
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnPlayerKicked
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnPlayerLeft
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
OnUserDataUpdate
)
 |
Steam
 |

Event Registration Functions
 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448584](
StartStopLobbyListener
)
 |
Steam
 |

##
Networking

 |
Service Functions
 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448622](
CloseSession
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448622](
FilterText
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448622](
GetAuthToken
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448622](
IsLoggedIn
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448622](
IsPacketAvailable
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448622](
ReadPacket
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448622](
SendPacket
)
 |
Steam
 |

Service Events

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448622](
OnCheckMultiplayerAccess
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448622](
OnGetSteamAuthTicketResponse
)
 |
Steam
 |

##
Overlays

 |
Service Functions

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448627](
OpenBrowser
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448627](
OpenDialog
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448627](
OpenDialogWithTargetUser
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448627](
OpenPurchaseOverlay
)
 |
Steam
 |

##
Remote Storage

 |
Service Functions

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
IsEnabled
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
GetFile
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
GetSharedFile
)
 |
Steam
 |

Service Events

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
OnDownloadedSharedFile
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
OnFileShared
)
 |
Steam
 |

Remote File Functions

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
Delete
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
Download
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
Exists
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
GetCacheList
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
GetFileSize
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
GetIdentifier
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
GetSharedFileSize
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
Read
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
ReadDataToFile
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
ReadSharedData
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
ReadSharedDataToFile
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
ReleaseRemoteFile
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
ReleaseSharedfile
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
ShareRemoteFile
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
WriteFromFile
)
 |
Steam
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
WriteData
)
 |
Steam
 |

User Generated Content Service Functions
 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448629](
CreateContent
)
 |
Steam
 |

##
Rich Presence

 |
Service Functions

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448635](
GetRichPresence
)
 |
Discord
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448635](
SetRichPresence
)
 |
Discord
 |

[/docs/static/engines/cryengine-5/categories/23756813/pages/76448635](
SetStatus
)
 |
Discord, Steam
 |

[#in-this-section](
In This Section
)
[#accounts](
Accounts
)
[#achievements](
Achievements
)
[#catalog](
Catalog
)
[#general](
General
)
[#leaderboard](
Leaderboard
)
[#matchmaking-and-lobbies](
Matchmaking & Lobbies
)
[#networking](
Networking
)
[#overlays](
Overlays
)
[#remote-storage](
Remote Storage
)
[#rich-presence](
Rich Presence
)
