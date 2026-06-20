# Mannequin Animation Clip Properties

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308449
- Page ID: 23308449
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Animation Clip Properties
- Parent: Mannequin Editor

## Content

##
Properties Window

When you select an animation clip, the properties window will show the animation clip properties.

![Image](https://www.cryengine.com/docs/static/attachments/23998313)

You will be able to edit these when in the
[Mannequin Fragment Editor](../Mannequin%20Editor.md#MannequinEditor-FragmentEditor)
, or when editing a transition clip in the
[Mannequin Transition Editor](../Mannequin%20Editor.md#MannequinEditor-TransitionEditor)
. In the
[Mannequin Previewer](../Mannequin%20Editor.md#MannequinEditor-previewer)
 you will only be able to view the properties.

Animation Clip Property

 |
Description

 |

**
Animation
**

 |
The animation played by the clip. Empty for 'None' clips.

 |

**
Playback Weight
**

 |
With this value between 0 and 1 you can control how much of the clip is blended onto the previous layers (which are displayed
*
above
*
 the layer you are working on).

 |

**
Playback Speed
**

 |
The factor with which the this animation will be sped up (or slowed down). By default it is 1. You can speed up by using higher values, slow down by using lower values.

 |

**
Start Time
**

 |
Time (in seconds) to skip at the beginning of the animation.

 |

**
Looping
**

 |
Whether or not this clip will loop (as opposed to repeating the last key).

 |

**
Time Warping
**

 |
(Advanced) Enable time warping during the blend-in. Maps to low level animation flag CA_TRANSITION_TIMEWARPING.

 |

**
Force Skeleton Update
**

 |
While this animation is playing, force the skeleton pose to be updated, even if the character is not on screen. Maps to low level animation flag CA_FORCE_SKELETON_UPDATE. (CRYENGINE 3.8.3 and higher)

 |

**
Idle2Move
**

 |
<deprecated - use mannequin transitions instead> Maps to low level animation flag CA_IDLE2MOVE.

 |

**
Full control over root movement
**

 |
When enabled: During blends with other animations the root motion of those other animations is ignored. This option only works on animations that end up on the lowest layer, layer 0, in the animation system. (CRYENGINE 3.7 and higher)

 |

**
Blend
**

 |
Blend-in duration (can also be edited visually by dragging the narrow vertical mark at the left of the clip).

 |

**
Use Joint Masking
**

 |
<prototype - do not use>

 |

**
Align to Previous
**

 |
This field is not editable.

When you put two clips right after each other on a layer, this option will be enabled automatically.

This tells the system to automatically realign this clip when the previous clip changes length (because the animation length changes).

This re-alignment code only runs in the editor and does not apply when the animation changed completely, only when its the same animation but its length changes.

 |

**
Blend Channel
**

 |
**
Advanced
**
(CRYENGINE 3.7 and higher)
**

**
Set up to 4 custom values that get blended along with the animation, using the same transition times as the animation clips. The final blended values are exposed as
[Mannequin Parameters](Mannequin%20Concepts/Mannequin%20Parameters%20Conditions.md)
 with names 'channel0' - 'channel3'. They can be picked up by procedural clips or actions like any other mannequin parameter though there will be 1 frame of delay.

(maps to the first 4 'userdata' channels specified in CryCharAnimationParams::m_fUserData when starting the animation. The final values can also be picked up by code using ISkeletonAnim::GetUserData(index))

 |

##
Context Menu

When you right click on an animation clip you get its context menu.

![Image](https://www.cryengine.com/docs/static/attachments/23998315)

Explanation for the options specific to animation clips: (only available in CRYENGINE 3.7 or higher)

Context Menu Item

 |
Description

 |

**
Open for editing
**

 |
If file is available locally, opens the file in the editor you configured in Tools/Preferences/General Settings/File. For bspace and comb files it uses the entry "BSpace Text Editor". For animations a .ma file is opened (if present) using the specified "Animation Editor".

If the file is not available locally, the tool tries to fetch the file from P4 version control first.

 |

**
Show in explorer
**

 |
Opens up a windows explorer window pointing at the file.

 |

**
Checkout or Add to Perforce
**

 |
Tries to check this file and associated files out from P4 version control. For animation clips, tries to check out the .i_caf, .animsettings as well as a .ma file.

 |

**
Find anim clip transitions
**

 |
Opens up the transition editor and filters out this specific animation clip.

 |
