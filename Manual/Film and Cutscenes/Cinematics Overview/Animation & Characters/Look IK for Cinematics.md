# Look IK for Cinematics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874180
- Page ID: 26874180
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Animation & Characters > Look IK for Cinematics
- Parent: Animation & Characters

## Content

### Overview

There are two way of using CRYENGINE's Look IK feature on animated characters: **Trackview** and ** Flowgraph**. Trackview is mostly used for camera controlled scenes, while Flowgraph is used in most player controlled scenes.

### Trackview

To use the LookIK feature in Trackview, you have to add the track "LookAt" to the Character you want to use the LookIK at. Then, choose your target Entity from the dropdown. To look at the player choose the currently active camera in camera controlled scenes, otherwise use _LocalPlayer. "Target Smooth Time" is the time the character interpolates to and between LookAt keys (good values for eyes are 0.1-0.2, for head 0.3-0.5, fullbody 0.7-0.9). Last option to set is the "Look Pose" which defines what part of the body the character aligns to the target. The type of look poses available is defined in the character used. To learn more about the process of creating look poses see Asset Creation Doc, chapter [Look IK](/docs/static/engines/cryengine-3/categories/1114113/pages/1310769).

You may create as many LookAt keys as you want. As soon as the Timeline hits one key the character will align himself to the new setup. If you want to reset LookIK altogether just place an empty key.

### Flowgraph

In Flowgraph you can use the node **Animations:LookAt** to make a character look at a specific target entity or the player. Just assign the Character to the Node and a TargetEntity or enable LookAtPlayer and trigger the start input to force LookIK on a character.

You probably want to use a ProximityTrigger to make a character looking at the player when he is close, but every other logic is also perfectly possible of course!

[Trackview](#trackview)[Flowgraph](#flowgraph)
