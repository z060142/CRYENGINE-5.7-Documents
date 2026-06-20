# View System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24283735
- Page ID: 24283735
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAction > View System
- Parent: CryAction

## Content

### Overview

The View System in CryAction keeps track of all the different views that can be created during your game runtime. It allows you to create, remove and switch between views as well as handling cutscene camera cut requests.

### CVars

The View System implements the following cvars:

name | purpose
--- | ---
cl_camera_noise | Adds hand-held like camera noise to the camera view. The higher the value, the higher the noise. (a value <= 0 disables it)
cl_camera_noise_freq | Defines camera noise frequency for the camera view. The higher the value, the higher the noise.
cl_ViewSystemDebug | Sets debug information of the ViewSystem
cl_DefaultNearPlane | Sets the default camera near plane. (default is 0,25)
