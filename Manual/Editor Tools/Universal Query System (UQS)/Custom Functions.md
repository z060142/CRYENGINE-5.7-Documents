# Custom Functions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450486
- Page ID: 29450486
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Custom Functions
- Parent: Universal Query System (UQS)

## Content

##
Overview

Functions basically serve 3 purposes:

-
They grant access to global input parameters.

-
They grant access to the current item that is being evaluated.

-
They can be used as "converters" in-between functions.

##
Function Hierarchies

As a function can call another function, we will eventually end up with a whole hierarchy of functions, which is then basically a tree. As such we need to distinguish between leaf and non-leaf functions.

Leaf functions are those that have no parameters. Non-leaf functions do have one or more parameters, and each parameter in turn resolves as a further (nested) function call.

Examples of leaf functions:

-
Global input parameter.

-
Current item the query is iterating on.

-
A literal value.
Examples of non-leaf functions:

-
A custom function that adds 2 vectors and returns their sum.

-
A custom function that returns the position of a given entity.

##
Built-in Functions

For the sake of convenience, the Universal Query System (UQS) automatically registers leaf functions for every registered item type. As such, each new item type will automatically add support for a global input parameter of exactly that type. The same can be said for functions that return a literal and grant access to the current item in a query.

##
Example Function: Vec3Add()

Custom functions always need to be non-leaf functions (i. e. functions that do take at least one parameter). There's currently no use-case which would require it to be different. Here's an example from the UQS's StdLib for for a custom function that takes 2 parameters:

```

`
class CFunction_Vec3Add : public UQS::Client::CFunctionBase<
    CFunction_Vec3Add,
    Vec3,
    UQS::Client::IFunctionFactory::ELeafFunctionKind::None>
{
public:

    struct SParams
    {
        Vec3 v1;
        Vec3 v2;

        UQS_EXPOSE_PARAMS_BEGIN
            UQS_EXPOSE_PARAM("v1", v1, "VECA", "First vector to add.");
            UQS_EXPOSE_PARAM("v2", v2, "VECB", "Second vector to add.");
        UQS_EXPOSE_PARAMS_END
    };

public:

    explicit CFunction_Vec3Add(const SCtorContext& ctorContext)
        : CFunctionBase(ctorContext)
    {}

    Vec3 DoExecute(const SExecuteContext& executeContext, const SParams& params) const
    {
        return params.v1 + params.v2;
    }
};
`

```

SParams
Notice that each custom function class
**
must
**
 have a
**
SParams
**
 struct embedded. The internal architecture of the UQS expects this to be present.

DoExecute()
Notice the
**
DoExecute()
**
 method, which will be called through a base class's method by applying the

**
[https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern](
https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern
)
**

##
Registering Custom Functions

In order for the UQS to be able to instantiate this new function later on at runtime, it needs a factory that knows about this specific function and how to create an instance of it:

```

`
UQS::Client::CFunctionFactory<CFunction_Vec3Add>::SCtorParams ctorParams;
ctorParams.szName = "std::Vec3Add";
ctorParams.guid = "5f4dd307-e32a-450c-a002-3c0e1cad490c"_uqs_guid;
ctorParams.szDescription = "Adds two Vec3s and returns the result.";

// Notice: This instance of CFunctionFactory<> must _not_ go out ouf scope for the lifetime of UQS,
//         since the UQS core will keep a pointer to this particular factory!
static const UQS::Client::CFunctionFactory<CFunction_Vec3Add> functionFactory_Vec3Add(ctorParams);
`

```

To finally expose your new function factory to the UQS core, the you'd just call this static helper method once receiving the
`
UQS::Core::EHubEvent::RegisterYourFactoriesNow
`
 event:

```

`
UQS::Client::CFactoryRegistrationHelper::RegisterAllFactoryInstancesInHub();
`

```

This is the same process as is already done when exposing item factories to the UQS core.

[#function-hierarchies](
Function Hierarchies
)
[#built-in-functions](
Built-in Functions
)
[#example-function-vec3add](
Example Function: Vec3Add()
)
[#registering-custom-functions](
Registering Custom Functions
)
