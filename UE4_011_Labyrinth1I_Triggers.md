# Unreal Engine | 011 | Marble Labyrinth 1I | Triggers and Overlap Events

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 011.001 | Box Triggers

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

<br><br>

---

## 011.003 | 

<br>

sdgg

<br>

- Ensure that the **TriggerBox** is selected

- Open your **Level Blueprint**

- **Right-click** in empty graph space and expand the **Add Event For Trigger Box 1** option (top of the list)

- Expand **Collision** to show *Collision* events

- Choose **Add On Actor End Overlap** - this will generate an event when the marble *leaves* the trigger box having made contact with it

> *OnActorBeginOverlap* fires when the Actor first touches it

<br>

![OnActorEndOverlap](https://user-images.githubusercontent.com/36719180/93311840-980dae80-f85a-11ea-8bfe-0dc2d23e9d26.png)

<br>

> *Overlapped Actor* is (in this case) essentially a reference to self - ie. THIS TriggerBox was overlapped

> *Other Actor* is a reference to whatever interacted with the TriggerBox

<br>

> To test this out, we'll print a messsage to the screen:

- Drag off the **Execution pin** and start typing **Print String** (and choose *Print String*)

- In the **In String** field, replace *Hello* with something like *Marble escaped*

<br>

![Print string](https://user-images.githubusercontent.com/36719180/93314532-fdaf6a00-f85d-11ea-8c8d-4a6fb7fdf115.png)

<br>

- Compile and hop back over to the editor

> If we tested this now, it wouldn't work - the reason is that the Marble has not been told to generate *Overlap Events*

- Select the **Marble**

- In the **Details** panel, locate the **Collisions** section

- Check the **Generate Overlap Events** checkbox

> You may want to move your marble so that it's just next to the exit to save you time

- Hit **Play** and try it out

<br>

![Marble escaped](https://user-images.githubusercontent.com/36719180/93314459-de184180-f85d-11ea-94e7-bf72ebbbe06b.png)

<br><br>







