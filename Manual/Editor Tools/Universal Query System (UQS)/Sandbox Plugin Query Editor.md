# Sandbox Plugin: Query Editor

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450476
- Page ID: 29450476
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Sandbox Plugin: Query Editor
- Parent: Universal Query System (UQS)

## Content

## Overview

The Universal Query Editor is a Sandbox-Plugin that lets the user create new query blueprints. These query blueprints can then be accessed by code via their name and get instantiated into a "live" query at runtime.

### Details

You can access the UQS Query Editor by going to**Tools -> UQS Editor**.

The Query Editor's main window will then open:

![Image](https://www.cryengine.com/docs/static/attachments/28900921)

- **Query Factory:** lets you pick between 3 different query types:
- - Regular: this is a query that actually generates and evaluates items.
- Fallbacks: a composite query that tries alternative queries should the "primary" query not find any items.
- Chained: a composite query that allows for passing the resulting items to the next query in the chain in the form of input parameters.
- **Name:** this is the name of the query blueprint which will be used to instantiate the respective query at runtime.
You should agree with your programmer on a specific name as it will have to be used in code as well.
- **Max items to keep in result set:** the number of items that we're interested in. Usually, this is something in the lower number range, e. g.:
- 1 if you're searching for a good combat position to stand in.
- 3 if your fancy SpellCaster character wants to pick 3 targets that he intends to attack.
- 0 is a special value: it will have the query return *all* items that have been found (this may be very performance demanding).
- **Shuttled Type:** this is only relevant for ** Chained Queries**. If one of the child queries expects to use the result set from its preceding sibling query, then this list specifies the item type the query can deal with. More precisely, this item type will be used to ensure the correct type between what the previous query returns and what an evaluator uses as input parameters to access that previous result.
- **Constant parameters:** this is a list of named parameters whose values can already be specified within the Query Editor. These parameters can be used by the generator and evaluators as part of * their* inputs.
- **Runtime parameters:** this is a list of named parameters whose values can only be set at runtime. For example, if the * position* of the agent running this query is relevant for a generator, then this position should be such a runtime parameter. These parameters can be used by the generator and evaluators as part of * their* inputs.
- **Generator:** this lets you specify a generator that will produce a set of items on which the query will then run. The input parameters of the generator can come from different sources:
- **PARAM:** one of the global parameters specified above.
- **LITERAL:** an immediate constant value.
- **a function:** this can be a function that returns a value of the same type as the parameter. Notice that functions can be nested and may require input parameters themselves.
- **Evaluators:** this lets you specify an arbitrary number of evaluators that shall run on all items. They will be used to score and discard items. Similar to the generator, evaluators can have input parameters. Additionally, there are input parameters that give access to the currently visited item:
- **ITER:** the item that the query is currently iterating on.
- **PARAM:** one of the global parameters specified above.
- **LITERAL:** an immediate constant value.
- **a function:** this can be a function that returns a value of the same type as the parameter. Note that functions can be nested and may require input parameters themselves.
