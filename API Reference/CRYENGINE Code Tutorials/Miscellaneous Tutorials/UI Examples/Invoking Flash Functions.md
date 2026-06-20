# Invoking Flash Functions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306542
- Page ID: 23306542
- Breadcrumb: CRYENGINE Code Tutorials > Miscellaneous Tutorials > UI Examples > Invoking Flash Functions
- Parent: UI Examples

## Content

##
Overview

CRYENGINE supports Scaleform GFx to load and render Flash assets within a game.

To load a flash file follow the
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306536](
Scaleform GFx and CRYENGINE
)
 document.

##
Calling a Flash function

In order to do this you have to write a global function in your Flash file:

```

`
  setHealth = function(_intHitpointsPercent)
  {
    // set text of a dynamic text box (don't forget to embed the charackter set)
    txtHealth.text = "Health: " + _intHitpointsPercent.toString();
  }

`

```

and call this function within your c++ code:

```

`
  CActor *pActor = static_cast<CActor *>(gEnv->pGame->GetIGameFramework()->GetClientActor());
  if (pActor != NULL)
  {
    int health = pActor->GetHealth();
    pFlashPlayer->Invoke1("setHealth", health);
  }

`

```

There are three Invoke functions that allow you to call flash functions:

```

`
  pFlashPlayer->Invoke0( "flashFunction" ); // 0 arguments
  pFlashPlayer->Invoke1( "flashFunction", arg1 ); // 1 arguments

  SFlashVarValue args[3] = { arg1, arg2 , arg3 };
  m_pFlashPlayer->Invoke( "setPlayerPos" , args , 3 ); // 2 or more arguments

`

```

##
Loading a Minimap

The Sandbox Editor has a function to create a minimap for your level. More information can be found in the
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048847](
Creating Mini Maps
)
 tutorial.

After you have created the .dds and .xml files of your level, you can easily load this .dds file into your flash hud.

You have to create a function in your Flash file that loads a file by a given filename into a MovieClip:

```

`
  setMiniMap = function(_strPathToMiniMap)
  {
    //_strPathToMiniMap:  scaleform compatible path to the background map image, should be .dds
    loadMovie("img://"+ _strPathToMiniMap, MiniMapMC);
  }

`

```

now you can call this function by c++

```

`
  pFlashPlayer->Invoke1("setMiniMap", "Levels\\PacificIsland\\PacificIsland.dds");

`

```

You may want to show some dynamic items on the minimap, player position, for example.

To do this you have to read the .xml file that is created by the Sandbox Editor to get the start and end values of the minimap.

```

`
  float mapStartX = 0;
  float mapStartY = 0;
  float mapEndX = 1;
  float mapEndY = 1;

  IXmlParser*  pxml = gEnv->pGame->GetIGameFramework()->GetISystem()->GetXmlUtils()->CreateXmlParser();
  if(pxml != NULL)
  {
    XmlNodeRef node = GetISystem()->LoadXmlFile("Levels\\PacificIsland\\PacificIsland.xml");
    if (node != NULL)
    {
      node = node->findChild("Minimap");
      if (node)
      {
        node->getAttr("startX", mapStartX);
        node->getAttr("startY", mapStartY);
        node->getAttr("endX", mapEndX);
        node->getAttr("endY", mapEndY);
      }
    }
  }

  float mapDimX = mapEndX - mapStartX;
  float mapDimY = mapEndY - mapStartY;
  // Note: you may check if the dimensions are not 0!

`

```

Now you can simply create position values between 0 and 1 and send them to Flash:

```

`
  CActor *pActor = static_cast<CActor *>(gEnv->pGame->GetIGameFramework()->GetClientActor());
  if (pActor != NULL && pActor->GetEntity() != NULL)
  {
    Vec3 pos = pActor->GetEntity()->GetWorldPos();
    float posx = (pos.x - mapStartX) / mapDimX; // value from 0 to 1
    float posy = (pos.y - mapStartY) / mapDimY;
    SFlashVarValue args[3] = { posx, posy , pActor->GetAngles().z *180.0f/gf_PI-90.0f}; // note that the minimap is rotated by -90 degree
    m_pFlashPlayer->Invoke("setPlayerPos", args, 3);
  }

`

```

On the Flash side you can implement a function that sets position and rotation of a MovieClip that represents the player position on the minimap:

```

`
setPlayerPos = function(_floatPosx, _floatPosy, _intRot)
{
  // the created minimap .dds file has dimensions 512*512
  var pX = _floatPosy * 512; // since map is rotated about -90 degree, switch x and y coordiantes
  var pY = _floatPosx * 512;

  PlayerPosMC._x = pX;
  PlayerPosMC._y = pY;

  PlayerPosMC._rotation = -_intRot;
}

`

```
