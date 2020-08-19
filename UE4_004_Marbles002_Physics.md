# Unreal Engine | 003 | MarbleGame 002 | Adding Physics

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

---

## 004.001 | Adding the Marble

<br>

Shortly, we'll add a ball to the level that we can roll around atop our *Floor* Actor.

In the process, we'll learn how to add content to our level from the *Content Browser*.

We'll also need to apply physics to that ball so that it rolls and balances as we need it to - so we'll get to that soon after.

Toward the end, we'll boost aesthetic appeal by applying various materials to the marble and the floor. 

<br>

Let's get that marble into the game:

- In the main editor, direct your attention to the **Content Browser**
- Navigate the folders to **Starter Content » Shapes**
- Locate the **Shape_Sphere** model
- Drag the **Shape_Sphere** model into the viewport and place it anywhere on the *Floor* Actor - notice that it snapped to the floor-plane - handy!

<br>

Just take a moment to take note of the fact that this is listed in the *Outliner* as a *StaticMeshActor*

---

## 004.002 | Renaming Actors

<br>

I probably don't need to explain why this is a good thing to know!

Let's call it **Marble**, instead.

<br>

![Rename](https://user-images.githubusercontent.com/36719180/90603614-a498ea00-e24f-11ea-819d-4175806a9c7e.png)

To rename the sphere do ONE of the following:

- Either double-click **Shape_Sphere** in the **Outliner**, or
- Select the sphere and edit the **Name** field atthe top of the **Details** panel

