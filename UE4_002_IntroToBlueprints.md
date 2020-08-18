# Unreal Engine | 002 | Intro to Blueprints

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

---

## 002.001 | Pawns

<br>
- First up, take note of how many actors are currently listed in the *Outliner.*
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

Let's take a look at this Level's Level Blueprint:

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

- In order to apply these changes, hit the **Compile** button in the toolbar and head back over to our main viewport tab
- Hit **Play** to test the game. You should see the word *Hello




