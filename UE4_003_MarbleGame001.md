# Unreal Engine | 003 | MarbleGame 001

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

---

## 003.001 | Marble Labyrinth

<br>

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

## 003.002 | Input Action Events

<br>

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
- Look in the **Details** panel and note that *Consume Input* is checked
- Hover your mouse cursor over the words *Consume Input* so that the tooltip appears. It says; *'Prevents actors with lower priority from handling this input'*. Currently, our *Input Action Event* is 'consuming' the input, thereby stopping the default [movement] functionality from happening.
- Uncheck **Consume Input**
- Compile - and go test it again. You should now be able to move.
- Hit **Stop**
- Head back into the **Level Blueprint**
- Select the **W** *Input Action Event* node and re-check **Consume Input**  

<br>

Rather than using *W* to control a Pawn, we'll use it to tilt a 'floor' Actor in our labyrinth, instead.
<br><br>

---

## 003.003 | Mobility

<br>

*Mobility* describes an Actor's ability to move within the World and determines how the engine will approach rendering that Actor.

<br>

- Out in the main viewport, select the *StaticMeshActor* called **Floor** - it's the thing that looks like a floor
- With it selected, look in the **Transform** section of the **Details** panel - specifically, the row marked **'Mobility'**
<br>

Currently, the floor actor is set to *Static.* This has implications on its mobility of course - but also on the way UE4 will render it. You may recall from Unity days that a static object can be included in baked lightmaps, improving performance at runtime. The same is true here.

Take a moment to view and bookmark [this](https://docs.unrealengine.com/en-US/Engine/Actors/Mobility/index.html?utm_source=GoogleSearch&utm_medium=Performance&utm_campaign=an*Internal_pr*UnrealEngine_ct*Search_pl*Brand_co*OC&utm_id=10824681733&sub_campaign=UE_Broad_EN&utm_content=July2020_Generic_V1b&utm_term=%2Bue4&gclid=EAIaIQobChMI1J70pKWm6wIV1X4rCh2nBAK2EAAYASAAEgJ25PD_BwE) documentation for more detail / future reference.

<br>

When you're ready:

- Set the *Floor StaticMeshActor*'s *Mobility* to **Moveable**

<br>

Now, the *Floor StaticMeshActor* will:

>- be allowed to move dynamically,
>- cast dynamic shadows, and
>- be rendered using the slowest available method - an acceptable sacrifice, as it's crucial that this thing moves!

<br><br>

---

## 003.003 | Mobility

<br>

*Mobi
