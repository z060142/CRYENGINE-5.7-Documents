# C# Coding Standard

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216343
- Page ID: 26216343
- Breadcrumb: CRYENGINE Build System > Accessing CE Source Code via GitHub > Coding Guidelines > C# Coding Standard
- Parent: Coding Guidelines

## Content

##
Table of Contents

##
Code formatting

##
Uncrustify code formatter

A C# compatible Uncrustify configuration is being investigated, however at the moment no such support is available.

##
Common rules

##
Curly Brackets

Curly brackets should always be on a new line

```

`
// good!
public MyGoodBar()
{
}

// bad
public MyGoodBar {
}

// Bad
public MyGoodBar {}
`

```

##
if statements

Curly brackets are always required, even for single-expression statements.

```

`
// Good
if(a < b)
{
    DoMainThing();
}
else if(a == b)
{
    DoSomething();
}
else
{
    DoOtherStuff();
}

// Bad
if (a < b)
    DoMainThing();
else if (a == b)
    DoSomething();
else
    DoOtherStuff();
`

```

##
Naming conventions

##
General naming rules

-
Use meaningful variable and type names never use inappropriate language like
*
crap, shit
*

-
All names and comments should be in American English.

-
Avoid non common abbreviations.

-
Do not write “2” and “4” as replacement for "to" and "for".

##
Namespaces

Name of a namespace should be in PascalCase.

Always use namespaces to indicate a larger subsystem of the engine, to avoid cluttering the root CryEngine namespace.

##
Examples

-
CryEngine.EntitySystem

-
CryEngine.FlowSystem

-
CryEngine.Serialization

##
Class name

Name of a class should be in PascalCase,
**
without
**
 any prefixes.

```

`
// Good
class MyClass
{
}

// Bad
class CMyClass
{
}
`

```

##
Interface name

Name of an interface should be in PascalCase, prefixed with 'I'.

```

`
// Good
public interface IUpdateReceiver
{
}

// Bad
public interface UpdateReceiver
{
}
`

```

##
Enum names

Name of an enum should be descriptive and written in PascalCase. Enums and their values should
**
not
**
 utilize prefixes.

```

`
// Good
enum SerializedObjectType
{
    Null,
    Primitive
}

// Bad
enum ESerializedObjectType
{
    Null,
    Primitive
}

// Bad
enum SerializedObjectType
{
    eNull,
    ePrimitive
}
`

```

##
Function name

Name of a function should be in PascalCase.

Always use Properties for simple get / set functionality.

##
Field name

Name of a field should always be prefixed with
**
_
**
 and a camelCase name. Wherever public fields are required, use Properties with automatically generated backing fields.

```

`
// Good
class Test
{
  int _someValue;
  bool _active;
}

// Better
class Test
{
  int SomeValue { get; set; }
  bool Active { get; set; }
}

// Bad
class Test
{
  public int someValue;
  public int active;
}
`

```

##
Property name

Name of a property should always use PascalCase
**
without
**
 a prefix.

Whenever a property requires fields, opt for backing fields where possible.

```

`
// Good
class Test
{
  int SomeValue { get; set; }
  bool Active { get; set; }
}

// Bad
class Test
{
  int someValue { get; set; }
  bool active { get; set; }
}

// Bad
class Test
{
  int someValue;
  bool active;

  bool GetSomeValue() { return someValue; }
  bool IsActive() { return active; }
}
`

```

##
Static class members

Use class members instead of separate managers for finding and manipulating instances.

```

`
// Good (usage: var myEntity = Entity.Spawn<MyEntity>();
public partial class Entity
{
  public static T Spawn<T>() where T : Entity, new()
  {
    // return ...
  }
}

// Bad
public class EntityFramework
{
  public static T Spawn<T>() where T : Entity
  {
    // return ...
  }
}
`

```

##
Comments

Every method and property that's either public or protected must have a summary. Summaries are in XML style and always positioned on the line before the object they describe.

```

`
// Good
/// <summary>
/// Clamps the specified value between 0 and 1.
/// </summary>
/// <returns>The value clamped between 0 and 1.</returns>
/// <param name="value">Value that needs to be clamped.</param>
public static float Clamp01(float value)
{
  // return ...
}

// Bad
public CheckBoxCtrl Ctrl; ///< The UIComponent controlling this element.
`

```

##
Files

##
File naming

The source file should always have the same name as the main type that resides inside it. Split out separate classes into multiple files.

##
Class layout

-
Define members in the following order:

-
Fields

-
Properties

-
Methods

-
Static Methods

##
Code quality

##
Unsafe

Our libraries can never contain unsafe code.

##
Loops

Use the correct loop for the proper context, for example simply iterating data in a container always use
**
foreach
**
.

[Code formatting](#code-formatting)
[Uncrustify code formatter](#uncrustify-code-formatter)
[Common rules](#common-rules)
[Naming conventions](#naming-conventions)
[Files](#files)
[Code quality](#code-quality)
