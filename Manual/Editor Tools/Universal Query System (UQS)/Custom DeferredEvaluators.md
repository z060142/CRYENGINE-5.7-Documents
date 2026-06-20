# Custom DeferredEvaluators

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450492
- Page ID: 29450492
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Custom DeferredEvaluators
- Parent: Universal Query System (UQS)

## Content

##
Overview

DeferredEvaluators can be used to do rather expensive computations for evaluating items.

Just like InstantEvaluators, they can either score an item within the [0 .. 1] or discard it.

The main difference to InstantEvaluators from an implementor's view is to be able to execute over multiple frames if needed.

##
Evaluation Modality and Cost Category

As opposed to InstantEvaluators, DeferredEvaluators are not categorized in terms of cost, and also don't adhere to a specific evaluation modality (tester vs. scorer).

They are implicitly treated as being expensive and therefore run during a query's expensive phase.

##
Example DeferredEvaluator: TestRaycast

eUnlike Items, Functions, Generators and InstantEvaluators there is no need for a helper base class that ensures type safety and does most of the grunt work for us. We can directly derive from the
**
uqs::client::IDeferredEvaluator
**
 interface.

```

`
// - a simple DeferredEvaluator that performs a raycast to check for line-of-sight between 2 points
// - the raycast request gets carried out by an external system

class CDeferredEvaluator_TestRaycast : public UQS::Client::IDeferredEvaluator
{
public:
    struct SParams
    {
        Vec3  from;
        Vec3  to;

        UQS_EXPOSE_PARAMS_BEGIN
          UQS_EXPOSE_PARAM("from", from, "FROM", "Start position of the raycast");
          UQS_EXPOSE_PARAM("to", to, "TO  ", "End position of the raycast");
          UQS_EXPOSE_PARAM("raycastShallSucceed", raycastShallSucceed, "SUCC", "Whether the raycast shall succeed or fail in order for the whole evaluator to accept or discard the item");
        UQS_EXPOSE_PARAMS_END
    };

private:
    // this is for keeping track of the external system that performs the raycast for us
    enum class ERaycastStatus
    {
        PendingStart,
        WaitingForRaycastResult,
        RaycastSucceeded,
        RaycastFailed
    };

    const SParams  m_params;
    ERaycastStatus m_raycastStatus;

public:
    explicit CDeferredEvaluator_TestRaycast(const SParams& params)
        : m_params(params)
        , m_raycastStatus(ERaycastStatus::PendingStart)
    {}

    virtual EUpdateStatus Update(const SUpdateContext& updateContext) override
    {
        // make a raycast request on first call
        if (m_raycastStatus == ERaycastStatus::PendingStart)
        {
            // pretend there is something like a global raycaster where we can enqueue requests and get notified once the raycast has been performed
            g_raycaster.QueueRaycast(m_params.from, m_params.to, &CDeferredEvaluator_TestRaycast::OnRaycastCallback, this);

            // from now on wait until the raycast request has been fulfilled
            m_raycastStatus = ERaycastStatus::WaitingForRaycastResult;
        }

        // has the raycast been performed by now?
        if (m_raycastStatus == ERaycastStatus::RaycastSucceeded || m_raycastStatus == ERaycastStatus::RaycastFailed)
        {
            // discard the item if the raycast failed (e. g. we don't have a line-of-sight to wherever we were trying to look at)
            if (m_raycastStatus == ERaycastStatus::RaycastFailed)
            {
                updateContext.evaluationResult.bDiscardItem = true;
            }

            return EUpdateStatus::Finished;
        }

        // keep waiting for the raycast request to get fulfilled
        return EUpdateStatus::BusyWaitingForExternalSchedulerFeedback;
    }

private:
    void OnRaycastCallback(bool bRaycastSucceeded)
    {
        m_raycastStatus = bRaycastSucceeded ? ERaycastStatus::RaycastSucceeded : ERaycastStatus::RaycastFailed;
    }
};
`

```

SParams
Notice that each custom DeferredEvaluator class
**
must
**
 come with an
**
SParams
**
 struct. The internal architecture of the UQS expects exactly such an embedded struct.

##
Registering DeferredEvaluators

In order for the UQS to be able to instantiate this new DeferredEvaluator later at runtime, it needs a factory that knows about this specific class and how to create an instance of it:

```

`
UQS::Client::CDeferredEvaluatorFactory<CDeferredEvaluator_TestRaycast>::SCtorParams ctorParams;
ctorParams.szName = "my::TestRaycast";
ctorParams.guid = "de510b26-1082-40e7-a83c-8a9083f6b641"_uqs_guid;
ctorParams.szDescription =
    "Tests a raycast between 2 given positions.\n"
    "Whether success or failure of the raycast counts as overall success or failure of the evaluator can be specified by a parameter.\n"
    "NOTICE: The underlying raycaster uses the *renderer* to limit the number of raycasts per frame!\n"
    "As such, it will not work on a dedicated server as there is no renderer (!) (Read: a null-pointer crash would occur!)\n"
    "You should rather consider this evaluator as a reference for your own implementation.";

// Notice: This instance of CDeferredEvaluatorFactory<> must _not_ go out of scope for the lifetime of UQS,
//         since the UQS core will keep a pointer to this particular factory!
static const UQS::Client::CDeferredEvaluatorFactory<CDeferredEvaluator_TestRaycast> deferredEvaluatorFactory_TestRaycast(ctorParams);
`

```

To finally expose your new DeferredEvaluator factory to the UQS core, you'd just call this static helper method once receiving the
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

[#evaluation-modality-and-cost-category](
Evaluation Modality and Cost Category
)
[#example-deferredevaluator-testraycast](
Example DeferredEvaluator: TestRaycast
)
[#registering-deferredevaluators](
Registering DeferredEvaluators
)
