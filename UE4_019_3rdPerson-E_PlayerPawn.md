# Unreal Engine | 019 | 3RD PERSON D | Player Pawn

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 019.001 | Player Pawn

<br>

[*Player Pawn*](https://docs.unrealengine.com/en-US/Gameplay/Framework/Pawn/index.html) is Unreal's term for the player character / avatar - whatever that may be.

In their words:

"The Pawn class is the base class of all Actors that can be controlled by players or AI. A Pawn is the physical representation of a player or AI entity within the world. This not only means that the Pawn determines what the player or AI entity looks like visually, but also how it interacts with the world in terms of collisions and other physical"

Ours will be a sphere (marble).

Let's get that into the game:

<br>

- Navigate to your **Blueprints** folder in the **Content Browser**
- **Right-click** inside that folder and choose **Blueprint Class**
- From the pop-up that appears, select **Pawn** - *".. an Actor that can be 'possessed' and receive input from a controller"*



