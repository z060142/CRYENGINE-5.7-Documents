# Double-Buffered Physical Entity Coordinates

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/44964142
- Page ID: 44964142
- Breadcrumb: Physics > Double-Buffered Physical Entity Coordinates
- Parent: Physics

## Content

## Overview

This feature can be useful for instant raytracing of fast-moving objects. Normally, a physics proxy will be one frame ahead of the render geometry due to multithreading, which means aiming at the render proxy can miss. Also, *pe_status_pos* will be guaranteed to return the same coordinates that were set by a preceding * pe_params_pos*, even if the command was queued and hasn't been fully executed yet.

This feature optionally keeps a second set of top-level entity coordinates (pos+quat) that is synchronized to the main set when a logged poststep event is sent (in the main thread), meaning it's in sync with the main CEntity coordinates. World queries (RWI, PWI, GEA) can optionally do tests using these coordinates. Also, *pe_params_pos* requests modify them instantly, and * pe_status_pos* can optionally read them instead of the main coordinates *(meaning that SetParams(pe_params_pos*); * GetStatus(pe_status_pos)*; will return the updated position even if * SetParams* was queued).

## Usage

To enable double buffering for a specific entity, *pe_params_pos.doubleBuffCords* must be set.

For character skeletons, it must be set for both *CLiving host* and the character itself.
To use these coordinates in RWI, PWI, and GEA,*ent_use_sync_coords* must be set in * objtypes*. To use them in * pe_status_pos, status_use_sync_coords* must be set in flags. By default sync coords are not enabled and not used.
