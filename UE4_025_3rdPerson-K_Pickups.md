# Unreal Engine | 025 | 3RD PERSON K | Pickups

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 025.001 | Creating Emissive materials

<br>

Everyone likes when things glow. We humans are weird like that.

Let's get our pickups glowing.

We'll achieve this by creating our own custom emissive material, applying it to our pickup and adding post-processing effects that allow the emissive material to glow.

<br>

- In the **Content Browser**, navigate to the root (**Content**) folder
- **Right-click** and create a **New Folder** called *Materials*
- Open the new folder
- **Rght-click** and create a **Material** called *M_Emissive01* (or some such) - we'll see by the thumbnail which colour it is so you needn't pick a colour now
- **Double-click** the new material to open the *Material Editor*

<br>

UE4 uses a PBR (Physically Based Rendering) model. You can read all about it [here](https://docs.unrealengine.com/en-US/Engine/Rendering/Materials/PhysicallyBased/index.html). This basically means that it makes its best attempt to visualise light and reflections etc. in a realistic way.

The initial node that we see here contains output channels - this is the *END* of the line, as it were. 

Many of these terms will be familiar, but I suggest you take a moment to read the tooltips for each output.







