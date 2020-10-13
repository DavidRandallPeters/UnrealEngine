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

When a node with a breakpoint is about to be executed, the game will pause and you'll be taken to the node in the Blueprint Editor's graph view. This gives us the opportunity to observe the values of variables and examine or step through the flow of execution within the Blueprin from that point forward.

<br>

- **Right-click** the **Branch** node and choose **Toggle Breakpoint** (or simply hit **F9**)
- **Compile** the blueprint - the breakpoint now shows a red icon, indicating that the breakpoint is set

<br>

![Breakpoint](https://user-images.githubusercontent.com/36719180/95828977-214cce00-0d92-11eb-9076-657fca76be7d.png)

<br>

- **Save** and hop over to the main editor
- Drag **BP_LevelRestartTrigger** into the viewport and scale / position it in such away that you can do a test

<br>

![Position box trigger](https://user-images.githubusercontent.com/36719180/95830396-198e2900-0d94-11eb-9a2d-e4fa50eb9301.png)

<br>

- Hit **Play** and roll off the edge - you should be taken to the breakpoint within the graph

<br>

![Breakpoint activated](https://user-images.githubusercontent.com/36719180/95831686-d6cd5080-0d95-11eb-9739-a4cf2bd11c49.png)

<br>

So, we've established that the *Box Trigger* is indeed detecting our *PlayerPawn*.

<br>

- Hop back into **BP_LevelRestartTrigger**
- Select the **Branch** node and hit **F9** to remove the breakpoint

<br><br>

---

## 024.002 | Restart current level

<br>

> We want to restart the level if our branch condition is *true*. 
- Drag off the **True** execution pin and search for **Get Current Level Name**
> Note: This node returns a *string* (pink)
- Drag off the **Get Current Level Name** node's execution pin and **Open Level** - as we did in the Labyrinth project
> Note: This node takes a variable input of type *name* (purple)
> *Names* are case INsensitive - they don't differentiate between capital and lower case
- Connect the **string** and **name** pins between these nodes - a conversion node is automatically created

<br>

![Level restart sequence A](https://user-images.githubusercontent.com/36719180/95922534-f1441000-0e0f-11eb-804b-20901f360f07.png)

<br>

- **Compile**, **Save** and go test it out

<br>

The level should now restart when your marble hits the *Box Collision*.

Remember that this blueprint is now completely reusable in any of your game's levels.

<br><br>

---

## 024.003 | Using Player Camera Manager to fade to black

<br>

UE4 spawns the *Player Camera Manager* into the game at runtime. You can see this for yourself by hitting *Play* and watching the *World Outliner*.

It's a non-physical class that contains functions and properties relating to the player's camera - and it's entirely accessible from any blueprint.

This is what we'll use to fade to black when the player screws up.

<br>

- Hop back into your **LevelRestartTrigger** blueprint
- Hold **Alt** and break the **Branch** node's **True** execution - we'll add the fade *BEFORE* the level restarts
- Drag the tail-end of the sequence off to the right to make some space
- **Right-click** in empty graph space and **Get Player Camera Manager**
- Drag off its **Return Value** and **Start Camera Fade**
- Connect **True** to **Start Camera Fade**

<br>

![Start Camera Fade](https://user-images.githubusercontent.com/36719180/95924894-f5266100-0e14-11eb-93fa-c280fad116b8.png)

<br>

> *From Alpha* is the "alpha at which to begin the fade" and has a range between 0 and 1. 0 is fully transparent and 1 is fully opaque.
- Leave *From Alpha* set to *0.0* and set **To Alpha** to **1.0**
> *Duration* is measured in seconds
- Give **Duration** a value of **1** or **2** seconds
- Change the fade *Color* if you wish. I'm leaving mine set to *black*
- If your game has (or will have) audio, you may wish to fade that by checking the bool box
- Set the **Hold when Finished** bool to **True**
> This node won't delay the exuction of code - so we'll need to add a *Delay* node with a duration that matches the fade
- Drag off the **Start Camera Fade** node's **Execution** pin and add a **Delay** node
> We could just enter the same value in each of these fields, but this comes close to being a magic number (despite it being clearly labeled within the node). To keep good practices, let's make a variable for this
- Via the **My Blueprint** panel, create a new variable of type **float** called *CameraFadeDuration*
- **Compile** (so that we can give this variable a value)
- In the **Details** panel, provide a value (in seconds) for your fade
- Drag the variable into the graph and **Get** it
- Connect **CameraFadeDuration** to both **Duration** inputs
- Connect the tail-end of the sequence:

<br>

![Add delay](https://user-images.githubusercontent.com/36719180/95925637-d1fcb100-0e16-11eb-9917-f2b41644da20.png)

<br><br>

- **Compile**, **Save**, and go try it out.

---

## 024.004 | Fade in at the start of play

<br>

We can't add to the above sequence to achieve this because:

a) the level will have been reloaded and the sequence will have therefore been abandoned

b) the first time we begin play, the *Box Collision* won't have been triggered

So we'll put this somewhere else - on something that we know will always be in any given level; the *PlayerPawn*.

<br>

- Open **BP_PlayerPawn**
- Find some space in the graph and repeat the appropriate steps above to acheive a camera fade-in - remember to invert the *From Alpha* and *To Alpha* values
> There's no need to *Hold when Finished* because, this time, the alpha will be transparent at the end of the fade.
- Connect this to the **Event Beginplay**

<br>

![Fade in](https://user-images.githubusercontent.com/36719180/95926519-01acb880-0e19-11eb-84f7-272243e486ed.png)

<br>

- **Compile**, **Save**, and go try it out. 

<br>

You should now have a fade-in at the start of the game, a fade-out when the player screws up and another fade-in when the level restarts.

<br><br>

---


