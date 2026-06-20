# AI Action Flow Graph

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535412
- Page ID: 25535412
- Breadcrumb: Scripting > Flow Graph Overview > AI Action Flow Graph
- Parent: Flow Graph Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933203) ## Overview AI Action flowgraphs allow designers to script AI behaviors without having to creating new code. These flowgraphs are kind of flowgraph macro-nodes used for common actions like drinking, observing the environment, or performing some other idle action. ## Sections [Sections](#sections)[Setup](#setup)[Example](#example) ### Setup To create such an AI Action, open the Flow Graph editor in Sandbox and follow these steps: - Open the Flow Graph editor in Sandbox - From the Flow Graph editor's menu select **File** ->** New AI Action** - You will be prompted to save that AI Action under a new XML file. Name the file however you want (for example "** sample1.xml**") and make sure it's in the `GameSDK\Libs\ActionGraphs\` directory (you may need to create the directory if it doesn't exist already) - Your new AI Action ** sample1** should now show up in the tree view under "AI Actions" - Create a new arbitrary flow graph for en entity - this flow graph will then house your AI Action - In that flow graph, add the node ** AI:Execute**, double-click the ** Action** property and select your new ** sample1** action from the list of available AI Actions AI Action flowgraphs use the following two entities as parameters: - ** User**: Usually the AI who executes the action - ** Object**: Can be any entity ### Example
