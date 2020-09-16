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

<br>

> ![Print Game Time](https://user-images.githubusercontent.com/36719180/93317246-57fdfa00-f861-11ea-8e00-5cff934ece56.png)

<br>

> The logic here is that when the marble passes through the TriggerBox, we'll found out how long it took to get there.

<br>

- **Compile** and hop back into the editor

- Hit **Play** and try it out

<br>

You should see the time printed on the side of the screen at the end of the run.

<br><br>

---

## 012.002 | 

The number that was printed had a few too many decimal places after the point.. it's overkill.

So we'll use one (of many) methods to clip those extra decimal numbers off the end.

<br>

- Go back into your **Level Blueprint**

- Delete the **Conversion** node

- Drag off the **Get Game Time in Seconds** node's **Return Value** and find **ToText (float)**

- Drag off the **ToText (float)** node's **Return Value** and plug it into **In String** - a *Conversion* node is created

- Expand the **drop-down** at the bottom of the **ToText (float)** node

- Set **Maximum Fractional Digits** to **2**

<br>

![Max digits](https://user-images.githubusercontent.com/36719180/93319441-fa1ee180-f863-11ea-9c57-e0fa6214a019.png)

<br>

- Compile and go test it out

<br>

The time is now displayed in a more truncated form.

Noice.

<br><br>











