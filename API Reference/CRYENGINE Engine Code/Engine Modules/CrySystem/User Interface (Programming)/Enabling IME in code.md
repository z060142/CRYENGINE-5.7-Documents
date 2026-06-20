# Enabling IME in code

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23309145
- Page ID: 23309145
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > User Interface (Programming) > Enabling IME in code
- Parent: User Interface (Programming)

## Content

##
 Enabling support for IME

When building the engine from source, make sure that
`
ENABLE_GFX_IME
`
 definition is set in
`
ConfigScaleform.h

`
This will link in the Scaleform IME support library.

Scaleform IME support library is only available for Windows.

For EaaS users, the engine is shipped as pre-compiled binaries. These binaries have Scaleform IME support.

At this point, IME support is available in the binaries, but it's not necessarily active.

You can edit
`
 game.cfg
`
 for your project and set the CVar:
`
sys_ime=1
`

**
Note
**
: IME support is never available in the Sandbox, it can only be used in the game launcher.

Related information:
[/docs/static/engines/cryengine-3/categories/1638401/pages/21891645](
IME
)
