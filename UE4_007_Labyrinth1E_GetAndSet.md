# Unreal Engine | 007 | Marble Labyrinth 1E | Getting and Setting

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br><br>

---

## 007.001 | Removing 'yaw-creep' by Getting and Setting values

<br>

### The problem

Okay - I totally just made up the term 'yaw-creep' - but it describes a small issue with our core gameplay mechanic.

<br>

Let's demonstrate:

<br>

- Play-test the game
- With your mouse, 'draw circles' - ie. keep making circles with your mouse and observe what the *Floor* Actor does..

<br>

As you continually pitch and roll, the *Floor* Actor becomes offset around its *yaw*.. It gradually creeps around the *Z-axis* and we don't want that because it'll mess up the synchronous between the orientation of our mouse-pad and the game-board - resulting in awkward gameplay.

We're now going to solve this problem with some new and versatile coding tricks.

<br>

### Getting values

In order to *set* values to suit our needs, we first need to *get* them.

<br>

- Go into your **Level Blueprint**
- Locate your *EventTick* sequence, select the **AddActorWorldRotation** node and delete it
>It's served us well so far - but we need a little more control
- Click and drag out from the Reference to **Floor**'s blue (Object) output pin and release
- Drill down to **Utilities » Transformation**
>This is where we previously found *AddActorWorldRotation*
- Keep scrolling down.. Locate and choose **GetActorRotation**

<br>

![GetActorRotation](https://user-images.githubusercontent.com/36719180/91001768-c06e0880-e620-11ea-86fa-df18ab451dfe.png)
>If you read the return pin's tooltip, you'll notice that the Return Value [variable] is of type *Rotator*
<br>

- **Right-click** the **GetActorRotation** pin's **Return Value** pin and choose **Split Struct Pin**
>We now have access to the three axis values

<br>


- **Right-click** one of the new **Return Value** pins (X, Y or Z) and choose **Recombine Struct Pin** to collapse them back down to a single return pin
> (Just wanted you to see that a *Rotation* variable actually contains three values)

<br>

- Click and drag off the singular **Return Value** pin and release to bring up the context-sensitive menu
- Start typing **Break Rotator** and choose it when it becomes available
> This is just another way to access those three values

<br>

![BreakRotator](https://user-images.githubusercontent.com/36719180/91004073-44c38a00-e627-11ea-8110-945b44538f4c.png)

<br><br>

### Setting values

We're now successfully retreiving the values we need. Now we'll see about setting those values to better suit our needs.

<br>

- Select your *Reference* to **Floor** and duplicate it (**Ctrl+W**)
- Click and drag off its return pin and release to bring up the menu
- Drill down to **Utilities » Transformation** and scroll until you find **SetActorRotation** and select it
- Connect the **Execuction** pins as you see below

<br>

>Your sequence should currently look something like this:

![TidyUp01](https://user-images.githubusercontent.com/36719180/91003747-3de84780-e626-11ea-9683-ab85f504b275.png)

<br>

- In the **SetActorRotation** node, check **Teleport Physics**
>read the tooltip if you've forgotten what this does

<br>

- 





<br><br>



---
