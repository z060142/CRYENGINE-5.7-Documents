# Filesystem_

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26874879
- Page ID: 26874879
- Breadcrumb: Filesystem_

## Child Pages

- [Avoiding Runtime File Access Stalls](Filesystem_/Avoiding%20Runtime%20File%20Access%20Stalls.md)
- [Reading & Writing XML](Filesystem_/Reading%20%26%20Writing%20XML.md)
- [Serializing JSON & XML](Filesystem_/Serializing%20JSON%20%26%20XML.md)

## Content

## Overview

CRYENGINE wraps the C-level 'fopen', 'fread' etc... functions via the [ICryPak](/docs/static/engines/cryengine-5/categories/28704770/pages/29797181) interface. This allows for supporting multiple platforms as well as the custom.pak archive implementation, without over complicating file access.

## Table of Contents

[API Types](#api-types)[Working Directory](#working-directory)[Aliases](#aliases)[PAK Archives](#pak-archives)

## API Types

- [ICryPak](/docs/static/engines/cryengine-5/categories/28704770/pages/29797181)

## Working Directory

By default, the working directory of the engine will be the project root, that is the directory that contains your.cryproject file. However, calls to 'fopen' etc... will first search the **Assets** directory, and then fall back to checking the project directory.

## Aliases

Paths specified to [ICryPak](/docs/static/engines/cryengine-5/categories/28704770/pages/29797181) can contain aliases wrapped in percentage signs (%) in order to access a predefined location. This is commonly used to access the Engine root directory or the user folder. The default aliases are.

Alias | Default Location | Description
--- | --- | ---
%USER% | <project root>/USER | Links to the user directory that stores locally compiled shaders and common user settings such as graphical settings
%ENGINEROOT% | - | Links to the root of the Engine installation. Useful when accessing Engine resources as the project folder can be completely independent of the Engine itself
%ENGINE% | <engine root>/Engine | Links to the Engine assets directory, inside the Engine installation.
%EDITOR% | <engine root>/Editor | Links to the Editor directory, used to access editor-only resources. **Not** available in release!

## PAK Archives

A very important aspect of [ICryPak](/docs/static/engines/cryengine-5/categories/28704770/pages/29797181) is its support for storing game content in compressed or uncompressed archives. This allows for both synchronous (stalls until the data is loaded) and asynchronous (streaming) loading of archived data.

### Creating a.pak File Using 7za

You can easily create a.pak file using the [7-Zip](http://www.7-zip.org/) tool using the command:

`7za a -tzip -r -mx0 <PakFileName> [file1 file2 file3...] [dir1 dir2...]`
---

### File Loading Order

The order in which CryPak tries to find a file varies depending on whether or not we are building a release.

#### During Development (Profile and Debug builds)

- Raw directory structure is queried using the native platform file system API
- If the file was not found we search through Pak archives (if any)

#### In Release Builds

In release builds, direct file system access is disabled by default - this means that a file search will only query the loaded.pak archives and completely ignore any files on the file system.

### Archive Search Order

If a file is requested for an opening operation, the CryPak system will loop through all registered.pak files in order to find the file. Pak files are searched in order of creation. This way, patch pak files, which have been added to the build at a later date are preferred.

### Unicode and Absolute Path Handling

Internally all path handling code is **ASCII**-based so there are ** no Unicode** (16bit characters for different languages) functions that can be used. This is to save memory and for simplicity. Actually, there is no real need for Unicode, as a game can and should be developed with ASCII path names. ** Note:** Productions without this requirement will have problems in the integration of other nationalities.

As the user might install games to a folder with Unicode characters, absolute path names are explicitly avoided throughout the whole Engine. Internal Engine systems will automatically convert paths to Unicode when accessing raw Windows APIs. This ensures that special characters can still be present in the Engine/project installation paths.
