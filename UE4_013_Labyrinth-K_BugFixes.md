# Unreal Engine | 013 | Marble Labyrinth K | Bug Fixes and Code Cleanup

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 013.001 | Code cleanup

<br>

We've kind of blazed through this without maintaining clean code practices - so we'll take a moment now to make everything spick and span.

<br>

- Open your **Level Blueprint**

> We'll keep our Mk.3 Mouse input control which runs as part of the *Event Tick*

<br>

![Event tick](https://user-images.githubusercontent.com/36719180/93944727-97f53d80-fd89-11ea-8505-cb794e7d8b8c.png)

<br>

> We'll keep the Trigger event that detects the marble's escape and restarts the level - but we should apply a descriptive comment group:

- Select this sequence, hit **C** and comment it something like: *Escape detection + congratlulations + level restart*

<br>

![Escape detection](https://user-images.githubusercontent.com/36719180/93944962-19e56680-fd8a-11ea-8f1d-92d476a5d170.png)

<br>

> We're not using any key input anymore - so we can delete this whole set-up (don't fret - you have these repo notes to refer to if you ever want to set up key input again)

- Select the **Key input system** and delete it

<br>

![Key input system](https://user-images.githubusercontent.com/36719180/93945230-9ed08000-fd8a-11ea-8381-880ddbe43c33.png)

<br>

> We're not doing anything with the *Event BeginPlay* - but there's a *Print String* node sitting there that you might want to use to display a welcome message?

- Reconnect the **Execution** pin in the **Event BeginPlay** sequence

- Adjust the **Delay** so that it shows the message earlier

- Double-check the **Duration** that it will be displayed for and apply something suitable

- Comment as you see fit

<br>

![Event Beginplay](https://user-images.githubusercontent.com/36719180/93945877-e60b4080-fd8b-11ea-9b7b-61a88099e8f0.png)

<br>

- If you still have your **Mk.1 Mouse input control** kicking around, delete that too

<br>

![Mk.1 Mouse Input](https://user-images.githubusercontent.com/36719180/93946137-9416ea80-fd8c-11ea-93d2-da35459f6ec8.png)

<br>

> Everything should now be lookin' nice and tidy.

<br>

![All tidy](https://user-images.githubusercontent.com/36719180/93946489-87df5d00-fd8d-11ea-950c-c310502c7a10.png)

<br>

- **Compile** and hop back over to the editor

- Select the **Floor** Actor in the **Outliner** and delete it - we're done with that

<br><br>

---

## 013.002 | Bug fix 01 | Multiple win messages

<br>

Issue: You may not be experiencing this - but it's currently entirely possible for the marble to trigger the win message multiple times on its way out.

Even if this hasn't been an issue for you, *do* add this fail-safe:

<br>

- Hop back into your **Level Blueprint**

- In your **Escape detection** sequence, drag off the **OnActorEndOverlap** node's **Execution** pin

- .. navigate to: **Utilities » Flow Control » Do Once**

> This node does what it says on the can; everything downstream of this node will only be allowed to fire once - meaning we won't receive multiple 'win' messages 

<br>

![Do Once](https://user-images.githubusercontent.com/36719180/93947087-ff61bc00-fd8e-11ea-80d8-5bd664c7159c.png)

<br>

- **Compile**

<br><br>

---

## 013.003 | Bug fix 02 | Marble clipping

<br>

Issue: The marble sometimes clips through the floor when the board tilts quickly.

This happens because of UE4's *teleport* physics which instantly repositions Actors between frames.

We've briefly addressed this already by adding *CCD (Continuous Collision Detection)* to the marble in an attempt to improve its physics simulation.

The next simplest fix we can attempt is to throttle the mouse input so that those changes in board position can't become quite so drastic.

<br>

- Open your **Level Blueprint**

- Locate the **Get Mouse X** input node in the **Mk.3 Mouse input Control** system

- Drag off its **Return Value** pin and add a **Clamp (float)** node

- Drag off the **Clamp (float)** node's **Return Value** and replace the top connection in the **+** node for the *X (Roll)* calculation (see below)

> The required value will be specific to your labyrinth, depending on scale the extent of your issues.. The following clamp value is indicative. You may wish to come back and adjust these values later.

- Enter a **Min** clamp value of **-1.0**

<br>

![Mouse clamp - roll](https://user-images.githubusercontent.com/36719180/93949191-6e8ddf00-fd94-11ea-9956-c7af5843c076.png)

<br>

- Repeat these steps for the **Y (Pitch)** calculation:

<br>

![Mouse clamp - pitch](https://user-images.githubusercontent.com/36719180/93949618-36d36700-fd95-11ea-8ddc-2474c78c7aef.png)

<br>

- **Compile** and go try to break it..

<br>







