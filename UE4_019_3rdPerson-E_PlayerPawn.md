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
- Name the new **Pawn** blueprint *BP_PlayerPawn*
- **Double-click** it to open it up
- Add a **Static Mesh** component
- Add a **Shape_Sphere** static mesh in the **Stative Mesh** section of the **Details** panel - you can do this way we did before.. or you can use the drop-down to manually search for it

<br><br>

---

## 019.002 | Spring Arms and Cameras

<br>

A *Spring Arm* is a component that won't render in the game - but acts to determine the distance between a Camera and an Actor - in this case our marble.

The Spring Arm is represented in the Blueprint editor by a red line.

<br>

- With the **StaticMesh** selected in the **Components** panel, add a **Spring Arm** component - it becomes a child of *StaticMesh*
- With the **SpringArm** selected in the **Components** panel, add a **Camera** component - it becomes a child of *SpringArm*
> The camera is now positioned at the end of the Spring Arm and faces the DefaultSceneRoot

> The Spring Arm is currently originating from 0,0,0 - we need it to originate from the centre of the sphere so that the camera is looking in the right place

- Set your grid snap to **50**uu and move the **SpringArm** upwards so that it originates from the centre of the marble

> The **Target Arm Length** parameter in the **Details** panel determines the distance of the Camera from the Static Mesh

> Rotating the Spring Arm around its **Y** axis adjusts its vantage point

- Tweak the values just mentioned - but don't stress - we'll fine-tune this later
- To make the **StaticMesh** the root of the scene, drag it (in the **Components** panel) and drop it on top of **DefaultSceneRoot**
- **Compile**

<br>

![Camera and Spring Arm](https://user-images.githubusercontent.com/36719180/94384799-efd3e000-019f-11eb-8fce-d2650ef7240a.png)

<br>

We now have a Camera that will render the action attached to a Spring Arm that's attached to our Player Pawn.

<br><br>

---

## 019.003 | dsgdsg

<br>

A *Spri



