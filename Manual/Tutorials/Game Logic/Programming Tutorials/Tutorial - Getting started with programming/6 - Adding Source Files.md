# 6 - Adding Source Files

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26875711
- Page ID: 26875711
- Breadcrumb: Tutorials > Game Logic > Programming Tutorials > Tutorial - Getting started with programming > 6 - Adding Source Files
- Parent: Tutorial - Getting started with programming

## Content

CRYENGINE uses
**
CMake
**
 to simplify the process of building the engine and projects across all platforms, meaning that we
**
don't
**
 use a Visual Studio project directly. This means that in order to add source files, we need to modify the
*
CMakeLists.txt
*
 file contained inside our project's
**
Code
**
**

**
folder.

##
Adding Source Files to CMake

Looking at the contents of our
*
CMakeLists.txt
*
 file, you should see the following snippet:

```

`
sources_platform(ALL)
add_sources("Code_uber.cpp"
    PROJECTS Game
    SOURCE_GROUP "Root"
    "GamePlugin.cpp"
    "StdAfx.cpp"
    "GamePlugin.h"
    "StdAfx.h"
)
add_sources("Components_uber.cpp"
    PROJECTS Game
    SOURCE_GROUP "Components"
    "Components/Player.cpp"
    "Components/Player.h"
)
`

```

This is what tells CMake what source files we should use. In our case, we split the build into two
**

**
Unity source files. Unity source files effectively combine multiple C++ source files into one unit in order to speed up compilation time. Each one is denoted by the 'add_sources' macro, and a unique name for the unity file.

Each Unity file can then contain any number of groups, known as filters in Visual Studio. In our case, we have "Root" and "Components". Then immediately afterwards, we declare the files to load in relation to where
*
CMakeLists.txt
*
 is on disk.

In our case, we can add a new source file easily here, resulting in:

```

`
sources_platform(ALL)
add_sources("Code_uber.cpp"
    PROJECTS Game
    SOURCE_GROUP "Root"
    "GamePlugin.cpp"
    "StdAfx.cpp"
    "GamePlugin.h"
    "StdAfx.h"
    "MySourceFile.cpp"
)
`

```

This will then be included with our build as soon as we attempt to build in Visual Studio.
