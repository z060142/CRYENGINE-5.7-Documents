# CryString

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306447
- Page ID: 23306447
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryCommon > CryString
- Parent: CryCommon

## Content

### Overview

CRYENGINE has a custom reference-counted string class **CryString** (declared in * CryString.h*) which is a replacement for the STL std::string. It should always be preferred over std::string. For convenience, **string** is used as a typedef for `CryString`.

### How to Use Strings as Key Values for STL Containers

The following code shows good (efficient) and bad usage:

```
const char *szKey= "Test";

map< string, int >::const_iterator iter = m_values.find( CONST_TEMP_STRING( szKey ) );   // Good way

map< string, int >::const_iterator iter = m_values.find( szKey );  // Bad way, don't do it like this!
```

By using the suggested method, you avoid allocation/deallocation and copying for a temporary string object. This is a common problem for most string classes. By simply using the macro `CONST_TEMP_STRING`, we trick the string class to use the pointer directly without freeing the data afterwards.

### Further Usage Tips

- Do not use **std::string** or ** std::wstring**, just ** string** and ** wstring** and never include the standard string header <string>.
- Use the `c_str()` method to access the contents of the string.
- Never modify memory returned by the `c_str()` method since strings are reference-counted and a wrong string instance could be affected.
- Do not pass strings via abstract interfaces; all interfaces should use const char* in interface methods.
- CryString has a combined interface of std::string and MFC CString, so both interface types can be used for string operations.
- Avoid doing many string operations at run-time as they are often causing memory reallocations.
- For fixed size strings (e.g. 256 chars) use `CryFixedStringT` (should be preferred over static char arrays).
