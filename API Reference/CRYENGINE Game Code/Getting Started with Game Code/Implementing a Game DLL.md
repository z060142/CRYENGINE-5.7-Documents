# Implementing a Game DLL

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306498
- Page ID: 23306498
- Breadcrumb: CRYENGINE Game Code > Getting Started with Game Code > Implementing a Game DLL
- Parent: Getting Started with Game Code

## Content

##
Dependencies

To compile the DLL, header files from both
`
Code\CryEngine\CryCommon
`
 and
`
Code\CryEngine\CryAction
`
 are required. STLport should be used if the rest of the engine is compiled using it.

##
Selecting a Game DLL

It's possible to instruct CryENGINE to load any specific Game DLL by setting the
**
sys_dll_game
**
 console variable inside system.cfg. It is not possible to switch to a different DLL during run-time.
