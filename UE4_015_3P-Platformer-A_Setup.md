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

![Lit Box brush](https://user-images.githubusercontent.com/36719180/93967466-5aa9a380-fdbb-11ea-8242-eea18cbba46a.png)

<br>

It's basically invisible.

<br><br>

### Switch view mode

This level is empty - therefore, we have no lights by which to see what we're doing. 

If you look in the top-right of the viewport, you'll see that we're currently in *Lit* mode - but this shit ain't lit.

<br>

- So, instead, choose **Unlit** 

<br>

![Unlit Box brush](https://user-images.githubusercontent.com/36719180/93967381-2f26b900-fdbb-11ea-8312-85dd314bf9ce.png)

<br>

We can now see what we're doing.

<br><br>

### Static lighting

We could work in *Unlit* mode.. but, I don't know about you, I prefer to see things a little more the way they'll look in the end-product.

So, if you like, bring a little lighting in and switch back to *Lit* mode.

<br>

- In the **Place Assets / Modes** panel, there's a **Lights** section.

- Drag a **Directional Light** into the scene

- Switch back to **Lit** mode

- Adjust the **Directional Light**'s properties in the **Details** panel

<br><br>

### Basic parameters

I'll give you some basic parameters, then invite you go to forth and block out your own level as you see fit.

<br>

- Position this first **Box** brush at **origin** (0,0,0)

- Rename it *Floor1* in the **Outliner** 

> This will be a simple floor asset that you can use as a guide for scale and orientation.

- In the **Brush Settings** section of the **Details** panel, set the **Box** brush's **Z** value to **20**

- Set its **Y** value to about **1000**

- Set its **X** value to about **2000**

- In the **Content Browser**, navigate to **Content » StarterContent » Shapes**

- Drag a **Shape_Sphere** into the scene and position it at **origin**

> Think of this sphere as the player's starting point and scale - (the player's marble avatar will be about this big).

- Move **Floor1** downwards a little so that the shpere sits on top of it

- Slide **Floor1** forwards as you see below (ie. **positively** in the **X-axis**)

> I suggest using a grid snap of **100**

<br>


<br>

- Hold **Left-Alt** and again slide **Floor1** positively in the **X-axis**

> This time, a duplicate is created called *Floor2*

<br><br>

That's about all I need to stipulate, for now.

Using this forward orientation and rough scale, **go ahead and design an initial level.**

> You may wish to review this [Geometry turorial](https://github.com/DavidRandallPeters/UnrealEngine/blob/master/UE4_009_Labyrinth-G_Geometry.md) as a refresher

<br><br>

**Some considerations:**

1. The marble will be controlled by key input

2. The marble will roll and have basic physics (eg. gravity) 

3. We'll give it variable torque, acceleration and deceleration 

4. We can create moving platforms (but suggest you save those for subsequent levels)

5. This is just the first level - so perhaps don't make it too difficult to clock this one - suggest you ramp up the diffulty in subsequent levels

6. I'd suggest an overall path-length of around 20,000 units - though the level needn't be linear

7. Include boundary walls

8. Consider including thin, winding pathways

9. Consider including drops to lower levels

10. Consider where you might place pickups (remember; the player will need to collect 'em all before being allowed to proceed)

<br><br>

Mine looks like this at the moment:

<br>


<br><br>

---


