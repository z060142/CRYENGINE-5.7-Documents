# Cluster Detector

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306460
- Page ID: 23306460
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Cluster Detector
- Parent: CryAISystem

## Content

### Overview

The **cluster detector** is a new service offered by the AI System to detect clusters of point in space.

The cluster detector uses a modified version of the K-mean algorithm to try to find a good subdivisions of the points into separate groups that satisfy specific properties.

Currently it's used in connection with the **AISquadManager** to group the different AI agents into dynamic squads.
