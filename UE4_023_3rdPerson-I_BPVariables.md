# Unreal Engine | 023 | 3RD PERSON I | Blueprint Variables

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 023.001 | Magic numbers

<br>

You'll [hopefully] recall Lucas talking about *magic numbers* - this is when we use numbers directly in source code - without meaning or explanation.

The use of an unnamed *magic number* in code makes it difficult to determine the intention behind that numbers' inclusion, increases opportunities for subtle errors to be introduced and reduces opportunities to extend the code in future.

To use a magic number is to break one of the oldest rules in programming - and it's entirely avoidable.

We use two of these in our input system:

<br>

![Input system](https://user-images.githubusercontent.com/36719180/95700303-34cd3b80-0ca3-11eb-9219-324ea61b17c8.png)

<br>

Here inour *BP_PlayerPawn* blueprint, we're multiplying our input by an incredibly large, arbitrary number.

The number is huge because the torque value takes the mass of the mesh into account (measured in Newton centimetres).

In real-world terms, this all makes sense. But here we're not actually much bothered about the sphere's mass.. we're just arbitrarily tweaking this large number to get some movement happening.

The solution, as you likely already figured, is to sub these magic numbers out with variables. 

We'll get onto that shortly. But first we'll make a couple of small tweaks to our input system.

<br><br>

### Accel change

At the bottom of the *Add Torque in Radians* node, there's a *boolean* input (red) labeled *Accel Change*.

The tooltip reads:

> If true, Torque is taken as a change in angular acceleration instead of a physical torque (ie. mass will have no effect)

This means that if this checkbox isset to 'true', the node will ignore the mass of the sphere. Therefore, we'll no longer need to use such a ridiculously large multiplier to get things rolling - it will apply the provided angular acceleration without taking the mass into account.

Let's make some adjustments:

<br>

- Check the **Accel Change** checkboxes in each of the two **Add Torque in Radians** nodes
- Adjust the huge numbers in the **multiply** nodes (probably 4,000,000 and -4,000,000) to something like **20** (and **-20**, respectively)
- **Compile**, **Save** and go test it out

<br>

Your game should play as it did before - possibly with slightly less impulse - but using more modest numbers under the hood.

<br><br>

---

## 023.002 | Replacing magic numbers with variables

<br>

I don't need to tell you the benefits of variables - you know these from Unity days - let's just get into implementation.

- Go back into **BP_PlayerPawn**
- In the **My Blueprint** panel, hit the **+** symbol to the right of the word **Variables** - a variable of type *boolean* (red) is created
> A boolean either holds a *true* or a *false* value
- Name the new variable *AccelerationMultiplier*

<br>

![New variable](https://user-images.githubusercontent.com/36719180/95704848-b080b580-0cae-11eb-936f-970798f18597.png)

<br>

> The magic numbers that we seek to replace are of type *float* - we can see this *a)* by its lime green colour-coding and *b)* by the fact that they have decimal places
- In the **Details** panel, change **Variable Type** to **Float**


<br>

![Variable implementation](https://user-images.githubusercontent.com/36719180/95705207-a7dcaf00-0caf-11eb-9142-09102a29be26.png)

<br>






