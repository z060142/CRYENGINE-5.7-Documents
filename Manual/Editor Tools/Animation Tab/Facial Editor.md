# Facial Editor

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450435
- Page ID: 29450435
- Breadcrumb: Editor Tools > Animation Tab > Facial Editor
- Parent: Animation Tab

## Content

## Overview

The Facial Editor (FE) is a tool for creating and editing asset files (except model files, which are created elsewhere). It provides a graphical interface for creating expression libraries and for using those expressions to create sequences.

This tool is not supported at the moment, but for those users who still use it, we've kept the information that's currently available. However, there will be no additions to this tool's documentation.

The image below shows an overview of the FE and its subwindows:

![Image](https://www.cryengine.com/docs/static/attachments/44971068)

The FE layout is user customizable; the Editor may be displayed differently for different users.

The Facial Editor interface is divided into several subwindows or panes, each of which is used to edit a different aspect of facial animation.

We'll discuss all these separately below.

### 1. Menu Bar

![Image](https://www.cryengine.com/docs/static/attachments/28900369)

#### Project

The project management facilities provided here have not been maintained recently.

**New** | Creates a new project.
--- | ---
**Open** | Opens a project.
**Save** | Saves the current project.
**Save As** | Saves the current project and lets you specify a name and location.

#### Edit

**Undo** | Undo last operation.
--- | ---
**Redo** | Redo operation after undo.

#### Expressions Library

**New** | Closes the current expression library and create a new one.
--- | ---
**Open** | Closes the current expression library and open another one.
**Save** | Saves expression library.
**Save As** | Saves the expression library under a different file name. Currently, unlike some other applications, save as will create the new document, but will not then switch to editing it. The editor will continue to display the previous document. This may change in the future.
**Export Selected Expressions** | Creates a new expression library consisting only of those expressions that are currently selected in the Expressions Explorer pane. These expressions can then be imported into a different library. The user will be prompted for the file name of the library to export to.
**Import Expressions** | Opens an existing expression library and merges the expressions into the current one. The user will be asked for the name of a library to import.
**Batch Update With Selected Expressions** | Selects a series of expression library files and merges the expressions that are currently selected into them, replacing the expressions in each library if they already exist. Can be used to perform sweeping changes to many expression libraries simultaneously. You will be shown an open dialog where he is asked to select the files to be updated. Files should be checked out by the user in Perforce, if necessary, before this operation is performed.
**Morph Check** | Displays a list of all morphs that are referenced in the expression library that are missing in the currently loaded character.

#### Character

**Load** | Load a new character to use in the preview. This character can be either a CHR of a head, a CDF of a head with eyes attached or a full body (CDF with head attached). If the head model does not contain any morph targets, the loading will fail.
--- | ---

#### Sequence

**New** | Close the existing sequence and create a new one. The user will be prompted to save the current sequence, if it is modified. He will then be shown a save dialog to pick the name of the new sequence.
--- | ---
**Open** | Close the current sequence and open another one. The user will be prompted to save the current sequence, if it is modified. He will then be shown an open dialog to pick the sequence file to open.
**Save** | Save sequence.
**Save As** | Save the sequence under a different filename. Currently, unlike some other applications, Save As will create the new document, but will not then switch to editing it.The editor will continue to display the previous document. This may change in the future.
**Load Sound** | Load a compatible.wav file into the sequence. The sound waveform will be displayed in the waveform control, and the sound will play when the play button is pressed. The sound will then be associated with the sequence and used for any subsequent lip-synching operations.
**Load Skeleton Animation** | Load a skeleton animation (.CAF file) into the current sequence. Only animations available through the cal (Crytek Animation List) file are accessible. The skeleton animation will then be previewed when the sequence is played, allowing the animator to view the facial animation as part of the skeleton animation. The skeleton animation will then be associated with the sequence when it is saved.
**Batch Apply Expression** | Unsupported.
**Export Selected Expressions** | Create a new sequence file containing only the currently selected channels. The user will be prompted for the filename of the new sequence. If any channel folders are selected, their children will be exported as well.
**Import Expressions** | Load a sequence and merge its channels into the current one. The user will be prompted for the name of the sequence to load. If a channel exists in the current sequence, the user will be asked whether he wants to overwrite it or keep the current one.
**Batch Update With Selected Expressions** | Open a series of sequences and merge the channels that are currently selected in the sequence dialog into each one, replacing the channels if they already exist.
**Load Video Extracted Sequence** | Load a text file generated by the FaceAnim utility, used for motion capture of an actors face. Both curves and video are imported.
**Load Video (Ignore Sequence)** | Load a text file generated by the FaceAnim utility used for motion capture of an actors face, but ignore the motion data and loads the video only.
**Load Group File** | Load a.grp file which was saved from the level editor. GRP files are exported sequence objects which appear in the level when a new trackview sequence is created. Saving these objects as grp files exports an XML format of everything contained in the sequence from audio positions, to skeletal animation and camera paths. This can then be imported into a facial sequence for use in the Facial Editor.

#### Joysticks

**New** | Create new joystick file.
--- | ---
**Open** | Open joystick file.
**Save** | Save joystick file.
**Save As** | Save joystick file and specify name/location.
**Create Expression From Current Positions** | Take the expression currently being shown on the character, as defined by the joysticks, and create an entry in the expression library that captures it.

#### Lip Sync

**Extract Phonemes** | Analyze the currently loaded waveforms and select a series of phonemes to use for lip synch. If known, the text that the sound represents can be entered - this is used to improve the accuracy of the result.
--- | ---
**Batch Process Directory** | Batch processes a directory of audio, into fsq files using the same name as the audio file itself.

### 2. Preview Pane

![Image](https://www.cryengine.com/docs/static/attachments/28900384)

The Preview window shows a character on which the selected expressions and animations can be previewed.

It can show any model supported by the engine as long as either the main mesh or an attachment features at least one morph target. The file that is currently being displayed is shown in the title text of the pane.

The model being shown can be changed by using the [LINK] option. Various preview options can be changed by using the Preview Options Pane.

### 3. Video Frame Pane

This pane is deprecated and has no functionality. It will be removed in the future.

### 4. Preview Options Pane

This pane provides options to control what is shown in the Preview Pane. Many of these options are the same as those provided in the Character Editor.

![Image](https://www.cryengine.com/docs/static/attachments/28900383)

Option | Description
--- | ---
**LookIK** | Causes the model to look toward the camera, using the spine, neck, head, and eye bones together
**LookIK Eyes Only** | If LookIK is enabled, move only the eyes
**Show Eye Vectors** | Shows lines pointing in the direction of the eyes bones; used for debugging
**Look IK Offset X** | Specifies the offset of the LookIK Target on the x-axis, relative to the center of the camera
**Look IK Offset Y** | Specifies the offset of the LookIK Target on the y-axis, relative to the center of the camera
**Procedural Animation** | Enables procedural animation of the eyes and eyelids, for automatic twitches and blinking
**Display Physics** | Draws the physics meshes of the model
**Show Grid** | Toggles the grid display along the z=0 plane
**Lighting** | Toggles the lighting on the model
**AnimLights** | Toggles between the static light position and the orbiting lights in the scene
**Background Color** | Alters the background color by using RGB values
**Object Ambient** | Chooses the ambient lighting for the model
**Light Diffuse1** | Alters light 1's diffuse color by using RGB values
**Light Diffuse2** | Alters light 2's diffuse color by using RGB values
**Light Diffuse3** | Alters light 3's diffuse color by using RGB values
**Show Wireframe1** | Shows the model as a wireframe
**Show Wireframe2** | Shows the model as a wireframe
**Show Tangents** | Displays lines along the tangents of each mesh vertex
**Show Binormals** | Displays lines along the binormals of each mesh vertex
**Show Normals** | Displays lines along the normals of each mesh vertex
**Show Skeleton** | Displays the underlying bones
**Show Joints Names** | Shows the debugging information for bones
**Show Joints Values** | Shows the debugging information for bones
**Show Shaders** | Displays the currently used shaders
**FOV** | Sets the Field of View (can be used to zoom in)

(1) Procedural animation must also be enabled by using the ca_face_procedural=1 (or 2 or higher) console command.

### 5. Effectors Slider Pane

![Image](https://www.cryengine.com/docs/static/attachments/28900467)

This pane shows a list of expressions in the current library and provides a slider control for each of them. Manipulating this slider control allows the expression to be previewed in the Preview pane. Multiple sliders can be simultaneously manipulated, and their effects will be cumulative.

The Effectors Slider pane contains two tabs. The first one is called **Morph Targets**, and shows only the expressions that are simple morph targets. The second tab is called ** All Effectors** and shows all effectors in the current library.

An expression can be quickly created from the current slider positions using the Effector Library Pane. This can be an efficient way to create new composite expressions. To the left of each slider is a check box that enables/disables the preview of that effector. Turning this box off is equivalent to setting the slider position to 0. On the far right of each slider is a control for setting the balance of the effector in the preview window.

Expressions can be dragged from this pane to the Expressions Explorer Pane to add sub-expressions to compounds, or to add an expression to a folder. To clear all previewed expressions quickly there is a button at the top of the pane called "**Clear All**".

#### Effectors Slider Pane Main Menu

![Image](https://www.cryengine.com/docs/static/attachments/28900440)

**Clear All** | Clears all applied expressions
--- | ---

#### Morph Targets Tab

Lists all available morph targets in the character. Weight sliders within this view allow the user to preview each morph by moving the slider to the left (negative values), or to the right (positive values). Balance allows asymmetrical preview of each shape or morph.

![Image](https://www.cryengine.com/docs/static/attachments/28900441)

**Effector** | Displays the name of the morph targets stored within the character; the checkbox next to the name of the morph enables and disables the effect of the weight slider.
--- | ---
**Weight** | Moves the morph target from the neutral position to the negative or positive values.
**Val** | Displays the position value of the slider, in the numerical form.
**Balance** | Controls the balance factor or symmetry of the morph.

#### All Effectors Tab

Similar to the previous tab, but lists all possible effectors from morphs to expressions.

![Image](https://www.cryengine.com/docs/static/attachments/28900442)

**Effector** | Displays the name of the effectors available, from morph targets to composed expressions; the checkbox next to the name of the effector enables or disables the effect of the weight slider.
--- | ---
**Weight** | Moves the effector from the neutral position to the negative or positive values.
**Val** | Displays the position value of the slider, in the numerical form.
**Balance** | Controls the balance factor or symmetry of the effector.

### 6. Expressions Explorer Pane

This pane allows the user to browse the expressions in the current library and to edit them. Expressions can also be created or deleted in this way.

![Image](https://www.cryengine.com/docs/static/attachments/28900468)

There are two halves to the pane. The left half is the **Expressions Tree View**, showing the composition of the expressions in the library. The expressions can be grouped into folders for organizational purposes. Just as expressions are shown as children of folders in the tree view, expressions have their own children - these are the sub-expressions that make up the compound expression. The icon next to each item indicates the type of expression, either a compound or primitive.

#### Functionality

When an expression is selected, it can be edited in the right half of the pane. The controls available for editing this expression depend on its type. If the expression is a morph target, it cannot be edited. It is completely determined by the model asset file. For a bone or attachment expression, there is an edit box for specifying the bone or attachment to manipulate, and a series of controls for specifying how much to move/rotate the object for each axis. Angles are in degrees.

In the case of compound expressions, the pane shows a small window for each sub-expression, along with a curve that maps the input display value to the display value for that child. This curve can be either linear or a spline. If it is linear, the only way to edit it is to change the slope of the line. This can be done by right clicking and selecting change weight.

If the curve is a spline, then it can be edited using the mouse. The spline is determined by placing control points. A control point is shown on the spline as a small square. These points can be dragged around using the left mouse button. Double clicking on a point deletes it; double clicking anywhere else on the curve creates a new control point at that position.

Above the sub-expression controls there are two sliders. The top one is used to preview the expression, by setting the display value somewhere between -1 and +1. The bottom slider is used to set the balance of the expression in the Preview Pane.

Above the sliders there is a toolbar. This toolbar shows the value of the slider as a numerical value. There is a play button that allows the preview to continue in real-time. The three buttons on the right can be used to set the preview value to minimum, maximum or zero.

Expressions can be dragged from their current position to another position in the tree. This will have the effect of adding the expression as a child of the target expression. However it will also remain in its previous position - there will now be an additional reference to it in the library. Expressions can also be dragged from this pane to the Sequence Pane to add new expression channels to the sequence.

#### Expressions Tree View

Lists expressions that have been assembled into an expression library. Within this view the user can define the existing morphs in the character and compose them into expressions using a right click menu interface (below).

![Image](https://www.cryengine.com/docs/static/attachments/28900444)![Image](https://www.cryengine.com/docs/static/attachments/28900445)

Expressions Tree View | Right-Click Menu
--- | ---
**New Folder** | Creates a new folder.
**New Expression** | Adds an existing morph or creates a new expression. If the name has already been used by an expression in the library, the new expression cannot be created - each expression name must be unique. In this case, the user is given the option of adding the existing expression as a child of the selected one.
**New Bone Control** | Creates a new bone controller or channel through which bones within the character can be animated. If the name is already used by an expression in the library, the new expression cannot be created - each expression name must be unique. In this case the user is given the option of adding the existing expression as a child of the selected one.
**New Attachment Control** | Create an expression that rotates an attachment (not supported for skin attachments). If the name is already used by an expression in the library, the new expression cannot be created - each expression name must be unique. In this case the user is given the option of adding the existing expression as a child of the selected one.
**Rename** | Rename an expression or folder.
**Copy** | Copy an expression.
**Paste** | Paste an expression.
**Remove** | Remove expression or folder.

#### Curves Tab

Curves tab allows the user to control how multiple shapes will blend when the expression transitions from minimum amplitude to full amplitude.

![Image](https://www.cryengine.com/docs/static/attachments/28900443)

![Image](https://www.cryengine.com/docs/static/attachments/28900446) **Expression Value** Time value from -1.0 to 1.0.

![Image](https://www.cryengine.com/docs/static/attachments/28900447) **Animate Expression Button** Plays the morph/expression sequence.

![Image](https://www.cryengine.com/docs/static/attachments/28900448) Toggles play button to start at -1.0 (off) or from 0 only (on).

![Image](https://www.cryengine.com/docs/static/attachments/28900431) Fixed Value Button Set slider position to -1.

![Image](https://www.cryengine.com/docs/static/attachments/28900430) **Fixed Value Button** Set slider position to 0.

![Image](https://www.cryengine.com/docs/static/attachments/28900432) **Fixed Value Button** Set slider position to +1.

**Expression Preview Slider** Top slider sets expression from -1.0 to 1.0. I ONLY SEE 1 SLIDER, IS THAT CORRECT? IF NOT, WHERE CAN I FIND BOTH?

![Image](https://www.cryengine.com/docs/static/attachments/28900433)

**Expression Balance Slider** Lower slider sets balance from -1.0 to 1.0.

![Image](https://www.cryengine.com/docs/static/attachments/28900434)

**Spline Display**

Defines how morph shapes blend in over the time an expression (multiple morphs) transition from minimum amplitude to full amplitude.

![Image](https://www.cryengine.com/docs/static/attachments/28900435)

#### Preview Tab

Displays a preview of the currently loaded asset.

### 7. Sequence Pane

![Image](https://www.cryengine.com/docs/static/attachments/28900370)

This pane is used to edit the sequence itself. It is divided into four main areas: the [Sequence Tree View](Facial%20Editor.md#FacialEditor-SequenceTreeView), the [Curve Track View](Facial%20Editor.md#FacialEditor-CurveTrackView), [/docs/static/engines/cryengine-5/categories/23756816/pages/29450435#FacialEditor-AudioTrack](Facial%20Editor.md#FacialEditor-AudioTrack) and the [Sequence View Toolbars](Facial%20Editor.md#FacialEditor-SequenceViewToolbars).

The **Sequence pane** displays all related information about the sequence from expressions, to audio and the curves/keyframes themselves.

#### Sequence Tree View

The left part is a tree view of the channels in the sequence. The channels are shown grouped into folders, which allow them to be logically organized. Allows the creation of a list of available expressions which can be directly animated within the sequence. These are assembled by adding shapes and expressions from the expression library into the tree view.

![Image](https://www.cryengine.com/docs/static/attachments/28900437)![Image](https://www.cryengine.com/docs/static/attachments/28900438)

Sequence View | Right Click Menu
--- | ---
**New Folder** | Create a new channel folder in the sequence. A dialog is displayed asking the user for the name of the folder to create.
**Rename Folder** | Only appears if a folder is selected. A dialog is displayed asking the user for the new name of the folder.
**Remove** | Remove element such as a folder or an expression.
**Add Balance** | Adds a balance channel to the current folder. This channel will control the balance for all expressions in the same folder as it and any child folders.
**Add Selected Expression** | Only appears if an expression is first selected in the Expressions Explorer Pane. Creates a new channel referring to the selected expression as a child of the selected folder.
**Cleanup Keys** | Apply an optimization algorithm to the key frames in the curves for this channel. This algorithm attempts to delete as many keys as it can without changing the shape of the curve more than a small threshold value.
**Smooth Keys** | Function to smooth over noise. Mostly used for mocap data.
**Remove Noise** | Function to remove noise. Mostly used for mocap data.
**Add Phoneme Strength** | Add a channel that controls the amplitude of the phoneme expressions during lip-synching. *seems to be only appearing in special cases.
**Add Morph Target Vertex Drag** | Unsupported.
**Add Procedural Animation** | Unsupported.
**Add Layer** | Adds an editing layer onto the channel. See [Channel Layers](Facial%20Editor.md#FacialEditor-ChannelLayers) for more information.
**Delete Layer** | Deletes the editing layer of the channel. See [Channel Layers](Facial%20Editor.md#FacialEditor-ChannelLayers) for more information.
**Collapse Layer** | Commit changes made within a layer to base curves permanently. See [Channel Layers](Facial%20Editor.md#FacialEditor-ChannelLayers) for more information.
**Insert Viseme Shapes** | Mode in which morphs can be entered in text form to produce overlapping shapes which blend in and out of one another. This is useful for producing fast layouts of visemes for keyframed lip sync. Expressions must have "visim" as a prefix in the name.

#### Curve Track

Selecting a channel in the tree view causes its curves to be shown in the top part of the curve Track (selecting a folder is equivalent to selecting all of its children recursively). This control displays the splines, similarly to the sub-expression control in the Expressions Explorer Pane.

![Image](https://www.cryengine.com/docs/static/attachments/28900421)

##### Curve Track Functionality

Curves can be edited here using the mouse. The curves are controlled by control points or keys, which appear as small squares. These can be dragged using the mouse. Double-clicking on a key deletes it, while double-clicking elsewhere on a curve creates a new key.

Multiple keys can be selected by clicking on an empty part of the control and dragging, creating a selection box. Holding down the control button allows keys to be added to the current selection set. When multiple keys are selected, they can all be dragged around at the same time.

Keys can be copied by holding down control and dragging. This creates a copy of all selected keys and begins dragging them.

Holding down the mouse wheel and dragging allows the display to be dragged around, allowing us to view different parts of the timeline.

The scale of the display can also be changed using the mouse. Scrolling the mouse wheel zooms in or out on the current position. Holding down the shift key and the mouse wheel and dragging the mouse left or right compresses or expands the time scale, while dragging up and down compresses the value axis. Effectively this allows zooming to be done on each axis independently of the other.

Above the curves there is a timeline control. This displays the time values along the time axis. Clicking on the timeline control sets the current sequence time to that position.

It also displays markers at each point on the timeline where a key exists for the currently displayed curves. These markers can be moved around and edited much like the keys can be, except that this restricts movement to the time axis (i.e. you cannot change the values of the keys), and each marker controls all the keys at that point on the timeline simultaneously.

The markers are also color-coded based on the number of keys at that point in time. A green color indicates that few of the channels in the sequence have keys at that position, while a red color indicates the opposite. Note that this color is determined by reference to all the channels in the sequence, rather than just the visible ones. This functionality allows the user to see whether a key is part of a major pose in the sequence, or whether the key is relatively unrelated to the positions of other keys.

The bottom part of the pane shows the waveform of the current sound, if one is loaded. This can be used to see critical parts of the sound in order to match up movements appropriately.

At the far bottom the current phonemes are displayed. These are usually generated by extracting them from the loaded sound (by right-clicking on the wave control). Once this has been done, however, the phonemes can be edited to improve the overall quality.

##### Curve Track - Key Bar (highlighted in red below)

The key bar displays any keys within the selected track which can be manipulated in the same way as in the main curve view, though locked to the horizontal axis. This is useful for scaling time of a group of keys without accidentally altering amplitude.

![Image](https://www.cryengine.com/docs/static/attachments/28900422)

##### Curve Track - Amplitude (highlighted in red below)

Amplitude displays the entire range accessible for a particular expression or joystick control. Though depending on actual setup ranges below zero may not necessarily have any effect.

![Image](https://www.cryengine.com/docs/static/attachments/28900423)

##### Curve Track - Curve Display (highlighted in red below)

The curve display shows both the curve of the selected track as well as the keys themselves.

![Image](https://www.cryengine.com/docs/static/attachments/28900424)

#### Audio Track

![Image](https://www.cryengine.com/docs/static/attachments/28900425)

##### Audio Track - Right Click Menu

![Image](https://www.cryengine.com/docs/static/attachments/28900426)

**Clear all Waveforms** | Removes all wav forms from the track.
--- | ---
**Lip Sync With Text** | Opens dialogue where text can be entered which matches the spoken audio and will generate an appropriate list of phonemes. If left empty the plugin does it's best to guess the phonemes necessary.
**Remove Sound** | Removes wav file from sound track.

##### Audio Track- Label Bar (highlighted in red below)

Labels the wav and lip sync portions of the audio track.

![Image](https://www.cryengine.com/docs/static/attachments/28900427)

##### Audio Track - Lip Sync Bar (highlighted in red below)

The lip sync bar displays the morphs which have been added through a referenced recording list, or through the "lip sync with text" option. The bar is split into 2 sections. The upper section stores the words that may have been entered to guide the lip synch extraction process and the lower half shows the phonemes that have been used to create the extracted lip synch.

![Image](https://www.cryengine.com/docs/static/attachments/28900428)

##### Audio Track - Wav Display (highlighted in red below)

Displays wav files added to the sequence in graphical form as well as the file name and it's location on disk.

![Image](https://www.cryengine.com/docs/static/attachments/28900429)

#### Sequence View Toolbars

![Image](https://www.cryengine.com/docs/static/attachments/28900412)

![Image](https://www.cryengine.com/docs/static/attachments/28900413) Play Sequence – Plays the sequence

![Image](https://www.cryengine.com/docs/static/attachments/28900414) Stop Sequence – Stops playback of the sequence

![Image](https://www.cryengine.com/docs/static/attachments/28900415) Facial Sequence Properties – Displays start and end times of the sequence or enables

![Image](https://www.cryengine.com/docs/static/attachments/28900416) Current Sequence Time – shows current sequence time.

![Image](https://www.cryengine.com/docs/static/attachments/28900417) Current Frame No – Shows frame number at current time.

![Image](https://www.cryengine.com/docs/static/attachments/28900418) Playback Speed – Shows current playback speed in percent.

![Image](https://www.cryengine.com/docs/static/attachments/28900419) Animate Skeleton – Plays back selected animation on the character.

![Image](https://www.cryengine.com/docs/static/attachments/28900420) Sequence Camera – Plays back camera animation loaded from a "sequence object" saved from a cinematic in trackview.

![Image](https://www.cryengine.com/docs/static/attachments/28900404) Overlap Sounds – Allows sounds to overlap when they have been placed in an overlapping fashion. When it is off, sounds are trimmed when a new sound begins to play.

![Image](https://www.cryengine.com/docs/static/attachments/28900398) The key tangent settings can be manipulated using the key settings toolbar buttons (see image above).

There are seven buttons that affect tangents, each of which affects the currently selected keys:

![Image](https://www.cryengine.com/docs/static/attachments/28900399) Clear all tangent settings for these keys - the key tangents will be automatically calculated.

![Image](https://www.cryengine.com/docs/static/attachments/28900400) Set the incoming (from the left) tangent to 0.

![Image](https://www.cryengine.com/docs/static/attachments/28900401) The spline stays at the value of the previous key until it gets to this key.

![Image](https://www.cryengine.com/docs/static/attachments/28900402) The incoming (from the left) tangent will be linear to the previous key. If the previous key has a linear out tangent then the line between the two keys will be straight.

![Image](https://www.cryengine.com/docs/static/attachments/28900403) Set the outgoing (to the right) tangent to 0.

![Image](https://www.cryengine.com/docs/static/attachments/28900386) The outgoing (to the right) part of the curve will be a step - ie the spline will stay at the value of this key until it reaches the next key.

![Image](https://www.cryengine.com/docs/static/attachments/28900387) The outgoing (to the right) tangent will be linear to the next key. If the next key has a linear in tangent then the line between the two keys will be straight.

![Image](https://www.cryengine.com/docs/static/attachments/28900388) Zoom Extents horizontal

![Image](https://www.cryengine.com/docs/static/attachments/28900389) Zoom Extents vertical

![Image](https://www.cryengine.com/docs/static/attachments/28900390) Grid snap horizontal

![Image](https://www.cryengine.com/docs/static/attachments/28900391) Grid snap vertical

![Image](https://www.cryengine.com/docs/static/attachments/28900405)

![Image](https://www.cryengine.com/docs/static/attachments/28900406) Key All – Creates key for every track selected in tree view.

![Image](https://www.cryengine.com/docs/static/attachments/28900407) Zero All – Sets keys for selected tracks in tree view to 0 amplitude.

![Image](https://www.cryengine.com/docs/static/attachments/28900408) Amplitude – Adjusts amplitude of curve for a selected range.

![Image](https://www.cryengine.com/docs/static/attachments/28900409) Smooth – Smooths noise of selected keys. Useful for mocap.

![Image](https://www.cryengine.com/docs/static/attachments/28900410) Smooth Value – Sets the value used for the smoothing operation.

![Image](https://www.cryengine.com/docs/static/attachments/28900411) Cleanup Keys – Removes keys based on user defined threshold.

![Image](https://www.cryengine.com/docs/static/attachments/28900395) Cleanup Keys Value – Sets value for cleanup operation.

![Image](https://www.cryengine.com/docs/static/attachments/28900396) Remove Noise – Attempts to remove noise based on user defined threshold.

![Image](https://www.cryengine.com/docs/static/attachments/28900397) Remove Noise Value – Sets value for remove noise operation.

#### Channel Layers

When dealing with curves that have many keys, such as motion captured data, normal key-frame animation becomes very unwieldy. To help alleviate this situation, animators can make use of channel layers.

A channel layer basically freezes all the keys in the curve and allows the animator to create a new set of keys. These new keys control a new spline that gets added to the underlying data. By doing this, the animator can offset large numbers of keys quickly and intuitively. Once he is done, the layer can be collapsed, which removes the layer and updates all the keys to hold the new values.

### 8. Joysticks Pane

![Image](https://www.cryengine.com/docs/static/attachments/28900392)

Joysticks are user defined 2d controllers with a single manipulator that can be assigned to multiple morphs, expressions or other shapes in order to animate them in a graphical way – much like moving a physical joystick.

The Joystick pane is where the user can start assembling joysticks and wire them up to morphs, expressions or visemes that have been made available in the sequence view.

![Image](https://www.cryengine.com/docs/static/attachments/28900393) Toggle edit mode to resize or move joysticks in the view.

![Image](https://www.cryengine.com/docs/static/attachments/28900394) Toggle create key mode, when a controller is moved a key is automatically created.

![Image](https://www.cryengine.com/docs/static/attachments/28900377) Key all joystick tracks.

![Image](https://www.cryengine.com/docs/static/attachments/28900378) Zero amplitude of all joysticks.

##### Joystick Right Click Menu

**Create Joystick** | Creates a basic joystick without any active connections.
--- | ---

##### Joystick Right Click (no expression selected in tree view)

![Image](https://www.cryengine.com/docs/static/attachments/28900379)

**Edit Joystick Name** | Renames joystick.
--- | ---
**Set Joystick Color** | Alters color of joystick.
**Delete Joystick** | Removes the joystick permanently.
**Joystick Properties** | Views properties page of joystick.

##### Joystick Right Click (expression selected in tree view)

![Image](https://www.cryengine.com/docs/static/attachments/28900380)

**Edit Joystick Name** | Renames joystick.
--- | ---
**Set Joystick Color** | Alters color of joystick.
**Set Horizontal Joystick Channel** | Assigns selected expression in tree view to the horizontal channel of joystick control.
**Set Vertical Joystick Channel** | Assigns selected expression in tree view to the vertical channel of joystick control.
**Flip Vertical Channel** | Inverts the control of the Vertical axis.
**Flip Horizontal Channel** | Reverses the control of the horizontal axis.
**Delete Joystick** | Removes the joystick permanently.
**Joystick Properties** | Views properties page of joystick.

##### Joystick Properties

![Image](https://www.cryengine.com/docs/static/attachments/28900381)

##### Channels

**X Channel** | displays the expression assigned to the X channel.
--- | ---
**Y Channel** | displays the expression assigned to the Y channel.
**Flipped Checkbox** | Inverts the X or Y channel.

##### Video Import Settings

**X Scale** | Scales X component upon import.
--- | ---
**Y Scale** | Scales Y component upon import.
**Offset** | Offsets X or Y component upon import.

[1. Menu Bar](#1-menu-bar)[2. Preview Pane](#2-preview-pane)[3. Video Frame Pane](#3-video-frame-pane)[4. Preview Options Pane](#4-preview-options-pane)[5. Effectors Slider Pane](#5-effectors-slider-pane)[6. Expressions Explorer Pane](#6-expressions-explorer-pane)[7. Sequence Pane](#7-sequence-pane)[8. Joysticks Pane](#8-joysticks-pane)
