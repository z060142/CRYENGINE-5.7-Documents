# 2 - Game Variables

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450191
- Page ID: 29450191
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Gameplay > 2 - Game Variables
- Parent: Tutorial - Getting Started With Gameplay

## Content

[![Image](https://www.cryengine.com/docs/static/attachments/44971011) 1 - Gameplay Setup](/docs/static/engines/cryengine-5/categories/23756816/pages/27593405)

[![Image](https://www.cryengine.com/docs/static/attachments/44971013) 3 - Creating our Token](/docs/static/engines/cryengine-5/categories/23756816/pages/29450268)

##
What is a GameToken?

Within the logic of Flow Graph is a system that keeps track of variables. These variables are stored in Tokens that can be used locally through a
**
Graph Token
**
 or globally through a
**
Game Token
**
. You can use these tokens for all sorts of gameplay elements like keeping track of a timer that counts down to the end of a round or the ability to keep track of score or enemies killed within the game.

Outside of the token setup the tokens themselves are exposed to Flow Graph through the following nodes:

-
Mission:GameToken

-
Mission:GameTokenCheck

-
Mission:GameTokenCheckMulti

-
Mission:GameTokenGet

-
Mission:GameTokenModify

-
Mission:GameTokenSet

-
Mission:GameTokenSetLevelToLevelRestore

-
Mission:GameTokenSetLevelToLevelStore
You will notice that they are all labelled Game Token and none is labelled Graph. By default the
**
GameToken
**
 nodes will also expose the
**
GraphToken
**
 variables directly to the same dropdown as the game tokens for selection. The benefit of Game Tokens is that you can save these out to an external XML to be read and not risk your data being lost for reference. However, in most cases you won't need to set up GameTokens outside of a level.

[![Image](https://www.cryengine.com/docs/static/attachments/44971011) 1 - Gameplay Setup](/docs/static/engines/cryengine-5/categories/23756816/pages/27593405)

[![Image](https://www.cryengine.com/docs/static/attachments/44971013) 3 - Creating our Token](/docs/static/engines/cryengine-5/categories/23756816/pages/29450268)
