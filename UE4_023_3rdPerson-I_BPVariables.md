# Unreal Engine | 023 | 3RD PERSON I | Blueprint Variables

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 023.001 | Blueprint variables

You'll [hopefully] recall Lucas talking about *magic numbers* - this is when we use numbers directly in source code.

The use of an unnamed *magic number* in code makes it difficult to determine the intention behind that numbers' inclusion, increases opportunities for subtle errors to be introduced and reduces opportunities to extend the code in future.

To use a magic number is to break one of the oldest rules in programming - and it's entirely avoidable.

We use two of these in our input system:

<br>

![Input system](https://user-images.githubusercontent.com/36719180/95700303-34cd3b80-0ca3-11eb-9219-324ea61b17c8.png)

<br>

Here, we're multiplying our input by an incredibly large, arbitrary number.

The number is huge because the torque value takes the mass of the mesh into account (measured in Newton centimetres).

In real-world terms, this all makes sense. But here we're not actually much bothered about the sphere's mass.. we're just arbitrarily tweaking this large number to get some movement happening.

