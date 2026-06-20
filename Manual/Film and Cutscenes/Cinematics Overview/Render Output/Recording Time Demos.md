# Recording Time Demos

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535455
- Page ID: 25535455
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Render Output > Recording Time Demos
- Parent: Render Output

## Content

##
Overview

This records player input/camera movement and plays it back. Some player actions such as vehicle movement are not supported.

You need to start and record in game mode (Press
**
Ctrl + G
**
 in the Editor after the level has been fully loaded, or load the level in Pure Game Mode.

After each playback you get a log printout that looks like the following (in the console and also in the file timedemo.log in the level directory for the level used):

```

`
TimeDemo Run 131 Finished.
Play Time: 3.96s, Average FPS: 50.48
Min FPS: 0.63 at frame 117, Max FPS: 69.84 at frame 189
Average Tri/Sec: 14037316, Tri/Frame: 278071
Recorded/Played Tris ratio: 0.99
`

```

##
Recording Controls

**
Command
**

 |
**
Keystroke
**

 |
**
Console Commands
**

 |

**
Start Recording
**

 |
Ctrl + PrintScreen

 |
record

 |

**
End Recording
**

 |
Ctrl + Break

 |
stoprecording

 |

**
Start Playback
**

 |
Shift + PrintScreen

 |
demo

 |

**
Stop Playback
**

 |
Ctrl + Break

 |
stopdemo

 |

##
Related Console Variables

-
**
stopdemo:
**
 Stop playing a time demo.

-
**
demo:
**
 Plays a time demo from file (Usage: demo demoname).

-
**
demo_fixed_timestep
**
: Number of updates per second.

-
**
demo_panormaic:
**
 Panormaic view when playing back demo.

-
**
demo_restart_level:
**
 Restart level after each loop: 0 = Off; 1 = use quicksave on first playback; 2 = load level start.

-
**
demo_ai
**
: Enable/Disable AI during the demo.

-
**
demo_savestats:
**
 Save level stats at the end of the loop.

-
**
demo_max_frames:
**
 Max number of frames to save.

-
**
demo_screenshot_frame:
**
 Make screenshot on specified frame during demo playback, If Negative, takes a screenshot every N frame.

-
**
demo_quit
**
: Quit game after demo runs finished.

-
**
demo_continue
**
: Continue game after demo runs finished.

-
**
demo_noinfo:
**
 Disable info display during demo playback.

-
**
demo_scroll_pause:
**
 ScrollLock pauses demo play/record.

-
**
demo_num_runs:
**
 Number of times to loop timedemo.

-
**
demo_profile
**
: Enable demo profiling.

-
**
demo_time:
**
 Time demo filename.
[Recording Controls](#recording-controls)
[Related Console Variables](#related-console-variables)
