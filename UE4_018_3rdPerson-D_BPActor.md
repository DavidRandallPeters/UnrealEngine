# Unreal Engine | 018 | 3RD PERSON C | Blueprint Actor Class

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 018.001 | Player Start

<br>

The in-built [Player Start](https://docs.unrealengine.com/en-US/Engine/Actors/PlayerStart/index.html#:~:text=Guide%20to%20using%20Player%20Starts.&text=The%20ability%20to%20spawn%20a,the%20player%20will%20start%20from.) marker is essentially a spawn point for our player's avatar. Should our marble fall into oblivion or otherwise be destroyed, this is how we can indicate where to respawn.

<br>

- Delete the **Shape_Sphere** that we placed at the start of the map for scale 

- From the **Basic** section of the **Place Actor / Modes** panel, drag a **Player Start** into the level

- Position it at the start of your level where you'd like the player to start / respawn

<br>

![Player Start](https://user-images.githubusercontent.com/36719180/94376080-b934a000-0174-11eb-8673-027fed6bad35.png)

<br>

> Note: if you get a *BAD size* icon - this usually means that Unreal is detecting a collision overlap. Moving the *Player Start* clear of any conflict will remove this icon. It may detect the *Shape_Sphere*'s collision for a few moments after its been deleted.

<br><br>

---

## 018.002 | Blueprint Actors

<br>

The 



