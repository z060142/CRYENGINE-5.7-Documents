# Using Console Variables

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26875243
- Page ID: 26875243
- Breadcrumb: CRYENGINE Code Tutorials > C# Programming > Using Console Variables
- Parent: C# Programming

## Content

## Creating Console Variables

Console variables can be declared in C# by using Properties and Attributes. Currently, there are four types of attributes (with corresponding properties) that can be declared.

The attribute and property types are listed in the table below:

Attribute Type | Property Type | Description
--- | --- | ---
*ConsoleVariableFloatAttribute* | *ConsoleVariableAttributeFloatProperty* | Floating point type
*ConsoleVariableIntegerAttribute* | *ConsoleVariableAttributeIntegerProperty* | 32-bit integer type
*ConsoleVariableInteger64Attribute* | *ConsoleVariableAttributeInteger64Property* | 64-bit integer type
*ConsoleVariableStringAttribute* | *ConsoleVariableAttributeStringProperty* | String type

There are two methods to create console variables in C#:

- Applying C# attributes.
- Manual initialization and deinitialization.

### Applying C# Attributes

Note that each console variable property must be matched with the correct attribute, and then initialized.

For example,

```
[ConsoleVariableString("aStringProperty", "Hello World", (uint)EVarFlags.VF_DEV_ONLY, "aStringProperty Test")]
public static ConsoleVariableAttributeStringProperty aStringProperty = new ConsoleVariableAttributeStringProperty();
```

A string console variable named *aStringProperty* is declared and initialized. If the console variable changes value in native C++ code, * aStringProperty* will also be modified and vice versa. Also note, that both **ConsoleVariableString** and ** ConsoleVariableAttributeStringProperty** must be the same.

Only a static property can be declared as a Console Variable with attributes.

You should be able to see the following option in the Sandbox Editor if the creation is successful ("Help->"Console Variables").

![Image](https://www.cryengine.com/docs/static/attachments/26956642)

### Manual Initialization and Deinitialization

Console variables can also be created in code:

```
public class MyConsoleVariables
{
public ConsoleVariableAttributeIntegerProperty testInt;

public MyConsoleVariables()
{
testInt = ConsoleVariableAttributeManager.CreateConsoleVariableIntegerProperty("an_int", int.MaxValue, "This is dynamic", (uint)EVarFlags.VF_CHEAT);
}
public void clearResources()
{
testInt.Dispose();
testInt = null;
}
}
```

In the sample code above, a non-static integer console variable is declared and initialized in a class. When no longer used, the console variable is disposed of and released.

All Console variable properties implement IDisposable and should be disposed of when not in use.

### Error Handling

A **ConsoleCommandConfigurationException** will be thrown if there are any misconfigurations.

There are two types of configuration error:

- Uninitialized static Console Variable property.
- Mismatch between Console Variable attribute and property.

#### Uninitialized Static Console Variable Property

```
[ConsoleVariableString("aStringProperty", "Hello World", (uint)EVarFlags.VF_DEV_ONLY, "This is null")]
public static ConsoleVariableAttributeStringProperty aStringProperty ; // this is null
```

In the above, the aStringProperty is null and uninitialized.

#### Mismatch Between Console Variable Attribute and Property

```
[ConsoleVariableString("aStringProperty", testStringPropertyWronglyValue, (uint)EVarFlags.VF_DEV_ONLY, "String attribute mismatched with float property")]
public static ConsoleVariableAttributeFloatProperty aWrongProperty = new ConsoleVariableAttributeFloatProperty();
```

In the above **ConsoleVariableString** attribute (string type) is used with the wrong property ** ConsoleVariableAttributeFloatProperty** (floating point type).
