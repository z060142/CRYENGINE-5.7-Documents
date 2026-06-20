# Audio & Cinematics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964892
- Page ID: 44964892
- Breadcrumb: Audio > Audio Overview > Audio & Cinematics
- Parent: Audio Overview

## Content

[Image: /docs/static/attachments/44964893]

##
Overview

This section describes how to play sounds in Trackview sequences.

##
Adding Sounds to Trackview Sequences

Create your sound and its play-event in Wwise.

In CRYENGINE use the ACE (Audio Controls Editor) to connect the Wwise play-event to an audio system Trigger. To learn more about the ACE read
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481](
here
.
)

Open the Trackview Editor (
Tools -> Track View
) and select the sequence from the drop-down menu in the Trackview toolbar.

Select the node of the Entity that should play the sound. If that node does not already contain a
*
Sound
*
 track, then right-click it and choose
Add Track –> Sound
.

In the
*
Sound
*
 track double-click to add a key. The key can be dragged to another time or the time can be entered manually above the Key properties on the right side.

[Image: /docs/static/attachments/44964929]

The Key properties you can edit are:

Property
 |
Description
 |

StartTrigger
 |
The audio system Trigger name that triggers on the key.
 |

StopTrigger
 |
The audio system Trigger name that triggers after the time set in
*
Duration
*
. Also refer to the default Start/StopTrigger behavior
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964879](
here
)
.

 |

Duration
 |
The time after the key position when the
*
StopTrigger
*
 is triggered. If the
*
Duration
*
 is 0, the
*
StopTrigger
*
 will not get triggered.
 |

Custom Color
 |
Changes the color of the duration in the track.
 |

*
Sound
*
 tracks in
*
Director Nodes
*
 can only play 2D sounds because no Entity is used in this case. Entity nodes can play 2D and 3D sounds.
