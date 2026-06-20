# CryMovie

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23308728
- Page ID: 23308728
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryMovie
- Parent: Engine Modules

## Content

### Purpose of CryMovie

CryMovie is the central point for managing camera and sequence related things in CRYENGINE. It offers a simple interface that is already used by other engine components such as flowgraph, viewports and the new trackview tool plugin. It allows you to easily animate certain values of an object like position or rotation data.

### Highlights of CryMovie

- General concept of sequences
- Sequence management
- Sequence playback
- Sequence captures
- Manage camera parameters

### General concept of sequences

- SequenceObject
Whenever you create a new sequence through Trackview, Sandbox will create a new SequenceObject for you. This SequenceObject is handled like a normal entity in the level and will be placed on the currently selected layer. All the sequence related settings will be attached to this entity object. Since it doesn't hold any valuable position or rotation information, it will be placed at 0,0,0. You can also find it by using the Level Explorer and typing in it's name.
- Additonal data & Flags
With every sequence Sandbox will also store its start- and end time as well as special sequence flags that represent the sequences behavior. The more important ones and their purpose are listed below:
flag name | purpose
--- | ---
PlayOnReset | Automatically starts the sequence on game reset/game start
OutOfRangeLoop | Defines if the sequence is played in a loop between start- and end time
CutScene | Defines if the sequence is a cutscene
NoUI | Disables all UI during playback (toggles sys_flash cvar)
NoPlayer | Disables the drawing of the player entity (must be implemented by game code)
NoSeek | Disables seek functionality in sequence
NoAbort | Disables the "abort" action during sequence playback
- Nodes
Depending on your content, your SequenceObject will hold a variety of nodes to separate the data. These nodes can be of different types like "Entity", "Camera", "Director" or special cases like "Depth Of Field".
**Please note that your SequnceObject doesn't store the specified object itself, but only holds a link to it.**
When you remove the linked object or disable the layer it is placed on, the sequence will ignore its node and data.
- Tracks
Every node can hold different track types to separate the data. Standard track types are "Position", "Rotation", "Scale" etc. Since those mentioned types require more than one value (e.g. x,y,z) the data will be separated again in sub tracks which will then assign the track values to a fixed time in your sequence.
Trackview will display this assignment in form of a single key in your timeline.
- Key time and framerate
Instead of seconds represented in floats, CryMovie now uses ticks to precisely store your time values and avoid rounding problems. The current constant equals to 6000 ticks per second, which allows precise timings up to 6000 fps. Old decimal values will be automatically converted to the new corresponding tick value. The new Trackview tool offers automatic conversion between ticks, timecode, time and frames for easier editing - keep in mind that this won't change the format of those values during serialization. **Therefore, sequences created with the new movie system are not backwards compatible**.

### Sequence management

- CreateSequence
Creates a new sequence and adds it to the general list of available sequences
- RemoveSequence
Removes an existing sequence from the general list of available sequences
- FindSequence
You can look for a specified sequence by name, id or guid
- GetNumSequences
Get the number of currently registered sequences
- GetPlayingSequence
Get a playing sequence by index
- GetNumPlayingSequences
Get the number of currently playing sequences

### Sequence playback

- PlaySequence
Start playback of a sequence by either sequence name or IAnimSequence pointer
- StopSequence
Stop playback of a sequence by either sequence name or IAnimSequence pointer
- AbortSequence
Abort a sequence (the way a sequence ends can be relevant for flowgraph logic and gamerules)
- StopAllSequences
Stops all sequences that are currently playing
- StopAllCutscenes
Stops all sequences with a cutscene flag
- Reset
Resets the sequence, optional parameters are "play on reset" and "seek to start"
- Pause/Resume
Pauses/resumes all playing sequences (used for game pause functionality)
- Set/GetPlayingSpeed
You can set the playback speed of the current sequence
- Set/GetStartEndTime
Change the duration of the current sequence

### Sequence captures

- Sequence captures in Sandbox
While in Sandbox you can use the "Render Output" tool in Trackview to output your sequence data to disk. It provides you with all the necessary options and offers batch render functionality.
- Sequence captures in pure game
To capture sequences in pure game mode you can use existing cvars. Make sure the following cvars are holding valid values:
cvar name | expected value
--- | ---
capture_file_format | Set the file format extension (default is "tga", currently supported file formats are "jpg" and "tga")
capture_frame_once | Defines if a single frame is going to be captured (screenshot) (default is "0" for sequence capturing)
capture_folder | Defines the folder within your game project (will be created if it doesn't exist already, data will be overwritten!)
t_FixedStep | Defines the timestep for the renderer (default is 0,033333 for 30 fps)
capture_file_prefix | Defines the prefix within the file name
capture_frames | Enables/Disables frame capturing, make sure all other values are set correctly before setting this to "1"

### Manage camera parameters

- General camera parameters
You can set and get the camera parameters for the currently active camera. Those parameters include:
parameter name | purpose
--- | ---
Camera Id | set/get the current camera entity id
Fov | fov setting of the currently active camera
Game Camera Influence | set/get the current game camera influence (implemented in gamecode)
NearZ | set/get the current NearZ value of the camera (default is 0.25)
- Camera shake
You can enable and disable the camera shake for the current sequence (no matter what camera is used). To create a camera shake effect you have to add the corresponding track to your camera entity in your sequence first - the shake feature is enabled by default.

### In This Topic
