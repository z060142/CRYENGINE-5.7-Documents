# Schematyc Support

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450506
- Page ID: 29450506
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Schematyc Support
- Parent: Universal Query System (UQS)

## Content

true
This is a Beta Feature
This Schematyc feature is still in beta and subject to constant change. We encourage you to use it in test projects and provide your feedback to us.

However, **DO NOT** use it in production where it creates dependencies! Always back up your projects to make sure that you can go back to a previous version.

## Overview

With CRYENGINE 5.4, we added preliminary support for Schematyc.

In order to enable Schematyc support via the Universal Query System (UQS) the following C++ macro needs to be set to 1:

`UQS_SCHEMATYC_SUPPORT`

This can be done via CMake using the following OPTION:

`OPTION_UQS_SCHEMATYC_SUPPORT`

Please make sure to then re-compile the complete code (all the UQS projects provided by the Engine as well as your game code) to ensure consistency across header files, libraries, and DLLs.

There is a Schematyc Component that allows the user to start a specific query and deal with the resulting items once the query finishes.

### Functions

##### UQS::BeginQuery

This prepares the Schematyc component for starting a new query.

Parameter direction | Parameter name | Description
--- | --- | ---
Input | `QueryBlueprint` | Name of the query blueprint that shall be started.
Input | `QuerierName` | For debugging purposes only: name of the querier to identify more easily in the query history.

##### UQS::AddParam

Adds a parameter to the query's runtime parameters. This function comes in different versions for different data types. If a query requires more than one runtime parameter, then this function needs to get chained for all of the runtime parameters.

Parameter direction | Parameter name | Description
--- | --- | ---
Input | `Name` | Name of the query's runtime parameter.
Input | `Value` | The actual data of the runtime parameter.

##### UQS::StartQuery

Actually starts the query that has been set up so far via **UQS::BeginQuery** and the various ** UQS::AddParam** calls.

Parameter direction | Parameter name | Description
--- | --- | ---
Output | `QueryID` | A unique ID to identify the freshly started query. This can be used later for fetching the resulting items once the query finishes.

##### UQS::GetResult

Allows for fetching all resulting items after a specific query has successfully finished. This function comes in different versions for different data types. You should use the function with the data type that matches with the data type of items that the query has generated.

Parameter direction | Parameter name | Description
--- | --- | ---
Input | `QueryID` | The ID of the query that UQS::StartQuery returned.
Input | `ResultIdx` | Index of the item that you want to fetch. This can be between 0 and the ResultCount of UQS::QueryFinished.

##### Equal

Compares two QueryIDs for equality.

Parameter direction | Parameter name | Description
--- | --- | ---
Input | `QueryID1` | First QueryID to use by the comparison.
Input | `QueryID2` | Second QueryID to use by the comparison.
Output | `Result` | True/false depending on whether the two QueryIDs are equal or not.

### Signals

##### UQS::QueryFinished

Gets fired when a query has finished without having encountered any problem while running.

Parameter name | Description
--- | ---
`QueryID` | ID of the query that has just finished (it's an ID that a previous call to UQS::StartQuery returned).
`ResultCount` | Number of resulting items (this may even be 0 if no item was found by the query).

##### UQS::QueryException

Gets fired when a query has encountered a problem while it was running.

Parameter name | Description
--- | ---
`QueryID` | ID of the query that has just finished (it's an ID that a previous call to UQS::StartQuery returned).
`ExceptionMessage` | Some text explaining what went wrong.

### Data types

##### QueryID

Unique ID of a live query.

[Functions](#functions)[Signals](#signals)[Data types](#data-types)
