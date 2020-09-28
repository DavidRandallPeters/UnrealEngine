# Unreal Engine | 020 | 3RD PERSON F | Game Mode BP Class

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 020.001 | Spawn at Player Start

<br>

We have a Player Pawn which we auto-possess at run-time.

We'll now make it so that we spawn in at Player Start.

To do this, we'll utilise one of Unreal's main classes; the *Game Mode Blueprint*.

The [Game Mode](https://docs.unrealengine.com/en-US/Gameplay/Framework/GameMode/index.html) class controls the rules of our game.

Part of that includes assigning the default Pawn class. It will also look for a Player Start within the level and spawn that class at the given location.

<br>

- Navigate to your **Blueprints** folder
- **Right-click** and create a **Blueprint Class** and select **Game Mode Base**
- Name it *BP_GameMode*
- Open it up
- Close it again!
- Open it up again!

> Curiously, we see a different view when we open it up for the second time.. This is a concise breakdown of its most important features.

> Note: We can still access the full blueprint by hitting *Open Full Blueprint Editor* at the top of this page. But there's no need to do that right now.

<br>

- Set  **Default Pawn Class** to the Player Pawn we created - **BP_PlayerPawn**
- **Compile**, **Save** and close this Blueprint

> If we were to hit Play right now, we still wouldn't be spawned at PlayerStart, as we haven't yet assigned our Game Mode.

- Use the **Settings** drop-down above the main viewport and choose **World Settings** - a new tab is opened alongside the *Details* panel
- In the **Game Mode** section of the **World Settings** panel, set **GameMode Override** to use **BP_GameMode**

> If we were to hit Play now, we STILL wouldn't be spawned at PlayerStart as we still have our Player Pawn manually added to the level. Unreal will default to that when present. To make this fully dynamic, we'll delete the PlayerPawn and hand Unreal the reigns.

- Select **BP_PlayerPawn** in the level (or the **Outliner**) and delete it
- Hit **Play** to test it out.

Our Player Pawn is now spawned at Player Start, wherever that may be. 

<br>

---

## 019.002 | Setting a custom Game Mode as default

<br>

There's one more thing we can do.

The method we've used to make Unreal use our custom Game Mode (and not the default) involved overriding the default for this level (we did that via the World Settings).

When we create subsequent levels, we'll need to keep applying this override as often as we create levels.

As our requirements are universal, a better approach for our game would be to set the Game Mode that we created as the default Game Mode throughout our project.

To do this:

<br>

- Open the **Project Settings** (**Edit » Project Settings**)
- Go to the **Maps & Modes** section
- Set the **Default GameMode** to **BP_GameMode**
- Close **Project Settings**

<br>

Aaaaaand we're done. Moving on.

<br><br>

---





