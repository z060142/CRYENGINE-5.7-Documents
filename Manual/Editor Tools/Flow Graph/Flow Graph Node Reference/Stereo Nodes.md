# Stereo Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450630
- Page ID: 29450630
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Stereo Nodes
- Parent: Flow Graph Node Reference

## Content

##
ReadStereoParameters

Used to read the HUD stereo display parameters.

[Image: /docs/static/attachments/29687997]

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
Read
**
 |
Any
 |
Start reading stereo values
 |

**
Stop
**
 |
Any
 |
Stop reading stereo values
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
EyeDistance
**
 |
Float
 |
Outputs eye distance
 |

**
ScreenDistance
**
 |
Float
 |
Outputs screen distance
 |

**
HUDDistance
**
 |
Float
 |
Outputs HUD distance
 |

**
Flipped
**
 |
Boolean
 |
Output if stereo is flipped
 |

##
StereoParameters

Used to output the HUD stereo display parameters.

[Image: /docs/static/attachments/29687996]

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
EyeDistance
**
 |
Float
 |
Sets the stereo eye distance
 |

**
ScreenDistance
**
 |
Float
 |
Sets the stereo screen distance
 |

**
HUDDistance
**
 |
Float
 |
Sets the stereo HUD distance
 |

**
Duration
**
 |
Float
 |
Duration of the interpolation in seconds
 |

**
Start
**
 |
Any
 |
Starts the interpolation
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
CurrentEyeDistance
**
 |
Float
 |
Outputs the current eye distance
 |

**
CurrentScreenDistance
**
 |
Float
 |
Outputs the current screen distance
 |

**
CurrentHUDDistance
**
 |
Float
 |
Outputs the current HUD distance
 |

**
TimeLeft
**
 |
Float
 |
Time left to the end of the interpolation
 |

**
Done
**
 |
Any
 |
Outputs when interpolation has completed
 |

[#readstereoparameters](
ReadStereoParameters
)
[#stereoparameters](
StereoParameters
)
