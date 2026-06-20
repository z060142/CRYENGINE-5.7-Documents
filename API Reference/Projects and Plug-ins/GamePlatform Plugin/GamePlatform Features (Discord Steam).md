# GamePlatform Features (Discord/Steam)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448424
- Page ID: 76448424
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam)
- Parent: GamePlatform Plugin

## Child Pages

- [Accounts](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md)
- [Achievements](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md)
- [Catalog](GamePlatform%20Features%20(Discord%20Steam)/Catalog.md)
- [General](GamePlatform%20Features%20(Discord%20Steam)/General.md)
- [Leaderboard](GamePlatform%20Features%20(Discord%20Steam)/Leaderboard.md)
- [Matchmaking & Lobbies](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md)
- [Networking*](GamePlatform%20Features%20(Discord%20Steam)/Networking.md)
- [Overlays](GamePlatform%20Features%20(Discord%20Steam)/Overlays.md)
- [Remote Storage](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md)
- [Rich Presence](GamePlatform%20Features%20(Discord%20Steam)/Rich%20Presence.md)

## Content

The following pages provide details on each GamePlatform plugin feature (matchmaking, rich presence, etc.) from an abstracted point of view. Certain implementations may have nuances involved that will require extra steps to achieve the same goal, while a few of them may not even be supported by a specific platform service (for example, [Remote Storage](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) only works on Steam). Not every service matches one-to-one with each other, and therefore some discrepancies will be noticed between different implementations.

Each feature that the GamePlatform plugin abstracts is categorized in code, and in nodes provided by Flow Graph and Schematyc (Experimental). That said, there are variations between the code categorization, and the designer level nodes categorization.

### In This Section

The following is a list of GamePlatform plugin features (plus corresponding functions and events) available to the Steam and/or Discord platforms:

Feature | Type | Name | Platform(s)
--- | --- | --- | ---
#### Accounts | Functions | [IsFriendWith](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Discord, Steam
[GetAccountInfo](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Discord, Steam |  |
[GetAvatar](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Discord, Steam |  |
[GetBlockedAccounts](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Discord, Steam |  |
[GetFriendAccounts](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Discord, Steam |  |
[GetLocalAccount](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Discord, Steam |  |
[RequestUserInformation](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Steam |  |
Events | [OnAccountAdded](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Discord, Steam |
[OnAccountRemoved](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Discord, Steam |  |
[OnAvatarImageLoaded](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Discord, Steam |  |
[OnPersonaStateChanged](GamePlatform%20Features%20(Discord%20Steam)/Accounts.md) | Steam |  |
#### Achievements | Service Functions | [Download](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam
[Get](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
[GetAchievement](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
[ResetAchievements](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
[ResetStatistics](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
[Set](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
[Upload](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
Specific Functions | [Achieve](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |
[GetName](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
[GetProgress](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
[Iscompleted](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
[Reset](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
[SetProgress](GamePlatform%20Features%20(Discord%20Steam)/Achievements.md) | Steam |  |
#### Catalog | Service Functions | [BrowseCatalog](GamePlatform%20Features%20(Discord%20Steam)/Catalog.md) | Steam
[GetLicenses](GamePlatform%20Features%20(Discord%20Steam)/Catalog.md) | Steam |  |
Service Events | [OnCatalogReceived](GamePlatform%20Features%20(Discord%20Steam)/Catalog.md) | Steam |
[OnMicroTransactionAuthorizationResponse](GamePlatform%20Features%20(Discord%20Steam)/Catalog.md) | Steam |  |
#### General | Service Functions | [GetApplicationId](GamePlatform%20Features%20(Discord%20Steam)/General.md) | Discord, Steam
[GetBuildId](GamePlatform%20Features%20(Discord%20Steam)/General.md) | Steam |  |
[GetEnvironmentValue](GamePlatform%20Features%20(Discord%20Steam)/General.md) | Discord, Steam |  |
[GetService](GamePlatform%20Features%20(Discord%20Steam)/General.md) | Discord, Steam |  |
[MarkContentCorrupt](GamePlatform%20Features%20(Discord%20Steam)/General.md) | Steam |  |
[OwnsApplication](GamePlatform%20Features%20(Discord%20Steam)/General.md) | Steam |  |
Service Events | [OnEnvironmentVariableChanged](GamePlatform%20Features%20(Discord%20Steam)/General.md) | Discord, Steam |
[OnOverlayActivated](GamePlatform%20Features%20(Discord%20Steam)/General.md) | Steam |  |
[OnShutdown](GamePlatform%20Features%20(Discord%20Steam)/General.md) | Discord, Steam |  |
#### Leaderboard | Service Functions | [GetLeaderboardData](GamePlatform%20Features%20(Discord%20Steam)/Leaderboard.md) | Steam
[UpdateLeaderboardScore](GamePlatform%20Features%20(Discord%20Steam)/Leaderboard.md) | Steam |  |
Service Events | [OnLeaderboardEntryDownloaded](GamePlatform%20Features%20(Discord%20Steam)/Leaderboard.md) | Steam |
#### Matchmaking & Lobbies | Matchmaking Service Functions | [AddLobbyQueryFilterString](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam
[CreateLobby](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[GetQueriedLobbyIdByIndex](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[GetUserLobby](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[JoinLobby](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[QueryLobbies](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
Matchmaking Service Events | [OnCreatedLobby](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |
[OnJoinedLobby](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnLobbyJoinFailed](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnLobbyQueryComplete](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnPreJoinLobby](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
Lobby Functions | [GetData](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |
[GetMemberAtIndex](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[GetMemberData](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[GetMemberLimit](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[GetNumMembers](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[GetOwnerId](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[Leave](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[SendChatMessage](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[SetData](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[SetMemberData](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[ShowInviteDialog](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
Lobby Events | [OnChatMessage](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |
[OnLeave](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnLobbyDataUpdate](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnPlayerBanned](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnPlayerDisconnected](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnPlayerEntered](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnPlayerKicked](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnPlayerLeft](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
[OnUserDataUpdate](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |  |
Event Registration Functions | [StartStopLobbyListener](GamePlatform%20Features%20(Discord%20Steam)/Matchmaking%20%26%20Lobbies.md) | Steam |
#### Networking | Service Functions | [CloseSession](GamePlatform%20Features%20(Discord%20Steam)/Networking.md) | Steam
[FilterText](GamePlatform%20Features%20(Discord%20Steam)/Networking.md) | Steam |  |
[GetAuthToken](GamePlatform%20Features%20(Discord%20Steam)/Networking.md) | Steam |  |
[IsLoggedIn](GamePlatform%20Features%20(Discord%20Steam)/Networking.md) | Steam |  |
[IsPacketAvailable](GamePlatform%20Features%20(Discord%20Steam)/Networking.md) | Steam |  |
[ReadPacket](GamePlatform%20Features%20(Discord%20Steam)/Networking.md) | Steam |  |
[SendPacket](GamePlatform%20Features%20(Discord%20Steam)/Networking.md) | Steam |  |
Service Events | [OnCheckMultiplayerAccess](GamePlatform%20Features%20(Discord%20Steam)/Networking.md) | Steam |
[OnGetSteamAuthTicketResponse](GamePlatform%20Features%20(Discord%20Steam)/Networking.md) | Steam |  |
#### Overlays | Service Functions | [OpenBrowser](GamePlatform%20Features%20(Discord%20Steam)/Overlays.md) | Steam
[OpenDialog](GamePlatform%20Features%20(Discord%20Steam)/Overlays.md) | Steam |  |
[OpenDialogWithTargetUser](GamePlatform%20Features%20(Discord%20Steam)/Overlays.md) | Steam |  |
[OpenPurchaseOverlay](GamePlatform%20Features%20(Discord%20Steam)/Overlays.md) | Steam |  |
#### Remote Storage | Service Functions | [IsEnabled](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam
[GetFile](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[GetSharedFile](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
Service Events | [OnDownloadedSharedFile](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |
[OnFileShared](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
Remote File Functions | [Delete](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |
[Download](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[Exists](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[GetCacheList](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[GetFileSize](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[GetIdentifier](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[GetSharedFileSize](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[Read](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[ReadDataToFile](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[ReadSharedData](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[ReadSharedDataToFile](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[ReleaseRemoteFile](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[ReleaseSharedfile](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[ShareRemoteFile](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[WriteFromFile](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
[WriteData](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |  |
User Generated Content Service Functions | [CreateContent](GamePlatform%20Features%20(Discord%20Steam)/Remote%20Storage.md) | Steam |
#### Rich Presence | Service Functions | [GetRichPresence](GamePlatform%20Features%20(Discord%20Steam)/Rich%20Presence.md) | Discord
[SetRichPresence](GamePlatform%20Features%20(Discord%20Steam)/Rich%20Presence.md) | Discord |  |
[SetStatus](GamePlatform%20Features%20(Discord%20Steam)/Rich%20Presence.md) | Discord, Steam |  |

[In This Section](#in-this-section)[Accounts](#accounts)[Achievements](#achievements)[Catalog](#catalog)[General](#general)[Leaderboard](#leaderboard)[Matchmaking & Lobbies](#matchmaking-and-lobbies)[Networking](#networking)[Overlays](#overlays)[Remote Storage](#remote-storage)[Rich Presence](#rich-presence)
