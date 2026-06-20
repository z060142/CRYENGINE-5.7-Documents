# Generating Stars DAT File

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306419
- Page ID: 23306419
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > Rendering Modules > Generating Stars DAT File
- Parent: Rendering Modules

## Content

### Overview

This document is targeted at people who want to modify the stars data that is used in the sky rendering. This assumes some familiarity with generating binary files.

- Data file: Build\Engine\EngineAssets`\Sky\stars.dat`
- Loader code file: CRESky.cpp, function CStars::LoadData

Chapters:

[File Format](#file-format)[Header (12 bytes)](#header-12-bytes)[Entry (12 bytes)](#entry-12-bytes)

### File Format

The file has a simple binary format, and you can easily write the data you want in there yourself with some tool.

All types stored in little-endian format, float32 in IEEE-754 format.

The file starts with a header. The header is immediately followed by entries for each star (the number of entries is stored in the header).

Layout and types are as follows:

#### Header (12 bytes)

Name | Offset | Type | Value
--- | --- | --- | ---
**Tag** | 0 | uint32 | 0x52415453 (ASCII: STAR)
**Version** | 4 | uint32 | 0x00010001
**NumStars** | 8 | uint32 | Number of star entries in the file

#### Entry (12 bytes)

Name | Offset | Type | Value
--- | --- | --- | ---
**RightAscension** | 0 | float32 | in radians
**Declination** | 4 | float32 | in radians
**Red** | 8 | uint8 | star color, red channel
**Green** | 9 | uint8 | star color, green channel
**Blue** | 10 | uint8 | star color, blue channel
**Magnitude** | 11 | uint8 | brightness, normalized range

Typically, you can use existing star catalogs to populate this information for you, or you can use the one that is provided in the SDK (which is based of real-world information).
