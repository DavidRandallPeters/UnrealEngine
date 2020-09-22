# Unreal Engine | 012 | Marble Labyrinth J | Return Game Time

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 012.001 | Returning Game Time in Seconds

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

## 012.002 | Manipulating text

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

---

## 012.003 | Append String

In order to construct a sentence that contains variable data, such as:

>*Congratulations! You Escaped the Maze in 45.64 seconds!*

.. we'd need to break it down into three parts: the words at the start, the variable data, and the words at the end.

Let's dive straight in:

<br>

- Open your **Level Blueprint**

- Hold **Alt** and click the **Print String** node's **In String** pin tp break the link

- Minimise the **ToText (float)** node's extra bits

- Drag those three connected nodes out of the way for a tic

- Drag out from the **Print String** node's **In String** pin and navigate to **Utilities » String » Append**

<br>

![Append string](https://user-images.githubusercontent.com/36719180/93324345-dd85a800-f869-11ea-8987-3ec37e21f9e9.png)

> This node allows us to combine strings

<br>

- Hit the **+** symbol in the **Append** node to add another input

- Connect the nodes and enter text something like this:

<br>

![Append string 2](https://user-images.githubusercontent.com/36719180/93325059-d27f4780-f86a-11ea-9283-3340fd789489.png)

> Note the space in the A string after *'in' and the space in the C string before *'seconds'*

<br>

- Compile and go test it out

<br>

![Congrats](https://user-images.githubusercontent.com/36719180/93325370-56d1ca80-f86b-11ea-800d-bc45af6011e9.png)

<br>

Hopefully you're also seeing something like this.

Okay - so, this isn't very pretty.. we can alter the colour of the string and the duration for which it displays, but that's about it.

We won't get into it just now, but a constructed string like this can readily be sent to off to Unreal's UMG Designer (used to design User Interfaces, among other things) where it can be rendered beautifully in any style you see fit.

Here, we're just getting our heads around the basics.

<br><br>

---

## 012.004 | Delay before restart

Before we wrap this one up, let's add a a wee pause (to give the player time to read the message) before restarting the game to give them another shot.

<br>

- Go back into the **Level Blueprint**

- Expand the **Print String** node's dropdown

- Set the **Duration to **5.0** - (change the text colour, too, if y'like)

- Drag off the **Print String** node's **Execution Pin** and find **Delay**

- Set the **Duration** to **5.0**

- Drag off the **Delay** node's **Completed** *Execution Pin* and navigate to **Game » Open Level**

- Type your level's name - *verbatim!* - in the **Level Name** field - (you can check it against the tab in the editor or the *Level* file in the **Maps** folder) - this does need to be exact

<br>

![Delay and restart](https://user-images.githubusercontent.com/36719180/93327740-e167f900-f86e-11ea-9d44-7cbcb4cde667.png)

<br>

- Compile and go test it out

<br>

The appended string should now display for 5 seconds before the level is reloaded.

That's all for now.

In the next session, we'll clean up our code and try to address any bugs we have.

After that, we'll package the game to make it playable outside of UE4 and move on to our 3rd person game.

<br><br>

<br><br>

#### Continued in UE4_013_Labyrinth-K_BugFixes

---





