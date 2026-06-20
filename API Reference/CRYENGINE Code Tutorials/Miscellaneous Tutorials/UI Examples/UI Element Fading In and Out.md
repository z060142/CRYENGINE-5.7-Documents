# UI Element Fading In and Out

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306544
- Page ID: 23306544
- Breadcrumb: CRYENGINE Code Tutorials > Miscellaneous Tutorials > UI Examples > UI Element Fading In and Out
- Parent: UI Examples

## Content

##
Overview

-
Copy and paste this code somewhere on the root stage of your Flash asset

```

`
// create onEnterFrame function to fade-in the root element (if UI Element is shown up)
// We are using the cry_onShow function, which is called by the engine when the element is made visible.
function cry_onShow()
{
   _root._alpha = 0; // We set the _root._alpha to 0, because we want to animate it and fade it in over time.
   onEnterFrame = function()
   {
    // Have we reached 100 % alpha ?
      if (_root._alpha < 100)
      {
         _root._alpha++;
      }
      else
      {
         // clear onEnterFrame function
         onEnterFrame = function() {};
      }
   }
}

// create onEnterFrame function to fade-out the root element (if requested by UI System)
// The same for the inverse action. We use the cry_requestHide function called by the engine, when the element is hidden.
function cry_requestHide()
{
   onEnterFrame = function()
   {
    // If the alpha is greater than 0
      if (_root._alpha > 0)
      {
         _root._alpha--;
      }
      else
      {
         // clear onEnterFrame function and notify UI-System that this element does not need to be drawn anymore.
         onEnterFrame = function() {};
     // We call the cry_hideElement fscommand, to tell the engine that this ui element is not visible anymore.
     // This is an optimization in a form, because the engine doesn't have to draw a transparent UI element enymore :)
         fscommand("cry_hideElement");
      }
   }
}
`

```

2. You can now fade in/out the element by triggering the port
**
show
**
 /
**
requestHide
**
 if the
**
UI:Display:Display
**
 Node.

-
Triggering the show port calls
**
*
cry_onShow
*
**
action script function.

-
Triggering the requestHide port calls
*
**
cry_requestHide
**
*
action script function.
![Image](https://www.cryengine.com/docs/static/attachments/25502643)
