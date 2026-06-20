# Developer Tools and Debugging

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873082
- Page ID: 26873082
- Breadcrumb: CRYENGINE Sandbox Programming > Developer Tools and Debugging
- Parent: CRYENGINE Sandbox Programming

## Content

## Developer Tools

### Command Line Options

**-waitfordebugger <seconds>**

Useful for doing remote debug sessions and trying to attach at the very beginning of the program execution. This is very useful when you can't launch Sandbox through Visual Studio with the already attached debugger.

5.3 and after:

- Run Sandbox with **-project "Path to Project"**
- Use CVar: **sys_project="Path to Project"**

5.2 and before:

- Register your local build by running the bat file found in **//ce/xxx/Tools/RegisterLocalBuild.bat**
- In your project folder, edit **project.cfg** to use your local version:**engine_version=local**
- Run**Editor.bat**
- Use -waitfordebugger argument in Editor.bat if you need to attach during startup.

### Playground Dockable

Playground dockable is a tool widget intended as a Sandbox for programmers to test anything in isolation.

This can be very useful when debugging a Qt issue in the actual tool is very cumbersome, but replicating and narrowing it down with dummy widgets in the playground dockable is much easier.

This can also be used to test new widgets in isolation, or test features without having to inject in any other tool.

To use this uncomment the registration macro in **PlaygroundDockable.cpp** and code away!

## Qt Debugging

### Visual Studio Plugin

With the release of Qt 5.6, the visual studio plugin is not available anymore. However, we have included the Visual Studio visualizers in the solution (qt5.natvis) so everybody should be able to visualize Qt classes properly in their debugger.

### Getting Qt Source Code

Having the source code is obviously useful to dig into the depths of Qt and see what goes wrong.

Bear in mind that Qt is not perfect, that there are bugs, and we have often had to find workarounds by providing our alternative classes to Qt when their behavior was not matching our expectations. See [Qt Programming in Sandbox](Qt%20Programming/Qt%20Programming%20in%20Sandbox.md)

Do not be afraid to investigate if a bug is within Qt and not in our code.

Links from the official Qt documentation:

[https://wiki.qt.io/Get_the_Source](https://wiki.qt.io/Get_the_Source)

[https://doc.qt.io/qt-5/windows-support.html](https://doc.qt.io/qt-5/windows-support.html)

[Developer Tools](#developer-tools)[Command Line Options](#command-line-options)[Playground Dockable](#playground-dockable)[Qt Debugging](#qt-debugging)[Visual Studio Plugin](#visual-studio-plugin)[Getting Qt Source Code](#getting-qt-source-code)
