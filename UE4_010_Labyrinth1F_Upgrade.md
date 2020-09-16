# Unreal Engine | 010 | Marble Labyrinth 1G | Upgrading the game

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 010.001 | Overview + mobility

<br>

So, we have a shiny new maze - but it just sits there when we playtest.

We need to hook it up to our *Level Blueprint*

Before we start, we should make sure this new *Static Mesh* doesn't remain static when we try to control it.

<br>

- Select the **Maze001** Actor 

- In the **Transform** section of the **Details** panel, set its *Mobility* to **Movable**

<br><br>

---

## 010.002 | Replacing references

<br>

To make the game use the new maze we built instead of the old floor Actor, we simply need to switch out our references.

<br>

- Make sure that the **Maze001** Actor is selected in the viewport

- Open your **Level Blueprint**

- Locate your **Event Tick** sequence

- Near the reference to **Floor**, right-click and **Create a Reference to Maze001**

- Delete the reference to **Floor**

- Connect the reference to **Maze001** to the **GetActorRotation** node in its place

- At the end of this sequence, do the same, connecting another reference to **Maze001** to the **SetActorRotation** node

- Compile and hop back over to the main editor / viewport

- Before we test this, adjust the location of your **Player Start** so that it has a decent view of the board

- Hit **Play** and test it out

<br>

![First test](https://user-images.githubusercontent.com/36719180/93291393-0e001e80-f837-11ea-9690-371a2142dbc3.png)

<br>

The board should now be tilting as we want it to - but the ball falls through the floor..

<br><br>

---

## 010.003 | Adding collision

<br>

To stop the marble from falling through the floor, we need to apply collisions to the *Maze001* Static Mesh.

Here's how:

<br>

- Browse your **Content Browser** to the **Mazes** folder

- Double-click the **Maze001** Static mesh to open it in its own window - (maybe dock this window alongside *Level01* etc.)

- In the top menu bar, here in the *Mesh Editor*, choose **Collisions » Box Simplified Collision**

<br>

This won't work for us as it is, because it's just a big box that covers our whole maze.. 

However, if one of the following two conditions are true for you, personally, you may wish to come back to this method, scale *Box Simplified Collisions* to fit your walls, and duplicate and scale multiple successive collision boxes - as this method will yield more accurate physical response - at least in the case of our marble labyrinth game. It should also be slightly lighter on resources. 

Here are those conditions:

1. You have time.
2. Your marble gets snagged on the collisions we're about to create.

<br>

- For now, delete the **Collision** that we just added

- Locate the **Collision** section of the **Details** panel on the right

- Via the **Collision Complexity** dropdown, choose **Use Complex Collision As Simple**

> Note that this method would get a bit heavy on resources in a larger production - the preferred method for generating collisions for larger games would be via modeling software such as Maya .. but this method will be perfectly fine for our wee maze game.

- Hop back over to the main editor/viewport

- Hit **Play** to test this out

<br>

If you find that your marble gets snagged, take the time to apply multiple *BoxSimplified Collisions*, as mentioned above.

You may find that the marble still clips through the floor sometimes. This will likely happen when you rotate the board too quickly.. The marble is on one side of the floor in one frame, and on the other side the next. I'll offer a quick-maybe-fix right now.. but we'll come back and fix bugs like these later in the piece.

<br><br>

### Quick bug fix: Marble clipping


