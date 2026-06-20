# Linking Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306592
- Page ID: 23306592
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Script Entity > Linking Entities
- Parent: Script Entity

## Content

##
Overview

In Sandbox, it is possible to link an entity to other entities. More information on this feature can be found in the Sandbox Manual under
[Grouping and Linking Objects](/docs/static/engines/cryengine-3/categories/1114113/pages/1048819)
.

These links are organized inside the Entity System. Each entity can link to multiple entities. Each link has a name associated to it.

![Image](https://www.cryengine.com/docs/static/attachments/23461420)

##
Script Example

The following Lua script will gather from the entity system any link to other entity which is named
*
"Generator"
*
.

```

`
function RadarBase:IsPowered()
  local i=0;
  local link = self:GetLinkTarget("Generator", i);

  while (link) do
    Log("Generator %s", link:GetName());

    if (link:GetState() == "PowerOn") then
      if (link.PowerConnect) then
        link:PowerConnect(self.id);
        return true;
      end
    end

    i=i+1;
    link=self:GetLinkTarget("Generator", i);
  end

  return false;
end

`

```

##
Script Functions

The ScriptBind functions related to Entity Links are listed in
[ScriptBind_Entity](../../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CRYENGINE%20Functions/ScriptBind_Entity.md)
.

The following functions will read or create entity links:

-
CountLinks

-
CreateLink

-
GetLink

-
GetLinkName

-
GetLinkTarget

-
RemoveAllLinks

-
RemoveLink

-
SetLinkTarget
