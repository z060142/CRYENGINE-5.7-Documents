# Effect System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24283706
- Page ID: 24283706
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAction > Effect System
- Parent: CryAction

## Content

### Overview

The Effect System manages a list of predefined CEffects. Those effects can include 3DEngine parameters and/or particles or other engine components. The System itself takes care of activating, updating and deactivating them in one central place.

### Initialization

The Effect System is created during the initialization of CryAction. It will get intialized right away and register your predefined effects.
