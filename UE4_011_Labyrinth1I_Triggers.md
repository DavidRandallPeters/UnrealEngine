# Unreal Engine | 011 | Marble Labyrinth 1I | Triggers and Overlap Events

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 011.001 | 

The goal here is to create an event when the marble passes through the escape hatch - allowing us to do things like congratulate the player and start loading the next level.

We'll do this by adding a adding a *Box Trigger* to the map that will detect the ball and generate an event.

<br>

- In the **Place Actors** panel, select the **Basic** category

- Scroll down and drag a **Box Trigger** into the viewport

- Position the **Box Trigger** beneath the escape hatch of your maze

- Scale it so that there's no way that the marble won't pass through this region on its way out

<br>

![Box Trigger](https://user-images.githubusercontent.com/36719180/93303463-97bbe600-f84f-11ea-911e-dd5156b9f531.png)

<br><br>

---

## 011.002 | Parenting

<br>

The *Box Trigger* is now positioned appropriately - but our maze will constantly be moving during gameplay - while the Box Trigger remains static in its current position. 

We can easily solve this by parenting it to the Maze001 Actor (ie. making it a child of that Actor) so that it moves whenever and wherever the maze does.

<br>

- In the **Outliner** simply drag the **TriggerBox** on top of **Maze001** to make *Maze001* the parent of *TriggerBox* - easy

- To test that we've got this right, select just the **TriggerBox**

- In the **Details** panel, scroll down to the **Rendering** section

- Uncheck **Actor Hidden In Game** - the *TriggerBox* will now render during gameplay

- Hit **Play** to double-check that the *TriggerBox* is moving with the *Maze001* Actor
