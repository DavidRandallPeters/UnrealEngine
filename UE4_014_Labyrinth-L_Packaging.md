# Unreal Engine | 014 | Marble Labyrinth K | Packaging the game

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 014.001 | Project settings

<br>

- In the top menu bar, go to **Edit » Project Settings**

> Here's your chance to determine the game's icon as it will be displayed in the *Epic Games Launcher* and file browsers

- Make an icon measuring 192px² and add it as the **Project Thumbnail** - (or you can use this one that I slapped together)

<br>

![Labyrinth icon](https://user-images.githubusercontent.com/36719180/93951560-c62f4900-fd9a-11ea-8f03-fa978f7df6f1.png)

<br>

- Enter a name for your game in the **Project Name** field

> There are other details here that you can fill out, if you like. But We probably don't need to worry too much about these for this particular project

- Under **Project**, select the **Maps & Modes** section

> You may alread have noticed that the UE4 editor often launches in a different level to the one you're working on. Here's where you can change that.
> It's also where we'll determine which level the built game should use.

- Adjust both the **Editor Startup Map** and the **Game Default Map** to use the level that contains your marble labyrinth - mine's called *Level01*

- Under **Project**, select the **Packaging** section

> Our project contains a whole lot of assets and levels that we won't want or need to include in this build. Here's where we cull that stuff.

- Hit the wee white arrow at the bottom of the **Packaging** section to **Show Advanced** options

- Check the **Cook only maps** checkbox

> That part states that we want to be selective - now we need to determine what to include

- Hit the **+** button to the right of **List of maps to include in a packaged build**

- Navigate to the map that you're using and select it - mine's called *Level01.umap* (don't choose any 'BuiltData' you find)

- Close **Project Settings** and hop back into the editor

<br><br>

---

## 014.002 | Packaging

<br>

You may have noticed when we created our various *Print String* nodes that written at the bottom of that node is: *Development only*

<br>

![Print string](https://user-images.githubusercontent.com/36719180/93953322-3fc93600-fd9f-11ea-9a7f-dc0d20affad9.png)

<br>

The tooltip when for this node states:

*This node will only be executed in the editor and in Development buildsin a packaged game (it will be treated as disabled in Shipping or Test builds cooked from a commandlet)*

So, those messages that we've carefully prepared won't be included in a *Shipping* build

We're about to package our game - and we'll be presented with the option to do a *Development* build or a *Shipping* build. We'll obviously be better off choosing *Development*, this time around.


- In the top menu bar, choose **File » Package Project** and select the platform that you're currently working on

- 







