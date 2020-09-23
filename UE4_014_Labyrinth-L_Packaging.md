# Unreal Engine | 014 | Marble Labyrinth K | Packaging the game

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 014.002 | Adding a 'quit' key

<br>

If we build this game now, the player won't have the ability to exit the game without hitting **CTRL + ALT + DELETE** or **ALT + F4** (PC) or otherwise hard-quitting.

So we'll quickly add an escape button before we build.

<br>

- Open your **Level Blueprint**

- Find some space, **Right-click** and add an **Escape** key event (**Input » Keyboard Events » Escape**)

- Drag off the **Execution** pin and add a **Quit Game** node

- Finally, give this sequence a comment

<br>

![Quit game](https://user-images.githubusercontent.com/36719180/93955825-c46a8300-fda4-11ea-9930-6e191ed42502.png)

<br>

> Note that this key won't work in the editor - but it will work in a build

<br><br>

## 014.002 | Project settings

<br>

- In the top menu bar, go to **Edit » Project Settings**

> Here's your chance to determine the game's icon as it will be displayed in the *Epic Games Launcher* and file browsers

- Make an icon measuring 192px² and add it as the **Project Thumbnail** - (or you can use this one that I slapped together)

<br>

![Labyrinth icon](https://user-images.githubusercontent.com/36719180/93951560-c62f4900-fd9a-11ea-8f03-fa978f7df6f1.png)

<br>

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

## 014.003 | Packaging

<br>

You may have noticed when we created our various *Print String* nodes that written at the bottom of that node is: *Development only*

<br>

![Print string](https://user-images.githubusercontent.com/36719180/93953322-3fc93600-fd9f-11ea-9a7f-dc0d20affad9.png)

<br>

The tooltip when for this node states:

*"This node will only be executed in the editor and in Development builds in a packaged game (it will be treated as disabled in Shipping or Test builds cooked from a commandlet)"*

So, those messages to the player that we've carefully prepared won't be included in a *Shipping* build.

We're about to be presented with the option to do a *Development* build or a *Shipping* build. We'll obviously be better off choosing *Development*, this time around.


- In the top menu bar, go to **File » Package Project » Build Configuration** and just check that it's set for **Development**

- Go to **File » Package Project** and select the platform that you're currently working on

- Choose a destination for the packaged game and hit **Select Folder** / **Open** (depending on your platform)

> UE4 will immediatey begin packaging your game

- Once it's done, navigate your OS file browser to the destination you chose - UE4 will have created a folder called *WindowsNoEditor* or *MacNoEditor* etc.

- Change the folder name to something more suitable or pull its contents out and delete the folder

- **Launch your game and play it!!**

<br><br>

### If your custom icon didn't apply (Mac)

- Open your icon in **Photoshop**

- Select all (**CMND + A**) and **copy**

- Navigate to the Game build

- **Right-click** it and choose **Get Info**

- Select the icon swatch at the top of the pop-up 

- **Paste** the image

<br><br>

### If your custom icon didn't apply (PC)

- No idea! It's complicated! Something about converting to .ico format files!?!? (Don't even get me started).

<br><br>

<br><br>

### That's it for the Labyrinth game! Let's move onto some cooler stuff!






