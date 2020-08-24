# Unreal Engine | 006 | Marble Labyrinth 1D | Event Tick

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br><br>

---

## 006.001 | Refactoring in Blueprints

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

Blah




<br><br>

---

## 006.XXX | Removing 'Yaw-Creep'

Okay - I totally just made up that term. But it describes a small issue with our core gameplay mechanic:

- Play-test the game
- With your mouse, 'draw circles' - ie. keep making circles with your mouse and observe what the *Floor* Actor does..

As you continually pitch and roll, the *Floor* Actor becomes offset around its *yaw* (Z-axis).. It gradually creeps around and we don't want that because it'll mess up the synchronous between the orientation of our mouse-pad and the game-board.




<br><br>

---