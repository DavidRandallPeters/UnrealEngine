# Unreal Engine | 007 | Marble Labyrinth 1E | Getting and Setting

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br><br>

---

## 007.001 | Removing 'Yaw-Creep'

<br>

Okay - I totally just made up that term. But it describes a small issue with our core gameplay mechanic.

Let's demonstrate:

<br>

- Play-test the game
- With your mouse, 'draw circles' - ie. keep making circles with your mouse and observe what the *Floor* Actor does..

<br>

As you continually pitch and roll, the *Floor* Actor becomes offset around its *yaw*.. It gradually creeps around the *Z-axis* and we don't want that because it'll mess up the synchronous between the orientation of our mouse-pad and the game-board - resulting in awkward gameplay.



<br><br>



---
