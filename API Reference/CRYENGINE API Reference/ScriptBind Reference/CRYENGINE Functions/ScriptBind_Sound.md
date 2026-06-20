# ScriptBind_Sound

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306599
- Page ID: 23306599
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CRYENGINE Functions > ScriptBind_Sound
- Parent: CRYENGINE Functions

## Content

##
GetAudioTriggerID

 Get the trigger TAudioControlID (wrapped into a ScriptHandle).

```

`
Sound.GetAudioTriggerID(char const* const sTriggerName)
`

```

**
Returns:
**
 ScriptHandle with the TAudioControlID value, or nil if the sTriggerName is not found.
Parameter
 |
Description
 |

sTriggerName
 |
unique name of an audio trigger
 |

##
GetAudioSwitchID

 Get the switch TAudioControlID (wrapped into a ScriptHandle).

```

`
Sound.GetAudioSwitchID(char const* const sSwitchName)
`

```

**
Returns:
**
 ScriptHandle with the TAudioControlID value, or nil if the sSwitchName is not found.
Parameter
 |
Description
 |

sSwitchName
 |
unique name of an audio switch
 |

##
GetAudioSwitchStateID

 Get the SwitchState TAudioSwitchStatelID (wrapped into a ScriptHandle).

```

`
Sound.GetAudioSwitchStateID(ScriptHandle const hSwitchID, char const* const sSwitchStateName)
`

```

**
Returns:
**
 ScriptHandle with the TAudioSwitchStateID value, or nil if the sSwitchStateName is not found.
Parameter
 |
Description
 |

sSwitchStateName
 |
unique name of an audio switch state
 |

##
GetAudioRtpcID

 Get the RTPC TAudioControlID (wrapped into a ScriptHandle).

```

`
Sound.GetAudioRtpcID(char const* const sRtpcName)
`

```

**
Returns:
**
 ScriptHandle with the TAudioControlID value, or nil if the sRtpcName is not found.
Parameter
 |
Description
 |

sRtpcName
 |
unique name of an audio RTPC
 |

##
GetAudioEnvironmentID

 Get the Audio Environment TAudioEnvironmentID (wrapped into a ScriptHandle).

```

`
Sound.GetAudioEnvironmentID(char const* const sEnvironmentName)
`

```

**
Returns:
**
 ScriptHandle with the TAudioEnvironmentID value, or nil if the sEnvironmentName is not found.
Parameter
 |
Description
 |

sEnvironmentName
 |
unique name of an Audio Environment
 |

##
SetAudioRtpcValue

 Globally sets the specified audio RTPC to the specified value

```

`
Sound.SetAudioRtpcValue( hRtpcID, fValue )
`

```

**
Returns:
**
 nil
Parameter
 |
Description
 |

hRtpcID
 |
the audio RTPC ID handle
 |

fValue
 |
the RTPC value
 |
