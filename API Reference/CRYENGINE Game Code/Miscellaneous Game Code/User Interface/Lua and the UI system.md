# Lua and the UI system

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306547
- Page ID: 23306547
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > User Interface > Lua and the UI system
- Parent: User Interface

## Child Pages

- [Flash UI Lua functions](Lua%20and%20the%20UI%20system/Flash%20UI%20Lua%20functions.md)

## Content

### Overview

It is possible to control the UI System via Lua scripts. See also: [List of Lua functions](Lua%20and%20the%20UI%20system/Flash%20UI%20Lua%20functions.md).

### Example

```
// Display UI Element
UIAction.ShowElement("MyUIElement", 0);

// Call actionscript
UIAction.CallFunction("MyUIElement", 0, "Foo", "paramStr1", "paramStr2", 123, 12.3, false);

// set variable
UIAction.SetVariable("MyUIElement", 0, "MyVariable", 23);

// get variable
local var1 = UIAction.GetVariable("MyUIElement", 0, "MyVariable");
if (var1) then
Log("Var1: %d", var1);
end

// set array
local newValues = {
"val1",
"val2",
"val3",
};
UIAction.SetArray("MyUIElement", 0, "MyArray", newValues);

// get array
local values = UIAction.GetArray("MyUIElement", 0, "MyArray");
local value;
if (values) then
for i,value in ipairs(values) do
Log("Value: %s", value);
end
end
```
