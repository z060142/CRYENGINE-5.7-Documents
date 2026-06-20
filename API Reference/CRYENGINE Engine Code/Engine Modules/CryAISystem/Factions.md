# Factions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306494
- Page ID: 23306494
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Factions
- Parent: CryAISystem

## Content

### Overview

AI use factions to determine their behavior when encountering other AI. This is a base set of behaviors such as neutral, friendly and hostile.

When an AI on the "Grunt" faction encounters an AI on the "Players" faction, the encounter will be hostile. Players encountering Civilians will be friendly, etc.

Factions are set in the properties of the [AI entity](/docs/static/engines/cryengine-3/categories/1114113/pages/1048711). You can also set factions via [Flowgraph](/docs/static/engines/cryengine-3/categories/1114113/pages/1048879).

### Setup

Currently, the CRYENGINE SDK has the following faction setup included by default: `GameSDK\Scripts\AI\Factions.xml`

```
<Factions>

<Faction name="Players">
<Reaction faction="Grunts" reaction="hostile" />
<Reaction faction="Civilians" reaction="friendly" />
<Reaction faction="Assassins" reaction="hostile" />
</Faction>

<Faction name="Grunts">
<Reaction faction="Players" reaction="hostile" />
<Reaction faction="Civilians" reaction="neutral" />
<Reaction faction="Assassins" reaction="hostile" />
</Faction>

<Faction name="Assassins">
<Reaction faction="Players" reaction="hostile" />
<Reaction faction="Civilians" reaction="hostile" />
<Reaction faction="Grunts" reaction="hostile" />
</Faction>

<Faction name="HostileOnlyWithPlayers" default="neutral">
<Reaction faction="Players" reaction="hostile" />
</Faction>

<Faction name="Civilians" default="neutral" />
<Faction name="WildLife" default="neutral" />

</Factions>
```
