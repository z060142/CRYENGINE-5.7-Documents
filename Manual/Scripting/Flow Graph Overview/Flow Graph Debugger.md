# Flow Graph Debugger

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450522
- Page ID: 29450522
- Breadcrumb: Scripting > Flow Graph Overview > Flow Graph Debugger
- Parent: Flow Graph Overview

## Content

## Overview

The Flow Graph Debugger enhances the integrated Flow Graph Editor for debugging any given Flow Graph.

You can add Breakpoints to any input or output ports of a given node.

When an input or output port with a Breakpoint gets triggered by the Flow Graph system, the game will be paused. Then the Flow Graph Editor opens the node which consist the Breakpoint, and centers that particular node in the Flow Graph viewer:

![Image](https://www.cryengine.com/docs/static/attachments/44971103)

### Enable Debugging

To enable debug mode, click on the **Debug** button in the Flow Graph toolbar:

![Image](https://www.cryengine.com/docs/static/attachments/35395037)

### Adding and Removing Breakpoints

To add a new Breakpoint, **right-click** on a specific port and choose ** Add Breakpoint**. You can also add a Breakpoint using ** Ctrl + Middle Mouse Button** on a specific port.

![Image](https://www.cryengine.com/docs/static/attachments/44971104)

To remove an existing Breakpoint, **right-click** on the specific node and select ** Remove Breakpoint**. You can also add a Breakpoint by using ** Ctrl + Middle Mouse Button**.

You can also remove all Breakpoints for a specific Flow Node or Flow Graph by using the following options:

- Remove Breakpoints for Node
- Remove Breakpoints for Graph

Note
Certain context menu options are grayed out if they are not available. For example, if a port already has a Breakpoint then the option **Add Breakpoint** will be grayed out. And if no Breakpoint exists on a node, the**Remove Breakpoint** option will be grayed out.

When a Breakpoint is added, a red dot will be displayed next to the input or output Port.

![Image](https://www.cryengine.com/docs/static/attachments/44971105)

### Enabling and Disabling Breakpoints

You can disable or enable specific Breakpoints by **right-clicking** the Flownode ports (first image below) or the Breakpoint overview window (second image below).

![Image](https://www.cryengine.com/docs/static/attachments/44971106)

*Enabling or disabling Breakpoint using Breakpoint overview window* *![Image](https://www.cryengine.com/docs/static/attachments/44971107)*

### Using Tracepoints

You can convert every Breakpoint into a Tracepoint. Unlike Breakpoints, the tracepoint prevents the game from pausing and the information about a triggered Breakpoint will be directed to the console and log file.

*Converting a Breakpoint into a Tracepoint using context menu*![Image](https://www.cryengine.com/docs/static/attachments/44971108)

*Converting a Breakpoint into a Tracepoint using * Breakpoint overview window**![Image](https://www.cryengine.com/docs/static/attachments/44971109)

Console output example:

[TRACEPOINT HIT - FrameID: 71054] GRAPH: AnimObject1 (ID: 96) - NODE: Entity:MaterialParam (ID: 5) - PORT: ValueColor - VALUE: 0.867136,0.005522,0.005522

### Breakpoints Overview

The Flowgraph Editor provides a Breakpoints overview panel (bottom right corner) to provide a better overview of all the Breakpoints added in the Flow Graph.

![Image](https://www.cryengine.com/docs/static/attachments/44971110)

When you click on a Breakpoint in the Breakpoint Overview window, it will open the corresponding or port in the Flow Graph.

You can also remove a specific Breakpoint or Breakpoints in an entire node or Flow Graph by **right-clicking** in the Breakpoint overview panel.

*![Image](https://www.cryengine.com/docs/static/attachments/44971111)*

### Resume the Game

To resume the game, when a Breakpoint is hit, you can press **F5** or click on the **Play** button in the Flow Graph Editor toolbar.

*![Image](https://www.cryengine.com/docs/static/attachments/35395038)*

### Basic Example

In this example, we are using a basic Flow Graph which should calculate a random number when the **R** key is pressed.

The Flow Graph Debugger allows you to see the calculated random number without requiring to add a debug message.

![Image](https://www.cryengine.com/docs/static/attachments/44971113)

When the **R** key is pressed in the game, the first Breakpoint will be hit and you can see the calculated random number in the Breakpoints Overview window in the bottom right:

![Image](https://www.cryengine.com/docs/static/attachments/44971112)

When you press **F5** or the **Play** button from the toolbar the second Breakpoint will be hit:

*![Image](https://www.cryengine.com/docs/static/attachments/44971114)*

When you press **F5** or the **Play** button again, the game will be resumed.

[Enable Debugging](#enable-debugging)[Adding and Removing Breakpoints](#adding-and-removing-breakpoints)[Enabling and Disabling Breakpoints](#enabling-and-disabling-breakpoints)[Using Tracepoints](#using-tracepoints)[Breakpoints Overview](#breakpoints-overview)[Resume the Game](#resume-the-game)[Basic Example](#basic-example)
