# Unreal Engine | 002 | Intro to Blueprints

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

---

## 002.001 | Pawns

First up, take a note of how many actors are currently listed in the *Outliner.* You likely see 7 Actors.

Now let's play-test this opus.

- Hit the big **Play** button in the main toolbar (top)
<br>

Nothing very much happens - though, there are now something like 18 Actors in the *Outliner* - one of these is the *DefaultPawn* Actor.

We now have the ability to look and move around our level using WASD and mouse input.

Notice that we also have some collision in place - we can't move through the 'Floor' *StaticMeshActor.*

We're currently playing the game as Unreal's default *Pawn*.
<br><br>

***Pawns:***  

A *Pawn* is an *Actor* (class) that can be possessed and controlled by a player - a physical representation of the player or AI entity in the *World.*

While the *Pawn* class provides only the bare essentials, the *DefaultPawn* subclass comes with some additional components and functionality.

That's all you need to know about them for now - but by all means, read more about them [here](https://docs.unrealengine.com/en-US/Gameplay/Framework/Pawn/index.html)
<br><br>


