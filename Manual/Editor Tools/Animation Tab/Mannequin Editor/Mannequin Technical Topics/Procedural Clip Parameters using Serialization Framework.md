# Procedural Clip Parameters using Serialization Framework

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308480
- Page ID: 23308480
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Technical Topics > Procedural Clip Parameters using Serialization Framework
- Parent: Mannequin Technical Topics

## Content

### Overview

The Procedural Clip (runtime structure) and Procedural Clip Parameter (static data structure) have gone through some structural changes in order to fix some of their shortcomings.

The Procedural Clip Parameters in the old format consisted of a fixed number of strings and floats. With the new format, implementers of Procedural Clips have control on the types, names and the number of parameters that they require, and on how those are presented to the user in the UI. This is achieved by having each Procedural Clip define the specific structure that it requires for its parameters.

Projects updating to this Mannequin version must update their code and data structures. See [Overview of Required Work for Conversion to New Structure](Procedural%20Clip%20Parameters%20using%20Serialization%20Framework.md#ProceduralClipParametersusingSerializationFramework-OverviewConversion) for more detailed information.

The [Serialization Library](../../../../../API%20Reference/CRYENGINE%20Engine%20Code/Engine%20Modules/CryCommon/Serialization%20Library.md) is used to serialize Procedural Clip Parameters both to disk and to the UI. For this to work, we must write a Serialize function for the Procedural Clip Parameter structure.

The ProcDefs.xml file is no longer needed.

The xml format for ADB files has changed. Some remarks:

- It is possible to load old ADB files. For loading ADB files saved in the old xml format a conversion file is necessary (See [Example of Data Conversion from Old Procedural Clips to New Procedural Clips](Procedural%20Clip%20Parameters%20using%20Serialization%20Framework.md#ProceduralClipParametersusingSerializationFramework-DataConversion) for more details)
- It is not possible to save to the old xml ADB format any more.

Procedural Clips and Procedural Clip Parameters don't use CryExtension. Both structures are created through the ProceduralClipFactory, accessible via the main MannequinInterface.

### Comparison of Old Procedural Clip Parameter and New Procedural Clip Parameter Structure

Old Procedural Clip Parameters structure consisted of a string, a string+crc32, a crc32 of a string, and and array of around 30 floats.

```
struct SProceduralEntry
{
...
SAnimRef animRef;
SProcDataCRC dataCRC;
TProcClipString dataString;

float parameters[MAX_PARAMS];
};
```

All Procedural Clips inherited from SProceduralParams and defined the floats variables they used, limited in number by the amount of floats specified in SProceduralEntry.

```
struct SProceduralParams
{
SAnimRef animRef;
SProcDataCRC dataCRC;
TProcClipString dataString;
};
```

Example:

```
struct SOldProceduralParamsExample
: public SProceduralParams
{
// Not using animRef or dataString, but still have them.
// dataCRC represents an attachmentName.
float additionalParam;
float offsetX;
float offsetY;
float offsetZ;
float bSomethingElse; // We need to encode other types (e.g. bool) as floats.
};
```

The initial values of the members were defined in ProcDefs.xml when we created a proc clip that used this parameter type.

As of the new version, SProceduralParms doesn't exist anymore.

We must inherit from the IProceduralParams interface, implement the Serialize function.

We initialize the values of the members in the constructor.

We don't require the ProcDefs.xml file anymore.

We are not restricted to just using floats or the amount/types of strings we have, and we can give all members meaningful names.

```
struct SNewProceduralParams
: public IProceduralParams
{
SNewProceduralParams()
: additionalParam(42.f)
, offset(ZERO)
, somethingElse(false)
{
}

virtual void Serialize(Serialization::IArchive& ar)
{
ar(attachmentName, "AttachmentName", "Attachment Name");
ar(additionalParam, "AdditionalParam", "Additional");
ar(offset, "Offset", "Offset");
ar(somethingElse, "SomethingElse", "Something Else");
}

SProcDataCRC attachmentName;
float additionalParam;
Vec3 offset;
bool somethingElse;
};
```

### Overview of Required Work for Conversion to New Structure

##### Update code structures

It is necessary to change the code to update Procedural Clips Parameters structure and how Procedural Clips get registered with the system.

For more details see the following sections:

- [Comparison of Old Procedural Clip Parameter and New Procedural Clip Parameter Structure](Procedural%20Clip%20Parameters%20using%20Serialization%20Framework.md#ProceduralClipParametersusingSerializationFramework-ParameterStructureComparison)
- [Example of Code Conversion from Old Procedural Clips to New Procedural Clips](Procedural%20Clip%20Parameters%20using%20Serialization%20Framework.md#ProceduralClipParametersusingSerializationFramework-CodeConversion)

##### Update animation databases

Create the "ProcClipConversion.xml" file.

- This allows to load databases saved in the old format into the new one.

Load the animation databases in the editor and save them again.

- This is a one time only operation, so it's important to check thoroughly that data conversion was successful.
- Double check the errors/warning in the log when loading and saving the animation databases.
- Double check the xml differences to make sure nothing went wrong.
- It's not possible to save into the old Procedural Clip format again.
- Once everything is converted "ProcClipConversion.xml" is not needed anymore.

For more details see the following section:

- [Example of Data Conversion from Old Procedural Clips to New Procedural Clips](Procedural%20Clip%20Parameters%20using%20Serialization%20Framework.md#ProceduralClipParametersusingSerializationFramework-DataConversion)

### Example of Code Conversion from Old Procedural Clips to New Procedural Clips

#### Old Format

In ProcDefs.xml

```
<AimPose anim="1">
<Params blendTime="1.0" layer="4"/>
</AimPose>
```

ProceduralClipAimPose.cpp:

```
#include "ICryMannequin.h"
#include <CryExtension/Impl/ClassWeaver.h>

// Procedural Clip Parameters
struct SAimIKParams
: public SProceduralParams
{
float blendTime;
float layer;
};

// Procedural Clip and Registration
class CProceduralClipAimPose
: public TProceduralClip<SAimIKParams>
{
public:
CRYINTERFACE_BEGIN()
CRYINTERFACE_ADD(IProceduralClip)
CRYINTERFACE_END()

CRYGENERATE_CLASS(CProceduralClipAimPose, "AimPose", 0x6B0AF1C0BDA843aa, 0xADDFE222F0547BAE)

...
};

CProceduralClipAimPose::CProceduralClipAimPose()
{
}

CProceduralClipAimPose::~CProceduralClipAimPose()
{
}

CRYREGISTER_CLASS(CProceduralClipAimPose);
```

#### New Format

##### Procedural Clip Parameters

The Procedural Clip Parameters structure becomes:

```
#include <ICryMannequin.h>

// Procedural Clip Parameters
struct SAimIKParams
: public IProceduralParams
{
SAimIKParams()
: blendTime(1.0f)
, layer(4)
{
}

virtual void Serialize(Serialization::IArchive& ar);

SAnimRef animRef;
float blendTime;
uint32 layer;
};
```

##### Serialize Function

To implement the Serialize function we must include the Serialization Framework.

```
#include <Mannequin/Serialization.h>

struct SAimIKParams
: public IProceduralParams
{
...

virtual void Serialize(Serialization::IArchive& ar);
{
ar(animRef, "Animation", "Animation");
ar(blendTime, "BlendTime", "Blend Time");
ar(layer, "AnimationLayer", "Animation Layer");
}

...
};
```

We can also give some hints to the Serialization Framework on how to present our attributes in the UI by using decorators.

The following shows how to have the Animation property display an Animation Browser and to limit the AnimationLayer to values between 0 and 15.

```
ar(Serialization::Decorators::AnimationName<SAnimRef>(animRef), "Animation", "Animation");
ar(blendTime, "BlendTime", "Blend Time");
ar(Serialization::Decorators::Range<uint32>(layer, 0, 15), "AnimationLayer", "Animation Layer");
```

You can find more information about the serialization function here: [Serialization Library](../../../../../API%20Reference/CRYENGINE%20Engine%20Code/Engine%20Modules/CryCommon/Serialization%20Library.md).

##### Procedural Clip and Registration

The Procedural Clip and its registration are also simplified a bit, by not requiring the CryExtension GUID anymore.

```
class CProceduralClipAimPose
: public TProceduralClip<SAimIKParams>
{
...
};
REGISTER_PROCEDURAL_CLIP(CProceduralClipAimPose, "AimPose");
```

### Example of Data Conversion from Old Procedural Clips to New Procedural Clips

To be able to read animation databases that were created when using the old Procedural Clip format, we have a helper class that will allow to load old Procedural Clips if we specify a mapping from the old parameter format to the new parameter format.

The mapping is defined in: `Scripts/Mannequin/ProcClipConversion.xml`

This file is used while loading when we encounter an old Procedural Clip type. It works on all platforms to make the transition from old data to new data as seamless as possible until the animation databases are upgraded by re-saving them in the editor.

This is how the format of the ProcClipConversion.xml file looks like:

```
<Conversion>
...
<NameOfProcClip anim="NewNameForThisParameter_Optional" string="NewNameForThisParameter_Optional" crcString="NewNameForThisParameter_Optional">
<Param value="NewNameForFloatParameter_1" />
<Param value="NewNameForFloatParameter_2" />
...
<Param value="NewNameForFloatParameter_N" />
<NameOfProcClip />
...
</Conversion>
```

Values for parameter names in ProcClipConversion are the serialized parameter names in the Serialize function.

This is how it would look like to convert automatically from old AimPose Procedural Clip parameters to the new format.

```
<AimPose anim="Animation">
<Param value="BlendTime" />
<Param value="AnimationLayer" />
</AimPose>
```

This structure can easily be obtained through some minor modifications to the ProcDefs.xml by filling in for each parameter the names that we use them

For reference, this is how the ProcDefs.xml entry for AimPose looked like:

```
<AimPose anim="1">
<Params
blendTime="1.0"
layer="0"/>
</AimPose>
```

And also for reference, this is how the Serialize function looks like:

```
ar(animRef, "Animation", "Animation");
ar(blendTime, "BlendTime", "Blend Time");
ar(layer, "AnimationLayer", "Animation Layer");
```

When converting old Procedural Clip Parameters via this method, the log will get filled with messages similar to the following:

```
Loading subADB animations/mannequin/adb/playerdeathreactions3p.adb
...
Converted old format procedural clip with type name 'AimPose' at line '444'.
Converted old format procedural clip with type name 'AttachEntity' at line '458'.

...
```

Warnings and errors will be logged in cases where the conversion fails, so it's important to check the log before saving the files as conversion might have failed. Clips that fail to convert become "None" clips.

It is ok to ignore the converter failing when encountering an old Procedural Clip of type "None", since that becomes a "None" clip in the new format. The error message will look like this:

```
[Error] CProceduralClipFactory::CreateProceduralClipParams: Failed to create procedural params for type with crc '-542986255'.
[Error] Could not create procedural clip parameters for procedural clip with type name 'None' and crc '-542986255' at line '462'.
```

[Comparison of Old Procedural Clip Parameter and New Procedural Clip Parameter Structure](#comparison-of-old-procedural-clip-parameter-and-new-procedural-clip-parameter-structure)[Overview of Required Work for Conversion to New Structure](#overview-of-required-work-for-conversion-to-new-structure)[Example of Code Conversion from Old Procedural Clips to New Procedural Clips](#example-of-code-conversion-from-old-procedural-clips-to-new-procedural-clips)[Example of Data Conversion from Old Procedural Clips to New Procedural Clips](#example-of-data-conversion-from-old-procedural-clips-to-new-procedural-clips)
