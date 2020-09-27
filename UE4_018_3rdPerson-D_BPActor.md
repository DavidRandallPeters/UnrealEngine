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

## 018.002 | Blueprint Actor Class

<br>

The first *Blueprint Actor* that we'll create will be the collectable objects - the items that the player must collect ALL of in order to complete the level.

The object needs a mesh (so that we can see something), a trigger of some sort so that the player can collect it, some motion (eg. spinning or bobbing up and down) and possibly some light emission?

The main property it should have, however, is *resuability.* That is, a lightweight asset that can deployed over and over again without costing the earth in resources.

The *Blueprint Actor Class* will achieve that. This is essentially Unreal's equivalent of a *Prefab*.

So:

<br>

- Create a **New Folder** in the **Content** root directory called **Blueprints** 
- Go into that folder, **right-click** and create a **Blueprint Class** - a pop-up appears
- From the **Pick Parent Class** pop-up, choose **Actor**
- Name the new Actor *BP_Pickup001*
> 'BP' is obviously an abbreviation of 'Blueprint' (so that we can readily identify it in lists etc. later on) and we're calling it 'Pickup 001' because a) it's our main pickup and b) you may wish to subsequently create other pickups that have different properties.
- **Double-click** **BP_Pickup001** to open it up

<br>

![Default Root](https://user-images.githubusercontent.com/36719180/94376680-8096c580-0178-11eb-80b3-45837e6870b1.png)

<br>

A *Blueprint Actor* contains *components*. In this case, our *Blueprint Actor* will contain a mesh, a light and a trigger.

*Actor Blueprints* also contain *graphs* (as we've so far only seen in the *Level Blueprint*. This is how we can also add custom funcationality to objects in addition to the components mentioned above.

Here inside the *BP_Pickup001* blueprint, as with the *Prefab* editor in Unity, we see a visualisation of the Actor and have the ability to assemble and transform its components. 

You'll notice a list of its components in the **Components** panel (top-left by default). Currently, we only see a *DefaultSceneRoot* - represented by the white sphere positioned at origin.

Every Actor needs a *root* component - its transform in the level is derived from this - additional components beyond the *root*, are *children of the root* (cool band name, right there) and are therefore positioned relative to the *root*.


<br><br>

---

## 018.003 | Adding components to a Blueprint Actor

<br>






