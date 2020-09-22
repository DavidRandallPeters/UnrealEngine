# Unreal Engine | 013 | Marble Labyrinth K | Bug Fixes and Code Cleanup

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 013.01 | Code cleanup

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

- Adjust the comment to include the welcome message

<br>

![Event Beginplay](https://user-images.githubusercontent.com/36719180/93945877-e60b4080-fd8b-11ea-9b7b-61a88099e8f0.png)

<br>



- **Compile** and hop back over to the editor

- Select the **Floor** Actor in the **Outliner** and delete it






