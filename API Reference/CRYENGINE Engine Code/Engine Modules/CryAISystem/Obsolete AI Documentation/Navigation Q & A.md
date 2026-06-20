# Navigation Q & A

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306453
- Page ID: 23306453
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Navigation Q & A
- Parent: Obsolete AI Documentation

## Content

### Big triangles and small links between them

**Q: I have created a big flat map, placed an AI (actor) on it, and generated AI navigation triangulation. I noticed that the AI doesn't always take the shortest straight path from point A to point B. Why?**

A: To illuminate the issue, you can use:

- - **ai_DebugDraw 74**, which shows AI navigation triangulation. ** ai_DebugDraw 79**, which is faster, will not suffice here, because it shows only local, close parts of the triangulation.
- **ai_DrawPath all**, which shows paths AIs take; additionally, it shows "links" - the corridors between adjacent triangles.
- **Ruler** tool of the Editor (between ** Snap Angle** and ** Select Object(s)**) to visualize paths - so you don't even need actual AIs on the map for the experiments.

The AI navigation triangulation is intended to be fast and have a small memory footprint. One of the decisions made in this regard is using 16-bit signed integers for storing corridor ("link") radius in cm between two adjacent triangles. So the maximum radius is 32767 cm = 327.67 m. And when an AI has to go to another triangle, it can only go through this corridor, which is naturally very narrow if the triangles are still gigantic. Also, it follows that the problem doesn't exist for triangles with edges less than 2 * 327.67 = 655.34 m

So the problem can only appear at a very, very initial stage of map development. Every Forbidden Area, every tree - basically, every map irregularity makes triangulation more developed, i.e. having more triangles, smaller in size, thus eliminating the problem.

### Path Following

**Q: But how path following actually works? Where to start?**

A: Try [Path Following](Path%20Following.md).

### Auto-disable

**Q: How to keep patrols always active, regardless of the distance to the player?**

A: Please consult [Auto-disable](../Auto-disable.md).
