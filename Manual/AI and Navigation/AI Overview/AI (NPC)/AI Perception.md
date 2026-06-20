# AI Perception

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29798764
- Page ID: 29798764
- Breadcrumb: AI and Navigation > AI Overview > AI (NPC) > AI Perception
- Parent: AI (NPC)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933200)

##
Overview

In this tutorial we're going to take a look at how to setup custom AI perceptions with some basic level markup and
[Flow Graph](/docs/static/engines/cryengine-3/categories/1114113/pages/1048897)
.

Before we begin, it's worth clarifying that CRYENGINE's AI system has two main perceptions: Audio, being what the AI can hear and Visual, being what the AI can see.

There are additional auxiliary systems such as 'bullet rain' which is the perception of bullets passing the AI nearby, these add to the AI's behavior, interests and overall believability.

##
Sections

[Sections](#sections)
[Flow Graph](#flow-graph)
[AI Anchors](#ai-anchors)

##
Flow Graph

There are numerous AI nodes available in Flow Graph to tweak the AI's behavior. The one we're going to look at now is
**
AI:PerceptionScale
**
.

This is a basic per-entity node with which you can control the perception of an individual AI, using both Audio and Visually. If you want to control the perception of all AI in the level, you can use
**
AI:AIGlobalPerceptionScale
**
, which can also be filtered down by Factions.

For now we'll stick with the first node as we're just going to deal with one AI character. Go ahead and
[setup your level ready for AI](/docs/static/engines/cryengine-3/categories/1114113/pages/11239886)
 and drop an AI character into the level.

Add your AI as the node input and add a basic input key trigger as follows:

Here's what the graph is doing step by step:

-
On Game:Start, enable the InputKey node and SetNumber to 0.

-
SetNumber 0 then Triggers the PerceptionScale node and sets both Visual and Audio values to 0 while displaying the current value on screen.

-
When the 'p' key is pressed the Sequentializer then sets the SetNumber to 0.5 which sets the AI perception to 50%.

-
Press 'p' again and it sets it to '1' for the standard 100% perception scale.
You can now jump in game and the AI character will not be able to see or hear you, unless you shoot near them, in which case their perception will be overridden by the aforementioned 'bullet rain' system.

For 100% oblivious AI, use the
**
ai_ignorePlayer
**
 CVar.

Go ahead and try setting the AI perception to 0.5 and see how the AI reacts differently compared to the full '1' value.

By using more gameplay applicable logic, such as Area/Proximity Triggers, you can fine-tune stealth gameplay areas and obtain more control over AI where you want them to be more, or less aware of the player.

*
Depending on your scene, you'd probably need to Logic:Gate some of those conditions
*

##
AI Anchors

Another method of controlling AI perception is by the use of
[AI Anchors](/docs/static/engines/cryengine-3/categories/1114113/pages/1048823)
. Unlike the above Flow Graph method which relies on logic, this method relies on object placement and level markup.

Add an AI Anchor into your level via
**
RollupBar -> Objects -> AI -> AIAnchor
**
 and then click on the '
**
...
**
' for the AnchorType parameter.

Built into the default available list are 4 "LightSpot" anchor types:

LIGHTSPOT_* type

 |
CVar

 |
CVar default value

 |

**
LIGHTSPOT_SUPERDARK
**

 |
"ai_SightRangeSuperDarkIllumMod"

 |
0.25

 |

**
LIGHTSPOT_DARK
**

 |
"ai_SightRangeDarkIllumMod"

 |
0.5

 |

**
LIGHTSPOT_MEDIUM
**

 |
"ai_SightRangeMediumIllumMod"

 |
0.8

 |

**
LIGHTSPOT_LIGHT
**

 |
(not explicitly handled by a cvar)

 |
1.0

 |

These four anchor types give you a decent amount of flexibility when it comes to just how perceptive you want the AI to be. They're also tied to the above mentioned CVars which can be tweaked further if needed.

For now, select the LIGHTSPOT_SUPERDARK option to get the most effect. You'll also need to set a radius value, try '5', for a 5 meter radius. You'll notice you now get a visual radius if you have Helpers enabled (Shift + Space).

One more thing you need to do is enable the
**
 IsAffectedByLight
**
 parameter under 'Perception' on the AI character.

What all of this means is the AI will have limited visibility inside this radius. If the player is inside this radius then they will have a lower perception of them.

One thing to keep in mind is that visual light, either entities or the Sun, actually plays no role in this because the computation required and performance loss would be huge. This is why its faked through anchors rather than being based off actual lighting.

Remember with the all-powerful
**
Entity:PropertySet
**
 node you have the ability of tweaking radius and other options on-the-fly via Flow Graph too.
