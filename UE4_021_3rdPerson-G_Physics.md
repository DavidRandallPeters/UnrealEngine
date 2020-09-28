# Unreal Engine | 021 | 3RD PERSON G | Adding Physics to Player Pawn

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 021.001 | Applying Physics

We need our Player Pawn to respond to physics for the game to even begin being enjoyable.

The first part of achieving this is easy. We've done it before (in the Labyrinth game). 

The same approach applies here, only we'll be asking the sphere inside our Player Pawn blueprint to simulate physics: 

<br>

- Open **BP_PlayerPawn**
- Select the **StaticMesh** [root] Actor in the **Components** tab
- In the **Physics** section of the **Details** panel, check **Simululate Physics**
- **Compile** and **Save**
- Go back to the main editor and raise your **PlayerStart** up into the air somewhat
- Hit **Play** to test it out

<br>

That's it.. That works.. The marble drops and the camera follows it. Grrrreat.

<br>

- Bring a **Basic » Cube** into the level from the **Place Actors / Modes** panel
- Quickly shape it like a ramp and position it under the **PlayerStart**
- Hit **Play** and test it out.

<br>

![Ramp](https://user-images.githubusercontent.com/36719180/94394501-fb340500-01b9-11eb-9228-350495a8b592.png)

<br>

Shit.

When the ball started rolling, the camera rolls with it..

This is because it's attached and relatively positioned to its parent; the Sphere Static Mesh.

So we need to mitigate.

<br><br>

---

## 021.002 | World Rotation vs. Relative Rotation

- Open **BP_PlayerPawn**
- Select the **SpringArm** in the **Components** panel
- In the **Transform** section of the **Details** panel, hit the drop-down arrow just to the right of **Rotation**
- Choose **World**
- **Compile**, **Save** and go test it out021

