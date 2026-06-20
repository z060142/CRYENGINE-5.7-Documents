# Mannequin Trumping

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450863
- Page ID: 29450863
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Trumping
- Parent: Mannequin Concepts

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934033)

#### Trumping

There is a certain complication which we have carefully avoided until now. When the game requests FragmentIDs, it is not guaranteed that the new fragment will immediately start. It is possible that the default transition between the previous fragment and the new fragment will delay the selection of the fragment. For example to finish an animation, or to wait until the correct foot is on the ground. In some cases this is fine, in other cases you really want to play the new fragment immediately. And this is what we call *Trumping*: basically just skipping the waiting period.

This can be simulated in the previewer too. Let's set up a little scenario where this happens.

Open the Idle (kneeling+tired) fragment up in the fragment editor.

- Just in case: Double check the fragmentID...
- ...and make sure you have the correct variation, kneeling+tired, selected.
- Select the first animation clip and uncheck the Looping setting.

![Image](https://www.cryengine.com/docs/static/attachments/23998471)

Now go back to the previewer and look at a simple sequence (if you lost your sequence just drag the "Idle (Kneeling+Tired)" and "Moving" fragments into the previewer again as before.

You might need to move the "Move" FragmentID key a bit to get exactly what is shown in the screenshot below, but you should notice that now the move animation is *delayed*!

![Image](https://www.cryengine.com/docs/static/attachments/23998472)

This means that the new animation only starts after the previous one has ended. This is the default behavior for non-looping fragments. Up until now we didn't set up sequences with non-looping fragments so it simply didn't show up yet.

It also means that this is the default behavior in the game. Whenever the game wants to skip this waiting period it sets things up in order to "trump". We can simulate this by:

- Selecting the Move fragmentID key.
- Checking the "Trump Previous Fragment" option.

![Image](https://www.cryengine.com/docs/static/attachments/23998473)

The result is the following, where the animation starts immediately:

![Image](https://www.cryengine.com/docs/static/attachments/23998474)
