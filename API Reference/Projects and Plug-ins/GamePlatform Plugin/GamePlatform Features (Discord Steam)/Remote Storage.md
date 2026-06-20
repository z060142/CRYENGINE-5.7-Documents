# Remote Storage

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448629
- Page ID: 76448629
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > Remote Storage
- Parent: GamePlatform Features (Discord/Steam)

## Content

## Overview

The Remote Storage abstraction of the GamePlatform plugin attempts to unify the interfaces for user storage on platform services.

This can, for example, be used to store saved files on a remote cloud service on the platform. The remote files handled by the Remote Storage interface can be shared to allow other clients to download and make use of the files.

- The name of a remote file must contain a filename and extension, along with a path (directory). If the remote file name does not have a filename and extension, it will not store the file on the platform service (reading and writing will fail).
- For now, only Steam supports the Remote Storage capability.

### Remote File Cache

To allow a more seamless usage of Flow Graph with respect to the Remote Storage interface, a Remote File Cache which resides in the GamePlatformNodes plugin is used.

- Simply opening/creating a file will keep it local. When writing data to it is attempted, the GamePlatform plugin will ask the platform to create the corresponding remote file in the Remote File Cache.
- The same file can be opened as many times as you like; as long as the cache is used, duplicate copies of the file will not be created locally (no duplicated are possible on the remote platform).
- However, if you use the C++ API, you could have separate individual copies of a remote file which may or not match. The Remote File Cache resides in the GamePlatformNodes plugin, and is used by the Flow Graph and Schematyc implementations by default.

You must remember to clear this cache when you are not using the remote files any more; you can do this per file, or every file per platform.

### User Generated Content

Alongside the Remote Storage system, CRYENGINE also provides an interface into the User Generated Content service for Steam. This allows the creation of Workshop Items directly in your game.

It is recommended to read the Steamworks documentation for more information on setting up your Workshop pages for your games, and on how Workshop items behave on the platform.

### Remote Storage Service Functions

#### IsEnabled

Checks if the remote storage capability is available on the platform.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteStorage::IsEnabled
Flow Graph Nodes | GamePlatform:RemoteStorage:IsEnabled
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::IsEnabled

#### GetFile

Retrieves a reference to a remote file.

- For the C++ API, this retrieves a data structure that allows you to then query the file size, or read/write the data on demand.
- For the Flow Graph implementation, the write/read/size etc. functions are used directly, with the filename specified each time.
- For Schematyc, this will retrieve a data type that you can pass to the read/write/size etc. functions (like an identifier).

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteStorage::GetFile
Flow Graph Nodes | N/A (handled via the file cache)
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::GetRemoteFileByName

#### GetSharedFile

Retrieves a reference to a shared remote file.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteStorage::GetSharedFile
Flow Graph Nodes | N/A (handled via the file cache)
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::GetSharedFileById

### Remote Storage Service Events

#### OnDownloadedSharedFile

Fired when a download request for a shared file is completed.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFileBase::IListener::OnDownloadedSharedFile
Flow Graph Nodes | GamePlatform:Listener:RemoteStorage:OnDownloadedSharedFile
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::RemoteStorage::OnDownloadedSharedFile

#### OnFileShared

Fired when a file has been shared by the local user.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFileBase::IListener::::OnFileShared
Flow Graph Nodes | GamePlatform:Listener:RemoteStorage:OnFileShared
Schematyc Nodes | Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::RemoteStorage::OnFileShared

### Remote File Functions

#### Delete

Attempts to delete a file from remote storage.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFile::Delete
Flow Graph Nodes | GamePlatform:RemoteStorage:DeleteRemoteFile
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::DeleteRemoteFile

#### Download

Attempts to download the specified shared file from remote storage.

Listen for the [OnDownloadedSharedFile](Remote%20Storage.md#RemoteStorage-ondownloaded)event after the download request.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::ISharedRemoteFile::Download
Flow Graph Nodes | GamePlatform:RemoteStorage:DownloadSharedFile
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::SharedFile::Download

#### Exists

Checks to see if the specified file exists on the remote storage.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFile::Exists
Flow Graph Nodes | GamePlatform:RemoteStorage:FileExists
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::RemoteFile::Exists

#### GetCacheList

Retrieves all cached files of the specified type in memory for the specified platform.

This function is not functional in Release builds; it will not compile (if not guarded) in Release builds, and is to be used for debugging purposes only.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteStorageCache::VisitCache
Flow Graph Nodes | GamePlatform:RemoteStorage:GetCacheList
Schematyc Nodes | N/A (Not Implemented)

#### GetFileSize

Attempts to retrieve the size of a file from remote storage.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFile::GetFileSize
Flow Graph Nodes | GamePlatform:RemoteStorage:GetFileSize
Schematyc Nodes | Function::GamePlatform::Service::RemoteFile::GetFileSize

#### GetIdentifier

Attempts to retrieve the shared file ID of the specified remote file.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFile::GetIdentifier
Flow Graph Nodes | GamePlatform:RemoteStorage:GetSharedFileId
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::RemoteFile::GetSharedId

#### GetSharedFileSize

Attempts to retrieve the size of a shared file from remote storage.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::ISharedRemoteFile::GetFileSize
Flow Graph Nodes | GamePlatform:RemoteStorage:GetSharedFileSize
Schematyc Nodes | Function::GamePlatform::Service::SharedFile::GetFileSize

#### Read

Attempts to read data from remote storage.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFile::Read
Flow Graph Nodes | GamePlatform:RemoteStorage:ReadData
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::RemoteFile::ReadData

#### ReadDataToFile

Attempts to read data from remote storage and write it to a local file.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFile::ReadToFile
Flow Graph Nodes | GamePlatform:RemoteStorage:ReadDataToFile
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::RemoteFile::ReadToFile

#### ReadSharedData

Attempts to read a shared file from remote storage.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::ISharedRemoteFile::Read
Flow Graph Nodes | GamePlatform:RemoteStorage:ReadSharedData
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::SharedFile::Read

#### ReadSharedDataToFile

Attempts to read a shared file and write the data to the specified local file.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::ISharedRemoteFile::ReadToFile
Flow Graph Nodes | GamePlatform:RemoteStorage:ReadSharedDataToFile
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::SharedFile::ReadToFile

#### ReleaseRemoteFile

Releases a cached remote file from the remote storage cache.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteStorageCache::ReleaseCache
Flow Graph Nodes | GamePlatform:RemoteStorage:ReleaseRemoteFile
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::RemoteFile::ReleaseCache

#### ReleaseSharedFile

Releases a cached shared file from the remote storage cache.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteStorageCache::ReleaseCache
Flow Graph Nodes | GamePlatform:RemoteStorage:ReleaseSharedFile
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::SharedFile::ReleaseCache

#### ShareRemoteFile

Attempts to share a file from remote storage.

- This function asks the platform to allow other users to query this file using the provided shared identifier.
- Upon success, the [OnFileShared](Remote%20Storage.md#RemoteStorage-onfileshared)event containing the identifier to pass to other users will be triggered on the local user.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFile::Share
Flow Graph Nodes | GamePlatform:RemoteStorage:ShareRemoteFile
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::RemoteFile::Share

#### WriteFromFile

Attempts to write data from a local file to remote storage.

CryPak handles resolution of the path, and you can prefix %USER% or %ENGINEROOT% to the file paths. This means you can use all the aliases and even read data from files inside encrypted PAK files (data cannot be written to PAK files).

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFile::WriteFromFile
Flow Graph Nodes | GamePlatform:RemoteStorage:WriteDataFromFile
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::RemoteFile::WriteFromFile

#### WriteData

Attempts to write data to a file in remote storage.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IRemoteFile::Write
Flow Graph Nodes | GamePlatform:RemoteStorage:WriteData
Schematyc Nodes | Function::GamePlatform::Service::RemoteStorage::RemoteFile::Write

### User Generated Content Service Functions

#### CreateContent

Creates a new user generated content item on the specified platform.

Platforms | Steam
--- | ---
API | Cry::GamePlatform::IUserGeneratedContentManager::CreateDirect
Flow Graph Nodes | GamePlatform:UserGeneratedContent:CreateContent
Schematyc Nodes | Function::GamePlatform::Service::UserGeneratedContent::Create

[Remote File Cache](#remote-file-cache)[User Generated Content](#user-generated-content)[Remote Storage Service Functions](#remote-storage-service-functions)[Remote Storage Service Events](#remote-storage-service-events)[Remote File Functions](#remote-file-functions)[User Generated Content Service Functions](#user-generated-content-service-functions)
