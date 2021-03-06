# Unreal Engine | 001 | Getting Started

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

---

## 001.001 | Getting started

Let's get straight into it.

- Fire up the **Epic Games Launcher**
- If you haven't already, create an account with Epic Games
- If/when you have an account ready, log in to it
- Locate the **Unreal Engine** tab at the top of the launcher and select it
- Hit the **drop-down arrow** to the right of the big yellow launch button and double-check that you're using the latest version of UE4 available in this lab. If not, select the latest version.
- Hit the big yellow **Launch** button  
<br>

![LaunchBar](https://user-images.githubusercontent.com/36719180/90474783-2fa7b080-e17a-11ea-8aef-b6ef6d01b22b.png)

Note: You can also launch your desired version via the *Library* tab.
<br><br>

---

## 001.002 | Creating a project

You're now being presented with the *Unreal Project Browser.*

You *may* see a list of varioius industries that UE4 is used within:

>1. Game
>2. Film, Television and Live Events
>3. Achitecture, Engineering and Construction
>4. Automotive, Product Design and Manufacturing

>(Game Development is by no means UE4's only application)  


<br>
.. Or you may be looking at a range of Game templates.

- If you see the applications listed above, choose **Game** 
- From the range of *Game* templates, choose the **Blank** project
- In *Project Settings,* we have the option of targeting *Desktop/Console* or *Mobile/Tablet*. Choose **Desktop/Console**.

>Note: your choice here can later be changed within the editor after launch (in the *Target Hardware* section of *Project Settings*)  


<br>

- We can also tweak the quality / performance characteristics of the project (leave this set to **Maximum Quality**) and choose whether to include Starter Content or not - *DO* choose **With Starter Content**
- We do want to create a Blueprint project rather than a C++ project - so leave that as it is - and the latest versions of UE4 allow real-time raytracing (which is rather exciting) - but leave **Raytracing Disabled** for now.  
<br><br>

![ProjectSettings](https://user-images.githubusercontent.com/36719180/90495055-41984c00-e198-11ea-8b40-2238dd3ecfb9.png)  
<br><br>


- Double-check the project's folder location
- And give it a name: **MarbleRun**  

>Note: This needs to be written in the CamelCase naming convention - spaces are not allowed  


<br>

- Finally, hit **Create Project** and your new project will initialise.  
<br><br>

---
## 001.002 | The Unreal Editor  

Having spent time using Unity, what you see now will feel familiar.. yet different.  

![UnrealEditor](https://user-images.githubusercontent.com/36719180/90500101-8921d680-e19e-11ea-939c-b39ad9477ed9.png)  


Some key differences:

>- What Unity calls the 'Heirarchy' is here called the *World Outliner*
>- What Unity calls the 'Inspector' is here called the *Details* panel
>- What Unity calls the 'Assets' panel is here called the *Content Browser*
>- What Unity calls GameObjects, Unreal calls 'Actors'

<br>

- Take some time to familiarise yourself with navigation in the viewport.

>Note: Unreal has handy snapping tools (top-right of viewport) that can be disabled and edited.

<br>

Your primary hotkeys are **W**, **E** and **R**.  
<br>

By all means rearrange the panels to make yourself comfortable.  
>Note: If you accidentally close a panel, these can be restored via the *Window* menu.  


<br><br>

---

## 001.003 | Actors in a World

In Unreal, what you'll think of as a 'Scene' is referred to as a *World* - (also, a *Level* or *Map*). Actors listed in the *World Outliner* (let's just refer to this as the 'Outliner') exist within this World. 

- Take some time to select various **Actors** in the **Outliner**, hit **F** to frame/focus/find them in the viewport (yip - that works here, too) and familiarise yourself with Unreal's approach to these familiar concepts.
<br><br>


---

## 001.004 | Starter Content

The chairs and table that we see in the viewport, we see because we chose to include *Starter Content*.

Notice, in the *Content Browser*, that there's a foler called *Starter Content.*

- Open the **Starter Content** folder - you'll see a range of other folders containing toys that we can play with
- Open the **Maps** folder - here's where this world is saved - it's called *Minimal Default*.
- Take note of the *Map* icon's appearance for future reference

![LevelIcons](https://user-images.githubusercontent.com/36719180/90502676-55e14680-e1a2-11ea-91cc-e179a4f4104d.png)

>By all means open the other worlds and take a look. You may need to wait some time for shaders to compile before they look pretty. The *StarterMap* contains various particle effects, materials and audio that you may wish to use for your own projects.  

![StarterContent](https://user-images.githubusercontent.com/36719180/90503630-e10f0c00-e1a3-11ea-8d0b-4568943e2c0b.png)
<br><br>

---

## 001.005 | Creating Levels

Before we make a start using Blueprints, let's freshen up and clear the board.

- When you're done exploring, go to **File » New Level** and choose **Default**
- By all means save the *Minimal Default* World, if you like
- Hit **Save Current** on the main toolbar (top left)
- Call it *Level01*
- In the **Content Browser**, navigate to the root directory (called **Content**). You'll see the new *Level01* Map and it's buddy - *Level01_BuiltData*
- Right-click in the **Content Browser** and create a new folder called *Maps*
- Select and drag **Level01** and **Level01_BuiltData** onto the **Maps** folder to keep things organised
- Choose **Move Here**

<br><br>

#### Continued in UE4_002_IntroToBlueprints

---



