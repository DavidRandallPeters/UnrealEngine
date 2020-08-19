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

![Mobility](https://user-images.githubusercontent.com/36719180/90589183-a489f180-e231-11ea-8efc-077d7d0b5be2.png)

<br>

Now, the *Floor StaticMeshActor* will:

>- be allowed to move dynamically,
>- cast dynamic shadows, and
>- be rendered using the slowest available method - an acceptable sacrifice, as it's crucial that this thing moves!

<br><br>

---

## 003.003 | AddActorWorldRotation

<br>

In our game, we'll need this floor actor to rotate on its own pivot.. causing the marble to roll in various directions - ultimately allowing it to reach its destination. We'll do this by somehow affecting its *Transform*..

Let's start working towards achieving that.
<br><br>

- With the *Floor StaticMeshActor* still selected in the main viewport, head back into the **Level Blueprint**
- **Right-click** in empty graph space (somewhere below the *W Input Action Event* node) - notice that, because we have the floor selected, the first entries in the list pertain directly to the *Floor* actor - handy!
- Select **Create a Reference to Floor** - a *Static Mesh Actor Object Reference* node is created

![FloorReference](https://user-images.githubusercontent.com/36719180/90589480-4d385100-e232-11ea-81a1-e2dbc6d8e48b.png)

- Click and drag off the lil' blue pin (in the new *Reference* node) - and release - notice that the menu is context-sensitive to actions that relate to this type of pin
- Scroll down the list and locate the **Utilities** section
- Expand that and locate **Transformation**
- Expand that and select **AddActorWorldRotation**
- Drag the nodes to tidy up a little
<br><br>

![AddActorWorldRotation](https://user-images.githubusercontent.com/36719180/90590189-f9c70280-e233-11ea-8a57-03bce55666ae.png)
<br>

This node allows us to affect the *Roll* (X-axis), *Pitch* (Y-axis) and *Yaw* (Z-axis) of the associated Actor.
We'll use this to make it so that when we press *D*, the floor will roll right and when we press *A*, the floor will roll left.  
<br>
- Select the **Print String** node that's attached to the *W Input Action Event* node and delete it
- Select the **W** *Input Action Event* node
- Duplicate it by hitting **CTRL+W** on your keyboard - position it below the first one somewhere
- With the second **W** *Input Action Event* node selected, look in the **Details** panel..
- Expand the **Input Key** drop-down (currently says *W*)
- Choose **Keyboard » D** - the node now handles a *D* key input
- Connect the **D** *Input Action Event*'s **Pressed** Execution pin to the **AddActorWorldRotation** node's input *Execution* pin

![DInput](https://user-images.githubusercontent.com/36719180/90591133-63e0a700-e236-11ea-8685-448addb9f991.png)

- Again, drag off the **Floor** *Reference* node's lil' blue pin (there is no limit as to how many times you can use a reference), start typing **AddActorWorldRotation** and select it - this will create a second *AddActorWorldRotation* node, connected to the *Reference* node

![AddActorWorldRotation](https://user-images.githubusercontent.com/36719180/90592654-3269da80-e23a-11ea-8fd5-4355d0a7ef62.png)

- Duplicate the **D** *Input Action Event* node (**CTRL+W**) and give it an **A** key input - as we did above
- Connect the **A** *Input Action Event*'s **Pressed** Execution pin to the new **AddActorWorldRotation** node's input *Execution* pin

![AddActorWorldRotation](https://user-images.githubusercontent.com/36719180/90592883-be7c0200-e23a-11ea-811a-9b065c20e6da.png)

<br><br>
We now have the ability to rotate the Floor Actor by pressing the *A* and *D* keys.
We'll now give the appropriate axes a value so that something actually happens when we press these keys.

<br>

- In the **AddActorWorldRotation** node that's attached to the **D** *Input Action*, give the **X-axis** a value of **5.0**
- In the **AddActorWorldRotation** node that's attached to the **A** *Input Action*, give the **X-axis** a value of **-5.0** to make it roll in the opposite direction
- Compile and head out to the main viewport

<br>

Before we test this, we'll quickly move the *PlayerStart* actor to the side so that we have a better view of the action at runtime. 
<br>

- Select the **PlayerStart** actor and move it backwards (that's negatively along its [red] X-axis) so that it's off the *Floo*r
- Move it upwards so that it's diagonally opposite the *Floor*
- Rotate it so that it's looking diagonally downward at the *Floor*

![CameraAngle](https://user-images.githubusercontent.com/36719180/90593795-f126fa00-e23c-11ea-8173-737c333f701c.png)

- Hit **Play**, click in the viewport to make sure it's focused and try it out

<br>

The floor should now rotate each time you hit the *A* and *D* keys.


