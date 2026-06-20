# Compiling CRYENGINE for Mono

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26875011
- Page ID: 26875011
- Breadcrumb: CRYENGINE Code Tutorials > C# Programming > Compiling CRYENGINE for Mono
- Parent: C# Programming

## Content

Compiling the CRYENGINE for Mono is only applicable when building the engine by yourself by retrieving the source from
[https://github.com/CRYTEK/CRYENGINE/tree/main](
Github
)
. The builds downloaded through the CRYENGINE Launcher have mono enabled by default.

To be able to use C# in the CRYENGINE, an extra option has to be enabled in CMake. To adjust this option, open CMake by either opening
**
cry_cmake.exe
**
 (when using the source from the
[https://github.com/CRYTEK/CRYENGINE/tree/main](
main branch
)
) in the source root folder, or
**
<root>/Tools/CMake/cmake_create_win32_solution.bat
**
. Once CMake is open make sure the following options are enabled:

-
`
OPTION_CRYMONO
`

-
`
OPTION_CRYMONO_SWIG
`

-
`
OPTION_BUILD_CSHARP_WITH_MCS
`
If you have trouble finding the options, check if in the top right of CMake the option
**
Grouped
**
 is enabled. All options are grouped in the
**
OPTION
**
 group. If some options are missing try enabling the options that you do have, and press
**
Configure
**
 button at the bottom of CMake. After configuring, it will show new values in red.

After this just press the
**
Configure
**
 button, and if some lines are still red after configuring press
**
Configure
**
 again. Once all lines are white press
**
Generate
**
 and the solution file with C# support will be generated. The solution will now contain extra
**
C#
**
 projects which are located in the
**
CryMono
**
 folder. The CryMonoBridge project can be found in
**
`
CRYENGINE/CryMono/
`
**
.

The CryMonoBridge will only trigger compilation if one of the interface generation source files (
**
<root>/Code/CryManaged/CryMonoBridge/SWIG/*.i
**
) has changed or if the temp directory (
**
<root>/BinTemp/<platform>/BinTemp/swig_files
**
) for the generated interface is missing. The compilation will
not
 be triggered, if one of the CRYENGINE source code files changed.
