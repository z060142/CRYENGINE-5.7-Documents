# Custom Generators

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450488
- Page ID: 29450488
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Custom Generators
- Parent: Universal Query System (UQS)

## Content

##
Overview

The purpose of generators is to create a set of "items" that will be evaluated by the query.

Generators can run over multiple frames, if the generation process of those items is expensive or relies on external systems.

##
Example Generator: PointsOnPureGrid

The generator shown below is actually one from the UQS StdLib.

```

`
// - generates points on an imaginary grid
// - the grid is specified by a center, size (of one edge) and a spacing between the points
class CGenerator_PointsOnPureGrid : public UQS::Client::CGeneratorBase<CGenerator_PointsOnPureGrid, Vec3>
{
public:
    struct SParams
    {
        Vec3   center;   // center of the grid
        float  size;     // length of one edge of the grid
        float  spacing;  // space between individual points on both, the x- and y-axis

        UQS_EXPOSE_PARAMS_BEGIN
            UQS_EXPOSE_PARAM("center", center, "CENT", "Center of the grid.");
            UQS_EXPOSE_PARAM("size", size, "SIZE", "Length of one edge of the grid.");
            UQS_EXPOSE_PARAM("spacing", spacing, "SPAC", "Space between individual points on both the x- and y-axis.");
        UQS_EXPOSE_PARAMS_END
    };

public:
    explicit CGenerator_PointsOnPureGrid(const SParams& params)
        : m_params(params)
    {}

    EUpdateStatus DoUpdate(const SUpdateContext& updateContext, client::CItemListProxy_Writable<Vec3>& itemListToPopulate)
    {
        const float halfSize = (float)m_params.size * 0.5f;

        const float minX = m_params.center.x - halfSize;
        const float maxX = m_params.center.x + halfSize;

        const float minY = m_params.center.y - halfSize;
        const float maxY = m_params.center.y + halfSize;

        std::vector<Vec3> tmpItems;

        for (float x = minX; x <= maxX; x += m_params.spacing)
        {
            for (float y = minY; y <= maxY; y += m_params.spacing)
            {
                tmpItems.emplace_back(x, y, m_params.center.z);
            }
        }

        itemListToPopulate.CreateItemsByItemFactory(tmpItems.size());
        for (size_t i = 0; i < tmpItems.size(); ++i)
        {
            itemListToPopulate.GetItemAtIndex(i) = tmpItems[i];
        }

        return EUpdateStatus::FinishedGeneratingItems;
    }

private:
    const SParams m_params;
};
`

```

SParams
Each custom generator class
**
must
**
 come with an
**
SParams
**
 struct. The internal architecture of the UQS expects exactly such an embedded struct.

DoUpdate()
Notice the
**
DoUpdate()
**
 method, which will be called through a base class's method by applying the

**
[https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern](https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern)
**

##
Registering Custom Generators

In order for the UQS to be able to instantiate this new generator later on at runtime, it needs a factory that knows about this specific generator class and how to create an instance of it:

```

`
UQS::Client::CGeneratorFactory<CGenerator_PointsOnPureGrid>::SCtorParams ctorParams;
ctorParams.szName = "my::PointsOnPureGrid";
ctorParams.guid = "c93c98fa-5241-4db5-9f0e-8a35e782e675"_uqs_guid;
ctorParams.szDescription =
    "Generates points on a grid.\n"
    "The grid is specified by a center, size (of one edge) and a spacing between the points.\n"
    "Notice: this generator is very limited and doesn't work well if you intend to use it for things like uneven terrain.";

// Notice: This instance of CGeneratorFactory<> must _not_ go out of scope for the lifetime of UQS,
//         since the UQS core will keep a pointer to this particular factory!
static const UQS::Client::CGeneratorFactory<CGenerator_PointsOnPureGrid> generatorFactory_PointsOnPureGrid(ctorParams);
`

```

To finally expose your new generator factory to the UQS core, you'd just call this static helper method once receiving the
`
UQS::Core::EHubEvent::RegisterYourFactoriesNow
`
 event:

```

`
UQS::Client::CFactoryRegistrationHelper::RegisterAllFactoryInstancesInHub()
`

```

This is the same process as is already done when exposing item factories to the UQS core.

[Example Generator: PointsOnPureGrid](#example-generator-pointsonpuregrid)
[Registering Custom Generators](#registering-custom-generators)
