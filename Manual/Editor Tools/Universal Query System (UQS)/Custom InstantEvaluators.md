# Custom InstantEvaluators

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450490
- Page ID: 29450490
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Custom InstantEvaluators
- Parent: Universal Query System (UQS)

## Content

##
Overview

InstantEvaluators are supposed to carry out quick computations to either score an item within [0.0 .. 1.0] or to discard the item completely.

Once the item is discarded, it will be completely removed from further considerations by other evaluators in a query.

##
Tester vs. Scorer

Internally, we distinguish between 2 evaluation modalities:

-
**
Testers:
**
 are supposed to simply check if the item passes a certain condition, if not then to discard the item.

-
**
Scorers:
**
 are supposed to simply provide a score for an item, and not discard the item.
These modalities are more of a hint to a query and to decide which kind of InstantEvaluators to run first: Testers are run before Scorers. This is to potentially reduce the remaining items as early as possible in order to prevent computations on items which might get discarded anyway.

The distinction between tester and scorer is not a hard rule - InstantEvaluators can be both depending on their domain-specific knowledge. For example an InstantEvaluator that evaluates a 3D point could fulfill two purposes:

-
Discard the point if it's closer than N meters or further than M meters away from the player.

-
Score the point gradually from [0 .. 1] otherwise.
In such a case, the evaluator's modality should be set to that of a tester.

##
Cheap vs. Expensive

A higher-level of optimization means to distinguish the cost level of InstantEvaluators. The purpose is to "guesstimate" how complex their computations are. Currently, we allow InstantEvaluators to fall into 2 cost categories:
**
cheap
**
 and
**
expensive
**
. What each cost category actually means is a very subjective thing and may vary from one game project to another. A rough rule of thumb (in reference to what the UQS StdLib provides) is:

-
Cheap = something like an euclidean distance check.

-
Expensive = check for whether a point resides on the Navigation Mesh (this involves a several orders of magnitude more complex computation than just juggling around some numbers).
The distinction between cheap and expensive InstantEvaluators dictates when specific InstantEvaluators will run:

-
First, the whole batch of cheap ones will run to filter out as many items as possible and to get an idea of the most promising ones.

-
Then, during the query's expensive phase, expensive InstantEvaluators alongside DeferredEvaluators will run.
The basic idea is to have the cheap InstantEvaluators do most of the "easy" work and do some preliminary sorting by their scores. Then, looking at the top N most promising items have the expensive InstantEvaluators and DeferredEvaluators do their final work - just enough until we have come up with enough items that we can clearly identify as the final "winners".

##
Example InstantEvaluator: ScoreDistance

The InstantEvaluator shown below is actually one from the UQS StdLib.

```

`
// - scores the distance between 2 points
// - the higher the distance the better the score
// - a threshold is used as a "reference distance" for increasing the score linearly; larger distances clamp the score to 1.0

class CInstantEvaluator_ScoreDistance : public uqs::client::CInstantEvaluatorBase<
    CInstantEvaluator_ScoreDistance,
    UQS::Client::IInstantEvaluatorFactory::ECostCategory::Cheap,
    UQS::Client::IInstantEvaluatorFactory::EEvaluationModality::Scoring
>
{
public:
    struct SParams
    {
        Vec3   pos1;
        Vec3   pos2;
        float  distanceThreshold;

        UQS_EXPOSE_PARAMS_BEGIN
            UQS_EXPOSE_PARAM("pos1", pos1, "POS1", "First position.");
            UQS_EXPOSE_PARAM("pos2", pos2, "POS2", "Second position.");
            UQS_EXPOSE_PARAM("distanceThreshold", distanceThreshold, "MIND", "Minimally required distance between Pos1 and Pos2. If smaller then the item will get discarded.");
        UQS_EXPOSE_PARAMS_END
    };

    ERunStatus DoRun(const SRunContext& runContext, const SParams& params) const
    {
        // guard against potential div-by-zero and other weird behavior
        IF_UNLIKELY(params.distanceThreshold <= 0.0f)
        {
            runContext.error.Format("param 'distanceThreshold' should be > 0.0 (but is: %f)", params.distanceThreshold);
            return ERunStatus::ExceptionOccurred;
        }

        const float distanceBetweenPoints = (params.pos1 - params.pos2).GetLength();
        runContext.evaluationResult.score = std::min(distanceBetweenPoints, params.distanceThreshold) / params.distanceThreshold;

        return ERunStatus::Finished;
    }
};
`

```

SParams
Notice that each custom InstantEvaluator class
**
must
**
 come with an
**
SParams
**
 struct. The internal architecture of the UQS expects exactly such an embedded struct.

DoRun()
Notice the
**
DoRun()
**
 method, which will be called through a base class's method by applying the

**
[https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern](
https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern
)
**

##
Registering InstantEvaluators

In order for the UQS to be able to instantiate this new InstantEvaluator later at runtime, it needs a factory that knows about this specific class and how to create an instance of it:

```

`
UQS::Client::CInstantEvaluatorFactory<CInstantEvaluator_ScoreDistance>::SCtorParams ctorParams;
ctorParams.szName = "my::ScoreDistance";
ctorParams.guid = "33161269-cd59-40ab-ad39-a0f561c28eeb"_uqs_guid;
ctorParams.szDescription = "Scores the distance between 2 points.\nThe higher the distance the better the score.\nA threshold is used as a 'reference distance' for increasing the score linearly; distances larger than that will clamp the score to 1.0.";

// Notice: This instance of CInstantEvaluatorFactory<> must _not_ go out of scope for the lifetime of UQS,
//         since the UQS core will keep a pointer to this particular factory!
static const UQS::Client::CInstantEvaluatorFactory<CInstantEvaluator_ScoreDistance> instantEvaluatorFactory_ScoreDistance(ctorParams);
`

```

To finally expose your new InstantEvaluator factory to the UQS core, you'd just call this static helper method once receiving the
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

[#tester-vs-scorer](
Tester vs. Scorer
)
[#cheap-vs-expensive](
Cheap vs. Expensive
)
[#example-instantevaluator-scoredistance](
Example InstantEvaluator: ScoreDistance
)
[#registering-instantevaluators](
Registering InstantEvaluators
)
