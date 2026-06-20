# Connecting Statoscope

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306650
- Page ID: 23306650
- Breadcrumb: CRYENGINE Tools > Statoscope > Connecting Statoscope
- Parent: Statoscope

## Content

### Overview

This article is a quick guide to the basics of logging data and using Statoscope.

The page will guide you though the necessary setup and some basics of the Statoscope interface.

Chapters:

[Quick-Start](#quick-start)[Platforms](#platforms)[Opening Logs](#opening-logs)[First look](#first-look)[Viewport Controls](#viewport-controls)

### Quick-Start

- Run the game or jump in-game from the Editor
- Set **e_StatoscopeEnabled 1**, to enable Statoscope
- Set **e_StatoscopeDataGroups** as you require, for example *"***fgu***"* will get you frame length, graphics stats and user markers. Default datagroups: "**fgmtuO**"
- Set **e_StatoscopeLogDestination** to:

- 1 for socket logging and choose *File -> Connect* in the tool
- 0 for file logging and drag the file from “*statoscope/perflog.bin”* file into the tool

- Launch Statoscope and connect to your target platform

### Platforms

Statoscope will connect to any console/platform that is connected directly to the PC or via an IP address specified in the connection dialog.

![Image](https://www.cryengine.com/docs/static/attachments/26964653)

### Opening Logs

#### Read from a File

From CRYENGINE version 3.6.3 and earlier:

If you chose **e_StatoscopeLogDestination = 0** The session file is stored in the location: **BuildRoot/statoscope/*.bin**

From CRYENGINE 3.6.4 and later:

If you chose **e_StatoscopeLogDestination = 0** The session file is stored in the location: **BuildRoot/user/statoscope/*.bin**

You can open logs in different ways:

- Dragging a log file onto the tool window
- Using the *File -> Open log* menu
- Connecting to a running game with *File -> Connect*

Each log opens a new tab. When you open a log that has been recorded across several levels with the user marker data group enabled ('u'), then each level is also opened in its own tab (this is based on level start and end user markers).

Middle click on a tab to close it.

By default, every stat will be drawn (which is usually far too many to be useful), so the first thing to do is to trim the view down to what you want.

There aren't any progress bars at the moment, so if the log being loaded is large, then the tool will freeze for a while as it processes the data.

#### Socket Logging

From *File -> Connect* you can connect to a running version of the game whose e_StatoscopeLogDestination is set to 1.

Choose the target platform you want to connect to.

If *Log to file* is enabled you will be given the option of saving the log to disk for opening later.

A slight limitation at the moment is that you must have enabled at least one data group before connecting, but you can change the data groups on the fly once connected.

If for any reason the connection fails, then you can reset it by setting e_StatoscopeLogDestination to a different value (e.g. 2) and then back to 1 again, and then reconnect.

### First look

After loading a log or connecting to a running application you will typically see the following layout in Statoscope:

![Image](https://www.cryengine.com/docs/static/attachments/26964654)

This screen corresponds to the default view with all the options enabled and the entire log fitted to screen. From here, you can start turning off the data groups that you do not need and zooming in on the display in the areas of interest.

### Viewport Controls

In the main graph window:

- Left click & drag - pans
- Right click & drag - zooms
- Right click & drag left/right - scales the view horizontally
- Right click & drag up/down - scales the view vertically
- Right click & drag top right/bottom left - scales both horizontally and vertically and at the same time
