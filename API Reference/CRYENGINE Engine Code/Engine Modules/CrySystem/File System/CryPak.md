# CryPak

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306406
- Page ID: 23306406
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > File System > CryPak
- Parent: File System

## Child Pages

- [Accessing Files with CryPak](CryPak/Accessing%20Files%20with%20CryPak.md)

## Content

##
CryPak File Archives

CryPak is a module which enables to store game content files in a compressed or uncompressed archive.

##
Features

-
Compatible with the standard zip format (implementation is based on the zlib library).

-
Supports storing files in an archive or outside in the standard file system.

-
Data can be read in a synchronous (stalls until the data is loaded) and asynchronous (streaming) way through
*
IStreamCallback
*
 (max 4GB offset, 4GB files).

-
Files can be stored in compressed or uncompressed form.

-
Uncompressed files can be read partially if required.

-
File name comparison is not case sensitive (internally everything is converted to lower case).

-
Supports loading of zip/pak files of up to 4GB in size (proven to work with more than 2.1GB).

##
Unicode and Absolute Path Handling

Internally all path handling code is
**
ASCII
**
-based so there are
**
no Unicode
**
 (16bit characters for different languages) functions that can be used. This is to save memory and for simplicity. There is no real need for Unicode as a game can and should be developed with ASCII path names. Productions without this requirement will have problems integrating other nationalities. As the user might install games to a folder with Unicode characters, absolute path names are explicitly avoided throughout the whole engine.

##
Layering

Usually the game content data is organized in several pak files which are located in the game directory. If a file is requested for an opening operation, the CryPak system will loop through all registered pak files in order to find the file. Pak files are searched through in order of creation. This way, patch pak files, which have been added to the build later, are preferred. It is also possible to mix pak files with loose files which are stored directly in the file system (not in a pak). If a file exists as a loose file as well as in a pak archive, the loose file is preferred when the game is in
**
devmode
**
. However, to avoid cheating in the shipped game, the file stored in the pak is preferred over the loose file when the game is not run in devmode.

##
Slashes

Usually forward slashes ( / ) are used for internal processing but users may enter paths that contain backslashes.

##
Special Folder Handling

The path alias
**
%USER%
**
 can be used to specify a path relative to the user folder. This might be needed to store user-specific data. Windows can have restrictions on where the user can store files. For example, the program folder might not be writable at all. For that reason, screenshots, savegame data and other files should be stored in the user folder. The following are examples of valid file names with path:

```

`
%USER%/ProfilesSingle/Lisa.dat
game/Fred.dat

`

```

##
Internals

-
There is a known implementation flaw which causes problems when using more than approximately 1000 files per directory.

-
Format properties:

-
The zip file format stores each file with a small header including its path and file name in uncompressed text form. For faster file access, there is a directory in the end of the file. The directory also stores the path and filename in uncompressed text form (redundant).

##
Creating a pak file using 7za

You can easily create a pak file using the
[7-Zip](http://www.7-zip.org/)
 tool using the command:

```

`
7za a -tzip -r -mx0 <PakFileName> [file1 file2 file3 ...] [dir1 dir2 ...]

`

```

##
Dealing with Large Pak Files

The zip RFC specifies two types of zip files, indicated by zip format version 45. Old zips have a 4GB offset possibility, but in case legacy i/o functions are used it's only possible to seek +- 2GB. Therefore the practical limit is at 2GB. The 4GB offsets have nothing to do with native machine types (and certainly don't change size across platforms and compilers or configurations), the offsets for older version zips are in a machine independent uint32, the offsets for the new version zips are in uint64 appended to the old version structs. The version a zip file uses is in the header, and applications have the freedom to not support the newer version:
[http://www.pkware.com/documents/casestudies/APPNOTE.TXT](http://www.pkware.com/documents/casestudies/APPNOTE.TXT)

You don't need to think of handling splits manually, the RC supports auto-splitting:

-
"zip_sizesplit" - "Split zip files automatically when the maximum compressed size (configured or supported) has been reached" (the limit is implicit 2GB if it's not explicit).

-
"zip_maxsize" - "Maximum compressed size of the zip in KBs" (this gives an explicit limit).
Splitting works in all cases, supports multi-threading, and incremental updates. It expands and shrinks the chain of necessary zip-parts automatically. Sorting is honored as much as possible, even in face of incremental modifications, but individual files can be stuffed at the end of the parts to fill in the leftover space instead of following strict sorting.

##
Further Reading

-
[Zip File Format Reference by Phil Katz](http://www.sxlist.com/techref/language/delphi/swag/ARCHIVES0022.html)
.

-
[http://www.pkware.com/documents/casestudies/APPNOTE.TXT](http://www.pkware.com/documents/casestudies/APPNOTE.TXT)
