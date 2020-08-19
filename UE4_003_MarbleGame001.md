# Unreal Engine | 003 | MarbleGame 001

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

---

## 003.001 | Marble Labyrinth

We're about to being programming gameplay in Blueprints for a simpe marble-rolling game. 

In the process, we'll cover a range of UE4 fundamentals that you can put to use in your own projects.
<br><br>

![ClassicMarbleGame](https://user-images.githubusercontent.com/36719180/90583492-63d7ab80-e224-11ea-8d8d-127b2857e38c.png)


Our marble game will feature:

>- A tilt-able 3D level
>- A roll-able marble
>- A starting point
>- An exit hole

<br>

---

## 003.001 | Input Action Events

Events can be of course called in response to player input - such as a keypress.

- Open the **Level Blueprint**
- Select the **Event Tick** node and hit *Delete* (on your keyboard) to remove it
- In the empty graph space where we just deleted that node, **right-click**. This will bring up a list entitled *All Actions for this Blueprint.*
- Scroll down the list to the **Inputs** category and expand it
- Find **Keyboard Events** and expand it. Here, we see all the keys on a keyboard
- Find and select the **W** key. This will create an *Input Action Event* for *W*
<br>

![W](https://user-images.githubusercontent.com/36719180/90584788-81f2db00-e227-11ea-95cc-9bf3b8e0faea.png)

<br><br>

Currently, if we hit *W* during a game, our *DefaultPawn* Actor moves forwards.


