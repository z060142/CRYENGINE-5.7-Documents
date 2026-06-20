# ScriptBind_GameStatistics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306613
- Page ID: 23306613
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CryAction Functions > ScriptBind_GameStatistics
- Parent: CryAction Functions

## Content

##
PushGameScope

Pushes a scope on top of the stack.

```

`
GameStatistics.PushGameScope(scopeID)
`

```

Parameter
 |
Description
 |

scopeID
 |
identifier of the scope to be placed on top of the stack.
 |

##
PopGameScope

Removes the scope from the top of the stack.

```

`
GameStatistics.PopGameScope( [checkScopeId] )
`

```

Parameter
 |
Description
 |

checkScopeId
 |
(optional)
 |

##
CurrentScope

 Returns the ID of current scope, -1 if stack is empty.

```

`
GameStatistics.CurrentScope()
`

```

##
AddGameElement

 Adds a game element to specified scope.

```

`
GameStatistics.AddGameElement( scopeID, elementID, locatorID, locatorValue [, table])
`

```

##
RemoveGameElement

 Removes element from the specified scope if data parameters match.

```

`
GameStatistics.RemoveGameElement( scopeID, elementID, locatorID, locatorValue )
`

```

##
Event

```

`
GameStatistics.Event()
`

```

##
StateValue

```

`
GameStatistics.StateValue( )
`

```

##
BindTracker

```

`
GameStatistics.BindTracker( name, tracker )
`

```

##
UnbindTracker

```

`
GameStatistics.UnbindTracker( name, tracker )
`

```
