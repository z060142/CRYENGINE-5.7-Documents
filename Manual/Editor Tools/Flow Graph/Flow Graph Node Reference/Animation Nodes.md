# Animation Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450568
- Page ID: 29450568
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Animation Nodes
- Parent: Flow Graph Node Reference

## Content

### AnimationEventListener

Listens for a specific animation event and triggers the output.

### AttachmentControl

By choosing a.cdf entity, you can choose all its attachments and hide or display them. The Barrel_Guy is a cdf entity, who has a Barrel attached to his hand.

This Barrel is getting shown or hidden based on Trackevent in a Trackview sequence.

![Image](https://www.cryengine.com/docs/static/attachments/28901194)

### BoneInfo

By choosing a.chr entity, you can choose all its bones and use the local and global position and rotation data of that bone to create attachments or link objects.

### CheckAnimPlaying

Can check if a defined animation is being played or not.

### CooperativeAnimation

Allows the playing of an exact positioned animation on one or two characters with alignment.

### LookAt

The LookAt node makes AI entities use LookAt control. Target is for an entityID and TargetPos is a position in space.

### NoAiming

Controls the AnimationGraph of the attached entity.

### PlayAnimation

Plays an animation on this character's skeleton - bypassing the AnimationGraph. The animation name can be specified directly as mapped in the.cal file.

### PlayCGA

Plays.cga files and their animation also plays.anm files belonging to the.cga file. Trigger starts the animation.

### PlaySequence

Plays a Trackview Sequence. Sequence has to point to the right Trackview Sequence. StartTrigger is starting the sequence. StopTrigger is stopping a sequence. PerformBlendOut would make sure that the camera has a seamless blend into the game camera when the sequence is over. Make sure to beam the player to the right place when the sequence starts. BlendPosSpeed and BlendRotSpeed sets the speed which the blending of position and rotation happens to the game camera. If BreakOnStop is set to True, stopping the sequence doesn't make it jump to the end. Start time sets the time from which the sequence starts playing.

Started outputs the start, Done outputs if the sequence is either played or skipped, Finished outputs only when the scenes complete without being skipped and Aborted outputs only when skipped. For example, if you want the game to fade in if the sequence is skipped, you would use Aborted, but in case the same sequence is finished, you want to trigger another sequence, you would use the Finished.

![Image](https://www.cryengine.com/docs/static/attachments/28901195)

### StopAnimation

Controls the AnimationGraph of the attached entity.

### SynchronizeTwoAnimations

Synchronize two animations between two entities.

### TriggerOnKeyTime

Triggers the animations based on the key time.

[AnimationEventListener](#animationeventlistener)[AttachmentControl](#attachmentcontrol)[BoneInfo](#boneinfo)[CheckAnimPlaying](#checkanimplaying)[CooperativeAnimation](#cooperativeanimation)[LookAt](#lookat)[NoAiming](#noaiming)[PlayAnimation](#playanimation)[PlayCGA](#playcga)[PlaySequence](#playsequence)[StopAnimation](#stopanimation)[SynchronizeTwoAnimations](#synchronizetwoanimations)[TriggerOnKeyTime](#triggeronkeytime)
