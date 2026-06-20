# Mannequin Track Properties

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308450
- Page ID: 23308450
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Track Properties
- Parent: Mannequin Editor

## Content

##
Overview

[Image: /docs/static/attachments/23998319]

Within the different sub sections of mannequin (
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-FragmentEditor](
Fragment Editor
)
,
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-previewer](
Previewer
)
 or
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-TransitionEditor](
Transition Editor
)
), you can find a panel listing the tracks. This panel has some additional functionality, as described below.

##
Muting Scopes & Tracks

[Image: /docs/static/attachments/23998323]

(CRYENGINE 3.7 and above only)

The green "dots" to the right of the track names can be used to mute scopes or individual layers. Right click on them to bring up their context menu to control this. The color of the dot becomes grey when a layer or scope is muted.

##
Adding/Removing Layers

[Image: /docs/static/attachments/23998320]

(not available in

[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-previewer](
Mannequin Previewer
)
)

Use the context menu of a scope or layer to add new layers (aka tracks). You can add as many proclayers as you like, but the number of animlayers is limited by how the scope is set up (see 'numLayers' in
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File
)
).

Use the context menu of a layer to remove it.

##
Change Context

[Image: /docs/static/attachments/23998317]

Only available in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-previewer](
Previewer
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-TransitionEditor](
Transition Editor
)
.

You can set the data inside a scope context using the Change Context option in the context menu of a scope.

The available options are configured in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308457](
Context Editor
)
, and saved in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-previewer](
Previewer
)
. For the example above we have the following option setup for the scope context "Weapon":

[Image: /docs/static/attachments/23998321]

As both the scopes "Weapon" and "WeaponForceFeedback" are using the scope context "Weapon", both will change. For example if we select "Shotgun" from the context menu, the result is the following:

[Image: /docs/static/attachments/23998318]

Note that the UI currently doesn't show the scope context, it only shows the names of the Scopes ("Weapon", "WeaponForceFeedback") and the names of the option selected into them ("Shotgun").

##
Include/Exclude Scope

[Image: /docs/static/attachments/23998322]

(only available in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-FragmentEditor](
Mannequin Fragment Editor
)
)

This is an advanced feature with which you can override the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450861](
Scopemask
)
 for specific fragments.

For example: Say all fragments within the Reload fragmentID play on the scopes Torso3P. But for a rocket launcher you might want to use FullBody3P+Torso3P instead. For this you need an "override", which becomes an "override element" in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File
)
.

You can create or edit an override for the current fragment by selecting Include/Exclude Scope in the context menu of a scope. Note that you can make more complicated setups manually in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File
)
 than you can make using this simple Include/Exclude interface. You could for example make an override for the tag "rifle" even though there is no fragment which only has "rifle" in its tagstate.

This feature can behave in a counter intuitive way:

-
In the above screenshot if you would do "Include Scope" on the Audio1 scope, the fragment that was playing on the Audio2 scope before would move onto the Audio1 scope. This is because the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308439](
Fragment Selection Process
)
 first gives Audio1 a chance to pick a fragment. And Audio2 won't be considered anymore because there already is another scope enabled on that scope context, and there can only be one. (both Audio1 and Audio2 are on the scopecontext Audio)

-
Similarly: in the above screenshot if you would do "Include Scope" on the Torso3P scope, the Torso3P scope disappears! This is because both FullBody3P and Torso3P run on the same scope context: Char3P. There already is a fragment assigned to FullBody3P, which comes first in the list, so Torso3P will not get a fragment anymore. The UI hides the scope in this case.
In both of these cases you can make sure the scopes never disappear by giving them a Scope Tag. Scope Tags are described in the document
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308435](
Mannequin TagState
)
.

There is no simple way in the editor at the moment to Exclude Scope once you accidentally Included it and it disappears as in the above examples. You can revert the file (Undo Changes to Selected Files in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308448](
File Manager
)
). Or you will have to edit the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File
)
 manually and remove the <override> section the editor added.

In a future release the idea of 'overrides' will be simplified and made more explicit.

[#muting-scopes-and-tracks](
Muting Scopes & Tracks
)
[#addingremoving-layers](
Adding/Removing Layers
)
[#change-context](
Change Context
)
[#includeexclude-scope](
Include/Exclude Scope
)
