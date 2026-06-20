# Track Events

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535447
- Page ID: 25535447
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Scene Interactivity > Track Events
- Parent: Scene Interactivity

## Content

### Overview

This document will guide you through setting up and using Track Events in the Track View and Flow Graph editors.

### Terminology

A **Track Event** is a one-way signal that will allow you to branch Flowgraph logic from a Trackview Sequence.

Each sequence may define any arbitrary number of Track Events, which can be called at any time from a Track Event Node. Each event may also carry with it a string value assigned to the key in the Track View editor.

When a Track Event is triggered from the sequence, its corresponding output port in a special Flowgraph node is activated, allowing you to branch Flowgraph logic very easily.

### Defining Track Events

Track Events may be defined per Trackview Sequence. First, open the Track View Editor and either create a new sequence or select an existing one. Once opened, right-click on the sequence in the tree view on the left and select the Edit Events option towards the bottom.

A dialog box labeled "**TrackView Events**" will open. To create a Track Event, select the ** Add** button and give the event a name. The event will then be added to the list. To remove this event, select it from the list and select the ** Remove** button.

When you are done, select the **OK** button to save your changes. The sequence's Track Events will then be updated.

### Adding Track Event Nodes

The Track Event Node will allow you to call a Track Event (with an optional string value) from the sequence. To add the node to your sequence, right-click on the sequence in the tree view on the left and select the **Add Event** option towards the bottom.

Give the node a name and it will then be added to your sequence. From here, you will be able to add keys to toggle the track events just like any other node.

If you select any of the keys you created on the event track, you can assign to it one of your predefined Event Names by choosing them on the right side menu, called Key Properties.

You can also edit the list of **Track Events** for the sequence quickly by double clicking on ** Edit Track Events**.

### Adding Flowgraph Logic

To add your Flowgraph logic, you will first need to create a new graph or open an existing one. Then you will need to place a **Track Event Node** which can be done by right-clicking anywhere in the graph and selecting it from the context menu.

The node will initially be empty and you will need to select your **Animation Sequence** for the Sequence input port.

Note if the sequence you choose does not exist, it will be erased and the value will remain empty. Once you select a valid sequence, output port will be created for each Track Event owned by that sequence.

In this example the events are triggering Particle Effects to start and to stop.

From this point, create your Flowgraph logic using the created output ports. When these events are triggered from the Animation Sequence as it plays through, the output ports will trigger, allowing your Flowgraph logic to execute.

If after placing a Flowgraph node you add or remove Track Events from the sequence, the Flowgraph node will update to reflect this change and the output ports will be created/removed as such.

If you had a link leading from the output port of an event that is later removed, the link will be deleted as well.

### Example

For the Cave Sequence showcased at GDC 2011 Crytek Presentation, a track event was used to trigger physical impulse on the rocks when the girl character is running.

*Flow Graph Setup for the Cave Sequence*

*Track Event for the Cave Sequence with the key frames setup in Track View*

Track Event is also useful to change the Time of Day per different shots.

[Terminology](#terminology)[Defining Track Events](#defining-track-events)[Adding Track Event Nodes](#adding-track-event-nodes)[Adding Flowgraph Logic](#adding-flowgraph-logic)[Example](#example)
