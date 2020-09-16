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


