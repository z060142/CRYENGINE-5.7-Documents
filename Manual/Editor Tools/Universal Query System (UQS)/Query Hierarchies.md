# Query Hierarchies

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450494
- Page ID: 29450494
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Query Hierarchies
- Parent: Universal Query System (UQS)

## Content

## Overview

There are 3 types of queries in UQS:

- Regular query
- Fallbacks query
- Chained query

A query is usually a combination of these, thus creating a *hierarchy* in the form of a tree. **Fallbacks** and ** Chained** queries are composite queries (i. e. are * branches* in the tree), whereas **Regular** queries do the actual grunt work of evaluating items (i. e. they are * leafs* in the tree).

![Image](https://www.cryengine.com/docs/static/attachments/28900925)

### Regular Query (CQuery_Regular)

This is the type of query that one will mostly think of in terms of a "query". It does the following:

- Generate items
- Evaluate the generated items
- Come up with the best 'N' items

A regular query cannot have any child queries.

Using the analogy of a Behavior Tree, then this type of query would be an **Action** node in the tree.

### Fallbacks Query (CQuery_Fallbacks)

This is a composite query that will try to run one child query after another until one finds some valid items. If none of the children come up with any items in the result set, then ultimately 0 items will get returned. Fallback queries are very common and are usually used to provide an alternative query with less restrictive conditions or parameters should the "primary" query not find any items.

Using the analogy of a Behavior Tree, then this type of query would be a **Selector** node in the tree.

### Chained Query (CQuery_Chained)

A chained query is a composite query that allows for more complex queries. It can be used to have the resulting items of a previous query carry over to the next query. There, the items can be used as input parameters for generators or evaluators. Basically, they allow for combining a previous result set with newly generated items. An example would be to work out which of the 'N' positions are visible from 'M' observers.

Using the analogy of a Behavior Tree, then this type of query would be a **Sequence** node in the tree.

[Regular Query (CQuery_Regular)](#regular-query-cqueryregular)[Fallbacks Query (CQuery_Fallbacks)](#fallbacks-query-cqueryfallbacks)[Chained Query (CQuery_Chained)](#chained-query-cquerychained)
