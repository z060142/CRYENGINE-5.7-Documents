# 3 - Creating our Token

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450268
- Page ID: 29450268
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Gameplay > 3 - Creating our Token
- Parent: Tutorial - Getting Started With Gameplay

## Content

[![Image](https://www.cryengine.com/docs/static/attachments/44971018)2 - Game Variables](/docs/static/engines/cryengine-5/categories/23756816/pages/29450191)

[![Image](https://www.cryengine.com/docs/static/attachments/44971019)4 - Opening a Locked Door](/docs/static/engines/cryengine-5/categories/23756816/pages/29450270)

#### What are the differences in tokens and what are the variable types?

In this section we will look at the two different ways in which we can create a GameToken to be used within our graphs. We will begin by creating a simple Integer GameToken called Score to keep track of how many times we have entered the proximity trigger in our level. Once completed we will look at another way of embedding the Graph Token type that is more local and not global, but will store graph variables quickly and is a useful alternative to writing out to global XML.

Several variable types are accessible to us and are listed below:

- Boolean - True or False
- Integer - Any whole number.
- Float - Any floating point number.
- String - Any sequence of characters.
- Vector 3 - Any 3 dimensional positional coordinate (x,y,z) - for example, 290,200,180.

[Embed: https://vimeo.com/271698129]

#### How to Create Game and Graph Tokens

You need to follow these below mentioned steps to create both Flow Graph Token types:

- To create a **GameToken** you need to navigate to the ** Tools->Database View tool** and then click the ** GameTokens** tab to see the default interface.
- Once inside we will be clicking Add Library and naming the library **gameQuickStart** then clicking ** Add New Item** and naming this token ** Score**.
- We can also now Set the variable type to be **Int** or ** Integer** for the ** Score** and then we can also set the ** default value** to be ** 0** directly below. You can finalise all changes by now clicking the ** Save** icon in the top left.
- This will be the last step to actually writing our a GameToken and now we will pivot back over to Flow Graph and create a Graph Token. Within the Flow Graph interface you will find the Graph Token creation housed in the **Tools->edit Graph Tokens**... button in the upper menu.
- Once clicking this we are presented with a **popup** window that requires us to enter in the ** Name** and ** variable type** just like the GameToken workflow. We will enter in the name ** graphScore** to not confuse us when looking to make sure they are registered in the next step.
- Now that we have registered our tokens we will expose them using a simple **Mission:GameToken** node and see if they come up in the listing on both in the properties panel.

[![Image](https://www.cryengine.com/docs/static/attachments/44971018)2 - Game Variables](/docs/static/engines/cryengine-5/categories/23756816/pages/29450191)

[![Image](https://www.cryengine.com/docs/static/attachments/44971019)4 - Opening a Locked Door](/docs/static/engines/cryengine-5/categories/23756816/pages/29450270)
