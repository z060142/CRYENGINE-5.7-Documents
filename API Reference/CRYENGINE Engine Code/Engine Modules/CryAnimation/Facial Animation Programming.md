# Facial Animation Programming

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306439
- Page ID: 23306439
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAnimation > Facial Animation Programming
- Parent: CryAnimation

## Content

##
Overview

##
CFacialEffector

An effector (also known as an expression) represents an action that the face can perform - it might be a simple morph target, a bone rotation, or a compound of simpler expressions.

Expressions can be applied to varying degrees, from -1 to 1. A value of 1 indicates that the expression is fully applied (Example: in the case of a morph target expression, the morph is completely applied to the mesh). A value of 0 indicates that the expression is off. -1 means that the opposite of the expression is applied (the morph target is subtracted from the model).

In the case of compound expressions, a CFacialEffCtrl object maps the input value to a value to pass to each child expression.

##
CFacialEffCtrl

This class is used by compound CFacialEffector instances to control a sub-effector. It is responsible for taking the input value and calculating the value to pass to the child control. This calculation can be controlled either by a linear mapping or by a spline.

##
CFacialEffectorsLibrary

This class represents a library of facial effectors (or expressions). This is usually read from a *.FXL file. Each model refers to a particular expression library, which it uses to display the current state of animation sequences.

Facial animations are designed to work with any expression library. This means that it should be possible to tweak expressions for a particular character and have facial animations work on them, even if they were authored using a different character/library.

##
CFacialModel

This class stores information relevant to a particular model as used in facial animation. Each character model that contains morphs also creates a CFacialModel instance that it owns. This class is used by the facial animation system to get information about what morphs the character contains.

It is also the class responsible for taking the final calculations for what morphs should be displayed (see CFaceState) and applying them to the character instance. This is implemented in the method ApplyFaceStateToCharacter().

##
CFacialInstance

This is the class that is most commonly dealt with by game code. It allows the client code to control the facial animation of a single character. In particular, the methods PlaySequence() and StopSequence() allow facial animation sequences to be started and stopped.

Internally, CFacialInstance delegates most aspects of playing sequences to CFacialAnimationContext, which contains a list of sequences that are currently being played. In the existing implementation, CFacialInstance actually only ever starts a single sequence instance in CFacialAnimationContext.

The sequence playing interface of CFacialInstance contains a number of sequence layers. Each layer can be playing a single sequence, or it can be inactive. Each layer has a different priority, and only the highest priority layer with an active sequence is actually passed to CFacialAnimationContext to be displayed on the character.

The different layers in the animation system are designed to reflect the different uses that the animation system is often put to. For instance, there is a layer reserved for animations played via the animation graph (see the EFacialSequenceLayer enumeration for a list of the available layers). Although this has the downside that it encodes knowledge of higher level systems within the facial animation code, it simplifies the use of the system and allows multiple client systems to manage concurrently playing sequences within the facial animation code.

Updating the facial instance is a two-part process. UpdatePlayingSequences() is the method that advances the time of the currently playing sequences, and deactivates them if they have finished. This should be called each frame, even if the character is not visible. This method does two major things: Firstly it calls UpdatePlayingSequences() for the context instance to update the state of the currently playing sequence. Then it updates all the layers in the instance and makes sure that the highest priority animation is being played in the CFacialAnimationContext.

Update() is the method that evaluates the current state of the playing sequences and applies the expressions that are being played to the character model. To do this, it uses an instance of CFaceState to represent the desired state of the face. It passes this instance to the CFacialAnimationContext, which evaluates all the splines in the sequence at the current point in time and stores the desired values in the face state.

The face state is then passed to the facial model, which applies all the desired expressions to the character model. This usually involves recursively evaluating the compound expressions, until the basic morph targets and bone rotations have been reached.

##
CFacialAnimation

This class is the major manager class for the facial animation system. There is a single instance created as part of the CharacterManager class, and so is therefore globally accessible via the instance of ISystem.

Its main responsibilities are providing methods for the creation and serialization of expression libraries and sequences. Caching is also performed by the object. It also manages joystick sets, although these are only used in the Editor.

Note this object does not manage facial instances – these are managed by the character instance that they represent.

##
CFacialSentence

This class is owned by CFacialAnimSequence, and represents the set of phonemes that make up the lip syncing for a given sound. Basically it contains a collection of phonemes and the times they begin and end.

During CFacialAnimSequence::Update(), this class is passed the CFaceState, and it then adds expressions to the face state to display the current lip syncing. It usually adds two expressions – one for the phoneme that is currently active and one for the next one, performing a smooth cross-fade between the two. These expressions are then applied to the facial model along with the expressions from the rest of the sequence splines.

##
CFacialAnimChannel

This class represents one of the animated expressions in a sequence. The sequence contains a collection of channels, each of which describe how a given expression varies over time, using a spline.

##
CFacialAnimSequence

This class represents a facial animation sequence. Usually this class is serialized in a *.FSQ file, but empty ones can also be created by the CFacialAnimation instance. It contains a collection of CFacialAnimChannels, and a collection of sound entries, each of which can contain a CFacialSentence.

The Animate() method is responsible for evaluating all parts of the sequence and updating a CFaceState instance to represent them. This method first loops through all the channels in the sequence and calculates the current value of the spline. It then adds the associated expression to the face state with that value. The remaining step is to loop through all the CFacialSentence instances and call Animate() on them.

##
CFaceState

This class is used to refer to the desired state of a face model. It is used to hold the state that is calculated by CFacialAnimationContext, and is then read by CFacialModel and applied to the mesh.

The object contains a list of facial effectors. Each one must be a simple expression - any compound expressions that need to be applied are first broken down into morph targets or bone rotation expressions.

##
CFacialAnimationContext

This class is not part of the external interface to the system. It is used internally by CFacialInstance to manage the playing of sequences.

The Update() member is responsible for calculating the desired face state based on all currently playing sequences at the current point in time. It works by first calling Animate() for all the current sequences to find out what expressions should be played at what intensity. It then recursively breaks down complex expressions into their sub-expressions, based on the curves in the CFacialEffCtrl instances associated with each sub-expression.

The UpdatePlayingSequences() is responsible for updating the time of the currently playing sequences. It simply adds the time delta to the current time of each sequence that is playing, and then removes any sequences from the list that are finished.

[CFacialEffector](#cfacialeffector)
[CFacialEffCtrl](#cfacialeffctrl)
[CFacialEffectorsLibrary](#cfacialeffectorslibrary)
[CFacialModel](#cfacialmodel)
[CFacialInstance](#cfacialinstance)
[CFacialAnimation](#cfacialanimation)
[CFacialSentence](#cfacialsentence)
[CFacialAnimChannel](#cfacialanimchannel)
[CFacialAnimSequence](#cfacialanimsequence)
[CFaceState](#cfacestate)
[CFacialAnimationContext](#cfacialanimationcontext)
