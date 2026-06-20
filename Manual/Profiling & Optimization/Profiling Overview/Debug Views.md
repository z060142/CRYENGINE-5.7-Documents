# Debug Views

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308523
- Page ID: 23308523
- Breadcrumb: Profiling & Optimization > Profiling Overview > Debug Views
- Parent: Profiling Overview

## Child Pages

- [Overdraw-complexity Debug View](Debug%20Views/Overdraw-complexity%20Debug%20View.md)

## Content

### Overview

This topic describes the debug views that are useful for debugging art assets. Enter the console command in the console to activate the mode and display the info.

### Wireframe

**Console command:** r_wireframe 1

This will draw the entire scene in wireframe, including objects hidden from view. (Can over complicate a busy scene).

![Image](https://www.cryengine.com/docs/static/attachments/23998971)
**Console command:** r_showlines 2

This view will overlay wireframe only on the front facing geometry. Anything behind doesn't get rendered.

![Image](https://www.cryengine.com/docs/static/attachments/23998970)

Both of these images are of the exact same scene, but visually r_showlines is easier on the eye.

### Default Material Views

**Console command:** e_DefaultMaterial = 1

Applies a uniform flat grey material to every surface in the game.

![Image](https://www.cryengine.com/docs/static/attachments/23998958)

**Console command:** r_TexBindMode = 6

Applies a uniform flat grey material with normal map information, to every surface in the game.

![Image](https://www.cryengine.com/docs/static/attachments/23998972)

### Helpers

**Console command:** e_debugdraw 15

This debug draw shows all exported helpers linked to the geometry in 3ds Max, like grab helper, touch bending helper, etc.

![Image](https://www.cryengine.com/docs/static/attachments/23998961)

### Physics Mesh

**Console command:** p_draw_helpers 1

This debug draw shows physics proxy meshes additionally to the render geometry.

![Image](https://www.cryengine.com/docs/static/attachments/23998969)

### Mass, Joints, Detailed Joint Status Information

**Console command:** p_debug_joints 1

This debug draw shows the mass of objects in kg and the joint linked to the object in 3ds Max. To display joints you have to activate p_draw_helpers 1 first.

![Image](https://www.cryengine.com/docs/static/attachments/23998968)
[Wireframe](#wireframe)[Default Material Views](#default-material-views)[Helpers](#helpers)[Physics Mesh](#physics-mesh)[Mass, Joints, Detailed Joint Status Information](#mass-joints-detailed-joint-status-information)
