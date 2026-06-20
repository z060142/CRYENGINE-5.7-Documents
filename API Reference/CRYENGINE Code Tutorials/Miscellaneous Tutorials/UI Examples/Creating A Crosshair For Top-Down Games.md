# Creating A Crosshair For Top-Down Games

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306543
- Page ID: 23306543
- Breadcrumb: CRYENGINE Code Tutorials > Miscellaneous Tutorials > UI Examples > Creating A Crosshair For Top-Down Games
- Parent: UI Examples

## Content

### Overview

In this tutorial you will learn how to create an animated crosshair for Top-Down games by using Flash and Scaleform. You will create an animated flash file which will follow the mouse cursor and be light projected towards the floor.

Modules used in this tutorial:Adobe Flash, Scaleform, Sandbox, Flowgraph.

### Creating Simple Flash Crosshair

If you already have a flash file you want to use as crosshair in-game you can skip this and the next chapter and continue where the flash file gets imported to the engine.

For creating a simple crosshair open up Adobe Flash and do the following:

- Choose**File -> New...**
- Select **ActionScript 2.0**
- Set **Width** and ** Height** both to ** 512**
- Set **Frame rate** to ** 30 fps**
- Press **OK**

![Image](https://www.cryengine.com/docs/static/attachments/23461381)

On the right **Properties** panel select ** Flash Player 8** as ** Target**.

![Image](https://www.cryengine.com/docs/static/attachments/23461379)

You can now use Flash as usual to create your scene. The following screenshot shows an example crosshair, already converted to a **Symbol**.

Before continuing please make sure your shape got also converted to a **Symbol** (mark the shapes and select ** Convert to Symbol...** from the context menu). In our example we use a ** Graphic**-Symbol.

![Image](https://www.cryengine.com/docs/static/attachments/23461378)

### Animating Flash Crosshair

Let's make the crosshair rotate by adding some keyframes to the flash scene.

**Select frame 100** from the ** Timeline**and choose** Insert Frame** from the context menu.

![Image](https://www.cryengine.com/docs/static/attachments/23461376)

**Select a frame between 1-100** and choose ** Create Motion Tween** from the context menu.

![Image](https://www.cryengine.com/docs/static/attachments/23461375)

![Image](https://www.cryengine.com/docs/static/attachments/23461374)

The crosshair is now ready to get animated. Select**frame 25** and** rotate the object by 90 degree**. Keep doing that until the crosshair has performed one cycle.

- **Frame 1:** original position
- **Frame 25:** rotate by ** 90** degree
- **Frame 50:** rotate by ** 180** degree
- **Frame 75:** rotate by ** 270** degree
- **Frame 100:** rotate by ** 360** degree

![Image](https://www.cryengine.com/docs/static/attachments/23461373)

If the scene is selected and you hit **Enter**, you get a preview of the animation.

The flash file does **not** need to be set up in loop-mode.

### Importing Crosshair into the Engine

The flash animation has been created successfully in the previous step.

Now it is time to export it by selecting **File -> Export -> Export Movie...** and storing the ** swf file** somewhere on your hard disk.

![Image](https://www.cryengine.com/docs/static/attachments/23461372)

To be able to load the flash file you need to convert the **swf** file to ** gfx**.

The easiest way to do this is by dragging the **swf** file on top of ** gfxexport.exe** which is located in: `<root>\Tools\GFxExport`

This will create a corresponding **gfx** file with the same name located in the same folder as the ** swf**.

![Image](https://www.cryengine.com/docs/static/attachments/23461370)

Create the following folder structure for the engine and place the **gfx** file inside: `GameSDK\Libs\UI`

```
root\GameSDK\Libs\UI\UIElements
```

Inside folder **UIElements** create a new ** xml** file which contains the following content. Depending on your setup you might have to adjust the name of your ** gfx**file.

```
<!-- Category name, of your own choosing -->
<UIElements name="Crosshair">

<!-- Object name, again, of your own choosing -->
<UIElement name="Crosshair" render_lockless="1">

<!-- Point it to the correct files and give it some default settings -->
<GFx file="crosshair.gfx" layer="0">
<Constraints>
<Align mode="dynamic" valign="center" halign="center" scale="0" max="0" />
</Constraints>
</GFx>

</UIElement>

</UIElements>
```

Your Flash MovieClip is now ready to be used inside the engine!

### Attaching Crosshair to Mouse Position

The idea of getting a crosshair into the engine is to use a light source which projects a flash movie on the floor. This will then be attached to the current mouse cursor position.

Create a light source via**Entity -> Lights -> Light** and ** rotate** the ** Y axis** by ** 90 degree**. Now, the projection is pointing on the floor.

Also make sure that the light source is not too far away from the floor (**1-2 meters** above the ground should be fine).

![Image](https://www.cryengine.com/docs/static/attachments/23461363)

- Set **DiffuseMultiplier** to ** 10**
- Set **Projector:Texture** to ** crosshair.ui** by typing the name into the text field (name depends on the ** gfx** filename)

![Image](https://www.cryengine.com/docs/static/attachments/23461361)![Image](https://www.cryengine.com/docs/static/attachments/23461362)

The light is now projecting to the floor. If you press **CTRL+G** to enter ** game mode**, you can observe that the animation is also played.

![Image](https://www.cryengine.com/docs/static/attachments/23461359)

You might want to tweak some values of the light as for example **ProjectorFov** to get a steeper projection angle.

![Image](https://www.cryengine.com/docs/static/attachments/23461358)

After you have found good settings for the light, select the light and choose **Create Flow Graph** from the context menu.

![Image](https://www.cryengine.com/docs/static/attachments/23461357)

This will create a new flowgraph for this light entity. To make the crosshair following the mouse cursor, build a similar flowgraph as shown in the picture below.

![Image](https://www.cryengine.com/docs/static/attachments/23461356)

[Creating Simple Flash Crosshair](#creating-simple-flash-crosshair)[Animating Flash Crosshair](#animating-flash-crosshair)[Importing Crosshair into the Engine](#importing-crosshair-into-the-engine)[Attaching Crosshair to Mouse Position](#attaching-crosshair-to-mouse-position)
