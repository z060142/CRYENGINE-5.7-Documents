# Important 3.8.1 EaaS Code and Data Changes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962926
- Page ID: 44962926
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.8 > EaaS 3.8.1 > Important 3.8.1 EaaS Code and Data Changes
- Parent: EaaS 3.8.1

## Content

##
Overview

Below are some important code and data changes that you should be aware of when moving to 3.8.1.

##
C++11

C++11 compilation is now enabled for all platforms. Related important code changes:

-
Using of
`
auto_ptr
`
 is now deprecated. Use
`
std::unique_ptr
`
 instead.

-
Uppercase macros
`
VIRTUAL, OVERRIDE, FINAL
`
 were deleted. Use
`
virtual, override, final
`
 instead.

-
`
register
`
 keyword was deleted from code.

##
Random numbers generators

Global (per-module) random number generators are now accessible via
`
cry_random_
`
xxx
`
()
`
 functions (see Code\CryEngine\CryCommon\Random.h).

Old random functions such as
`
ai_rand(), cry_frand(), rnd(), RandomNum(), frand()
`
 etc. were deleted. Use
`
cry_random_xxx()
`
 instead.

Class
`
CLCGRndGen
`
 (a simple linear congruential generator) was refactored and renamed to
`
CRndGen
`
.

Note that ranged functions (cry_random(minValue, maxValue), GetRandom(
minValue, maxValue
), etc.) return random value within the
**
inclusive
**
 range between minValue and maxValue. See function declarations for details.

##
Devirtualizer macros

The following devirtualizer-specific macros are no longer used and were removed:
`
UNIQUE_IFACE, UNIQUE_VIRTUAL_WRAPPER, DEVIRTUALIZE_HEADER_FIX, DEVIRTUALIZATION_VTABLE_FIX, DEVIRTUALIZATION_VTABLE_FIX_IMPL
`
.

##
Unicode/UTF-8 support

We have started moving our default string representation to UTF-8 (was, ASCII/ANSI).

This change also deprecates the use of all wide strings (UTF-16, UCS-2, UTF-32, UCS-4) except at API boundaries that do not accept UTF-8.

Because UTF-8 strings can be stored in strings consisting of bytes, this change does not affect all code files, but it does affect all existing strings.

You may encounter compilation errors (in non-vanilla code) when calling previously-existing wide string APIs, and you will have to port to UTF-8 as part of this version upgrade.

For implementation details please consult the
[/docs/static/engines/cryengine-3/categories/1638401/pages/19380649](
Text Localization & Unicode Support
)
 page.

##
C ctrings

Safe string copying/concatenating functions cry_strcpy(), cry_wstrcpy(), cry_strcat(), cry_wstrcat() were added to Code/CryCommon/StringUtils.h. Those functions are recommended to be used instead of strcpy(), strcpy_s() etc.

##
CRC-32

Computation of CRC-32 is now handled by CCrc32 class from Code/CryCommon/CryCrc32.h. See comments in CryCrc32.h file. CrySystem's "crc32 generator" methods were removed.

##
CryExtension

Renamed functions that clashed with Win32 API defines:

-

-
ICryFactory::GetClassName renamed to GetName

-
IEntityClassRegistry::RegisterClass renamed to RegisterEntityClass

-
IEntityClassRegistry::UnregisterClass renamed to UnRegisterEntityClass

##
Changes in RC

##
Syntax changes in "rc.ini"

The following settings in the config file have been changed:

##
colorspace

'srgb' option is no longer supported, it is replaced by 'colorspace'.

colorspace option specifies color spaces for input and output images.

**
Format:
**
colorspace=<input>,<output>

-
<input> is one of: linear, sRGB;

-
<output> is one of: linear, sRGB, auto.
'auto' selects best encoding (linear or sRGB) automatically, based on the brightness of the output image.

Default value of colorspace is linear,linear.

Use the the table below to replace srgb with colorspace
in your rc.ini file
:

-
srgb=0 -> colorspace=linear,linear

-
srgb=1
->
 colorspace=sRGB,auto

-
srgb=2
->
 colorspace=sRGB,sRGB

-
srgb=3
->
 colorspace=linear,sRGB

-
srgb=4
->
 colorspace=sRGB,linear

##
Aliases

Added support of aliases for preset names: check the new section [_presetAliases] in
*
Bin64/rc.ini
*
.

##
Preset changes

We cleaned up the texture presets available in CryTIF and adjusted the names to be more in line with our physical based renderer. To maintain backwards compatibility, the old preset names are automatically remapped to the new presets. See the
*
rc.ini
*
 file for the exact remapping rules. The most important name changes are:

-

-
**
Diffuse
**
 is called
**
Albedo
**
 now

-
**
Specular
**
 is called
**
Reflectance
**
 now

-
**
Gloss
**
 is called
**
Smoothness
**
 now

##
Alternative roughness distribution

Gloss (smoothness) values are mapped to the roughness used by our BRDF using a square function now. Compared to the previous function, this produces results that are slightly more perceptually linear. The more important benefit however is that the squared distribution has become very common across the industry, so switching to it makes it easier to use scanned roughness data available from various sources inside CRYENGINE. For backwards compatibility, gloss maps using the old preset (
*
NormalsWithGlossInAlpha_highQ
*
) are automatically converted to the new distribution when processed by the RC.

[#c-11](
C++11
)
[#random-numbers-generators](
Random numbers generators
)
[#devirtualizer-macros](
Devirtualizer macros
)
[#unicodeutf-8-support](
Unicode/UTF-8 support
)
[#c-ctrings](
C ctrings
)
[#crc-32](
CRC-32
)
[#cryextension](
CryExtension
)
[#changes-in-rc](
Changes in RC
)
