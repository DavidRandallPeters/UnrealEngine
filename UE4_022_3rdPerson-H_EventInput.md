# Unreal Engine | 022 | 3RD PERSON H | Event Graphs + Input Mapping

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 022.001 | Blueprint Classes + Event Graphs

<br>

In the previous [Labyrinth] project, we exclusively used the *Level Blueprint* to achieve everything.

That was fine while we were getting to grips with things and working within a singular level - but this won't always/often be the right approach.

*Blueprint Classes* (eg. the Pawn Class) each have their own *Event Graphs* - which we can *a)* use to write code directly where it's needed and *b)* reuse that code anywhere in the game, across multiple levels.

Let's take a look at the Player Pawn's Event Graph:

<br>

- Open **BP_PlayerPawn**
- Just above the main viewport inside *BP_PlayerPawn*, you'll find a tab marked **Event Graph** - select that

<br>

![Event Graph](https://user-images.githubusercontent.com/36719180/94495649-d047c080-024e-11eb-8038-7adeca85a2fe.png)

<br>

We're now inside *BP_PlayerPawn*'s Event Graph. It looks about the same as the *Level Blueprint*. 

Code written here is contained here (as with C# scripts) and of course the *BP_PlayerPawn* Blueprint can be instanced as many times as we need it, across multiple levels (just like a C# script).

On the other hand, you can only have *one* Level Blueprint in each level and that Level Blueprint is stuck within that level.

So, in fact, the Level Blueprint should only be used for very specific [local] level events - as it can't be used globally.

<br><br>

### References within Blueprint Classes

You'll remember, in the Level Blueprint, we could easily reference Actors in our scene by:

<br>

1. Selecting them in the Outliner (or viewport),
2. entering the Level Blueprint,
3. right-clicking..
4. ..and simply creating a reference to that Actor.

<br>

Easy peasy. Just like that, you're talking to the Actor in question.

This isn't possible with Event Graphs - because, unlike the Level Blueprint, a Blueprint Class can be reused in different levels. If we referenced an Actor in one level, it might not exist in another.

Blueprint Classes can absolutely still make references - we just need to take a different approach to achieve that.

<br><br>

___

## 022.002 | Input Mapping

<br>

We need to get this Player Pawn to respond to player input so that we can move it around the map.

Remember that there are two different types of input: *Action Events* (such as a keypress) and *Axis Events* (such as mouse input - these continually fire).








