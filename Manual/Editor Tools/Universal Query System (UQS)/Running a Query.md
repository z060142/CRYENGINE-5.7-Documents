# Running a Query

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450500
- Page ID: 29450500
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Running a Query
- Parent: Universal Query System (UQS)

## Content

##
Overview

Running a query involves several steps at different points in time:

##
The Easy Way

If you don't care too much about the internal details such as the book-keeping of the running status and the setup of a callback of a query, then here's some good news: as of release 5.4 we added 2 helper classes that do most work for you.

```

`
UQS::Client::CQueryHost
UQS::Client::CQueryHostT<>
`

```

All you need to do is keep an instance of this class and start a query on it whenever you wish to. This class allows for polling or notification (once a query finishes) so that you can pick up the resulting items from it.

##
The Explicit Way

##
Starting a Query

Starting a query is comprised of several steps:

-
Using a CQueryBlueprintID to specify the query blueprint to instantiate

-
Providing runtime parameters that are specific for the query that you want to run

-
Providing a callback for when the query finishes

-
Checking for errors
Here's an example of how the code to start a single query could look like:

```

`
if (UQS::Core::IHub* pHub = UQS::Core::IHubPlugin::GetHubPtr())
{
    // this is the query blueprint that we want to instantiate
    const char* szQueryBlueprintName = "HideFromEnemy";

    //
    // find the blueprint ID of the query blueprint that we want to start (we could also cache the CQueryBlueprintID and re-use it at any time)
    //

    const UQS::Core::CQueryBlueprintID blueprintID = pHub->GetQueryBlueprintLibrary().FindQueryBlueprintIDByName(szQueryBlueprintName);
    assert(blueprintID.IsOrHasBeenValid());

    //
    // runtime params
    //

    UQS::Shared::CVariantDict runtimeParams;
    runtimeParams.AddOrReplaceFromOriginalValue("actor", self);

    //
    // make a query request and start it
    //

    UQS::Client::SQueryRequest queryRequest(blueprintID, runtimeParams, "Human_1", functor(*this, &CMyGame::OnUQSQueryFinished));
    UQS::Shared::CUqsString error;
    const UQS::Core::CQueryID queryID = pHub->GetQueryManager().StartQuery(queryRequest, error);

    //
    // check for errors (e. g. missing runtime parameters)
    //

    if (!queryID.IsValid())
    {
        // oops
        CryWarning(VALIDATOR_MODULE_GAME, VALIDATOR_WARNING, "UQS: failed to start query '%s': %s", queryRequest.queryBlueprintID.GetQueryBlueprintName(), error.c_str());
    }
}
`

```

##
Callback

Once the query finishes, it will use the callback provided by the earlier
*
SQueryRequest
*
 to notify of its result:

```

`
void CMyGame::OnUQSQueryFinished(const UQS::Core::SQueryResult& queryResult)
{
    const bool bSuccess = (queryResult.status == UQS::Core::SQueryResult::EStatus::Success);

    // Notice: success doesn't guarantee that any items were found (the result set might very well be empty!) - it only means that no unexpected runtime errors occurred)

    if (bSuccess)
    {
        const UQS::Shared::CTypeInfo& itemType = queryResult.pResultSet->GetItemFactory().GetItemType();

        // sanity check: expect Vec3 as items (Careful: this assumes that the query actually produces Vec3 items!)
        if (itemType == UQS::Shared::SDataTypeHelper<Vec3>::GetTypeInfo())
        {
            const size_t numFoundItems = queryResult.pResultSet->GetResultCount();

            if (numFoundItems > 0)
            {
                // run through all found items
                for (size_t i = 0; i < numFoundItems; ++i)
                {
                    const Vec3* pItem = static_cast<const Vec3*>(queryResult.pResultSet->GetResult(i).pItem);

                    // ... do something with the retrieved item ...
                }
            }
        }
    }
    else
    {
        // an unexpected runtime error occurred (e. g. the query's reasoning space got corrupted)

        UQS::Shared::CUqsString queryIdAsString;
        queryResult.queryID.ToString(queryIdAsString);

        CryWarning(VALIDATOR_MODULE_GAME, VALIDATOR_WARNING, "CMyGame::OnUQSQueryFinished: query #%s ended up with an error: %s", queryIdAsString.c_str(), queryResult.error);
    }
}
`

```

##
Canceling (Optional)

Canceling a query can be useful in certain situations:

-
The querier is no longer interested in the result of the started query

-
The querier is about to go out of scope and needs to clean up the callback provided to the running query
This is very important to prevent a later crash should i.e. the query try to call back into the querier once it has finished.

```

`
if (UQS::Core::IHub* pHub = UQS::Core::IHubPlugin::GetHubPtr())
{
    pHub->GetQueryManager().CancelQuery(m_queryID);
    m_queryID = UQS::Core::CQueryID::CreateInvalid();
}
`

```

[#the-easy-way](
The Easy Way
)
[#the-explicit-way](
The Explicit Way
)
[#starting-a-query](
Starting a Query
)
[#callback](
Callback
)
[#canceling-optional](
Canceling (Optional)
)
