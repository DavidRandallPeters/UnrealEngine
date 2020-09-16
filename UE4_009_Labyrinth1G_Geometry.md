# Unreal Engine | 009 | Marble Labyrinth 1G | Adding Geometry

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 009.001 | Creating geometry using BSP brushes

<br>

Let's start adding some walls to our labyrinth so that this poject begins qualifying as a game.

We'll being by adding a floor plane which we'll later cut a hole in so that the marble has an escape point.

You'll get a feel for what a BSP brush is by following this tutorial, but if you'd like a little more information about them:

[Matthew Wadstein awkwardly explains](https://www.youtube.com/watch?v=3Kc2VzxBFqQ&ab_channel=MathewWadstein)

<br>

We do already have a floor.. but we won't use this one in the end-product. So:

<br>

- Select the **Floor** Actor, **Shift-select** the **Marble** Actor and move them off to the side - somewhere out of the way

- Locate the **Place Actors** panel (formerly known as the *Modes* panel). This is likely on the left of your screen - otherwise, go to **Window » Place Actors** (may be called *Modes* in your version of Unreal)

- Select the **Geometry** category

> These objects are referred to as 'brushes' 

- Click and drag the **Box** brush into the viewport

- Rename this new Actor to *FloorBoxBrush* in the **Outliner**

- Using the **Transform** section of the **Details** panel, send the box to **origin** (0,0,0)

- Briefly ast your eyes over the **Brush Settings** in the **Details** panel and notice that the brush is set to 200³ units - ie. our box was created at a scale of 200 *Unreal units* cubed

- In the **Brush Settings**, set the box's **Z** value to 30 units

- Set the box's **X** value to **1400**

- Set the box's **Y** value to **2000**

> Quick note: When adjusting brush scales, always use the *Brush Settings* - using the *Scale* tool will result in stretched materials

<br>

![Floor scaled](https://user-images.githubusercontent.com/36719180/93279318-0e8abc00-f81b-11ea-9c69-99a7f757e90e.png)


<br>

- Drag another **Box** brush out from the **Place Actors** panel into the scene

- Rename this new Actor to *WallBoxBrush01* in the **Outliner**

- With **WallBoxBrush01** selected, change its **Y** dimension to **100** in **Brush Settings**

- Send **WallBoxBrush01** to **origin** (0,0,0)

- Set the **grid snap** value to **50** - so that we can precisely match our box placement to the checker pattern on the floor

<br>

![Grid snap](https://user-images.githubusercontent.com/36719180/93279913-8e655600-f81c-11ea-96bf-71964819214d.png)

<br>

- Place **WallBoxBrush01** in the lower-left corner of the **FloorBoxBrush** Actor

<br>

![Put wall in corner](https://user-images.githubusercontent.com/36719180/93281799-fae25400-f820-11ea-8c1b-86c32eaea14f.png)

<br>

> To change the length of that wall, we'll use *Brush Editing* mode

- Locate the **Modes** dropdown at the top of the viewport and expand it - select **Brush Editing** - a new tab should open next to *Place Actors*

- Reselect **WallBoxBrush01** if it's not selected and blue manipulators will appear

- Hit **F** to focus on **WallBoxBrush01** and select the face that we'll need to extend to cover the edge of the floor

- Drag that face out until it's flush with the edge of **FloorBoxBrush**

<br>

![Brush editing](https://user-images.githubusercontent.com/36719180/93282552-c079b680-f822-11ea-98b0-0af8b3ad92dc.png)

<br>

- Select the top face of **WallBoxBrush01** and increase the height of the wall to whatever height feels good

<br><br>

---

## 009.002 | Applying materials to BSP brushes

<br>

We already know how to apply materials to Actors. We have a bunch of materials ready to go in our *StarterContent* folder.

So let's apply some materials to this wall..

<br>

- Find a suitable material and drag it onto **WallBoxBrush01**

> Notice that, whereas previously the material would be applied to an entire Actor, the material here is only applied to ONE face

- Select **WallBoxBrush01** in the **Outliner**

- In the **Geometry** section of the **Details** panel, hit the **Select** button

- Choose **Select All Adjacent Surfaces** - all faces of **WallBoxBrush01** are now selected

- In the **Surface Materials** section of the **Details** panel, hit **Display *n* materials** - here's where we view which materials this brush is using

- Drag and drop your chosen material onto any of those displayed materials to combine the elements into one unified material

<br>

![Surface Materials](https://user-images.githubusercontent.com/36719180/93283993-c3c27180-f825-11ea-957f-64f54cd3924a.png)

<br>

- With that material still selected in the **Content Browser** create another **Box** brush, as we did before (drag it out from the **Place Actors** panel**)

> Because the material was selected, this brush was created with that material already applied to all faces.

- Name this new brush *WallBoxBrush02*

- Give **WallBoxBrush02** an **X** value of **100** in the **Brush Settings** section of the **Details** panel

- Via the **Modes** dropdown (above the viewport) choose **Select** mode

- Position **WallBoxBrush02** on another edge of the floor and repeat previous steps to extend it out

- Finish up the outside wall of the labyrinth in this way, naming new brushes as you go

- Apply a material to all surfaces of the **FloorBoxBrush**

<br>

![Walls done](https://user-images.githubusercontent.com/36719180/93285305-acd14e80-f828-11ea-93bb-76be82590e04.png)

<br><br>

---

## 009.003 | Build a maze

<br>

- Using these skills, **design a simple maze** that has a start and a finish

- Drag your marble into the starting position

<br>

![Maze built](https://user-images.githubusercontent.com/36719180/93287484-c923ba00-f82d-11ea-88c8-64205257286f.png)

<br><br>

---

## 009.004 | Cutting an escape hole

<br>

We'll make a hole in the floor for the marble to escape through. 

This involcves blah

So:

<br>

- Look at the bottom of the **Geometry** category in the **Place Actors** panel - we have *Add* and *Subtract* modes for the geometry - set it to **Subtract**

- Drag a **Box** brush into the viewport as we've done before - placing it at the end of your maze

- Name the new brush *EscapeHatch*

- Reposition the new brush in such a way that it cuts a hole at the end of your maze

<br>

![Escape hatch](https://user-images.githubusercontent.com/36719180/93288046-1f452d00-f82f-11ea-8f0f-add4cd1083b4.png)

<br><br>

---

## 009.005 | Converting BSP to Static Mesh

<br>

BSP can't be utilised within blueprints.. which will pose a problem for us.

So we'll convert all the BSP geometry that we've made down to a single *Static Mesh*.

A wee catch, though - if we select all the BSP geometry to then convert, the Static Mesh will inherit the pivot point of the last object selected.. which is going to screw up our whole tilting game mechanic.

So we'll make sure we select *FloorBoxBrush* LAST - as it has a central pivot point that we can use.

<br>

- Select all your BSP geometry except **FloorBoxBrush**

- Finally, select **FloorBoxBrush**

- In the **Brush Settings** section of the **Details** panel, hit the little white downward arrow (its tooltip says **Show Advanced**) to show advanced brush settings

- Hit **Create Static Mesh** - a *Select Path* dialogue pops up

- **Right-click** on the **Content** folder and choose **New Folder** - don't click out before you've named it!

- Name the new folder **Mazes**

- In the **Static Mesh Name** field, name it *Maze001*

- Hit **Create Static Mesh**

<br>

![Static Mesh](https://user-images.githubusercontent.com/36719180/93289312-333e5e00-f832-11ea-870f-18f908ad72dc.png)

<br>

We've now collapsed all that geometry into a single *Static mesh.*

Grrrrrrrrreat.

<br><br>

#### Continued in UE4_010_Labyrinth1F_Upgrade

---









