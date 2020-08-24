# Unreal Engine | 006 | Marble Labyrinth 1D | Event Tick

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br><br>

---

## 006.001 | Event Tick

<br>

### Refactoring in Blueprints

Hopefully you're familiar with the concept of refactoring. It's the practice of reviewing code with a view to reduce resource costs and optimise performance, code resuability (elsewhere within your programme) and make your scripts more intuitive - for yourself and any other coders who might work on them in future.

Currently, our mouse input control system runs checks on each mouse axis between 50-100 times every second.. so, 100-200 calls every second.

We can halve that with a few tweaks.

<br>

- Open your **Level Blueprint**
- Drag a selection marquee around your mouse input control system and hit **C** to add a comment box
- Name it **Mk.1 mouse input control system**
- Break the links on the **Mouse X** and **Mouse Y** *Execution* pins (**Alt-click**)

<br>

![Mk1Mouse](https://user-images.githubusercontent.com/36719180/90993932-00c28c00-e60b-11ea-8151-94e1d53c6e5e.png)

<br>

- Find some space on the graph near *EventBeginPlay*, right-click and add an **Event Tick** node
>As you'll recall, this node runs on every frame
- Again, **Shift-select** a reference to **Floor** and a connected **AddActorWorldRotation** node
- Pan back to the *EventTick* node and hit **Ctrl-W** to duplicate the selected nodes
- Connect the **Execution** pins as you see below
- To test, just check that you have a value in one of the **Delta Rotation** fields (I have 5.0 in the X)

<br>

![EventTick01](https://user-images.githubusercontent.com/36719180/90994449-dbcf1880-e60c-11ea-81ae-abc076702abb.png)

<br>

- Compile and test it out

>The Floor should spin by 5 units on every frame.. just spinning constantly like a windmill.

<br>

Previously, we obtained the mouse axis information via the *Mouse X* and *Mouse Y* *Input Axis Events.*

These were found in the *All Actions for this Blueprint* menu under *Input » Mouse Events» ..* 

This time, we'll fetch *Mouse Values.*

<br>

- Back in the **Level Blueprint**, **right-click** in the graph near the **Event Tick**
- Drill down to **Input » Mouse Values** and choose **Mouse X**

<br>

![GetMouseX](https://user-images.githubusercontent.com/36719180/90994907-5f3d3980-e60e-11ea-886f-96538d5ff786.png)

>This node allows us to get the mouse axis value without using a dedicated Event.

<br>

- If the **Delta Rotation** pin isn't already split, split it now (**Right-click** it and choose **Split Struct Pin**)
- Connect the **Get Mouse X** node to the **Delta Rotation X (Roll)** input
- Add a **Get Mouse Y** node as we did just before
- We again need to invert the *Y* - Drag off the **Get Mouse Y** node's float output, release and search for **float*float**
- Set the **float*float** node -1.0 (to flip the value)
- Connect the **float*float** node to the **Delta Rotation Y (Pitch)** input

<br>

![GetMouseY](https://user-images.githubusercontent.com/36719180/90995659-b5ab7780-e610-11ea-82a5-7ce433f411e8.png)

<br>

Great. So we've acheived the exact same thing as before, but we've reduced our code.

At this point, you can delete the entire *Mk.1 Mouse input control system* if you like - or keep it around for reference.

<br>

- Comment your Event tick nodes as you see below:

<br>

![EventTick03](https://user-images.githubusercontent.com/36719180/90996168-0ec7db00-e612-11ea-82dc-57026abf9994.png)

<br>

- Do a general tidy-up in your *Level Blueprint* - maybe it looks something like this:

<br>

![TidyUp](https://user-images.githubusercontent.com/36719180/90996251-4767b480-e612-11ea-8156-026c1bd53772.png)

<br>

- Compile and test the game

<br>

We now have the exact same functionality as we did before - only we're using less code to achieve it.

We've also learned three different ways to capture input:

<br>

1. Key input Events
2. Mouse Axis Events
3. Get Mouse Values

<br>

Noice.

<br><br>

---

## 006.XXX | Removing 'Yaw-Creep'

Okay - I totally just made up that term. But it describes a small issue with our core gameplay mechanic:

- Play-test the game
- With your mouse, 'draw circles' - ie. keep making circles with your mouse and observe what the *Floor* Actor does..

As you continually pitch and roll, the *Floor* Actor becomes offset around its *yaw* (Z-axis).. It gradually creeps around and we don't want that because it'll mess up the synchronous between the orientation of our mouse-pad and the game-board.



<br><br>

---
