# Video Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450648
- Page ID: 29450648
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Video Nodes
- Parent: Flow Graph Node Reference

## Content

##
Video:ClipCapture

Used to capture video clips while a game is running and save them locally or to the cloud.

[Image: /docs/static/attachments/29688102]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Capture
**
 |
Any
 |
Begins capturing a video clip
 |

**
DurationBefore
**
 |
Float
 |
Records the specified number of seconds before the
**
Capture
**
 input triggers
 |

**
DurationAfter
**
 |
Float
 |
Records the specified number of seconds after the
**
Capture
**
 input triggers
 |

**
ClipName
**
 |
String
 |
Usage details are specific to the operating system
 |

**
LocalizedClipName
**
 |
String
 |
Usage details are specific to the operating system
 |

**
Metadata
**
 |
String
 |
(Optional) Tags video clips
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
BeganCapture
**
 |
Any
 |
Triggers when video clip capturing begins
 |

**
Error
**
 |
Any
 |
Triggers when a clip capture error occurs
 |

##
Video:VideoPlayback

Video player node that is using USMPlayer UIElement.

[Image: /docs/static/attachments/29688101]

[#videoclipcapture](
Video:ClipCapture
)
[#videovideoplayback](
Video:VideoPlayback
)
