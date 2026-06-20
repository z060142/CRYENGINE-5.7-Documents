# Item-Monitors

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450496
- Page ID: 29450496
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Item-Monitors
- Parent: Universal Query System (UQS)

## Content

## Overview

Item-Monitoring is an optional feature that runs alongside an ongoing query. Its purpose is to detect changes in the reasoning space that might yield to a corruption (of it) and therefore could cause crashes or unpredictable behavior.

### Example

Consider a query that evaluates triangles of the navigation mesh: a custom item-monitor might have been installed to detect when certain regions of the navigation mesh regenerate at runtime. If any of the triangles (items) would be affected by the regeneration, the item-monitor could report a corruption, and the whole query would then bail out with an error.

### Installation and Lifetime of Item-Monitors

Item-monitors usually get installed by the custom item generator of a running query. They will persist for at least as long as that particular query is running. In the case of Chained Queries though, the item-monitors will persist even longer - namely until the very last child query has been processed. This is to ensure that items of earlier queries in the chain cannot become corrupt (go unnoticed) by the time they get used as input parameters by a later query in the chain.

You can add as many item-monitors to a query as you want via this method:

```
UQS::Core::IQueryManager::AddItemMonitorToQuery(const CQueryID& queryID, UQS::Client::ItemMonitorUniquePtr&& pItemMonitorToInstall);
```

Typically, you'd do this in a generator. Here's an excerpt from one of the StdLib's generators:

```
UQS::Client::IGenerator::EUpdateStatus CGenerator_PointsOnNavMesh::DoUpdate(const SUpdateContext& updateContext, client::CItemListProxy_Writable<Vec3>& itemListToPopulate)
{
// ...
std::unique_ptr<CItemMonitor_NavMeshChangesInAABB> pItemMonitorNavMeshChanges(new CItemMonitor_NavMeshChangesInAABB(m_params.navigationAgentTypeID));
// ...
UQS::Core::IHubPlugin::GetHub().GetQueryManager().AddItemMonitorToQuery(updateContext.queryID, std::move(pItemMonitorNavMeshChanges));
// ...
}
```
