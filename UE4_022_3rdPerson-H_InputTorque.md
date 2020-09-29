# Unreal Engine | 022 | 3RD PERSON H | Input Mapping + Torque

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

We'll get to that soon.

<br><br>

___

## 022.002 | Input Mapping

<br>

We need to get this Player Pawn to respond to player input so that we can move it around the map.

Remember that there are two main types of input: *Action Events* (such as a keypress - these fire once at a time) and *Axis Events* (such as mouse positional input - these continually fire and send an input value).

In addition to this, we can create custom input mappings that can bebound to multiple inputs.

<br>

- Open **Project Settings** (**Edit » Project Settings** in the main menu)
- Navigate to **Engine » Input** and locate the **Bindings** section

<br>

We'll make the pawn move forwards and backwards (using the *W* and *S* keys) and we'll make it move left and right (using the *A* and *D* keys).

As we want our key-signal to continuously fire (for continuous movement), we'll need to use an *Axis Mapping*.

<br>

### Forwards-Backwards movement

- Hit the **+** button next to **Axis Mappings**
- Expand **Axis Mappings** (if it's not already expanded)
- Rename the event to *Movement forwards-backwards*
- Expand the event itself
- Click where it says **None** and locate and select **W** *Keyboard* input - leave *Scale* set to *1.0*
- Hit the **+** button next to the **Movement forwards-backwards** Event to add a second input
- Apply **S** *Keyboard* input
- Set the **Scale** of **S** to -1.0 - so that the marble moves backwards on this keypress

<br>

### Left-Right movement

- Again, hit the **+** button next to **Axis Mappings**
- Expand **Axis Mappings** (if it's not already expanded)
- Rename the new event to *Movement left-right*
- Expand the event itself
- Click where it says **None** and locate and select **D** *Keyboard* input - leave *Scale* set to *1.0*
- Hit the **+** button next to the **Movement left-right** Event to add a second input
- Apply **A** *Keyboard* input
- Set the **Scale** of **A** to **-1.0** - so that the marble moves oppositely on this keypress

<br>

Your Axis Mappings should look like this:

<br>

![Axis Mappings](https://user-images.githubusercontent.com/36719180/94497027-78ab5400-0252-11eb-8262-1b0f6944a998.png)

<br>

### Implementation

<br>

- Close **Project Settings** and hop back into the **Event Graph** of **BP_PlayerPawn**
- **Right-click** somewhere in the Event Graph and navigate to **Input » Axis Events** - here, you'll see the bindings we just created
- Choose **Movement forwards-backwards**
- Repeat those steps for **Movement left-right**

<br>

![Custom input nodes](https://user-images.githubusercontent.com/36719180/94497472-ceccc700-0253-11eb-9366-f7620013366e.png)

<br><br>

---

## 022.003 | Adding torque

<br>

Our Player Pawn has physics applied to it. When we apply key input, we want it not just to move in the directions we intend but to roll along the ground - we want to apply rotational force to the mesh.

Torque (in real world terms) is a measure of the force that can cause an object to rotate about an axis. The same definition is true in game engines.

It's the mesh component of our *BP_PlayerPawn* that we need to apply this to, so let's start by getting a reference to that. 

First though, we'll quickly update the name of the mesh to be more descriptive.

<br>

- In the **Components** panel of **BP_PlayerPawn**, rename **StaticMesh** to *SphereMesh*
- Drag **SphereMesh** out from the **Components** panel and into the **Event Graph** to create a reference to it
- Drag off its pin and navigate to **Physics** and choose **Add Torque in Radians**

<br>

![Add torque](https://user-images.githubusercontent.com/36719180/94499451-389b9f80-0259-11eb-9f96-befa7e1efb51.png)

<br>

As you can see, the *Target* of this torque is the Sphere Mesh.

Meanwhile, the value of *Torque* is given as a *Vector3* (X, Y and Z values).

<br><br>

### Understanding Torque

The tooltip that pops up when you hover over *Torque* reads:

*"Torque to apply. Direction is axis of rotation and magnitude is strength of torque"* ... WTF?

<br>

When dealing with torque, direction is not 'the direction you want a thing to move in', rather 'the axis around which you want a thing to spin'. 

<br>

![Torque diagram](https://user-images.githubusercontent.com/36719180/94500227-46522480-025b-11eb-893b-b4f51e4e8409.png)

<br>

In the above diagram, if we wanted the wheel to roll positively on the X-axis (forwards), we'd apply 'magnitude' to the Y-axis.

Y-axis would be the desired 'Direction'.

<br>

So where does Magnitude come into it?

Simply, the greater the value (Magnitude) that's applied to our chosen axis, the greater the force that's applied to the mesh will be.

<br>

If that's still complicated, don't stress - hopefully writing the following sequence will make things clearer.

<br><br>

---

## 022.004 | Key input » Torque

<br>

- Connect the **Movement forwards-backwards** node's **Execution** pin to the **Add Torque** node
- **Right-click** the **Torque** input pin and **Split Struct Pin** so that we can target specific axes

> When we hold down *W* or *S*, the value provided will be either *1* or *-1* (remember the *Scale* parameter when we did the Input Mapping?).

> That's here measured in Newton centimetres.. a value of *1* or *-1* is stupidly small in relation to the mass of our sphere - nowhere near large enough to actually move it.

> So we need to amplify that input. A LOT.

- Drag off the **Axis Value** and add a **float*float** node.
- Enter a value of **4,000,000** - (That's four million. Yeah I know. It's nuts)
- Connect the **float*float** output to **Torque Y** (to apply Magnitude to the appropriate Direction)

<br>

![Torque multiplier](https://user-images.githubusercontent.com/36719180/94502379-7c45d780-0260-11eb-88bb-ac3577b8e30c.png)

<br>

- **Compile** and **Save** and go test it out

<br>

You should now be able to roll your marble forwards and backwards using the *W* and *S* keys.

If you can't, go back and up the value of that multiplier. 

Conversely, you may have too much force. In which case, reduce that number until it feels right.

<br>

So, we chose the *Y-axis* as our forward-backwards torque direction.

To roll this thing left and right, we'll need to use the *X-axis* (

<br>

- Hop back into **BP_PlayerPawn**
- 





___















