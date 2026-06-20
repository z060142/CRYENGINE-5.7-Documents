# Entity Property Prefixes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306399
- Page ID: 23306399
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryEntitySystem > Entity Property Prefixes
- Parent: CryEntitySystem

## Content

##
Overview

The editor supports typed properties where the type is derived from special prefixes in the property name. For a complete list of supported prefixes, refer to the
**
s_paramTypes
**
 array defined in
`
Objects/EntityScript.cpp
`
 in the Editor solution. This array maps prefixes to variable types.

The following is the list of prefixes supported by CryENGINE 3.0.0:

```

`
  { "n",                  IVariable::INT, IVariable::DT_SIMPLE, SCRIPTPARAM_POSITIVE },
  { "i",                  IVariable::INT, IVariable::DT_SIMPLE,0 },
  { "b",                  IVariable::BOOL, IVariable::DT_SIMPLE,0 },
  { "f",                  IVariable::FLOAT, IVariable::DT_SIMPLE,0 },
  { "s",                  IVariable::STRING, IVariable::DT_SIMPLE,0 },

  { "ei",                 IVariable::INT, IVariable::DT_UIENUM,0 },
  { "es",                 IVariable::STRING, IVariable::DT_UIENUM,0 },

  { "shader",             IVariable::STRING, IVariable::DT_SHADER,0 },
  { "clr",                IVariable::VECTOR, IVariable::DT_COLOR,0 },
  { "color",              IVariable::VECTOR, IVariable::DT_COLOR,0 },

  { "vector",             IVariable::VECTOR, IVariable::DT_SIMPLE,0 },

  { "snd",                IVariable::STRING, IVariable::DT_SOUND,0 },
  { "sound",              IVariable::STRING, IVariable::DT_SOUND,0 },
  { "dialog",             IVariable::STRING, IVariable::DT_DIALOG,0 },

  { "tex",                IVariable::STRING, IVariable::DT_TEXTURE,0 },
  { "texture",            IVariable::STRING, IVariable::DT_TEXTURE,0 },

  { "obj",                IVariable::STRING, IVariable::DT_OBJECT,0 },
  { "object",             IVariable::STRING, IVariable::DT_OBJECT,0 },

  { "file",               IVariable::STRING, IVariable::DT_FILE,0 },
  { "aibehavior",         IVariable::STRING, IVariable::DT_AI_BEHAVIOR,0 },
  { "aicharacter",        IVariable::STRING, IVariable::DT_AI_CHARACTER,0 },
  { "aipfpropertieslist", IVariable::STRING, IVariable::DT_AI_PFPROPERTIESLIST,0 },
  { "aiterritory",        IVariable::STRING, IVariable::DT_AITERRITORY,0 },
  { "aiwave",             IVariable::STRING, IVariable::DT_AIWAVE,0 },

  { "text",               IVariable::STRING, IVariable::DT_LOCAL_STRING,0 },
  { "equip",              IVariable::STRING, IVariable::DT_EQUIP,0 },
  { "reverbpreset",       IVariable::STRING, IVariable::DT_REVERBPRESET,0 },
  { "eaxpreset",          IVariable::STRING, IVariable::DT_REVERBPRESET,0 },

  { "aianchor",           IVariable::STRING, IVariable::DT_AI_ANCHOR,0 },

  { "soclass",            IVariable::STRING, IVariable::DT_SOCLASS,0 },
  { "soclasses",          IVariable::STRING, IVariable::DT_SOCLASSES,0 },
  { "sostate",            IVariable::STRING, IVariable::DT_SOSTATE,0 },
  { "sostates",           IVariable::STRING, IVariable::DT_SOSTATES,0 },
  { "sopattern",          IVariable::STRING, IVariable::DT_SOSTATEPATTERN,0 },
  { "soaction",           IVariable::STRING, IVariable::DT_SOACTION,0 },
  { "sohelper",           IVariable::STRING, IVariable::DT_SOHELPER,0 },
  { "sonavhelper",        IVariable::STRING, IVariable::DT_SONAVHELPER,0 },
  { "soanimhelper",       IVariable::STRING, IVariable::DT_SOANIMHELPER,0 },
  { "soevent",            IVariable::STRING, IVariable::DT_SOEVENT,0 },
  { "sotemplate",         IVariable::STRING, IVariable::DT_SOTEMPLATE,0 },
  { "gametoken",          IVariable::STRING, IVariable::DT_GAMETOKEN, 0 },
  { "seq_",               IVariable::STRING, IVariable::DT_SEQUENCE, 0 },
  { "mission_",           IVariable::STRING, IVariable::DT_MISSIONOBJ, 0 },

`

```
