# Unreal Engine | 003 | Marble Labyrinth B | Adding Physics

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

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

![Sphere](https://user-images.githubusercontent.com/36719180/90603806-f772a180-e24f-11ea-8133-7833b48389de.png)

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

<br>

---

## 004.003 | Applying Materials

<br>

![MaterialDetails](https://user-images.githubusercontent.com/36719180/90604058-618b4680-e250-11ea-8cfb-5ab1c7eabda6.png)

<br>

Notice that when you havethe _Marble_ Actor selected, you can see its *Material* details in the *Details* panel (as above).

Applying existing materials is extremely straightforward.

Again, you have two options:

<br>

- First, navigate in the **Content Browser** to: **Starter Content » Materials**
- Explore the folder until you've identified a material that you'd like to use for your *Marble*

<br>

To apply:

- Either drag that material from the **Content Browser** directly onto the **Marble** Actor in the viewport, or
- With the **Marble** Actor selected, drag that material from the **Content Browser** into the **Materials** slot in the **Details** panel

<br>

In either case, the *Materials* slot in the *Details* panel will be updated to reflect that change.

While we're at it, we might as well apply a fresh Material to the floor.

<br>

- Repeat the above steps to give the **Floor** Actor a lick o' paint

<br>

![MaterialsAdded](https://user-images.githubusercontent.com/36719180/90605619-b9c34800-e252-11ea-8c08-14eaa4caef85.png)

<br>

---

## 004.004 | Applying Physics

<br>

If you hit *Play* now, your marble will simply remain wherever you placed it. We need to apply physics in order for it to interact with other Actors in the level. This is also pretty straightforward:

- Select the **Marble** Actor
- In the **Details** panel, scroll down until you find the **Physics** section
- Check the **Simulate Physics** checkbox

<br>

![SimulatePhysics](https://user-images.githubusercontent.com/36719180/90606497-06f3e980-e254-11ea-86e1-189c1ec66d5b.png)

<br>

That's all there is to it.

<br>

- Reposition the **Marble** Actor so that it's a little bit in the air above the **Floor** Actor
- Hit **Play** and test it out
- Try tilting your *Floor* Actor using the keyboard inputs that we programmed earlier

<br>

Okay, so things get a bit freaky pretty quickly - but this is a good start. We'll take measures to make this more playable.

<br>

---

## 004.005 | 'Teleport' Physics

<br>

Our marble is being dramatic because default UE4 physics have been applied.

When we tilt the Floor, UE4 reads this as its velocity changing momentarily - so it logically applies an upwards force to the ball.

In another game, we might want *exactly that* to happen. But here, we want a little more finesse.

<br>

What we're going to do to solve this is *'Teleport' the physics state of the Actor*.

Don't let that freak you out - its bark is worse than its bite:

<br>

- Go into your **Level Blueprint** and locate any of your **AddActorWorldRotation** nodes
- Expand the node by hitting the arrow at the bottom of the node - notice the *Teleport* checkbox
- Hover your mouse cursor over that checkbox and read the tooltip:



![TeleportTooltip](https://user-images.githubusercontent.com/36719180/90608287-7cf95000-e256-11ea-8a21-cd8d58ae7461.png)

This is basically a confusing way of determining whether or not to use collisions.

<br>

- Check the **Teleport** checkbox in all four of your rotation functions:

![TeleportOn](https://user-images.githubusercontent.com/36719180/90610804-10805000-e25a-11ea-869e-c98b3507793d.png)

<br>

- Compile and head back out to the editor viewport
- Hit **Play** to test the game

<br>

You should now find it somewhat more playable.

Certainly, it's not perfect.. it's a bit difficult to control and we have to button-mash the controls to keep up.

But that's okay - we're going to add programming that makes this a smoother experience.

<br><br>

#### Continued in UE4_005_Labyrinth-C_AxisEvents.md

---














