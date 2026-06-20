# Tactical Point System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306474
- Page ID: 23306474
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Tactical Point System
- Parent: CryAISystem

## Content

##
Overview

##
Introduction

The Tactical Point System (TPS):

-
Allows AIs to ask intelligent questions about their environment.

-
Is a structured query language over sets of points in the world.

-
Is used for finding any relevant kind of point in the world: hidespots, attack points, navigation waypoints.

-
Optimizes queries automatically.
The language is simple, powerful, and designed to be very readable. In a (simplified) example:

```

`
hidespots_from_attentionTarget_around_puppet = 7
coverSuperior = true, canReachBefore_the_attentionTarget = true
distance_from_puppet = -1
`

```

This means:

-
Generate locations where I can hide from my attention target, within 7 meters of myself.

-
Only accept places of excellent cover, that I can get to before my attention target could.

-
Prefer those that are closest to me.
TPS uses a highly efficient method to rank points, keeping expensive operations like raycasts and pathfinding to an absolute minimum.

##
Overview

The Tactical Point System (TPS) provides the AI system with a powerful method of querying the environment for places of interest.

The main features include:

-
Use of a structured query language.

-
Powerful and quick to change, in C++ and Lua.

-
Inclusion of wide variety points:

-
Not just conventional hiding places behind hide objects.

-
Points at position of nearby entities.

-
Points along terrain features, points suggested by designers.

-
Arbitrary resolutions of nearby points in the open, on terrain.

-
Arbitrary combination of queries, e.g.:

-
Somewhere to my left ¬and¬ behind me not soft cover and not including my current spot.

-
Hidden from my attention target and visible to the companion.

-
Preferential weighting.

-
Choose the nearest to (or furthest from) me (or my target, or the companion).

-
Balance being near to me with being far from the player.

-
Prefer solid cover to soft cover.

-
Fallback options included in a query.

-
Go for good cover nearby or if none go backwards to any soft cover.

-
Query visualization.

-
See which points are acceptable and which rejected, as well as their relative scores.

-
See how many expensive tests are being used by a query and on which points.

-
Automatically optimized queries.

-
Understands relative expenses of the individual evaluations comprising queries.

-
Dynamically orders points by potential fitness, according to weighting criteria.

-
Evaluates "fittest" first, to perform expensive tests on as few points as possible.

-
Recognizes when relative fitness dictates that a point is better than any other candidate could be, further reducing evaluations.

-
Good framework for further optimization, specific to architecture, level or locale.
In terms of the code itself, rather than its use, some of the advantages of the framework include:

-
Separation of action from query.

-
Arbitrary queries can be made at any time without changing puppet state.

-
Easy to expand query language.

-
Easy adaption for time-slicing (and in principle multi-threading).

-
Progression through query is fine-grained.

-
Progress is tracked as state, so could be easily paused and resumed.

-
Mechanism for delaying expensive validity tests on generated points until needed.

##
Execution Flow

A summary of the stages in definition and execution of a TPS query.

 Note that only stages 3 and 4 are significant to performance, chiefly 4 (point evaluation).

-
Query parsing:

-
Parse query strings and values.

-
Usually performed once and cached.

-
Query request:

-
Query made from C++, ScriptBind, MBT, etc.

-
Stateless, so does not imply a movement operation.

-
Point generation:

-
Creation of a set of appropriate candidate points.

-
Based on Generation criteria of query.

-
Point evaluation:

-
Points may be rejected based on Conditions criteria.

-
Points are given relative scores based on Weights criteria.

-
By far most intensive stage.

-
Fallback queries:

-
If no point matched Conditions criteria, consider fallbacks.

-
Where there is a fallback, return to step 3.

-
Visualization:

-
If visualization is required, draw all points to screen.

-
Include data such as accepted/rejected and relative scores.

-
Query result:

-
Returns one or more requested points, if any fit query conditions.

-
Points are returned as structures describing the point chosen.
There are some possible execution-flow dependent optimizations, for instance caching any relevant query results between fallback queries.

##
C++ Interface

This is provided to allow full use of the system from other C++ code, and Lua queries are translated through it. In fact there are two C++ interfaces:

-
Internal - Just for use within the AI system:

-
Build up queries using a CTacticalPointQuery object.

-
Supports creating queries on the fly, or adapting queries on the fly.

-
Allows greater access to relevant AI system classes.

-
External - Can be used from any module:

-
Suitable or crossing DLL boundaries.

-
Simpler, not object-oriented.

-
Based on stored queries for efficiency.

-
Just as powerful.

##
Internal syntax example

```

`
// Check for shooter near cover using the TPS
static const char *sQueryName = "CHitMiss::GetAccuracy";
ITacticalPointSystem *pTPS = gEnv->pAISystem->GetTacticalPointSystem();
int iQueryId = pTPS->GetQueryID( sQueryName );
if ( iQueryId == 0 )
{
  // Need to create query
  iQueryId = pTPS->CreateQueryID( sQueryName );
  pTPS->AddToGeneration( iQueryId, "hidespots_from_attentionTarget_around_puppet", 3.0f);
  pTPS->AddToWeights( iQueryId, "distance_from_puppet", -1.0f);
}
pTPS->Query( iQueryId, CastToIPuppetSafe( pShooter->GetAI() ),vHidePos, bIsValidHidePos );

`

```

##
TPS Syntax Examples

Some parsing is obviously taking place here and this is crucial to the generality of the system.

 Here are some simple examples and their explanations – a proper grammar is given later.

`
option.AddToGeneration("hidespots_from_attTarget_around_puppet", 50.0)
`

 Given as generation criteria and supplied with a float which represents distance in this case.

 This is broken up into 5 words. "Hidespots" indicates we should generate points behind known cover in the conventional manner. "From" is just a glue word to aid readability. "Target" specifies from whom we are hiding. "Around" is, again, glue. "Puppet" specifies where we will centre our point generation. The supplied float tells us the radius from that point within which we should generate points.

Note that no raycasts are performed at this stage, and that we have here considerable flexibility in, for example, hiding from the player somewhere around the player, hiding from him somewhere near us, hiding near a friend but from the player, and indeed specifying some completely different target to hide from, such as an imagined player position, or the girl, etc. By allowing some flexibility at the generation stage we can make more powerful queries and let the user focus our computations in the right general area.

`
option2.AddToConditions("visible_from_player",true)
`

 Given as a condition so we can assume a Boolean result. Here we parse "Visible", which specifies a kind of raytest, "From" is glue, "Player" specifies who to raycast to (from the generated point). Here we specify it must be visible, which is curious but perfectly valid.

`
option2.AddToConditions("max_coverDensity",3.0)
`

 Given as a condition so we can assume a Boolean result. Here we parse "Max", which is specifies that the resulting value must be compared against the given value and must be less to be considered further. "Density" specifies a density query (to be implemented) which can measure the distance of various things such as cover objects, friendly AIs, etc. "Of" is glue, and "Cover" specifies what kind of density we are interested in.

`
option1.AddToWeights("distance_from_puppet",-1.0)
`

 Given as a weight so the result of the query will be 0-1 (this is normalized as required). Boolean queries are in fact allowed and thus allow preference (e.g. Primary over Secondary cover) – they return 0.0 for false and 1.0 for true.

 "Distance" specifies the type of query we will do. "From" is glue. "Puppet" is required to tell us where we are measuring distance from – it could be the player, the girl, etc.

##
Lua Interface

In Lua-land the way to use the TPS is through a ScriptBind.

-
**
Scriptbinds
**
 allow you to give TPS queries from a Lua behaviour and have the results returned as a table without any side-effects. This can be useful for:

-
Higher-level environmental reasoning (see "Future Plans and Possibilities"):

-
Choosing behaviors based on suitability of environment.

-
E.g., Only choose a "sneaker" behavior if there is lots of soft cover around.

-
Running final, very specific tests on a shortlist of points, rather than adding a very obscure query to the TPS system.

-
Environmental awareness.

-
E.g., Tell me three good hidepoints nearby, so I can glance at them all before I hide.

##
Query Specification

Both methods define query specifications using the same table structure. For example:

```

`
Hide_FindSoftNearby =
{
  -- Find nearest soft cover hidespot at distance 5-15 metres,
  -- biasing strongly towards cover density
  {
    Generation= {  hidespots_from_attentionTarget_around_puppet = 15 },
    Conditions= {  coverSoft = true,
       visible_from_player = false,
      max_distance_from_puppet = 15,
      min_distance_from_puppet = 5},
    Weights =   {  distance_from_puppet = -1.0,
  coverDensity = 2.0},
  },
  -- Or extend the range to 30 metres and just accept nearest
  {
    Generation ={  hidespots_from_attentionTarget_around_puppet = 30 },
    Weights =   {  distance_from_puppet = -1.0}
  }
}
AI.RegisterTacticalPointQuery( Hide_FindSoftNearby );

`

```

*
Note that registering a query returns a query id that then refers to this stored query.
*

##
Scriptbind

```

`
AI.GetTacticalPoints( entityId, tacPointSpec, pointsTable, nPoints )

`

```

*
Performs a query using an existing specification. See Scriptbind_AI.h comments for details.
*

##
Query Language Syntax

There are ways to define a query in both C++ and Lua (and potentially in XML), but the same core syntax is used. Here we formally define this language, taking the top-level units to be the Generation, Conditions or Weights that can be given. The semantics are defined in the following section. Non-terminal symbols are in bold. A few of the symbols are not yet implemented, present just for illustration.

Grammar:

```

`
Generator ::= GenerationQuery '_' 'around' '_' Object
Condition ::= BoolQuery | (Limit '_' RealQuery)
Weight    ::= BoolQuery | (Limit '_' RealQuery) | RealQuery

GenerationQuery ::= ( 'hidespots' '_' Glue '_' Object)
                      | 'grid' | 'indoor'

BoolQuery ::= BoolProperty | (Test '_' Glue '_' Object)

BoolProperty ::= 'coverSoft' | 'coverSuperior' | 'coverInferior'         | 'currentlyUsedObject' | 'crossesLineOfFire'

Test ::= 'visible' | 'towards' | 'canReachBefore' | 'reachable'

RealQuery = ::= RealProperty | (Measure '_' Glue '_' Object)

RealProperty ::= 'coverRadius' | 'cameraVisibility' | 'cameraCenter'

Measure ::= 'distance' | 'changeInDistance' | 'distanceInDirection' | 'distanceLeft' | 'directness' | 'dot' | 'objectsDot' | 'hostilesDistance'

Glue ::= 'from' | 'to' | 'at' | 'the'

Limit ::= 'min' | 'max'

Object ::= 'puppet' | 'attentionTarget' | 'referencePoint' | 'player'
    | 'currentFormationRef' | 'leader' | 'lastOp'

`

```

##
Query Language Semantics

##
Symbol Definitions

-
"Tunable" denotes that the exact values used should be possible to tweak/tune later.

-
"Real" here means that it returns a float value (rather than a boolean).

##
Generation

-
hidespots – Individual points just behind a potential cover object with respect to the "from" object; typically one point per cover object. Should eventually generate multiple points behind large cover objects and cope with irregularly shaped and dynamic objects.

-
around – Special glue word, followed by object upon which to centre the generation radius.

##
Conditions/Weight Properties (use no object)

-
Stand alone, relating to the point alone.

-
coverSoft – Boolean property, true iff this is a hidespot using soft cover

-
coverSuperior - Boolean property, true iff this is a hidespot using superior cover

-
coverInferior – Boolean property, true iff this is a hidespot using inferior cover

-
currentlyUsedObject – Boolean property, true iff this point is related to the object the puppet is already using, if any (e.g. the current hide object)

-
coverRadius – Real (float) property, representing the approximate radius of the cover object associated with this point, if any, or 0.0 otherwise. When used for tests, returns an absolute value in metres. When used as a weight, returns a normalised value, mapping the range [0.0-5.0m] to [0.0-1.0]. (Tunable)

-
coverDensity - Real property, representing the how many potential hidepoints there are close by to the point. When used for tests, returns an absolute value which is an estimate of the number of hidepoints per square metre, using a 5m radius sample. When used as a weight, returns a normalised value, mapping the range (0.0-1.0) (hidepoints per square metre) to [0.0-1.0]. (Tunable)

##
Conditions/Weight Test/Measures (require object)

-
All relate a point to a given object. E.g. distance_to_attentionTarget or visible_from_referencePoint

-
distance – Real (float) measure w.r.t. an Object, representing the straight-line distance from the point to the Object. When used for tests, returns an absolute value in metres. When used as a weight, returns a normalised value, mapping the range [0.0-50.0m] to [0.0-1.0]. (Tunable)

-
changeInDistance – Real (float) measure w.r.t. an Object, representing how much closer we will be if we move to the point. Takes the distance to the Object from here, and subtracts it from the distance to the Object from the point. When used for tests, returns an absolute value in metres. When used as a weight, returns a normalised value, mapping the range [0.0-50.0m] to [0.0-1.0]. (Tunable)

-
distanceInDirection – Real (float) measure w.r.t. an Object, representing. the distance of the point in the direction of the Object. Takes the dot product of the vector from the puppet to the point and the normalised vector from the puppet to the Object. When used for tests, returns an absolute value in metres. When used as a weight, returns a normalised value, mapping the range [0.0-50.0m] to [0.0-1.0]. (Tunable)

-
directness – Real (float) measure w.r.t. an Object, representing how much directly moving to this point would approach the Object. Takes the difference in distance to the Object achieved if we moved to the point, and divides it by the distance we would go to get there. Always uses the range [-1.0 – 1.0], where 1.0 is a perfectly direct course and negative values represent moving further away.

##
Limits

-
min | max – Limits against which to test a Real to coerce it into a Boolean. Useful for Conditions (E.g. MAX_DISTANCE = 10) which can also be used as coarse Weights (to express that a distance less that 10 is preferable, but without generalising that to favour nearer points in a more general way).

##
Objects

-
puppet – The AI making this query.

-
attentionTarget – The AI's attention target.

-
referencePoint – The AI's ref point.

-
player – The human player. (Chiefly useful for debugging, and quick hacks).

##
Glue

-
from | to | at | the – Glue words for readability. One must be present, but the parser doesn't care which. Nonetheless the user is encouraged to choose appropriately. No active function.

##
Failing queries

There are a few different ways queries can fail, and it's important to understand how each case is handled.

Firstly, where no points matched the conditions and so none can be returned, this is not a failure, but a valid result - we can carry on to fallback queries, or the AI can try a different behaviour.

Otherwise, broadly speaking, where a query doesn't make sense in the context of an individual point, this isn't an error and we try to return the "least surprising" result, but where the context of the puppet means that a query will fail on all points, this is an error, and the query should not have been made.

The failure modes are:

-
Failed queries due to point context – Sometimes a query doesn't make sense for a certain point or at a certain time. E.g.:

-
We ask "is this soft cover?" when in fact this point was generated in the open.

-
Result will be "false", since this is not any kind of cover!

-
Query names should be chosen carefully to help avoid confusion on this.

-
If this boolean value is used as a weight, it will of course return 0.

-
Failed queries due to puppet context – A query that won't make sense on this puppet, at this time for any point. E.g.:

-
We ask "am I visible to my attention target?" when I do not have an attention target.

-
This could return false, but it would disqualify every point.

-
Usually will indicate a code error – we thought they would have this attention target at this point, but in fact they don't.

-
Is flagged as a code error.

-
Also "generate hidespots from my attention target" would cause exactly the same problem but at the generation phase – and is flagged as an error likewise.

-
Failed queries due to code error – We can test for errors in TPS queries themselves and raise them there also – e.g. a query or combination that hasn't been fully implemented yet, or as a kind of assert to test variables.

##
Point Generation

##
Purpose

To generate a set of points for consideration.

##
Input

Specifications of what kind of points we're interested in.

 Need a central position to find points around – e.g. the puppet itself, att target, given position, etc.

 For some generation queries, we need a secondary object – e.g. a target to hide from.

##
Work

Hence we start by generating points to consider. They fall into two types:

-
**
Hidepoints
**
 – generated from:

-
Hideable objects.

-
Requires a position to hide from.

-
We generate final positions here, for instance calculating position behind the cover.

-
Just using the object and delaying finding the actual point is a possibility.

-
**
Open points
**
 – generated according to requested specification:

-
Usually on terrain, but potentially on surfaces etc.

-
Resolution/pattern (, say, triangular with 1m spacing).

-
Could potentially perform more general sampling to find an exact point, but an initial resolution would still be required.

-
Radial/even distributions.
Multiple point generation criteria can be used, for instance generating around myself and my attention target.

##
Output

A list of point objects, giving position and simple relevant meta data (like any associated hide object).

##
Point Evaluation

##
Purpose

Here we try to establish the "fitness" of each point – that is, how well it matches the desired criteria. We wish to choose one good point, or the top n good points.

##
Input

The list of candidate points from the Generator. The point evaluation criteria, which are of two types:

-
Boolean – criteria which include or exclude a point independently of any other points.

-
Weight – criteria which combine to give a measure of fitness relative to other points, assuming that the Boolean factors include the point.

##
Work

To test the points against the specification and find an adequately good point as fast as possible.

 Often "adequately good" can mean "the best" but there's a lot of potential for optimizing if we allow a user-specified degree of uncertainty.

The order of evaluation is crucial to efficiency and is non-trivial. I hope this description at least gives the flavour of it.

The rough scheme is:

-
Cheap Booleans – on the order of one function call or some vector arithmetic.

 E.g. Is this a primary or secondary hidespot? Is it less that 5m from target?

-
Cheap Weights – similar expense.

 E.g. Closeness to player * 3 + Leftness * 2.

-
Expensive Booleans – expensive yes/no queries, probably 100 times costlier.

 E.g. Is this visible from the player? (raytest).

-
Expensive Weights – similar expense.

 E.g. Nearby hidepoint density * 2.
The strategy behind this is to minimize the number of expensive evaluations.

-
The cheap Booleans allow us to completely discount many points without significant cost.

-
The cheap Weights allow us to gauge likelihood that a given point will eventually be the optimal choice, and reduce the number of expensive tests we require.

-
Expensive Booleans are then good choices as they will eliminate points from further tests.

-
The expensive weights are the final stage, that we seek to reduce as far as possible.

##
Algorithmic details

It turns out that we can go further with this, by interleaving the last two steps and making evaluation order completely dynamic.

Unlike Conditions, Weights don't explicitly discount points from further evaluations. However, by tracking the relative "fitness" of points during evaluation, we can still employ Weights to dramatically reduce evaluations. The basic principles are:

-
We should evaluate points in order of their maximum possible fitness, so that we fully evaluate the optimal point as soon as possible.

-
If we can establish that, given Weights computed so far, a point is better than any other point could be, then we should complete its Conditions immediately. If it passes them all then we need not evaluate any other points further, and need not evaluate any remaining weights on this point – we already know it is optimal.
The implementation is based on a heap structure that orders points according to their maximum possible fitness and tracks the evaluation progress of each point separately. Each Weight evaluation collapses some of the uncertainty around the point, adjusting both the minimum and maximum possible fitness. If the Weight evaluation scored highly, the maximum will decrease a little and the minimum increase a lot; if it scored badly the maximum will decrease a lot and the minimum increase a little.

In each iteration we do the next most expensive evaluation on the point at the top of the heap and then re-sort it into place if necessary. If it occurs that we've completed all evaluations on a point, and it still has the maximum possible fitness, then it must be the optimal point. In this way we can tend towards evaluation of the optimal point with relatively few evaluations on all the others.

##
Output

A point, or n points, with the potential to request all the metadata that lead to it's choice. Hence behaviors can adapt their style to reflect the nature of the hidepoint they received

##
Integration with the Modular Behavior Tree system

From inside the Modular Behavior Tree, one can use the
**
<QueryTPS>
**
 node to call predefined TPS queries by their name. If the query succeeds, then the <QueryTPS> node will return Success, otherwise Failure. The most common usage pattern of the <QueryTPS> node goes along in conjunction with the
**
<Move>
**
 node inside a
**
<Sequence>
**
.

```

`
<Sequence>
    <QueryTPS name="SDKGrunt_TargetPositionOnNavMesh" register="RefPoint"/>
    <Move to="RefPoint" speed="Run" stance="Alerted" fireMode="Aim" avoidDangers="0"/>
</Sequence>
`

```

Here, we're making a call to the predefined TPS query "
**
SDKGrunt_TargetPositionOnNavMesh
**
" and if it succeeds, we will move to the queried position. That TPS query could look like this:

```

`
AI.RegisterTacticalPointQuery({
    Name = "SDKGrunt_TargetPositionOnNavMesh",
    {
        Generation =
        {
            pointsInNavigationMesh_around_attentionTarget = 20.0
        },
        Conditions =
        {
        },
        Weights =
        {
            distance_to_attentionTarget = -1.0
        },
    },
});
`

```

##
Future Plans and Possibilities

##
Higher-level environmental reasoning

This is more about one possible use of the TPS than future plans for the implementation.

Rather than just using the TPS to choose a point and go to it, there is potential for some nice environmental deduction based on its results.

For example: The player runs around a corner and when the AI puppet follows, he is no longer visible. The puppet queries the TPS for places he would choose to hide from himself.

-
TPS returns that 1 hide point is much better than any other. This is because there is a single large box in the middle of an empty room. AI assumes the player is there and charges straight at the box, firing.

-
TPS returns that there are several good hiding places. This is because we're just come to a stand of good cover trees. We store all the hidespots in a group blackboard, and I (and my buddies, if I have some) cautiously approach each spot in turn to discover the player.
Obviously these require some extra code, but it becomes much easier when built upon the TPS.

##
Sampling methods

When generating points in the open, here I have only proposed that we generate points in a grid or radially around objects and treat each point individually. This is really a very trivial sampling method. Where an area must be sampled, we can usually assume some kind of coherency in the evaluation functions and so could use some adaptive sampling approaches instead.

##
Dynamic cost evaluation

The must crucial aspect of optimizing the TPS will actually be adjusting the relative expense function of queries. The costs of evaluations will vary across platforms, different levels, and even locations within levels, as well as changing over time as the code changes. Making sure that the order is correct is crucial, or more expensive evaluations will be favored over cheaper ones.

Essentially, we will need to profile the evaluation function in all these difference circumstances – which suggests and automatic profiling solution at run-time.

Ideally, the relative weighting of Weight criteria should also be considered – that is, a cheaper query may not be worth doing first if it only contributes 10% of the final fitness value, and an expensive query that contributes 90% may actually save many other evaluations.

##
Relaxing the optimality constraint

As described earlier, while evaluating points we always know both the maximum and minimum potential fitness at every stage – error bounds, or the relative uncertainty we have about the point.

We could relax the optimality constraint and accept a point when we know that no other point could be significantly better. For example, the minimum potential fitness of this point may be less than, say, 5% lower than the maximum potential fitness of the next best point. Hence we might stop evaluation early and yield a further performance saving.

[#introduction](
Introduction
)
[#execution-flow](
Execution Flow
)
[#c-interface](
C++ Interface
)
[#lua-interface](
Lua Interface
)
[#query-language-semantics](
Query Language Semantics
)
[#point-generation](
Point Generation
)
[#point-evaluation](
Point Evaluation
)
[#integration-with-the-modular-behavior-tree-system](
Integration with the Modular Behavior Tree system
)
[#future-plans-and-possibilities](
Future Plans and Possibilities
)
