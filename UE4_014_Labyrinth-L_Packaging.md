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

- Hit the **+** button to the right of **List of maps to include in a packaged build*

- Navigate to the map that you're using and select it - mine's called *Level01.umap* (don't choose any 'BuiltData' you find)

- Close **Project Settings** and hop back into the editor

<br><br>

---

## 014.002 | Project settings

<br>







