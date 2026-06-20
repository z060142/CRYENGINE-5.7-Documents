# Remote Shader Compiler

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306645
- Page ID: 23306645
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > Rendering Modules > Shaders > Shader Cache > Remote Shader Compiler
- Parent: Shader Cache

## Content

##
Overview

Unlike PC, many consoles cannot compile shaders locally. For this reason, the CRYENGINE SDK contains a server application that can handle shader compilation by assigning a server on the local network that can communicate over TCP. The server receives the shader source file from a machine running CRYENGINE, compiles it and sends back the binary shader which the client machine can then load and use. This application is called the Remote Shader Compiler.

In addition, the remote shader compiler is also used to store all the shader combinations which have been requested by the game so far (per platform). These lists are used during the shader cache generation, when all the requested shaders are packed for use by the game.

In the following, the steps to set up and configure the Remote Shader Compiler will be explained.

Chapters:

[Launching the Remote Shader Compiler](#launching-the-remote-shader-compiler)
[Remote Shader Compiler Configuration](#remote-shader-compiler-configuration)
[Shader Cache Lists](#shader-cache-lists)
[Game Configuration](#game-configuration)
Related Pages:

##
Launching the Remote Shader Compiler

The Remote Shader Compiler can be found in the folder
`
<Root>\Tools\RemoteShaderCompiler
`
. The executable is called
**
CrySCompileServer.exe
**
. A configuration file is also available that can be used to configure the TCP port the server application will listen on.

You can launch the Remote Shader Compiler by starting
**
CrySCompileServer.exe
**
 manually. However, usually it makes sense to set it up as a service, so that it is always started with the operating system.

Requests for shaders are executed in parallel, it can make sense to ensure sufficient cores are available for the server, if you notice significant delays in acquiring shaders at runtime.

##
Remote Shader Compiler Configuration

There are four important variables that should be set in the config.ini file:

-
*
MailError
*
 should be set to an internal company e-mail address to which notifications about compilation errors will be sent.

-
The cache directory (
*
TempDir
*
), in which the binary shaders are stored once they got compiled, needs to point to a valid absolute path (default is <WorkingDirectory>\Temp).

-
*
port
*
 is the TCP port, which has to match the setting in the game's system.cfg

-
*
MailServer
*
 is the mail server of your company.
The complete config.ini file should look like this:

```

`
MailError = shadererror@your_company.tld
MailInterval = 1
port = 61453
TempDir = C:\SHADER_CACHE
MailServer = put.here.your.mailserver
PrintErrors = 1
`

```

##
Platform-Specific Shader Compilers - Versions and Paths

In the root folder of the Remote Shader Compiler, each supported platform has its own sub-folder with additional sub-folders for different version numbers. The paths are hard-coded and can be configured in
`
RenderDll\Common\Shaders\ShaderCache.cpp
`
 if required.

All paths follow this pattern:
`
<Root>\Tools\RemoteShaderCompiler\Compiler\<platform>\Vxxx
`
.

You can always find all the information about the path used by the Remote Shader Compiler inside the file ShaderCache.cpp, function
**
mfGetShaderCompileFlags
**
.
[]()
As part of the engine package distributed to you, the appropriate shader-compilers are already included for your use, that match the code of that version. Just copy the entire RemoteShaderCompiler folder and run the provided binary.

##
Shader Cache Lists

The cache subfolder of the remote shader compiler will contain different txt list files of all the combinations requested so far by the game. The listfiles in the root folder contain all the global shader combination, which have ever been requested on a certain platform on any level.

The game submits the requests to the remote shader compiler either during actual gameplay or during loading phases, even when remote shader compiling itself is disabled. This is to be sure that all possible shader combinations are collected, and the shader caches which are generated during the shader cache generation phase are as complete as possible.

##
Game Configuration

Usage of the Remote Shader Compiler by the game can be configured with the following cvar setting which is usually put into the system.cfg file:

r_ShadersRemoteCompiler=1

If
**
r_ShadersRemoteCompiler
**
 is set to 0, no remote shader compilation will be performed and the engine will do local shader compilation instead (which will fail on consoles).

When enabled, the game has to know the location of the Remote Shader Compiler. The IP address of the server can be configured with the following CVar:

r_ShaderCompilerServer=
*
<IPv4_of_PC_running_the_RemoteShaderCompiler>
*

It is possible to specify more than one Remote Shader Compiler, as shown in the following sample. The IP addresses need to be separated by semicolons.

r_ShaderCompilerServer=10.0.0.10;10.0.0.11

Please note that it is not possible to use the network name of the server instead of the IP address since no name resolving is performed.

If the remote shader compile server uses user-defined port number (as specified in config.ini), the port number can be configured with the following CVar.

r_ShaderCompilerPort=
*
<portnumber>
*

Submitting request lines to the remote shader compiler can also be disabled with the following cvar, which can be handy when experimenting with shaders and you don't want to have these combinations added to the global shader cache:

r_shaderssubmitrequestline=0

As a final note, it is not required to have a central remote shader compile server for the whole company. It is also possible to set up the Remote Shader Compiler locally on each PC that requires shader compilation and it is actually handy when writing shaders.
