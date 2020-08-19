# Unreal Engine | 002 | Intro to Blueprints

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

---

## 002.001 | Pawns

<br>
- First up, take note of how many actors are currently listed in the *Outliner*.

<br><br>

You likely see 7 Actors - one of these is a *PlayerStart* Actor.  

![PlayerStart](https://user-images.githubusercontent.com/36719180/90562920-1a249c00-e1f7-11ea-8351-6207ee79aa39.png)

<br>

Now let's play-test this opus.

- Hit the **Play** button in the main toolbar (top)
<br>

There are now something like 18 Actors in the *Outliner* - one of these is the *DefaultPawn* Actor.
This was spawned at the location of *Player Start* when we hit play.
<br><br>

We now have the ability to look and move around our level using WASD and mouse input.

Notice that we also have some collision in place - we can't move through the 'Floor' *StaticMeshActor.*

We're currently playing the game as Unreal's default *Pawn*.
<br><br>

***Pawns:***  

A *Pawn* is an *Actor* (class) that can be possessed and controlled by a player - a physical representation of the player or AI entity in the *World.*

While the *Pawn* class provides only the bare essentials, the *DefaultPawn* subclass comes with some additional components and functionality.

That's all you need to know about them for now - but by all means, read more about them [here](https://docs.unrealengine.com/en-US/Gameplay/Framework/Pawn/index.html).
<br><br>

___

## 002.002 | Blueprints Visual Scripting

<br>

_Blueprints_ is a powerful node-based scripting system that effectively allows you to write in C++ without the need to actually know the C++ coding language.

I suggest you bookmark [this](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) reference for later.

![BlueprintsDemo](https://user-images.githubusercontent.com/36719180/90563504-0e85a500-e1f8-11ea-9954-cbfe19631143.png)

We'll make a start using Blueprints now.
<br><br>

***The Level Blueprint***

A [Level Blueprint](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Types/LevelBlueprint/index.html) is a specialised type of *Blueprint* that acts as a level-wide global event graph. A *Level Blueprint* is created by default in each level of your project.
<br><br>

Let's take a look at this Level's *Level Blueprint:*

- In the top menu bar, hit the **Blueprints** button and choose **Open Level Blueprint**

- I suggest you grab the new window's tab and dock it alongside your main one 
<br><br>

Here, the main viewport contains what's referred to as a *graph*. This is where we 'write' code.

Unreal has provided two commonly used nodes by default:
<br><br>

>1. Event BeginPlay - This event is triggered for all Actors when the game is started.
>2. Event Tick - if enabled, this will run on every frame

<br>
The wee sockets that you see within the nodes are referred to as *pins.* 
The white arrow on each node is called the *Execution pin*.
Note the invitation to 'Drag off pins to build funcionality.'
<br><br>

Let's test this by printing a message to the screen:

- Click and drag off the **Event BeginPlay**'s **Execution pin** - and release.
We're presented with a huge list of 'Executable Actions'.
<br><br>

We want to find a *function* called *Print String*. We can absolutely select this option by drilling in to *Utilities » String » Print String* - but a much faster method would be to start typing *Print String* in the search field.

- Begin typing **Print String** in the search field and select it when it appears in the list
<br><br>

![PrintString](https://user-images.githubusercontent.com/36719180/90566267-4a226e00-e1fc-11ea-888c-cedc5bba6be1.png)
<br><br>

You can no doubt intuit that the flow of execution runs from left to right. When the game begins, a string will be printed - in this case, that string will read 'Hello' - but, by all means write what you like in the *In String* field.
<br><br>

- Expand the **Print String** node by hitting the **drop-down arrow** at its base
- Try changing the **Text Color** to something else
- Adjust the display **Duration** of the string to something like 5 seconds
- In order to apply these changes, hit the **Compile** button in the main toolbar and head back over to the main viewport tab to test
- Hit **Play** to test the game. You should see the word *Hello* appear in the top-left of the viewport in the colour you chose, for the duration you determined
- Hit **Stop**

<br><br>
***Delay***

This is a handy and simple function that will delay the execution of code by a certain time (measured in seconds). Calling the node again while it is counting down will be ignored.

Let's try it out:

- Reenter the *Level Blueprint.*
- Alt-click the **Event BeginPlay**'s **Execution** pin - (that's the white arrow). This will sever its link to the *Print String* node
- Click and drag the **Print String** node to the right to create some space
- Click and drag off the **Event BeginPlay**'s **Execution** pin and release..
- Start typing *Delay* - choose **Delay** when it becomes available
<br><br>

![DelayMenu](https://user-images.githubusercontent.com/36719180/90579955-bb254e00-e21b-11ea-9586-cae968050142.png)
<br><br>

Notice that the *Delay* function is:

>a) coloured blue  
>b) has an *f* beside it  

UE4 will always colour-code like-operations (eg. all functions are blue and are indicated with an *f* ).
<br><br>

- Set the duration of the delay in the **Delay** node to about 3 seconds
- Drag off the **Delay** node's **Execution** pin and connect it to the **Print String**'s input **Execution** pin, like so: 
<br>

![DelaySequence](https://user-images.githubusercontent.com/36719180/90581809-430d5700-e220-11ea-876d-caf125a3428f.png)

<br>

- Compile, head back to the main viewport and try it out
<br><br>

Your message will appear after the *Delay* that you determined - and for the *Duration* that you determined.


<br><br>

#### Continued in UE4_003_MarbleGame001

---





