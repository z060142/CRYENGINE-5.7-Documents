# Common Lua

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306626
- Page ID: 23306626
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryScriptSystem > Lua Scripting > Common Lua Functions > Common Lua
- Parent: Common Lua Functions

## Content

### Common Globals and Functions

- File location: `Game/Scripts/common.lua`
- Loaded from: `Game/Scripts/main.lua`

### Globals

The following globals should be used to avoid temporary Lua memory allocations:

**Global Name** | **Description**
--- | ---
g_SignalData_point | Basic 3D vector value used by **g_SignalData.**
g_SignalData_point2 | Basic 3D vector value used by **g_SignalData.**
g_SignalData | Used for passing signal data in the AI behavior scripts (see: [AI.Signal](../../../CryAISystem/Signals.md)).
g_StringTemp1 | Commonly used for temporary strings inside Lua functions.
g_HitTable | Commonly used by the **Physics.RayWorldIntersection** function within the Lua scripts as the last parameter.

The **g_HitTable** content after a ** Physics.RayWorldIntersection** call:

Parameter name | Description
--- | ---
pos | 3D vector world coordinates of the ray hit.
normal | 3D normal vector of the ray hit.
dist | hit distance of the ray hit.
surface | surface type identifier of the surface that was hit.
entity | if an entity was hit, this contains the scripttable of the entity.
renderNode | contains a scripthandle to a foliage or static render node.

The **g_SignalData** table can contain the following parameter types:

Parameter type | Description
--- | ---
Vec3 | Possible 3D vector you need to pass along.
Vec3 | Possible 3D vector you need to pass along.
ScriptHandle | Normally used to pass along an entity identifier (**EnityId**).
Floating Point | Possible floating point value you need to pass along.
Integer | Possible integer or number value you need to pass along.
Integer | Possible integer or number value you need to pass along.
String | Possible string value you need to pass along.
String | Possible string value you need to pass along.

### Functions

- [#AIReload](Common%20Lua.md#CommonLua-AIReload)
- [#AIDebugToggle](Common%20Lua.md#CommonLua-AIDebugToggle)
- [#ShowTime](Common%20Lua.md#CommonLua-ShowTime)
- [#count](Common%20Lua.md#CommonLua-count)
- [#new](Common%20Lua.md#CommonLua-new)
- [#merge](Common%20Lua.md#CommonLua-merge)
- [#mergef](Common%20Lua.md#CommonLua-mergef)
- [#Vec2Str](Common%20Lua.md#CommonLua-Vec2Str)
- [#LogError](Common%20Lua.md#CommonLua-LogError)
- [#LogWarning](Common%20Lua.md#CommonLua-LogWarning)
- [#Log](Common%20Lua.md#CommonLua-Log)
- [#dump](Common%20Lua.md#CommonLua-dump)
- [#EmptyString](Common%20Lua.md#CommonLua-EmptyString)
- [#NumberToBool](Common%20Lua.md#CommonLua-NumberToBool)
- [#EntityName](Common%20Lua.md#CommonLua-EntityName)
- [#EntityNamed](Common%20Lua.md#CommonLua-EntityNamed)
- [#SafeTableGet](Common%20Lua.md#CommonLua-SafeTableGet)

#### AIReload()

Reloads the **aiconfig.lua** Lua script (* Game/Scripts/AI/*).

#### AIDebugToggle()

Toggles the [ai_DebugDraw](/docs/static/engines/cryengine-3/categories/9895942/pages/9215946) console variable on and off.

#### ShowTime()

Logs the current system time to console. Formatting is like the following: ***Day/Month/Year, Hours:Minutes***

#### count(_tbl)

Returns the amount of key-value pairs of a given table.

**Parameters** | **Description**
--- | ---
_tbl | table to get the amount of key-value pairs from.

#### new(_obj, norecurse)

Creates a new table based on the given one in the parameter **_obj**. Commonly used for creating a local table based on an entity parameter table.

**Parameters** | **Description**
--- | ---
_obj | base table you want to create a new one from.
norecurse | if set to **true** it avoids recursive recreation of all sub-tables.

#### merge(dst, src, recurse)

Used to partly merge 2 tables without merging the functions from the source table.

**Parameters** | **Description**
--- | ---
dst | destination table to merge to.
src | source table to get the table information from.
recurse | recursive merging of all sub-tables.

#### mergef(dst, src, recursive)

Used to completly merge 2 tables with all functions of the source table.

**Parameters** | **Description**
--- | ---
dst | destination table to merge to
src | source table to get the table information from
recursive | recursive merging of all subtables

#### Vec2Str(vec)

Used to convert a 3D vector table into a string and returns it as follows: **(x: X.XXX y: Y.YYY z: Z.ZZZ)**

**Parameter** | **Description**
--- | ---
vec | vector table e.g: ``` {x=1,y=1,z=1} ```

#### LogError(fmt,...)

Used to log an error message to the console and the log file. The text color is set to red in the console.

**Parameters** | **Description**
--- | ---
fmt | formatted string message
... | possible argument list e.g: ``` LogWarning("MyError: %f", math.pi); ```

#### LogWarning(fmt,...)

Used to log a warning message to the console and the log file. The text color is set to yellow in the console.

**Parameters** | **Description**
--- | ---
fmt | formatted string message
... | possible argument list e.g: ``` LogWarning("MyWarning: %f", math.pi); ```

#### Log(fmt,...)

Used to log a message to the console and the log file. Commonly used for debugging purposes.

**Parameters** | **Description**
--- | ---
fmt | formatted string message
... | possible argument list e.g: ``` Log("MyLog: %f", math.pi); ```

#### dump(_class, no_func, depth)

Dumps the table information to console.

**Parameters** | **Description**
--- | ---
_class | table you want to dump to console (e.g: **g_localActor**)
no_func | if set to **true** it won't dump the table functions
depth | defines the table tree depth you are interested in

#### EmptyString(str)

Checks whether a given string is set and it's length is greater than zero and returns true if so.

**Parameter** | **Description**
--- | ---
str | string to check if it is an empty string

#### NumberToBool(n)

Checks whether a number value is **true** or ** false**. In this case ** true** means the number is not equal to 0.

**Parameter** | **Description**
--- | ---
n | number to check

#### EntityName(entity)

Returns the name of the given entity table or the entity identifier or an empty string if the entity doesn't exist.

**Parameter** | **Description**
--- | ---
entity | entity table or entity identifier (**EntityId**)

#### EntityNamed(name)

Returns true if an entity with the given name exists in the entity system. Commonly used for debugging.

**Parameter** | **Description**
--- | ---
name | name of the entity to check

#### SafeTableGet(table, name)

Checks if a subtable with a given name exists in the given table and returns it, otherwise it returns **nil**.

**Parameters** | **Description**
--- | ---
table | base table to check for the subtable
name | name of the subtable
