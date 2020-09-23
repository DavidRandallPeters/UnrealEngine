# Unreal Engine | 015 | 3rd Person / Platformer A | Setup

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 015.002 | Overview

<br>

We're going to make an arcade-style game that can switch between top-down, third person and platformer as you see fit.

The player will control a rolling marble that must get from A to B (in a 3D environment of your design) and collect all instances of a given item before they're allowed to exit the level.

We'll again us BSP geometry to contruct mesh assets within UE4 - but I *do* invite you create your own level components in your favourite 3D software and import these. You may wish to view [these tutorials](https://github.com/DavidRandallPeters/3DModeling) to achieve this.

We'll include stationery adversaries who will shoot projectiles, look at UE4's lighting system and I'll try to include particular features in these tutorials at your request - and if time permits. 

Of course, I invite you to do any of your own research that might contribute to you making the game that you want to make.

Let's go.

<br><br>

---

## 015.002 | Getting started

<br>


- Launch the **Unreal** editor

- On the way in, choose a **Blank** *Blueprint* project and include **Starter Content**

- Determine a sensible folder location

- Name the project something like *ThirdPerson* or give it something more imaginative if you already have ideas for it in mind
