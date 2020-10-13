# Unreal Engine | 024 | 3RD PERSON J | Level Restart

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 024.001 | Custom Trigger Blueprint

<br>

We'll now create a custom *Box Trigger* blueprint that restarts the level when the sphere enters it.

This is how we can handle fuck-ups on the player's part - eg. falling into oblivion or otherwise touching something that mustn't be touched.

Unlike last time, in the Labyrinth game (which had only one level), we here want to create something that can be rolled out easily across multiple levels without repeating code.

So, instead, we'll create a custom BP Actor that we can place in each level and reuse endlessly.

While we're at it, we'll make it a little more cinematic and have the screen fade out before resarting the current level.

Let's begin!

<br>

- In the **Content Browser**, navigate to **Content» Blueprints**
- **Right-click** inside the folder and create a **Blueprint Class**
- Choose **Actor** and name it *BP_LevelRestartTrigger*
- Open **BP_LevelRestartTrigger**
- In the **Components** panel, hit **Add Component** and choose **Box Collision**
- Rename the new component to *BoxTrigger*
> Note: we won't make *BoxTrigger* the SceneRoot because it'll be handy to have the default sphere as a 'handle' when designing our level - the *Box Collision* will be difficult to select and scale on its own

<br>

![Box collision added](https://user-images.githubusercontent.com/36719180/95826524-eac18400-0d8e-11eb-9861-5c05e0631a51.png)

<br>

- Select **BoxTrigger**
- In the **Details** panel, locate the **Events** section
- Locate **On Component Begin Overlap** and hit its **+** button
> Nothing happens here in the *Viewport* - but an event has been created within this blueprint's *Event Graph*
- Tab over to this blueprint's **Event Graph** (if UE4 didn't take you there automatically)
> You may recall that *Other Actor* returns the value of the thing that collided with the *Box Collision*. We'll use this to check whether that thing was our *PlayerPawn*
- Drag off the **Other Actor** pin and release - search for **Equal (Object)**
> We'll use this to see if the returned value is 'equal to' our pawn
- **Right-click** in empty graph space and search for **Get Player Pawn**
> As this is not a multiplayer game, we know that our one and only *PlayerPawn* is at position zero in the array - so we can ignore this node's input
- Connect the **Get Player Pawn** node's **Return Value** to the **Get Player Pawn** node

<br>

![GetPlayerPawn](https://user-images.githubusercontent.com/36719180/95827672-87385600-0d90-11eb-9a4c-37d7d2a8804b.png)

<br>

> Notice that the **Equal (Object)** returns a boolean (true or false) + (red)
> We'll create a *branch* to field the result
- Hold the **B** key and **left-click** in empty graph space to create a branch
- Connect the **boolean** pins
- Connect the **execution** pins

<br><br>

### Breakpoints

[Breakpoints](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Debugging/index.html#:~:text=modes%20are%20active.-,Breakpoints,the%20Blueprint%20Editor's%20graph%20view.) are a means of debugging in Unreal.



