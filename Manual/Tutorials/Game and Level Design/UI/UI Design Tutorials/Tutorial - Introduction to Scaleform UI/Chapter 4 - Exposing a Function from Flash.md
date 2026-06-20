# Chapter 4 - Exposing a Function from Flash

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/89456814
- Page ID: 89456814
- Breadcrumb: Tutorials > Game and Level Design > UI > UI Design Tutorials > Tutorial - Introduction to Scaleform UI > Chapter 4 - Exposing a Function from Flash
- Parent: Tutorial - Introduction to Scaleform UI

## Content

### How Do We Expose Scoring?

Now that we have explored how to expose both vector and bitmap images, the following chapters will look at how you can use visual scripting to call a function in your game that will change a text label in Flash.

Considering how you will learn to expose a function that provides the dynamic textbox a value to print out, you will learn a valuable aspect of UI and how easy it is to show your score or game time on screen for a more engaging gameplay experience.

### Exposing a Function for Dynamic Text

#### Scaleform 3

- Draw a Dynamic Textbox inside of the Flash canvas and type "Score: 0." in the box.![Image](https://www.cryengine.com/docs/static/attachments/90833159) *Dynamic Textbox*
- Name the instance "lblScore" and click the **Selectable Button** to disable selecting the text if the cursor is enabled. You can also set the ** Paragraph** option to left-justified.![Image](https://www.cryengine.com/docs/static/attachments/90833160) * lblScore*
- Access the Actions Window by either pressing **F9** or going to ** Window → Actions** in the menu.![Image](https://www.cryengine.com/docs/static/attachments/90833550) * Window → Actions*
- Considering how this is the most basic form of ActionScript we can enter, we will house the script in the default layer as is (Scene 1 → Layer 1: Frame 1), and enter the following code to expose our function and allow Scaleform to call it:
```
function updateScore(value:Number)
{
lblScore.text = "Score: " + value;
}
```
![Image](https://www.cryengine.com/docs/static/attachments/90833162) *House the script in the default layer*
- Now that you have defined your function, you can compile your GFx file through the exporter as explained in [Chapter 2 - Flash and Gfx](Chapter%202%20-%20Flash%20and%20Gfx.md), then enter the following adjustments to your UI Elements XML file to expose the function to visual scripting:
```
<functions>
<function name="UpdateScore" funcname="updateScore" desc="Updates our score">
<param name="value" desc="New score" type="int" />
</function>
</functions>
```
![Image](https://www.cryengine.com/docs/static/attachments/90833163) *Exposing the function to visual scripting*

#### Scaleform 4

- Draw a Dynamic Textbox inside of the Flash canvas and type "Score: 0." in the box.![Image](https://www.cryengine.com/docs/static/attachments/90833165) *Dynamic Textbox*
- Name the instance "lblScore" and make sure a suitable color and size is chosen.![Image](https://www.cryengine.com/docs/static/attachments/90833557) *lblscore*
- Access the Actions Window by either pressing **F9** or going to ** Window → Actions** in the menu.![Image](https://www.cryengine.com/docs/static/attachments/90833167) * Window → Actions*
- Considering how this is the most basic form of ActionScript we can enter, we will house the script on the default layer as is (Scene 1, Layer 1, Frame 1), and enter the following code to expose our function and allow Scaleform to call it:![Image](https://www.cryengine.com/docs/static/attachments/90833168) *House the script in the default layer*
```
function updateScore(value:Number)
{
lblScore.text = "Score: " + value;
}
```
- Now that we have defined our function, we can compile our GFx file through the exporter as explained in [Chapter 2 - Flash and Gfx](Chapter%202%20-%20Flash%20and%20Gfx.md),, then enter the following adjustments to our UI Elements XML file to expose the function to visual scripting:
```
<functions>
<function name="UpdateScore" funcname="updateScore" desc="Updates our score">
<param name="value" desc="New score" type="int" />
</function>
</functions>
```
![Image](https://www.cryengine.com/docs/static/attachments/90833163) *Exposing the function to visual scripting*

[How Do We Expose Scoring?](#how-do-we-expose-scoring)[Exposing a Function for Dynamic Text](#exposing-a-function-for-dynamic-text)[Scaleform 3](#scaleform-3)[Scaleform 4](#scaleform-4)
