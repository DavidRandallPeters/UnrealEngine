# Unreal Engine | 012 | Marble Labyrinth 1J | Return Game Time

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 012.001 | 

In this one, we'll count how long a player takes to get through the maze and return that time in seconds.

We'll also generate message to congratulate / report to the player.

We'll then utilise a *Delay* function to make a pause prior to restarting the game.

<br>

- Open your **Level Blueprint

- Find some empty space in your graph (just beneath *OnActorEndOverlap*) and **right-click**

- Choose **Utilities » Time » Get Game Time in Seconds**

<br>

![GetGameTimeInSeconds](https://user-images.githubusercontent.com/36719180/93316628-9515bc80-f860-11ea-99ff-f037ccd2bd9e.png)

<br>

> This does what it says on the can - it will tell us in seconds how much time has passed since we hit 'play'

- Connect the **Return Value** to the **In String** pin on the **Print String** node - a *Conversion* node is automatically created

> ![Print Game Time](https://user-images.githubusercontent.com/36719180/93317246-57fdfa00-f861-11ea-8e00-5cff934ece56.png)

- Compile
