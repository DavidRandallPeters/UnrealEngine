# Unreal Engine | 015 | 3P / PLATFORMER | Setup

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 015.002 | Overview

<br>

We're going to make an arcade-style game that can switch between top-down, third person and platformer as you see fit.

The player will control a rolling marble that must get from A to B (in a 3D environment of your design) and collect all instances of a given item before they're allowed to exit the level.

We'll again us BSP geometry to construct mesh assets within UE4 - but I *do* invite you create your own level components in your favourite 3D software and import these. You may wish to view [these tutorials](https://github.com/DavidRandallPeters/3DModeling) to achieve this.

We'll include stationery adversaries that will shoot projectiles, take a look at UE4's lighting system and I'll try to include particular features in these tutorials at your request - and if time permits. 

Of course, I invite you to do any of your own research that might contribute to you making the game that you want to make.

Let's go.

<br><br>

---

## 015.002 | Getting started

<br>


- Launch the latest version of the **Unreal** editor

- On the way in, choose a **Blank** *Blueprint* project and include **Starter Content**

- Determine a sensible folder location

- Name the project something like *Marble3P* or give it something more imaginative if you already have ideas for it in mind

- Once you're in the editor, go to **File » New Level**

- Choose **Empty Level** - we're presented with an empty level

- Create a new folder in the **Content Browser** called *Levels*

- Got to **File » Save Current** and save the level as *Level01* in the folder we just made

- Open the **Project Settings** (**Edit » Project Settings**)

- In the **Maps * Modes** category, set **Level01** as both **Default Maps**

- Close **Project Settings**


<br><br>

---

## 015.003 | White boxing

<br>

White boxing is simply the process of placing primitives to represent the final shape and volume of the level. It allows other developers on your team to prototype without having to wait for the artists to make the actual level content.

But you're judge, jury and executioner on this project, so right now, we'll do it as a means to start sketching out your level design.

<br>

- Start by getting a simple **Box** brush into the level (via the **Geometry** section of the **Modes** panel - aka **Place Actors** panel)

<br>

![Lit Box brush](https://user-images.githubusercontent.com/36719180/93967381-2f26b900-fdbb-11ea-8312-85dd314bf9ce.png)

<br>

It's basically invisible.

<br><br>

### Switch view mode

This level is empty - so we have no lights by which to see what we're doing. Placed Actors will all pretty much be invisible.

If you look in the top-right of the viewport, you'll see that we're currently in *Lit* mode - but this shit ain't lit.

<br>

- So, instead, choose **Unlit** 

<br>

![Unlit Box brush](https://user-images.githubusercontent.com/36719180/93967381-2f26b900-fdbb-11ea-8312-85dd314bf9ce.png)

<br>

> We can now see.

- 
