# Auto-disable

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306465
- Page ID: 23306465
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Auto-disable
- Parent: CryAISystem

## Content

##
Overview

You can save CPU time by not updating distant AIs. This can be controlled on per-AI basis and globally. This feature is called "auto-disable".

##
Per-AI Auto-disable

Per-AI auto-disable is controlled by the entity property "AutoDisable". Please refer to
[AI Entities](/docs/static/engines/cryengine-3/categories/1114113/pages/1048711)
 or
[Vehicle Entities](/docs/static/engines/cryengine-3/categories/1114113/pages/1048745)
 for more details.

You can also change this property (and behavior) at run time:

##
Auto-disable in C++

```

`
pAIActorProxy->UpdateMeAlways(true);
`

```

##
Auto-disable in Lua

```

`
AI.AutoDisable(entity.id, 1);
`

```

##
Auto-disable in Flow Graph

![Image](https://www.cryengine.com/docs/static/attachments/23461221)

##
Global Auto-disable

To control auto-disable of all vehicles, please use the console variable
**
v_autoDisable
**
.

To control auto-disable of all AIs, please use the console variable
**
ai_UpdateAllAlways
**
.
