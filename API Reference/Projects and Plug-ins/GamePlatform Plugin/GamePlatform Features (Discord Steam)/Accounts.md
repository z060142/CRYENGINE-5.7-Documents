# Accounts

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448430
- Page ID: 76448430
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > Accounts
- Parent: GamePlatform Features (Discord/Steam)

## Content

## Overview

An Account in the GamePlatform plugin is an abstraction of the platform account it belongs to., allowing for identification of actions targeted at specific platform accounts (the local user, friends or matchmade accounts, for example).

On the technical side, the Account contains a unique identifier based on the underlying identification data provided by the platform (e.g.: a Steam ID on the Steam platform). It also contains the unique platform service identifier that the platform account belongs to.

An account from one platform cannot be used on another platform as they are platform specific.

### Account Service Functions

Account service functions and events provide a way to get information related to any account on a platform. For example, you can retrieve avatars and nicknames of users, retrieve a list of the local user's friends and blocked users on the platform, and be notified when another user on the platform changes their nickname etc.

#### IsFriendWith

Checks if the supplied platform account is on the local account's friends list.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::IsFriendWith
Flow Graph Nodes | GamePlatform:Account:CheckIsFriend
Schematyc Nodes | Function::GamePlatform::Service::Accounts::IsFriendWith

#### GetAccountInfo

Retrieves details of the specified account on the platform.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::GetAccountInfo
Flow Graph Nodes | GamePlatform:Account:GetAccountInfo
Schematyc Nodes | - Function::GamePlatform::Service::Accounts::GetNickname - Function::GamePlatform::Service::Accounts::IsLocal

#### GetAvatar

Retrieves the specified account's avatar texture ID of a specified size.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::GetAvatar
Flow Graph Nodes | GamePlatform:Account:GetAvatar
Schematyc Nodes | Function::GamePlatform::Service::Accounts::GetAvatar

Some platforms only have one size of avatars (e.g. Discord), while others only provide the Small size by default. To get the Medium and Large sizes, you need to use the [RequestUserInformation](Accounts.md#Accounts-requestuser) function and wait for the [OnAvatarImageLoaded](Accounts.md#Accounts-onavatar) event.

#### GetBlockedAccounts

Retrieves a list of accounts blocked by the local account.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::GetBlockedAccounts
Flow Graph Nodes | GamePlatform:Account:GetBlockedAccounts
Schematyc Nodes | Function::GamePlatform::Service::Accounts::GetBlockedAccounts

#### GetFriendAccounts

Retrieves a list of "friend" accounts associated with the local account.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::GetFriendAccounts
Flow Graph Nodes | GamePlatform:Account:GetFriends
Schematyc Nodes | Function::GamePlatform::Service::Accounts::GetFriendAccounts

#### GetLocalAccount

Retrieves the identifier of the local account on the platform.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::GetLocalAccount
Flow Graph Nodes | GamePlatform:Account:GetLocalAccount
Schematyc Nodes | Function::GamePlatform::Service::Accounts::GetLocalAccount

#### RequestUserInformation

Requests user information (nickname, avatar) from the remote server for the specified account on the specified platform.

Listen for the [OnPersonaStateChanged](Accounts.md#Accounts-onpersona)and [OnAvatarImageLoaded](Accounts.md#Accounts-onavatar) events for changes.

Platform(s) | Steam
--- | ---
API | Cry::GamePlatform::IService::RequestUserInformation
Flow Graph Nodes | GamePlatform:Account:RequestUserInfo
Schematyc Nodes | Function::GamePlatform::Service::Accounts::RequestUserInformation

### Account Service Events

#### OnAccountAdded

Fired when an account is added to the internal registry (for example, when a friend was added to the local account).

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::IListener::OnAccountAdded
Flow Graph Nodes | GamePlatform:Listener:Account:OnAccountAdded
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Accounts::OnAccountAdded

#### OnAccountRemoved

Fired when an account is removed (a friend was removed, for example).

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::IListener::OnAccountRemoved
Flow Graph Nodes | GamePlatform:Listener:Account:OnAccountRemoved
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Accounts::OnAccountRemoved

#### OnAvatarImageLoaded

Fired when the platform service has provided a requested avatar image.

Platform(s) | Discord, Steam
--- | ---
API | Cry::GamePlatform::IService::IListener::OnAvatarImageLoaded
Flow Graph Nodes | GamePlatform:Listener:Account:OnAvatarImageLoaded
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Accounts::OnAvatarImageLoaded

#### OnPersonaStateChanged

Fired when a user's persona data (name, friend/blocked status, permissions such as can send messages/invitations, voice chat, etc.) has changed.

Platform(s) | Steam
--- | ---
API | Cry::GamePlatform::IService::IListener::OnPersonaStateChanged
Flow Graph Nodes | GamePlatform:Listener:Account:OnPersonaStateChanged
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Accounts::OnPersonaStateChanged

[Account Service Functions](#account-service-functions)[IsFriendWith](#isfriendwith)[GetAccountInfo](#getaccountinfo)[GetAvatar](#getavatar)[GetBlockedAccounts](#getblockedaccounts)[GetFriendAccounts](#getfriendaccounts)[GetLocalAccount](#getlocalaccount)[RequestUserInformation](#requestuserinformation)[Account Service Events](#account-service-events)[OnAccountAdded](#onaccountadded)[OnAccountRemoved](#onaccountremoved)[OnAvatarImageLoaded](#onavatarimageloaded)[OnPersonaStateChanged](#onpersonastatechanged)
