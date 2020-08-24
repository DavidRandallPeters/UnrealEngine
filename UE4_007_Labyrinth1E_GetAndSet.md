# UnrealEngine
Material, blueprints and assets for Massey University's 289.210 Game Technology Project course.





## 006.XXX | Removing 'Yaw-Creep'

Okay - I totally just made up that term. But it describes a small issue with our core gameplay mechanic:

- Play-test the game
- With your mouse, 'draw circles' - ie. keep making circles with your mouse and observe what the *Floor* Actor does..

As you continually pitch and roll, the *Floor* Actor becomes offset around its *yaw* (Z-axis).. It gradually creeps around and we don't want that because it'll mess up the synchronous between the orientation of our mouse-pad and the game-board.



<br><br>

UE4_007_Labyrinth1E_GetAndSet

---
