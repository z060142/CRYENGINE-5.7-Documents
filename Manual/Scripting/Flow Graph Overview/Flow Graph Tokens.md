# Flow Graph Tokens

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450527
- Page ID: 29450527
- Breadcrumb: Scripting > Flow Graph Overview > Flow Graph Tokens
- Parent: Flow Graph Overview

## Content

##
Overview

A
Graph Token
 is a variable that is used for storing values and then re-using those values within the same graph.

These tokens can be used for performing simple logic manipulations and checks within the flow graph script.

##
Graph Tokens in Action

Graph Tokens in the
Flow Graph Editor
share many similarities with
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869337](
Game Tokens
)
. They can have the same types of variables set and even appear under the CVar
**
command gt_show=1
**
 along with the rest of the game tokens.

It's important to understand that unlike
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869337](
Game Tokens
)
, Flow Graph Tokens can only be used locally to a single flow graph.
They are typically used to communicate different variables across a very large graph and to reduce the need for extra flow node connections.

##
Creating Graph Tokens and Accessing Them in Flow Graph

In this tutorial, we will create our own Graph Token that checks if the player has spawned into the game or not. We will then use a check to see the value of the Graph Token and display that value to the screen.

-
In Flow Graph, choose
**
 Tools ->
Edit Graph Tokens
**
.

-
In the
**
 Graph Tokens
**
 window, click
**
New Token
**
 to create a new Token. Enter a new name for the token and select the data type to use:

[Image: /docs/static/attachments/35395040]

-
Use the
**
Mission:GameTokenSet
**
 (or other Mission flow nodes) to set/get/adjust the value on the graph token.

-
**
Double-click
**
 the
**
Token
**
 port to enter the desired token. Make sure you zoom-in on the node before you double-click it.
[Image: /docs/static/attachments/44971118]

You can also use
**
Browse
**
 button to selected the saved Token.

*
[Image: /docs/static/attachments/35395042]
*

It's checked on start (in the same frame) and the value is seen as 1 using the game token debug view gt_show=1.

5. In the console, type "
gt_show=1"
 and switch to game mode to see the token value change.

##
Additional Information and Useful CVars

-
Graph Tokens are only local to the flow graph they exist in.

-
The Entity ID stores the flow graph, you need to set the
*
<graphid>
*
 value (88 above).

-
gt_show Value="1":
 Shows game token and graph token state (1 screen and log , 2 screen only and 3 log only).

-
gt_showFilter Value="":
 Filters string for game tokens and graph token.

-
gt_showLines Value="25":
Decides on total lines to show.

-
gt_showPosX Value="0”:
 Location on the screen to show in X axis (left right).

-
gt_showPosY Value="0":
 Location on the screen to shown in Y axis (up down).
