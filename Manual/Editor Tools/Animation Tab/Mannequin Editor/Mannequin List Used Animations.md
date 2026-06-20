# Mannequin List Used Animations

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308460
- Page ID: 23308460
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin List Used Animations
- Parent: Mannequin Editor

## Content

##
Overview

This functionality exports a list of used animations to a text file you can subsequently open as a spreadsheet. This includes used blendspaces (bspace, comb) and the animations referred by those.

![Image](https://www.cryengine.com/docs/static/attachments/23998340)

You can find it in the Tools menu in the Mannequin Editor.

-
**
List Used Animations...
**
:
The tool lists animations used by any preview file it can find in Animations/Mannequin/Preview. (it opens all files ending in XML that it can find in that folder or its sub-folders)

-
**
List Used Animations (Current Preview)...
**
: The tool lists animations used by the currently opened preview file.

##
Example when Using Microsoft Excel 2007

After you exported the file, you can simply open it (a CSV file) in Excel by double clicking on it.

Which results in a table looking like this:

![Image](https://www.cryengine.com/docs/static/attachments/23998341)

##
Exported Data

Each line in the exported file is a specific reference to an animation from mannequin. As there are many ways through which mannequin can refer to a certain file, there will be typically many lines referring to the same animation file.

Here is a description of the columns:

Column
 |
Description
 |
Example
 |

**
Animation Name
**
 |
Short name of the animation, also called the 'alias'. This is the name the game uses to refer to animations.

It is derived from the animation's file name using the rules set up in the CHRPARAMS file.
 |
NPC_Alligator_Idle
 |

**
Blend-space
**
 |
The blend-space name that refers to this animation (if any)
 |

 |

**
Animation Path
**
 |
The path of the animation, relative to the game data folder.
 |
animations/npc_alligator/npc_alligator_idle.caf
 |

**
Skeleton Path
**
 |
Path to the skeleton (aka model) which was used to find the animation paths.
 |
objects/characters/npc_alligator/npc_alligator.chr
 |

**
Animation Events Path
**
 |
Path to the animation events (found within the CHRPARAMS assigned to the skeleton)
 |
Objects/characters/NPC_Alligator/NPC_Alligator_animevents.animevents
 |

**
Animation Database Path
**
 |
Path to the mannequin animation database (ADB) containing the fragment.
 |
Animations/Mannequin/ADB/AlligatorAnims_Creature.adb
 |

**
Fragment Name
**
 |
FragmentID assigned to the fragment.

(when this animation is part of a transition, this is the source FragmentID of the transition)
 |
Idle
 |

**
Fragment TagState
**
 |
Tags assigned to the fragment.
 |
Relaxed+Small
 |

**
Destination Fragment Name
**
 |
When this animation is part of a transition, this shows the destination FragmentID of the transition.

Otherwise blank.
 |
Slide
 |

**
Destination Fragment Tagstate
**
 |
When this animation is part of a transition, this shows the destination tags of the transition.

Otherwise blank.
 |
Alerted
 |

**
Option Index
**
 |
Option index of the fragment.
 |
0
 |

**
Preview File Path
**
 |
Path of the preview file which containing the skeleton and animation database path.
 |
Animations/Mannequin/Preview/alligator.xml
 |

To explain why there can be many references to the same file through different paths, this is a simplified diagram showing how mannequin refers to files:

![Image](https://www.cryengine.com/docs/static/attachments/23998342)

Some examples:

-
The same animation (I_CAF) can be referred to with different animation names.

-
The same animation can be referred to from within multiple blend-spaces.

-
One fragment can contain the same animation more than once in different clips.

-
An ADB file can contain many fragments or transitions referring to the same animation.

-
There can be many skeletons referred to from within one Preview File. For example an interactive door might refer to the player's skeleton and animations for preview purposes.
