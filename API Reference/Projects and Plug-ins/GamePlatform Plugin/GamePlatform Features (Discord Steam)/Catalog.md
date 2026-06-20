# Catalog

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448503
- Page ID: 76448503
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > Catalog
- Parent: GamePlatform Features (Discord/Steam)

## Content

##
Overview

The Catalog abstraction allows interaction with platform store services. The catalog can contain consumables or DLC content that a user can opt to buy via the platform.

-
This module does not facilitate merchant capabilities, and relies on the platform store and proper setup of your game on that platform.

-
Some platforms require additional development of a web-API based platform handled by a centralized game server, to handle tracking and approval of transactions.

##
Catalog Service functions

##
BrowseCatalog

Requests the catalog in the specific sorting order.

Wait for the
[OnCatalogRecieved](Catalog.md#Catalog-oncatalogreceived)
event after requesting the catalog.
**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IService::BrowseCatalog
 |

Flow Graph Nodes
 |
GamePlatform:Catalog:BrowseCatalog
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Catalog
::BrowseCatalog
 |

##
GetLicenses

Retrieves the list of application licenses this user owns (e.g. DLCs).

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IService::GetLicenses
 |

Flow Graph Nodes
 |
GamePlatform:Catalog:GetLicenses
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::
Catalog
::GetLicenses
 |

##
Catalog Service Events

##
OnCatalogReceived

Fired when a response to a
[BrowseCatalog](Catalog.md#Catalog-browsecatalo)
request was received.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IService::IListener::OnCatalogReceived
 |

Flow Graph Nodes
 |
GamePlatform:Listener:OwnedItems:OnCatalogReceived
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::
Catalog
::OnCatalogReceived
 |

##
OnMicroTransactionAuthorizationResponse

Fired when a response was received from a microtransaction authorization request.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IService::IListener::OnMicroTransactionAuthorizationResponse
 |

Flow Graph Nodes
 |
GamePlatform:Listener:OwnedItems:OnMicroTransactionAuthResponse
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Catalog::OnMicroTransactionAuthorizationResponse
 |

[Catalog Service functions](#catalog-service-functions)
[BrowseCatalog](#browsecatalog)
[GetLicenses](#getlicenses)
[Catalog Service Events](#catalog-service-events)
[OnCatalogReceived](#oncatalogreceived)
[OnMicroTransactionAuthorizationResponse](#onmicrotransactionauthorizationresponse)
