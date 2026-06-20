# 9 - Reading the XML

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450276
- Page ID: 29450276
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Gameplay > 9 - Reading the XML
- Parent: Tutorial - Getting Started With Gameplay

## Content

[/docs/static/engines/cryengine-5/categories/23756816/pages/29450274](
[Image: /docs/static/attachments/44971061]
8 - Writing to XML
)

Now that we have explored how we can write our data to disk, we'll take a look at how to read the data that we just wrote in
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450274](
8 - Writing to XML
)
. The logic for this is quite easy to understand through how we will open the document and then subsequently get the the child once again and the score located within it.

In order to finish of the lesson we will use a concatenation node of a string that prefixes the score attribute and prints to the screen through a display message on the viewport.

##
How To Read XML

Follow the steps below to read XML data within Flow Graph:

-
Create a
**
XML:OpenDocument
**
 node and passing the
**
Success
**
 port of the
**
 XML:SaveDocument
**
 from the prior lesson into the
**
Execute
**
 input port.

-
Inside of the
**
 XML:OpenDocument
**
, look for the name of the document we saved in the previous chapter and in this case add
**
.xml
**
 (example: Collin.xml)

-
Create a
**
XML:GetChild
**
 node and then we will look for the child
**
Score
**
 which we declared in the previous chapter and connect the
**
Success
**
 port from the
**
XML:OpenDocument
**
 node.

-
Create a
**
XML:GetValue
**
 node and connect the
**
Success
**
 port of the
**
 XML:GetChild
**
 node into the
**
Execute
**
 trigger of the
**
XML:GetValue
**
.

-
Take the value and pass this on to a
**
String:Concat
**
 node in order to add "DISK READ: " to our printed text and outputting to a
**
Debug DisplayMessage
**
 node in order to differentiate the read text from the printed one.

-
Jumping into game (
**
Ctrl+G
**
) and killing 5 AI should show text similar to as shown in the image below.

##
Step 1

[Image: /docs/static/attachments/29931640]

##
Step 2

[Image: /docs/static/attachments/29931641]

##
Step 3

[Image: /docs/static/attachments/29931642]

##
Step 4

[Image: /docs/static/attachments/29931643]

##
Step 5-1

[Image: /docs/static/attachments/29931644]

##
Step 5-2

[Image: /docs/static/attachments/29931645]

##
Final Result

[Image: /docs/static/attachments/29931646]

##
Conclusion

Although this tutorial has concluded, feel free to venture out on your own development path based on what we've covered in the previous chapters.
For information on the topics covered in this tutorial and more
, please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23307414](
CRYENGINE V Manual
)
.

[/docs/static/engines/cryengine-5/categories/23756816/pages/29450274](
[Image: /docs/static/attachments/44971061]
8 - Writing to XML
)
