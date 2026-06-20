# Custom Item types

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450484
- Page ID: 29450484
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Custom Item types
- Parent: Universal Query System (UQS)

## Content

##
Overview

Item types are custom data types that can be exposed to the Universal Query System (UQS) under a specific name.

Items are used in various places inside UQS:

-
They represent the reasoning space of a query and will be "evaluated" one after another by a running query.

-
They are used by input parameters for Generators, Functions, and Evaluators.

-
They represent the return value of Functions.
Item types can optionally be registered with callbacks for visualizing the individual items that are being evaluated in a query.

A typical item type would be a Vec3 to represent points that need to be scored and tested in the 3D world.

The UQS Standard Library already provides several types geared around
`
Vec3
`
, most notably
`
Pos3
`
,
`
Ofs3
`
 and
`
Dir3
`
.

For in-depth details as to how these item types (among others) are brought into the UQS core, you can check out the private
`
UQS::StdLib::CStdLibRegistration::InstantiateItemFactoriesForRegistration()
`
 method.

##
Registering Item Types

Registration of item types happens in C++ code by using the convenient helper class
`
CItemFactory
`
<>, this comes out of the box with UQS:

```

`
UQS::Client::CItemFactory<>
`

```

Registration then happens through a static global instance of the
`
CItemFactory<>
`
 class template:

```

`
struct SMyCustomType
{
  int a, b, c;
};

// ...

UQS::Client::CItemFactory<SMyCustomType>::SCtorParams ctorParams;
ctorParams.szName = "my::CustomType";
ctorParams.guid = "0142838d-9c8b-454c-866f-b1d4b925f803"_uqs_guid;
// ...

// Notice: This instance of CItemFactory<> must _not_ go out of scope for the lifetime of UQS,
//         since the UQS core will keep a pointer to this particular factory!
static const UQS::Client::CItemFactory<SMyCustomType> itemFactory_MyCustomType(ctorParams);
`

```

You can register as many different item types as you want. If doing so, make sure that they all go under different GUIDs and that no data type gets registered more than once.

To finally expose your item types (and generators, functions and evaluators) to the UQS core, you'd just call this static helper method once receiving the
`
UQS::Core::EHubEvent::RegisterYourFactoriesNow
`
 event:

```

`
UQS::Client::CFactoryRegistrationHelper::RegisterAllFactoryInstancesInHub()
`

```
