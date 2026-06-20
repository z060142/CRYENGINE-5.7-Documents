# C++ Coding Standard

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/25530454
- Page ID: 25530454
- Breadcrumb: CRYENGINE Build System > Accessing CE Source Code via GitHub > Coding Guidelines > C++ Coding Standard
- Parent: Coding Guidelines

## Content

With CRYENGINE 5.1.0, we have deprecated the support for Visual Studio 2012 and 2013. For more information, please check [Visual Studio Supported Versions](../../Visual%20Studio%20Supported%20Versions.md). This has implications on the language features that can be used in the code-base.

## Coding standard

This document outlines the most important coding standards that are applicable to CRYENGINE. Its main purpose is to achieve overall code consistency and software structural quality. It is a helper for improving code readability and easing maintenance. Programmers are expected to follow this standard while writing code for CRYENGINE.

There may be few exceptions to deviate from the coding standard, since we cannot predict every scenario or situation that may occur in the future. The majority of code should follow these rules, so that we can have a clearer and maintainable code base. These rules apply to CRYENGINE, Sandbox and plug-in/extensions thereof. (All the code can be found under Code/CryEngine, Code/Sandbox and Code/CryExtensions)

When you intend to deviate from the guidelines, you should mention this in the code review so that:

- Reviewer spends less time marking them.
- You can immediately state the reason for the deviation to avoid any confusion.

### Disabled C++ features

The CRYENGINE codebase is written in C++. The use of C language is discouraged, but may be appropriate for interactions with 3rd party C libraries, at your discretion. These features are disabled at the compiler level for all CRYENGINE modules, and cannot be used:

- Exceptions
- Run-time type information (RTTI)
- `dynamic_cast` operator

Some plugins or extensions may (at their discretion) enable one or more of these features. However, it is then the responsibility of those plug-in or extension to ensure that no exceptions can propagate into the CRYENGINE modules, as this may cause undefined behavior. RTTI must be assumed to be incompatible across modules (use it only with types from the containing module).

### Uncrustify code formatting tool

We recommend using our customized Uncrustify code formatting tool to format the code according to the rules described in this document.

It can be found in *<root>/Code/Tools/uncrustify*, along with a config file (CryEngine_uncrustify.cfg).

Note that any deviation from the guidelines introduced by the tool that cannot be formatted is acceptable. Unfortunately, no tool is 100% accurate, however if there is a systematic issue please inform the tool maintainer so that they can try to fix it.

##### Common rules:

- Curly brackets should not be in the same line with other text (allowed exclusions are short single-liners in header files: constructors/destructors and get/set-like functions)
- Opening and closing curly brackets should be on the same column (allowed exclusions are '{}' in header files and single-liners mentioned above)
- When changing code in another module, mimic the style which is already present in the module
- Use one statement on each code line which:
- helps setting debugger breakpoints
- simplifies reading
- simplifies code merging
- allows to add an end-of-line comment easily when required

A sample code block is outlined below:

```
// good
CMyGoodBar()
: m_memberA(0)
, m_memberB(0)
{
}

// acceptable (exclusion)
CMyGoodBar()
: m_memberA(0)
, m_memberB(0)
{}

// acceptable (exclusion)
CMyGoodBar() : m_memberA(0), m_memberB(0) {}

// bad
CMyGoodBar()
: m_memberA(0)
, m_memberB(0) {
}

// bad
CMyGoodBar()
: m_memberA(0)
, m_memberB(0) {}

// bad
CMyGoodBar() : m_memberA(0), m_memberB(0)
{}

// bad
CMyGoodBar() : m_memberA(0), m_memberB(0)
{
}
```

### Tabs and spaces

Format of every non-empty line of code should be:

```
[<tabs>]text[<spaces>]text[<spaces>]...
```

The following formatting options are not allowed:

- Space characters in the beginning of a row
- Tab characters in the right part of a row

Recommended tab size is 2, although any setting can be used if the above rule is followed, and code should look good regardless.

By setting the tab size to 2, the formatting tool will attempt to create a fixed block (spaces only) out of certain contexts, such as multi-line macro's, in an attempt to maintain right-alignment for the escape-newline sequence. However, more than 99% of the code should not be fixed-block since there is no right-alignment option that can be performed.

**Note**: Don't use ** Convert tabs to spaces** or similar options in your editor. Use Tab character to insert tabs in the code.

If you follow this rule, then you can use any tab size without destroying existing format. Note that some old code still uses space characters instead of tabs and assumes that indentation is 2 to view such code properly, you can use Visual Studio's macros to switch between tabs size 2 and 4.

Do not use space characters or multiple tabs to align expressions after wrapping lines. Preferably, let the formatting tool do this for you. Alternatively, you should use exactly one tab for indentation of wrapped lines if the tool cannot be used.

### Spaces in expressions

Please ensure the below mentioned conditions are met:

- No space between function’s name and parentheses"**(**"
- No space before comma, semicolon, and parentheses
- Single space character before open and close brackets except while using double parentheses "**))**", and also after a comma
- Single space character before and after binary arithmetic operators (+, -, *, /, *, /, %, &, &&, |, ||, |=, ==, +=, etc.) and before unary operators (-,!, ~, etc.)
- Single space character before and after '**?**' and '**:**' in the conditional operator
- No spaces around **<** and **>** in template argument lists (see example below)
- Single space character between statement (if, while, for, switch, etc.) and the opening '**(**'

```
if (a > b * c * (e - f))
{
Grid<Sensor<float, double>> grid;
const float r = ((a * 15.4f) / 3) + 2 + d * 4;
DoSomething(&grid, a, c, e * f);
...
}
```

### Long and complex expressions

The below mentioned conditions should be followed while using long and complex expression in the code:

- Do not add multiple expressions, parameters or variables on the same line as it complicates both reading and code merging. It's always recommended to use a separate line for different expressions. Exceptions are possible.
- Do not use very complex expressions, especially as part of control statements. This may cause confusion for the user while decrypting the logic. Split complex expressions into multiple parts and use temporary const variables. It will make the code more readable and easier to debug.
- Use parentheses/brackets to improve readability of complex logical and arithmetical expressions. Understanding a complex braceless expression requires more time than understanding an expression with braces.

```
// good
int a = 3;
int b = 5;
// bad
int a = 3, b = 5;
```

Even though an expression is well-formed and non-ambiguous according to the C++ operator precedence rules, compilers will typically warn about omitted parentheses in certain expressions, even though they don't change the meaning of the expression. Therefore, prefer to introduce parentheses to clarify intentions when operators are "competing" inside one sub-expression:

- Two logical operators: `a && b || c` clarify to`(a && b) || c`
- Two bitwise operators:`a | b & c` clarify to`a | (b & c)`
- A shift and a compare`: a >> b > c clarify to``(a >> b) > c`
- Any non-top-level assignment expression: `if (a = b * c)` clarify to`if ((a = b * c))`

### Wrapping

The formatting tool will maintain alignment for wrapped lines (By using spaces, it looks identical regardless of tab-space). This guideline can still be used for code where the code formatting tool cannot be used, but is generally obsolete since the code-base was reformatted.

Use single tab indentation for wrapped lines. Do not align with ‘**(**‘, such alignment is hard to maintain in case of renaming functions and also sometimes it just looks like hanging in the middle of a page. If you think that the code looks bad after wrapping then use temporary variables to decrease sizes of the expressions.

```
// good
DoSomethingImportant(
plumCount, “Alabama”, name, age, mass, validationPassed);

// good
DoSomethingImportant(plumCount, “Alabama”,
name, age, mass, validationPassed);

// bad
DoSomethingImportant(plumCount, “Alabama”,
name, age, mass, validationPassed);
```

### Long function parameter lists

Avoid long function parameter lists. Use separate line for each parameter, with single tab indentation. It improves readability and helps in code merging.

```
// good
void DoSomething(
int someNumber,
const char* someName,
const char* someText,
int peachCount)
{
...
}

// bad - 'int someNumber' should be moved to the second row
void DoSomething(int someNumber,
const char* someName,
const char* someText,
int peachCount)
{
...
}

// bad - uses multiple tabs/spaces for aligning. should use single tab instead.
void DoSomething(int someNumber,
const char* someName,
const char* someText,
int peachCount)
{
...
}
```

### if statement

Curly braces are required even for single-expression statements. See also “**Common rules**”, under ** Uncrustify code formatting tool**section above.

As an exception, you may write one-liners if you have at least two similarly looking statements and if it really enhances readability (not recommended). You may do it only when the lines contain single expressions and there is no 'else' function.

Do not use curly braces in one-liners.

In general, do not use assignment operator ‘**=**’ within "** if**"statement. It may be acceptable when you are declaring a new pointer (-like) variable where the scope is the conditional statements, and the "** if**" statement is part of some larger "expected path" which would otherwise grow significantly vertically.

```
// good
if (a < b)
{
DoMainThing();
}
else if (a == b)
{
DoSomething();
}
else
{
DoOtherStuff();
}

// bad - curly braces should be on separate lines
if (a < b)
{
DoMainThing();
} else if (a == b)
{
DoSomething();
} else
{
DoOtherStuff();
}

// acceptable
if (x == 5) sum *= 2;
if (x == 6) sum /= 2;

// bad - curly braces should be on separate lines and vertically aligned:
if (x == 5) { sum *= 2; }
if (x == 6) { sum /= 2; }

// bad - uses assignment inside of 'if' statement
if ((imageCount = GetImageCount()) > 5)
{
...
}

// acceptable
if (SFoo* pFoo = TryGetFoo())
{
...
}
```

### for statement

Curly braces are required even for single-expression statement. See also “**Common rules**”, under ** Uncrustify code formatting tool**section above. For incrementing loop variables use pre-increment.

```
// good
for (int i = 0; i < 10; ++i)
{
DoIt(i);
}

// bad - missing { }
for (int i = 0; i < 10; ++i) DoIt(i);

// bad - bad placement of { }
for (int i = 0; i < 10; ++i) { DoIt(i); }
```

### Infinite loops

A sample example of Infinite loops is outlined below:

```
// good
for (;;)
{
...
}

// good
while (true)
{
...
}
```

### switch statement

Make sure you add a single space between **switch** and**(** character. In the below example, **case** and ** default** labels are in same column with bracket **{**. Make sure you have added ** default** and ** break** functions. If you want to continue execution instead, use the following comment “*// falls through*”. Nested curly braces are only allowed when defining local variables, see **case 2** in the example below.

```
switch (x)
{
case 0:
HandleZero();
break;
case 1:
ReportSingle();
// falls through
case 2:
{
const int result = HandleSmallNumber(x);
Report(result);
}
break;
case 3:
case 4:
break;
default:
if (x < 0)
{
return -1;
}
HandleBigNumber(x);
break;
}
```

### Conditional operator (ternary)

A sample example of conditional operator is outlined below:

```
// good
const int count = isHungry ? 2 : 1;

// good
const int count =
isVeryHungry
? EatMeatballs(personName, meatType)
: EatCookies(personName, isSugarFree);

// bad grouping
const int count = isVeryHungry
? EatMeatballs(personName, meatType)
: EatCookies(personName, isSugarFree);

// bad grouping
const int count = isVeryHungry ? EatMeatballs(personName, meatType)
: EatCookies(personName, isSugarFree);

// bad grouping
const int count =
isVeryHungry ? EatMeatballs(personName, meatType)
: EatCookies(personName, isSugarFree);

// bad alignment/wrapping, must use single tab
const int count = isHungry ? EatMeatballs(personName, meatType)
: EatCookies(personName, isSugarFree);
```

### Constructor initialization lists

Order of elements in a constructor initialization list should match order of declarations in class/struct.

From C++11, initialization for nonstatic members can be used instead. When you mix both the styles, try to group the class-initialized members separately from the constructor which is initialized in the class declaration.

```
// implementation in cpp
Taxi::Taxi(float maxSpeed)
: m_passengerCount(4)
, m_maxSpeed(maxSpeed)
, m_mass(1200.0f)
{
...
}

// good for header
class LineEdit
: public Widget
{
public:
LineEdit(Widget* parent) : Widget(parent) {}  // ok for header
LineEdit(Widget* parent, int advance, int curvature)
: Widget(parent)
, m_advance(advance)
, m_curvature(curvature)
{
}
virtual ~LineEdit() {}         // ok for header
virtual ~LineEdit() = default; // preferred
};
```

### Formatting rules for composite types

'*****' (pointer) and '**&**' (reference) should be added to the type without any space and should be separated with a single space on the right side. It separates name from type and also doesn’t look like an operator. It also simplifies text search for pointers or references in a type. The ** const** keyword can be placed to the right or left of the type. However, it's technically more correct to place the ** const** keyword to the right of types as compilers always evaluate the ** const** keyword to the left first. That additionally ensures a more consistent code formatting. For example pointers and methods cannot be "consted" by placing the ** const** keyword to the left of the object. As this is quite a sensible and subjective topic as personal preference is heavily involved where to place the ** const** keyword is left to the programmer. As always keep in mind that you're working on corporate code and that a consistent look and feel are the main goals to achieve here.

```
// accepted
void DoIt(
const int& a,
const char* b,
char* const c,
const char* const d,
const int f);

// accepted
void DoIt(
int const& a,
char const* b,
char* const c,
char const* const d,
int const f);

// in these cases consider using typedefs or using directive!
const int* const* const var = &a;
int const* const* const __restrict var = &a;
```

### Namespaces

Although it is preferable to leave comments on closing braces, doing so is optional. If you do decide to comment on closing braces, they should be done as follows:

```
namespace Cry
{
} // namespace Cry
```

- In the case of the above example, the comment /`/ namespace Cry` for the closing brace would be the appropriate format and not `//~Cry namespace` as may be seen in other files.
- The name of a namespace should be in PascalCase.

In nested scenarios, the C++17 style must be used. Ideally only one namespace of the same name and level should exist per file (header or source), and comments for closing braces should be made as shown in the following example:

```
namespace Cry::Math
{
} // namespace Cry::Math

namespace Cry
{
struct MyStruct;
namespace Math
{
} // namespace Math
} // namespace Cry
```

The following code block shows a second namespace of the same name being opened on the same level, which should be avoided:

```
namespace Cry
{
level 1
namespace Math
{
level 2
} // namespace Math
} // namespace Cry

namespace Cry // A second namespace with the name "Cry" being opened on the same level as the previous. Please avoid.
{
level 1
namespace Renderer
{
level 2
} // namespace Renderer
} // namespace Cry
```

It is recommended to move the `Renderer` namespace in the above code example into the already existing` Cry`namespace so that the example looks like this:

```
namespace Cry
{
namespace Math
{
} // namespace Math
namespace Renderer
{
} // namespace Renderer
} // namespace Cry
```

- Keep the number of nested namespaces reasonable and avoid going overboard needlessly.
- When creating some utility class that the user is not expected to use themselves, choose to put those classes into a helper namespace (the typical name is `Detail`). However, it is not allowed to import namespaces or names into the global namespace with ` using`.
- It is not allowed to inject types into the `std` namespace

## Naming conventions

### General naming rules

The naming conventions should follow the below mentioned rules:

- Use meaningful variable and type names. Never use inappropriate language such as *crap, shit.*
- Use common one-letter counter variables in loops (I, j, k, l, m, n).
- All names and comments should be in American English.
- Avoid uncommon abbreviations, or short form such as 2 and 4 as replacement for "to" and "for".
- Apply capitalization rule for abbreviations in names such as crc (not CRC), myCrc (not myCRC), or m_crc (not m_CRC).
- The more visible a variable or function is (the larger scope it has), the more descriptive its name needs to be since less information is provided in the context.

### Class name

Name of a class should be in PascalCase, prefixed with '**C**'.

```
class CSomeClass
```

### Struct name

Name of a struct should be in PascalCase, prefixed with '**S**'.

All data members of a struct must be public.

```
struct SSomeStruct;
```

### Interface name

Interfaces are **struct** (it allows to avoid writing ‘* public:*’). Name of an interface should be in PascalCase, prefixed with '**I**'.

```
struct ISomeInterface;
```

### Custom type name (typedef, using)

Name of a custom type (created by using `typedef`) should be in PascalCase, and it should not be prefixed. It is also acceptable to use a character T as a prefix to indicate a name that refers to a type (this may be valuable when mixing type and non-type template parameters). The same naming convention applies for ` using` a type alias with a declaration.

```
// good
typedef std::list<CSomeClass*> SomeClassList;

// acceptable
typedef std::vector<SFoo> TFooVector;

// good
template<typename T>
using MyCustomAllocatorVector = std::vector<T, MyAllocator>;
```

### Primitive types

*Code/CryEngine/CryCommon/CryCore/BaseTypes.h* contains sized primitive types which can be used for better portability of your code.

Using non-sized types (`short int, unsigned int, long` etc) are not recommended.

No custom defined primitive types are allowed (`uchar, schar, ushort, sshort, uint, sint, ulong`, etc.).

The following list contains the list of approved types:

- `uint8` (8-bit unsigned integer)
- `int8` (8-bit signed integer)
- `uint16` (16-bit unsigned integer)
- `int16` (16-bit signed integer)
- `uint32` (32-bit unsigned integer)
- `int32` (32-bit signed integer)
- `uint64` (64-bit unsigned integer)
- `int64` (64-bit signed integer)
- `intptr_t, uintptr_t`
- `size_t`

### Enum names

Name of an enum should be descriptive, and must be written in PascalCase, prefixed with '**E**'.

- Plain enums: Every enumerant name should have a prefix 'e', then the complete name of the enum (without 'E' prefix), then the underscore character, and then the PascalCase descriptive name of the enumerant. The prefix 'k' is also acceptable, especially when the intent of the enum is to introduce compile-time values.
- Enum classes: Every enumerant name should be PascalCase and descriptive.

If enum values are supposed to be used as indices in an array, then you should write a comment about it.

```
// good plain enum
enum ECarType
{
eCarType_Fast,
eCarType_SuperFast,
eCarType_Slow
};

// good enum class
enum class ECarType
{
Fast,
SuperFast,
Slow
};

// bad plain enum - enumerants should use 'eCarType_' prefix instead of 'eCT_'
enum ECarType
{
eCT_Fast,
eCT_SuperFast,
eCT_Slow
};
```

### Template name

Templates should follow the same naming rules as non templates.

```
CSomeTemplateClass<T>
SSomeTemplateStruct<T>
```

### Function name

Name of a function should be in PascalCase.

Any function usually performs an action, so name of any function should be started with a verb. Exceptions: some well-known names for container classes, like length(), size(), etc., although even in those cases it’s better to use GetLength(), GetSize().

Avoid using nouns in names of “**set**” functions with Boolean arguments. Use adjectives instead. The ** get** member functions should not modify object’s state, so they should be declared ‘** const**’.

Purpose of a function should be obvious from its name. If it’s not the case, then the function should be renamed. If the function performs multiple actions, it cannot be described in a name then the function should be split to few functions. If it cannot be split, then it should have a comment describing its purpose.

`void` ` ComputeIncome();` `// good` ` float` ` GetSalary();` `// good` ` float` ` Salary();` `// bad (missing verb)` ` void` ` SetVisible(``bool` ` isVisible);` `// good (uses adjective)` ` void` ` SetVisibility(``bool` ` isVisible);` `// bad (uses noun)`
---

#### Complement names

Complement names must be used for complement operations, such as:

``` get/set, add/remove, create/destroy, start/stop, insert/remove, increment/decrement, begin/end, first/last, up/down, min/max, next/previous, old/new, open/close, show/hide, suspend/resume, construct/destruct, initialize/terminate ``` etc.

### Non-member variable name

Name of a variable should be in camelCase starting with a lowercase character.

```
int countSomeStuff;
```

### Member variable name

Non-static member variables should have prefix **m_** and then a camelCase name.

Static member variables should have prefix **s_** and then a camelCase name.

Exception: if a struct or a class has only public member variables, they should not have **m_** prefix (for example x, y, z in the Vector3 class).

```
class CTest
{
private:
int m_someValue;
bool m_isActive;
void* m_pInternalData;
};

struct SPerson
{
string firstName;
string lastName;
int age;
bool hasChildren;
};
```

### Global variable name

Global variables are prefixed with **g_** followed by camelCase:

```
int g_countSomeStuff;
```

### Static variable name

Static variables are prefixed with **s_** and after that camelCase:

```
static int s_countSomeStuff;
```

### Thread-local storage variable name

Thread-local storage variables are prefixed with **tls_** and after that camelCase:

```
thread_local int tls_countSomeStuff;
```

### Macro name

Macros are all uppercase with words separated by an _:

```
#define SOME_MACRO(name) name
```

### Variable naming prefixes

Make sure you follow the below mentioned naming prefixes for a variable:

Mandatory, the only variant allowed:

- **p**: pointer-like (raw and smart pointers)
- **sz**: char* and const char* (zero-terminated C string)
- **h**: OS specific handle (socket, mutex, Win32 object, etc.)
- Prefer wrapping handles RAII structures when possible

Deprecated (do not use these prefixes in new code):

- **f**: a floating point number (float or double)
- **n**: an integer
- **s**: a string
- **k**: compile time constants
- **b**: bool
- for booleans use auxiliary verbs such as **was**, ** can**, ** is**, ** must** and so on. See code block below for an example

```
// Good
if (wasActive && receivedData)
{
if (canRun || mustProceed)
{
}
}

// Deprecated (do not use!)
if (bActive && bData)
{
if (bRun || bProceed)
{
}
}
```

### File naming

Make sure the below mentioned conditions are followed for naming a file:

- The source file will be called **SomeClassName.cpp** and the header file will be called ** SomeClassName.h** for the class CSomeClassName.
- For the interface ISomeInterfaceName, the header file is named **ISomeInterfaceName.h**.
- Avoid using CRT file names "**string.h**", "** math.h**", etc. for your own files

### Copyright notice

Each CRYENGINE code file must begin with the below mentioned copyright notice. An empty line should separate it from subsequent code or comments. Copyrights are globally updated (through tools) and must not be individualized by developers themselves to prevent automation issues.

```
// Copyright 2001-2019 Crytek GmbH / Crytek Group. All rights reserved.
```

### Implementation details in common interfaces

Implementation details in the common interfaces (CryCommon) should be avoided, but in the case that this is necessary they should be hidden from the public API using Doxygen hints:

```
//! \cond INTERNAL
/* code */
//! \endcond
```

Alternatively, namespaces matching the following expressions will be ignored:

- *detail::*
- private::*
- *_Internal::*

For example, the following namespace would be automatically hidden from documentation:

```
namespace CryMath_Internal
{
/* code */
}
```

### Layout of C++ classes

The layout for C++ classes should follow the below mentioned format:

- Avoid having multiple classes in the same header/source file (exceptions to this rule are short classes, or classes which are nested inside other classes).
- Prefer a namespace to a class with only static member functions.
- Do not mix methods and member variables in class declarations.
- All C++ class declarations should follow this basic layout:

```
class CSomeClass
{
// enums and typedefs and nested classes
public:
protected:
private:

// Methods
public:
// Start with constructor/destructor if needed
protected:
private:

// Members
public:
protected:
private:
};
```

```
// Example of a wrong class:
class CBadClass
{
public:
void TestMethod();
float m_testVariable;

void TestMethod2();
float m_testVariable2;
};

// Example of a correct class:
class CGoodClass
{
public:
void TestMethod();
void TestMethod2();

protected:
float m_testVariable;
float m_testVariable2;
};
```

- When implementing an interface, all interface functions should be grouped together and should be in the same order as they appear in the interface.
- When adding or modifying existing classes, and when you add C++11 initializers in the class body (such that both initialized and uninitialized members exist), group them separately if possible (this makes implementing/checking constructors for completeness more straightforward).
- Group implementation functions together separating them with the comments.
- Avoid using public member variables in classes.
- If your interface needs to declare and use a `struct`, ` class`, ` typedef` or ` enum`, then put the declaration within the interface structure, avoid polluting the global namespace unnecessarily.
- Interface should not have member variables.
- Usually all interface methods should be virtual and pure. Having a virtual destructor is required.
- Use '**virtual**' and '** override**' keywords for virtual methods in derived classes.
- Use '**final**' keyword on entire classes or methods wherever possible.
```
struct IMyInterface1
{
virtual ~IMyInterface1() = default;
virtual void Method1() = 0;
virtual void Method2() = 0;
};
struct IMyInterface2
{
virtual ~IMyInterface2() = default;
virtual void Method3() = 0;
virtual void Method4() = 0;
};
// Use 'final' keyword if it's the final class in the hierarchy.
class CMyClass final : public IMyInterface1, public IMyInterface2
{
public:
// Option1
//////////////////////////////////////////////////////////
// IMyInterface1 implementation
virtual void Method1() override;
virtual void Method2() override;
//////////////////////////////////////////////////////////
//////////////////////////////////////////////////////////
// IMyInterface2 implementation
virtual void Method3() override;
virtual void Method4() override;
//////////////////////////////////////////////////////////
// Option2
// IMyInterface1
virtual void Method1() override;
virtual void Method2() override;
// ~IMyInterface1
// IMyInterface2
virtual void Method3() override;
virtual void Method4() override;
// ~IMyInterface2

void TestMethod();
void TestMethod2();
};
```

- When implementing multiple interfaces, place the interface function blocks in the same order as they appear in the class declaration.
```
class CSomeClass
: public ISomeInterface1
, public ISomeInterface2
{
...
}
```

### header files

The header files should follow the below mentioned format:

- See [Copyright notice](C%2B%2B%20Coding%20Standard.md#C%2B%2BCodingStandard-copyrightnotice)
- Always use '*#pragma once*', it is supported by all modern compilers.
- Don't use #include guards (#ifndef... #define... #endif).
- Use forward declarations when possible, don’t '#include' just because you need to have a class name available.
- Avoid having function implementations in header files, prefer headers with declarations only, it allows to have less '#include's in headers.
- Avoid using #include in a header file that are not required (put all include needed in the.cpp instead).
- Include third party headers with *#include < >* and just file name (a subfolder prefix may be allowed when that is the convention of the third party library, for example boost), provide include directory to third party headers through build script.
- Order of includes: Current project headers, other project headers, third party headers, system headers.
- Implementation files of a module must not include headers from other modules (Exception is CryCommon, and Public subfolder for interfaces of CryExtension modules).

### source files

The source files should follow the below mentioned format:

- See [Copyright notice](C%2B%2B%20Coding%20Standard.md#C%2B%2BCodingStandard-copyrightnotice)
- Classes should not be split across multiple source files.
- Order of includes: stdafx.h, header file corresponding to the source file, current project headers, other project headers, third party headers, system headers.
- The exception being platform.h, if not provided through stdafx.h

```
// Copyright 2001-2018 Crytek GmbH / Crytek Group. All rights reserved.

#include "stdafx.h"
#include "MyFile.h"

#include "Other1.h"
#include "Other2.h"

#include <cstring>
```

## C++11 and newer, on the use of Modern C++

Up to CRYENGINE 5.1.X, only certain features of C++11 were allowed due to limited compiler support across platforms. Starting with CRYENGINE 5.2 we have dropped support for some of the older compilers, and the state of this document reflects 5.2. Specifically, when considering future use, check the current minimum compiler supported at [Visual Studio Supported Versions_dup](/docs/static/engines/cryengine-5/categories/23756813/pages/23306511) page.

The use of entire C++11 is allowed, with certain exceptions listed below.

For a full list of allowed features, see [Allowed C++ Standard Features](Allowed%20C%2B%2B%20Standard%20Features.md).

The following features **must not** be used, even though they are standard-compliant as of C++11, since we have found issues with them on at least one platform. This list may increase or decrease based on the set of in-use compilers changes, or when we discover additional problems.

- SFINAE using unevaluated contexts (such as those in `sizeof`, `alignof` and `decltype`) is not allowed, since it's not well supported in MSVC.
Note that the use of "**explicit**" SFINAE using `std::enable_if` is allowed, as that seems to work correctly on all compilers.
- The `alignas` keyword is not allowed. Instead use ` CRY_ALIGN` macro in the same context. Note that ` CRY_ALIGN` only works with a literal integral value.
- The use of`std::aligned_storage` type is not allowed if the desired alignment may exceed`alignof(std::max_align_t)`(typically 8 bytes).
Note that you can use `SAlignedStorage` as a direct replacement for this type, which either provides the requested alignment or will fail to compile.
- The `std::auto_ptr` type must not be used, use` std::unique_ptr` instead

When writing variadic template code or deeply recursive constexpr code, please carefully consider the impact on compilation times, and try to minimize the amount of instantiations, and, if possible, avoid including such code in more translation units than necessary.

As the author of modern C++ code, please carefully consider the readability of the code that you write. The closer you are to the fore-front of such technology, the more you have to ensure that people who encounter such features for the first time, still needs to be able to understand and maintain your code.

### Using std::enable_if

When writing a template function that relies on **SFINAE** with ** std::enable_if**, prefer using ** std::enable_if** on the return type where possible. For best readability, the use of the following pattern is recommended:

```
template<...>
typename std::enable_if<..., ReturnType>::type // This should appear on it's own line
inline /*ReturnType*/ MyFunction(...)  // Return-type mentioned again so it reads similar a non-SFINAE function.
```

### Using smart pointers

Starting with C++11, several new smart-pointer types were added (specifically, `std::shared_ptr`, ` std::weak_ptr` and ` std::unique_ptr`. C++98 also already contained ` std::auto_ptr`(but this should not be used, see above). In addition, CRYENGINE offers the `_smart_ptr` type. Each of those have different features and trade-offs, so you should know about the differences when writing code, so you can make a good choice.

Property | _smart_ptr | std::shared_ptr | std::unique_ptr
--- | --- | --- | ---
Ownership | Shared (ref-counted). The ref-counting depends on the type implementation (see next row). | Shared (ref-counted). The ref-counting is always thread-safe. | Single (only one `unique_ptr` instance may point to an object instance at a time)
Target type requirements | COM-like (must implement `AddRef` and `Release`). Typically done by inheriting from ` CMultiThreadRefCount`(thread-safe ref-counting) or`_reference_target_t` (non-thread-safe ref-counting) | None. May optionally derive `std::shared_from_this` (see below). | None.
Deletion | Implemented by `Release` (when ref-count goes to 0). ` CMultiThreadRefCount` and `_reference_target_t` use C++ ` delete` | Deleter type specified on construction (type-erased). The default deleter uses C++ `delete` | Deleter type specified as template parameter. The default deleter uses C++ `delete`
Creation | `_smart_ptr<T> mySmartPtr(new T(...));` | `std::shared_ptr<T> mySmartPtr = std::make_shared<T>(...);` (use ` std::allocate_shared` for custom deleter) | `std::unique_ptr<T> mySmartPtr(new T(...));`(use ` std::unique_ptr<T, TDeleter>` for custom deleter)
Smart pointer size | sizeof(void*) | 2 * sizeof(void*) | sizeof(void*) (+ size of custom deleter, if used)
Run-time cost | (maybe atomic) ref-counting on create/copy/destroy | atomic ref-counting on create/copy/destroy | none
Passing across module boundaries*** | Depends on the Release implementation. `CMultiThreadRefCount`: Safe to pass across boundary `_reference_target_t`: Not safe to pass across boundary | Safe to pass across boundary. | Not safe to pass across boundary. (unless a custom deleter is used that takes care of this manually)

***) This refers to the passing of the smart-pointer itself. The pre-requisite is that the type being pointed to is also safe to pass across module boundary.

Note that`std::shared_ptr` has some additional features not mentioned in the table:

- The ability to share ownership with `std::weak_ptr` (those do not keep the object alive), which can be useful with observer patterns.
- The ability to alias more than one object to the same ref-count (useful if you want to return `std::shared_ptr` to a class member, if the class instance is shared already).

Note that`std::shared_ptr` also has some caveat:

- It is possible to construct a `std::shared_ptr` from a raw-pointer (only explicitly). When you do this, the ` std::shared_ptr` will create a new ref-count instance on the heap, which is usually NOT what you want (if the object was already shared, there is now two conflicting ref-counts). You can derive your class from ` std::shared_from_this` so the ref-count is automatically shared in this scenario.

Note that `std::unique_ptr` is a move-only type (since it cannot share ownership, you can never make a copy of ` std::unique_ptr` by design). If you want to hand over the ownership of a ` std::unique_ptr`, you should use "` std::move(myUniquePtr)`".

As a rule of thumb, the best smart-pointer type in terms of performance are:

- `std::unique_ptr`
- `_smart_ptr`
- `std::shared_ptr`

As a rule of thumb, when trying to pick the right smart pointer type for some scenario, answer those two questions:

- Do I need shared ownership? If not, pick `std::unique_ptr`
- Do I need weak_ptr or aliasing support? If not, pick`_smart_ptr`
- Worst case, pick`std::shared_ptr`

## Code quality

These rules provide some guidelines on how to write good code, as compared to strictly-acceptable code. For new or refactored code, they must be complied to but they can be ignored for small changes in existing code to preserve local consistency. In general, whenever you modify the existing code, you should improve the code quality based on the conditions and formats mentioned in this section.

### Globals

The global variables should follow the below mentioned format:

- Avoid global variables (and singletons)
Rationale: Globals suffer from initialization and destruction order problems, and using them creates difficulties in reasoning about side-effects of the code. Globals invite writing non-thread-safe code.
- Don't pollute the global namespace with functions, enums, types, macros in headers that are not or infrequently used outside the implementing file. Move types into source files or put them into the corresponding namespace. If types have to be global make sure to place them inside the engine global "**`Cry`**" namespace.
Rationale: Less types makes browsing code more straightforward and makes auto-completion features more powerful by providing relevant options only.

### Macros

The Macros should follow the below mentioned format:

- Reduce usage of macros. Consider using a template helper (in a child namespace) if the functionality needs to operate on several/all types. Consider an inline helper function when only a few (or a single) types are supported. If the macro needs to do syntactic trickery, consider refactoring such code.
Rationale: Non-compiler tools are much better at parsing non-macro types, and macro's cannot be stepped into with a debugger.
- If you use macro parameters, always use enclosing () around uses of those parameters. Consider wrapping the macro implementation in a "**`do {... } while(false)`**" block. (Note there is no trailing semicolon, the user of the macro should provide that).
Rationale: The user of a macro may want to pass a complex expression to a macro and the parentheses make sure it's evaluated in the intended order. The do/while construct makes macro's work as if they are a single statement (which they look like syntactically, but otherwise may not expand to).

### Pointers and memory

The pointer and memory should incorporate the following conditions:

- Initialize pointers (to `nullptr` when there is no other initializer`)`.
- Check for `nullptr` pointers, always assume pointer can be `nullptr.`
- Exception: When you already established an invariant that guarantees a non-null value, for example by using address-of within the function.
- When a function should never be called with a `nullptr`, use **` CRY_ASSERT_MESSAGE()`** to establish this invariant at runtime (and to make it clear that this is the intent).
- When allocating memory dynamically, do not forget to deallocate it. Consider using `std::unique_ptr.`
- When using static arrays you must ensure that all code respects the size boundaries (char buffer[256])
- Never do `memset(this,0,sizeof(this))` in the constructor of a class, it may break C++ objects.
- When casting pointers prefer using static_cast<>, const_cast<> etc., avoid using C style casts.

### Const correctness

To maintain correctness while using const, follow the below mentioned conditions:

- Use const wherever possible, always write const correct code.
- Unmodified variables should be const.
- Function parameters (passed by reference or pointer) that are never modified should be const.
- Declaring a by-value parameter as const is acceptable, but mind existing surrounding code's style.
- Input string parameters that are not modified must always be **`const char*`** not just **` char*`**.
- The same applies to pointers. (**`char const* const`**)

```
size_t GetItemCount() const;
```

- Pass the complex types by const reference and not just by value.

```
void Test(Matrix44 m) const;        // bad
void Test(const Matrix44& m) const; // good
```

- You should pass complex types by value if the function would otherwise make a copy anyway. In this case, the caller may use a move-constructor (if available and possible) at the call-site to prevent the copy.
- When writing templated functions, where the argument type is dependent on the instantiation, prefer r-value references (T&&) and perfect forwarding, unless you have a specific reason not to do so.

### Numeric compile-time constants

The numeric compile-time constants should incorporate the following conditions:

- Avoid using magic numbers (prefer const, constexpr or enum, instead of #define).
- Don't use named constants for specifying array sizes in cases when it is self-explanatory except for where the array size is used in more than 1 location in code.
- Engine wide naming rules for variables apply as well to compile time constants (camelCase). Remove deprecated '**k**' prefix if encountered in edited code.
- Using or omitting '**static**' for local compile-time constants is up to you. Using of anonymous enums for integer compile-time constants is allowed.
- Format of floating point literals: 7.0 or 7.0f (don't use 7. or 7.f), 0.3f (don't use.3f), 3.4e-15f (don't use uppercase E).

```
enum : uint8 { cornersInTriangle = 3 };         // good
const uint8 cornersInTriangle = 3;              // good
static constexpr uint8 s_cornersInTriangle = 3; // good

char buffer[256];  // good, use of the number is self-explanatory
```

### Best practices

Ensure, you follow the below mentioned best practices:

- Never copy any code from other games or programs! (Use of any third party code requires TD authorization and license check such as, opensource, MIT etc.)
- Be explicit when writing the types that you want to use (for return types, variables, etc*). Using auto is allowed, but make sure the code is still understandable.

```
unsigned count; // Wrong, type-size not set
uint32 count; // Correct

auto myLambda = [](Type1 t1, Type2 t2) -> ReturnType { ... }; // Specify return-type explicitly
```

- Never use anonymous structs or unions.
- Never use using-directives ('using namespace xxx;') and using-declarations ('using xxx::yyy;') in the global namespace in header and source files.
- In no-uber type build scenarios those will unintentionally "bleed" into other source files.
- Don't create a new type, if a type exists in another project use it (e.g. Vec3, Matrix34, etc.).
- Avoid goto functions.
- Prefer pre-incrementing for loop counters/iterators (++i instead of i++). It is more efficient (especially for STL containers and debug builds).
- Always perform error checking; ideally a function should never fail when it receives bogus data (null pointer, etc.).
- Note: Error *handling* is optional, using `assert()` to detect them is much better than nothing at all.
- Use assertions for unhandled errors during development (`assert()` or `CRY_ASSERT()`, not `ASSERT()`).
- Only use asserts to detect code/logic errors, don't check for invalid data (file contents). Such errors must be handled (even if through `CryFatalError()`)
- Only submit code without compiler warnings. Avoid modifying warning settings to achieve this.
- We will treat warnings as errors by default.
- Sync to head revision and test before submitting.
- Avoid redundant dereferencing (m_pGame->m_pSystem->GetStuff()->DoStuff()) it makes the code unreadable.
- No logging spam, don't flood the game or console with debug messages.
- Do not submit debug code (even when in #if 0 blocks). Do not submit #pragma optimize.
- All unnecessary files under source control should be removed.
- Avoid compiler-specific and platform-specific code at all costs. Use platform abstractions that are available in CryCommon, or add them.
- Code that does not function on all our supported platforms are always suspected in reviews.
- Never cast a pointer to int, to cast a pointer to an integer type only use **intptr_t** or ** u****intptr_t** (32/64-bit portability).
- If it has to be used always protect **#pragma warning** with **push** and **pop**.
- If it is placed in a.cpp it will be valid for the whole.cpp file and error might not be spotted
- If it is placed in a.cpp it will carry over to any.cpp that follow the.cpp file when using uber file builds

```
#pragma warning(push)
#pragma warning(disable:4355) // 'this': used in base member initializer list

// my code

#pragma warning(pop)
```

### Commenting

We use Doxygen as our documentation-generation tool for CryCommon. It parses header files looking for comments in a particular style, which it then processes to make HTML pages.

Use Doxygen comments to document the public interface of the engine, i.e. those types and their members that a user is expected to work with. For implementation details and internals, use either Doxygen or regular C++ comments.

Below is an example of the right format:

```
//! A simple class to describe somebody who likes cheese.
class CheeseLover
{
public:
//! Find the type (e.g. "blue", "mild", or "feta") of the named cheese (if it is in the specified fridge).
//!  This is mostly used in whimsical introductory scenes to give an idea of a character's personality (e.g. "blue" = heroine, "mild" = psychopath).
//!  This function is best used to search small fridges, as it first sorts all the items in the fridge, which can cause performance problems if there are many items.
//! Cheese names are taken from https://en.wikipedia.org/wiki/Cheese.
//!  \param fridgeID Fridge in which to look.
//!  \param nameOfCheese Name of the cheese for whose type we are looking.
//!  \return Description of the cheese type for the first named cheese (if available) or "Not found" if it is not available.
//! \see FindFruitInFridge, IsFridgeEmpty
//! \note This is only appropriate for full-sized fridges.
//! This is still part of the same note, telling you not to use it for mini-fridges.
std::string FindCheeseTypeInFridge(std::string fridgeId, std::string nameOfCheese);

protected:
std::string m_bestCheese;  //!< Name of the best cheese in the world.
private:
std::string m_guiltyPleasure; // No one needs to know about this
};
```

The first line in a block of '//!' comments is always taken as a brief description that is shown in overviews, therefore it should be a complete sentence.

The lines after the //! block are free-flowing text that describes what the function/class/variable etc. is for. This is a good place to explain when somebody is likely to want to call the function and any potential issues (for example, performance) that might result from calling it.

Parameters of functions are listed one per line, starting with the '**\param**' keyword.

The return is denoted by '**\return**', it is a free form description of what the function returns, it is important to document all possible return values, particularly error results.

The '**\see**' tag is for related functions that people might also be interested in/need when they are using this function.

**Rules**:

- - Each line of a documentation comment must begin with '//!'. There must be a space between this marker and the rest of the comment.
- Comments after variable names (on the same line) must start with '//!<' and have a space between this marker and the rest of the comment.
- Comments should start with a capital letter and end with a full stop.
- When using algorithms from external sources, link to the reference (web-page, PDF, etc*). Doxygen detects links automatically.
- This documentation will be publicly available, so keep it professional.
- Descriptions must be meaningful - simply repeating the function or variable name is not allowed.
- Do not introduce commented code. Rather create a backlog task for TODOs.

### Preprocessor

When doing a cascade of **`#ifdef`** cases, indent the body using tabs (starting after the `#`). Also, it is a good practice to provide an `#error` in the final else statement:

```
#if defined(GO_WEST)
#   define BLAH 1
#elif defined(GO_EAST)
#   define BLAH 2
#else
#   error Unknown direction
#endif
```

### CRT

- CryEngine uses custom memory and file managers, and not all CRT functions are supported.
- Do not use iostreams.
- Do not use these CRT functions: **strdup** (not supported), any file i/o functions (unless you need to save file for debugging).

#### Memory allocation

Within CRYENGINE, the new and delete functions are globally remapped to the CRYENGINE heap allocator. Avoid using `malloc` and ` free,`instead use` CryMalloc/CryFree`if that behavior is preferred. You must assume that all memory allocated in a module A cannot be freed in a module B. (Nowadays, we tend to use one heap for all modules but mixing this will still skew the memory budgets that are tracked per module, so don't do this).

Memory allocation for C++ objects may be assumed to always succeed (since it's typically impossible to continue without memory anyway). When handling large amounts of memory, especially when dealing with large contiguous blocks, it's a good idea to handle allocation failure if it's possible to signal that failure in a meaningful way. Either way, allocation failure may set the OOM flag, which is considered "fatal error" in the general case.

### Standard Template Library (STL)

There are a number of methods in STL that are documented to throw exceptions in certain scenarios. As exceptions are disabled by default, such a scenario that otherwise would have thrown an exception now invokes undefined behavior at run-time. Thus, you must ensure that such scenario's cannot happen at run-time, either by designing the code such that it's impossible (you can place assert to check this), or by testing at run-time and placing such method calls into a conditional section.

- We use STL containers by default, unlike other game developers.
- Prefer using STL instead of your own containers.
- You may add different container types, but only after you have, through appropriate profiling, determined why the STL code was slow, and you have proven objectively that the new code solves that performance problem. When you do this, document this through comments (or at least in the review).
- Make new containers are compatible with STL paradigms wherever possible (works with range-for and algorithms).
- Use STL algorithms when appropriate.
- Use **`.empty()`** instead of **`.size() == 0`** for readability.
- Always use iterators to traverse the container. Always assume iterators are invalidated on every call that the standard invalidates the iterators (unless you took specific measures that prevent invalidation, such as`reserve()`, in which case you should put a comment).
- Never pass STL datatypes through DLL boundaries (this includes (pointers to) std::string and iterators)
- Interfaces should always use char* strings (probably const char*)
- Avoid using std::list; in most cases std::vector will be more effective (for relatively small number of entries).
- For further reference take a look at Scott Meyers' "**Effective STL**".
- There's a namespace **stl::** with several useful STL helper functions:
- stl::find_in_map(map, key,defaultValue)
- stl::binary_find(sortedVector, value)
- stl::insert_unique(container, value)

### Strings

The strings should incorporate the following conditions:

- CRYENGINE uses a custom reference counting string class.
- Do not use **std::string*** or ** std::wstring**, just enter ** string** and ** wstring.**
- Use **c_str()** method to access to the contents of the string
- Never modify memory returned by the **c_str()** function from string. Strings are referenced counted and wrong string can be affected.
- Do not pass strings via abstract interfaces. All interfaces must use `const char*` in interface methods.
- CRYENGINE string class have a combined interface of the **std::string** and of the ** MFC CString**, you can use both kind of functions to operate on it.
- Avoid performing many string operations at run-time as they often cause memory reallocations.
- For fixed size strings, use a **`CryFixedStringT`** class, prefer using it over static char arrays (ex. char [256]).
- Use `cry_strcpy()`,`cry_strcat()`,`cry_sprintf()` etc. instead of `strcpy()`,`strcat()`,`sprintf()` etc.
For more information, see CryCommon/CryString/CryStringUtils.h.

### Compiler-specific features

- Never rely on compiler specific functionality (e.g. #pragma), if impossible, always surround them with a compiler guard.
- Stay away from platform-specific API functions (everything that starts with **_** is not standard - _findfirst, __int64, etc.).

### Undefined behavior

Never rely on undefined behavior in your code. Visual C++ allows many forbidden things, so just because it compiles with Visual C++, it is not a guarantee that you have written good code. For example:

```
edge->next  {{ edge }}  otherEdge; // assignment order is not guaranteed!!
```

### Miscellaneous

#### Express your intentions clearly

To check whether or not a container is empty always use **empty()**, not ** size()!= 0**. Using ** empty()**is closer to what you think when writing or reading code. Basically, you ask “is this array empty?”, not “is size of this array not equal to zero?”.

Avoid using **`Boolean == true`** or **` Boolean == false`**, always use **` Boolean`**or **`!Boolean`**. They're identical in meaning, but the former is closer to how the sentences are constructed.

```
if (!tooLateForMeeting)         // preferable : "If not too late for a meeting"
if (tooLateForMeeting == false) // better to avoid: "If the fact that it's too late for a meeting is false"
```

#### Reduce code complexity

Below is a compact version of bitsquid blog post: [http://bitsquid.blogspot.de/2012/08/cleaning-bad-code.html](http://bitsquid.blogspot.de/2012/08/cleaning-bad-code.html)

Smart programmers organize the way they work so that they don't have to be that smart.

- Remove the functionalities that you are not using. Only have the things that you know you need them most. Add more complicated stuff whenever you need it.
- Remove unnecessary abstractions, replace with concrete implementations.
- Remove unnecessary virtualization and simplify object hierarchies.
- If only one setting is ever used, get rid of the possibility of running the module in other configurations.

#### Get rid of shared mutable state

Below is a compact version of bitsquid blog post:

[http://bitsquid.blogspot.de/2012/08/cleaning-bad-code.html](http://bitsquid.blogspot.de/2012/08/cleaning-bad-code.html)

Shared mutable state complicates understanding of code since a single piece of code could easily change behavior of a completely different piece of code. Getting rid of shared mutable state makes multithreading much simpler.

Sources of shared mutable state:

- Non-const global variables.
- Complex non-const objects with data members (especially if data members are used to pass information between member functions).
- Very big functions (their local variables are almost as bad as global variables; it becomes impossible to tell the effects of a simple change to a local variable might have on 2000 lines further down in the code).
- Non-const reference and pointer parameters (they can be used to subtly shared mutable state between the caller, the callee and anyone else who might be passed the same pointer).

Getting rid of shared mutable state:

- Split big functions into smaller ones.
- Split big objects into smaller ones by grouping members that belong together.
- Make data members private.
- Change member functions to be const and return the result instead of mutating state.
A const member function can only read members of a class. Naming a const member function “**Get...**” allows to tell the user that the function doesn’t change object state even if it performs a complex operation.

- Change member functions to be static and take their arguments as parameters instead of using data members.
We use static member functions that belong logically to a class but are not allowed to read or write anything. Often they have names started with "**Create...**". Such functions operate on the input values only and return a result (which gives the compiler some opportunities for optimizations).

- Make local variables const.
- Change pointer and reference arguments to const.
- In very extreme cases, you may consider getting rid of objects entirely and implement the functionality as pure functions without side effects.

See also John Carmack’s blog post: [http://gamasutra.com/view/news/169296/Indepth_Functional_programming_in_C.php](http://gamasutra.com/view/news/169296/Indepth_Functional_programming_in_C.php)

[Coding standard](#coding-standard)[Naming conventions](#naming-conventions)[C++11 and newer, on the use of Modern C++](#c-11-and-newer-on-the-use-of-modern-c)[Code quality](#code-quality)
