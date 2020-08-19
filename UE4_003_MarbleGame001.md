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

<br>

Currently, if we hit *W* during a game, our *DefaultPawn* Actor moves forwards.
Just quickly, let's check for input by printing a string in response to a *W* key press..

- **Alt-click** the **Event BeginPlay**'s **Execution** pin to stop our previous string from printing
- Drag off the **Pressed** execution pin of the **W** *Input Action Event* and choose **Print String**
- Enter the string: *MOVE FORWARD*

![PrintMoveForward](https://user-images.githubusercontent.com/36719180/90586515-7dc8bc80-e22b-11ea-9160-1dd515e03a4c.png)

- Compile, head back to the main viewport and hit **Play**
- Click inside the viewport to make sure it's focused
- Hit **W** and you should see *MOVE FORWARD* printed on the left

<br>

Notice that we no longer do move forward.. That's because we've hijacked that default functionality and over-ridden it with our own custom functionality.

<br>

- Head back into the **Level Blueprint**
- Select the **W** *Input Action Event* node
- 
