# Automatic Generation of Breakable Joints in Sandbox

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308033
- Page ID: 23308033
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Interactive Geometry > Breakable Objects > Automatic Generation of Breakable Joints in Sandbox
- Parent: Breakable Objects

## Content

### Overview

Automatic joints generation allows you to take a compound (multiple node) cgf and generate joints between its touching parts, and also use a break template to pre-break an arbitrary mesh part. This is done by placing several Physics/JointGen entities around an entity or a brush, and applying Modify/Physics/Generate Breakable Joints on it. It will offer to save a new cgf if everything went well, and replace the original object with a broken version so that it can be immediately tested in game (to repeat breaking, reload script is necessary).

JointGens should be placed at specific points hitting which with a specified impulse should result in some breaking (as a reference, SDK pistol has impulse around 130). Additionally, JointGen can specify a break template cgf for each source part (if there are several templates for one part, the one with the longest name will be used). Break template is something that looks like this (on the right the parts are deliberately pushed apart a bit):

![Image](https://www.cryengine.com/docs/static/attachments/23994772)

i.e. it’s essentially a pre-broken box. In this case it’s a very simple tessellation, but it can be as complex as a pre-broken AAA-quality asset. When applied to a source mesh, it does a Boolean intersect for all template parts.

Here's a full list of JointGen's properties:

Property | Description
--- | ---
**BreakTemplate** | A cgf file that contacts the break template. example: [broken_cube.cgf](/docs/static/attachments/23994774) (note - it has no material). Some CryEngine versions can have problems with immediate cgf loading, so as a precaution have that cgf loaded in a separate asset on the level (just to make sure it's loaded). Alternatively, set e_StreamCgf to 0 before using the feature.
**Material** | Optional material override for the break template (must be a.mtl file). example: [break_tpl.mtl](/docs/static/attachments/23994773)
**Alignment** | Allows to specify the alignment of the break template relative to the source object's node. For random alignment, AlignmentSeed can be used to make random numbers reproducible (if several JointGens affect the source object, either only one of them should have a seed, or all seeds must be the same)
**ForceEntityPieces** | Equivalent to adding 'entity' keyword to each tpl piece's UDP. Use it if you have problems with particles for one reason or another
**Hierarchical** | Enables hierarchical breaking for cut parts (generated pieces will remain hidden until any of them break, which is good for performance).
**Impulse** | An impulse of this strength, applied at the jointgen's location directed towards the source's surface, will cause breaking
**radius** | Radius of the sphere used to check collisions with the source object
**scale** | By default, the template's longest and shortest dimensions are aligned with that of the source piece and scaled to be a little bit larger. This scale can apply additional scaling if necessary
**offset** | Optional template offset relative to the aligned position (can be used if the default position produces unwanted results)
**Timeout** | Pieces can be made to disappear after this timeout (0 disables)
**TimeoutInvis** | Similar to Timeout, but only ticks when a piece is invisible
**TimeoutMaxVol** | Disables Timeout on pieces with volume larger than this
**TimeoutVariance** | Applies randomness to pieces' timeouts (specified in fractions of 1, i.e. Timeout 10 with variance 0.2 gives the range 8..12)

Pre-broken template pieces can (and, for complex meshes, should) have phys proxies, which can be just simplified versions of the render meshes, but can also be primitives (only one per piece though). If a piece is fully inside the source mesh, the proxy (and the render mesh) will be used as it is, and if it intersects the source, the piece’s proxy will be Boolean-intersected with the source’s proxy (*if* the piece’s proxy is either a mesh or a box; otherwise its intersected render mesh will be physicalized).

For each JointGen, it will compute the threshold scaling for all joints that would result in *some* breakage when hit at that point, and then ‘average’ between the solutions (if there are several JointGens), with each solution having more weight around the corresponding JointGen. Initially all joints have strength proportional to the contact area between the corresponding pieces. The pieces are supposed to ‘touch’ each other, but they don’t need to penetrate since the intersection is computed with a bit of extra scaling.

Source parts and template pieces can have masses specified in node UDPs. For parts that are broken with templates, source mass is re-distributed between pieces based on volumes. If template pieces have explicit masses, however, they’ll override this (i think it mostly makes sense to set 0 masses in templates to mark ‘ground’ pieces). As usual, masses are relative, so when used in an entity with a specific mass, piece masses are scaled to match the total.

Once the joints are generated, they can immediately be tested in game in the original entity/brush. It's useful to have the corresponding physics helpers enabled during testing, and **p_debug_joints**, which will show pieces' masses and joints' hit-points. Also, generation outputs the summary report in the log.

In case of cutting, both the source mesh and break templates must use multi-sub-materials. Additionally, each source piece that's being cut and each template piece must use a single sub-material slot. Normally, Boolean intersection will append the template's sub-material to the source (unless it's already there). If the source material is outside a pak, it will be saved automatically if the.cgf is saved.

Attached is a[jg_pillar.grp](/docs/static/attachments/26517143) that can be placed on a level. It uses attached[jg_sample.zip](/docs/static/attachments/26517144).
