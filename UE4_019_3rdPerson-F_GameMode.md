# Unreal Engine | 020 | 3RD PERSON F | Game Mode BP Class

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 019.001 | Spawn at Player Start

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

Curiously, we see a different view when we open it up for the second time.. This is a concise breakdown of its most important features.

> Note: We can still access the full blueprint by hitting *Open Full Blueprint Editor* at the top of this page. But there's no need to do that right now.

<br>

- Set  **Default Pawn Class** to the Player Pawn we created - **BP_PlayerPawn**
- **Compile**, **Save** and close this Blueprint

If we were to hit Play right now, we still wouldn't be spawned at PlayerStart, as we haven't yet assigned our Game Mode.

- sdgdsg

