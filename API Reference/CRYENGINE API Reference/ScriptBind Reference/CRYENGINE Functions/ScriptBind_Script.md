# ScriptBind_Script

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306604
- Page ID: 23306604
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CRYENGINE Functions > ScriptBind_Script
- Parent: CRYENGINE Functions

## Content

##
LoadScript

 Loads the script.

```

`
Script.LoadScript(scriptName)
`

```

Parameter
 |
Description
 |

scriptName
 |
name of the script to load
 |

##
ReloadScripts

 Reloads all the scripts.

```

`
Script.ReloadScripts()
`

```

##
ReloadScript

 Reload the script.

```

`
Script.ReloadScript()
`

```

##
ReloadEntityScript

Reloads the specified entity script.

```

`
Script.ReloadEntityScript( className )
`

```

Parameter
 |
Description
 |

className
 |
Name of the entity script.
 |

##
UnloadScript

 Unloads the script.

```

`
Script.UnloadScript()
`

```

##
DumpLoadedScripts

 Dumps all the loaded scripts.

```

`
Script.DumpLoadedScripts()
`

```

##
SetTimer

  Set a general script timer, when timer expires will call back a specified lua function. Lua function will accept 1 or 2 parameters, if userData is specified luaFunction must be: <preformatted>LuaCallback = function( userData,nTimerId )
        -- function body
     end;</preformatted> if userData is not specified luaFunction must be: <preformatted>LuaCallback = function( nTimerId )
        -- function body
     end;</preformatted>

```

`
Script.SetTimer( nMilliseconds, luaFunction [, userData [, bUpdateDuringPause]] )
`

```

**
Returns:
**
 ID assigned to this timer or nil if not specified.
Parameter
 |
Description
 |

nMilliseconds
 |
Delay of trigger in milliseconds.
 |

luaFunction
 |
.
 |

userData
 |
(optional) Any user defined table. If specified will be passed as a first argument of the callback function.
 |

bUpdateDuringPause
 |
(optional) will be updated and trigger even if in pause mode.
 |

##
SetTimerForFunction

  Set a general script timer, when timer expires will call back a specified lua function. Lua function will accept 1 or 2 parameters, if userData is specified luaFunction must be: <preformatted>LuaCallback = function( userData,nTimerId )
            -- function body
      end;</preformatted> if userData is not specified luaFunction must be: <preformatted>LuaCallback = function( nTimerId )
            -- function body
      end;</preformatted> .

```

`
Script.SetTimerForFunction( nMilliseconds, luaFunction [, userData [, bUpdateDuringPause]] )
`

```

**
Returns:
**
 ID assigned to this timer or nil if not specified.
Parameter
 |
Description
 |

nMilliseconds
 |
Delay of trigger in milliseconds.
 |

luaFunction
 |
.
 |

userData
 |
(optional) Any user defined table. If specified it will be passed as a first argument of the callback function.
 |

bUpdateDuringPause
 |
(optional) will be updated and trigger even if in pause mode.
 |

##
KillTimer

 Stops a timer set by the Script.SetTimer function.

```

`
Script.KillTimer( nTimerId )
`

```

Parameter
 |
Description
 |

nTimerId
 |
ID of the timer returned by the Script.SetTimer function.
 |
