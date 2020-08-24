# Unreal Engine | 007 | Marble Labyrinth 1E | Getting and Setting

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br><br>

---

## 007.001 | Removing 'yaw-creep' by Getting and Setting values

<br>

Okay - I totally just made that term up. But it describes a small issue with our core gameplay mechanic.

Let's demonstrate:

<br>

- Play-test the game
- With your mouse, 'draw circles' - ie. keep making circles with your mouse and observe what the *Floor* Actor does..

<br>

As you continually pitch and roll, the *Floor* Actor becomes offset around its *yaw*.. It gradually creeps around the *Z-axis* and we don't want that because it'll mess up the synchronous between the orientation of our mouse-pad and the game-board - resulting in awkward gameplay.

We're going to solve this with some new and versatile coding tricks.

<br>

- Go into your **Level Blueprint**
- Locate your *EventTick* sequence, select the **AddActorWorldRotation** node and delete it
>It's served us well so far - but we need a little more control
- Click and drag out from the Reference to **Floor**'s blue (Object) output pin and release
- Drill down to **Utilities » Transformation** - this is where we previously found *AddActorWorldRotation*
- Keep scrolling down and locate and choose **GetActorRotation**

<br>

![GetActorRotation](https://user-images.githubusercontent.com/36719180/91001768-c06e0880-e620-11ea-86fa-df18ab451dfe.png)
>If you hover your cursor over the return pin, you'll notice that the return value (variable) is of type 'Rotator'
<br>

- 


<br><br>



---
