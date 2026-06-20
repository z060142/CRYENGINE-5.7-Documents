# 3 - Clock Counting Down

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27591905
- Page ID: 27591905
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Flow Graph > 3 - Clock Counting Down
- Parent: Tutorial - Getting Started With Flow Graph

## Content

[/docs/static/engines/cryengine-5/categories/23756816/pages/27591903](
[Image: /docs/static/attachments/52593277]
2 - Spawning your Player
)

[/docs/static/engines/cryengine-5/categories/23756816/pages/27591908](
[Image: /docs/static/attachments/52593279]
4 - Debugging
)

For this sample we will be looking at how we can create a countdown timer in order to limit a round and communicate the remaining time to the player. The concept is simple to understand in that we need to start at a set number and then subtract a single value each second. Some things we will have to manage are the counting and also the pausing of the number decremented when it hits the value of zero.

##
How to Make a Clock Ticking Down

You need to follow these below mentioned steps to test your animations in a scene:

-
Add a
**
Math:SetNumber
**
 node and setting the value to
**
99
**
. This will be the length of our round.

-
Add a
**
Game:Start
**
 node at the beginning and then hook the number value out of
**
SetNumber
**
 into the
**
Show
**
 and
**
Message
**
 slots of a
**
Debug:DisplayMessage
**
 node.

-
Jump into your level (
**
Ctrl+G
**
) and test to see that the value is printed on the top left of the screen.

-
With the value now printed at
**
99
**
 we will begin to add a countdown by first adding a
**
Time:Timer
**
 node to update each frame (
**
1
**
) and a
**
Math:Counter
**
 node in order to increment the count of a value.

-
In order to connect the
**
SetNumber
**
 and the
**
Math:Counter
**
 we need to add a
**
Math:Sub
**
 node and then subtract the
**
SetNumber
**
 of
**
99
**
 in the
**
A
**
 slot and the
**
Math:Counter
**
 subtracting in the
**
B
**
 slot.

-
Complete the checking to see if the counter has reached 0 by checking the
**
Counter
**
 through a
**
Math:Equal
**
 node set to
**
99
**
 and it connecting to the
**
Time:Timer Pause
**
 slot when the counter of
**
99
**
 outputs true.

-
The last step is simply connecting the
**
output
**
 of the
**
Math:Sub
**
 node into the
**
DisplayMessage
**
 node in the
**
Show
**
 and
**
Message
**
 slots.

##
Step 1-2

[Image: /docs/static/attachments/36309392]

##
Step 3

[Image: /docs/static/attachments/36309393]

##
Step 4

[Image: /docs/static/attachments/36309394]

##
Step 5

[Image: /docs/static/attachments/36309396]

##
Step 6

[Image: /docs/static/attachments/36309397]

##
Step 7

[Image: /docs/static/attachments/36309399]

[/docs/static/engines/cryengine-5/categories/23756816/pages/27591903](
[Image: /docs/static/attachments/52593277]
2 - Spawning your Player
)

[/docs/static/engines/cryengine-5/categories/23756816/pages/27591908](
[Image: /docs/static/attachments/52593279]
4 - Debugging
)
