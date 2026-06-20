# Depth of Field Track

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874161
- Page ID: 26874161
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Track Cameras > Depth of Field Track
- Parent: Track Cameras

## Content

##
Overview

Depth of field is a way to enhance the realism of a Track View sequence in CRYENGINE by simulating the way a real-world camera works.

You can use a broad depth of field to focus on all or nearly all of a scene. And if you only want to focus on objects that are within a certain distance from the camera, use a narrow depth of field.

*
Example: Changing Focus from the object in front to the object in the background
*

##
General Concept

In CRYENGINE there are three values that allow you to adjust the depth of field: FocusDist(ance), FocusRange and BlurAmount. While the latter one should be self-explanatory, the other two (and especially the second one) are often misunderstood.

-
FocusDist describes how far away your Focus should be from the Camera; positive values are infront of the camera, negatives are behind (yes that is perfectly valid!).

-
FocusRange describes the size of the shape until the maximum blurriness (as defined by BlurAmount) is reached; it accelerates in a linear fashion in both directions: TO the camera and AWAY from it.
The effective distance in both directions is FocusRange / 2, which means half of the FocusRange is spread away from the FocusDistance.

For further illustration let me show you the following scene:

 |

Here we have a flat surface on the ground and three characters with different distances to the camera.

The character on the left is completely out of focus in the FOREground,

the character in the middle is completely out of focus in the BACKground, and

the right leg of the character on the right is in focus, while the left leg is halfway out of focus.

Note: the markings are aligned on the ground surface (= their feet define the distance to the camera)!

 |

 |

Lets take a look at the same scene in DoF debug mode (i'll explain in a second how to access it).

Here you can clearly see what is in focus: everything that is

**
BLACK
**
 is perfectly in focus,

**
GREY
**
 is slightly out of focus,

**
WHITE
**
 is completely out of focus.

 |

##
Workflow in Sandbox

First, this is an important command, remember it:
**
r_hdrdebug 4
**

##
Best practice

Create toolbox macros to be able to switch it on/off with a button click!

-
Tools -> Configure User Commands.

-
Tools -> Configure Toolbox Macros
When working with this debug mode you probably want to disable motion blur (r_motionblur 0), because it will interfere with the DoF when scrubbing in trackview (reason is because that mode is actually a blur debug mode).
In Sandbox there are two ways to control DoF: by Trackview and by Flowgraph. Lets have a look at trackview first, because that's what you will use in 90% of the time!

##
Trackview

In Trackview there a two node you can use to access DoF: you can add a DepthOfField node inside the Director node or you can add a Depth of Field track to any camera node.

If there are both, the latter takes precedence over the first one. You should use the node inside the Director node when you want to use the same DoF setup over different cameras, though most of the time you want specific DoF for each camera because you have more control over it!

You can add as many keys as you want, and of course use the curve editor to further tune your DoF changes over time.

##
Flowgraph

If you have a scene with full player control, adding DoF through flowgraph may be the better choice. You can do that by adding the
**
Image:EffectDepthOfField
**
 node. Usage is the same as with the trackview option.

Use Interpol:Float nodes to smoothly fade the DoF in and out. Generally you should avoid using to close and too much DoF through flowgraph, because its hard to track where and what the player is looking at.

In C2 we used it only to limit ViewDistances during cinematics to give it more of a "cinematic feeling".

##
General Rules

-
Keep your characters in focus!

-
Shift focus slowly and carefully, no "focus jumps"! (extremely important for 3D!)

-
Do not over do it. super blurriness almost always looks super dumb.

-
Do not use DoF for scenes that are far away. Your objects/characters will look like miniatures then. It works best for differentiation between close ups and background.

-
Use your own eyes to focus at different distances and try to see what is sharp and what is blurred (use your thumb as a helper). It should give you a good sense on how it should look like in your scene.
[#general-concept](
General Concept
)
[#workflow-in-sandbox](
Workflow in Sandbox
)
[#general-rules](
General Rules
)
