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

<br>

![Material output](https://user-images.githubusercontent.com/36719180/95930654-800e5800-0e23-11eb-8b7f-bed838c90ae8.png)

<br>

- From the **Palette** panel, drag a **Constant3Vector** into the graph
> Note: Another way of creating a *Constant3Vector* is to hold *3* and *left-click* in the graph
- Connect the **Constant3Vector** node's output to the **Emissive Color** output
- Either use the **Constant** swatch in the **Details** panel or double-click the **Constant3Vector** node to change the RGB values to make a colour you're into
> For the colour to actually display, slide the **Value** slider up from its default (black) position

<br>

![Choose a colour](https://user-images.githubusercontent.com/36719180/95931333-581ff400-0e25-11eb-85d0-e316f82edaf7.png)

<br>

- Hold **M** and **left-click** to create a *multiply* node - we'll use this to amplify the colour - essentially making it glow more
- Connect the **Constant3Vector** node's output to the **Multiply** node's **A** input
- Connect the **Multiply** node's output to **Emissive Color** - (replacing the existing input)
> We're currently multiplying by *1* - which has no effect - we now need to provide a higher value to multiply by
- With the **Multply** node selected, adjust the value of **Const B** in the **Details** panel to your liking
> For now, I'm going with *40*
- Hit **Apply** and **Save**

<br>

![Multiply applied](https://user-images.githubusercontent.com/36719180/95931894-db8e1500-0e26-11eb-8da5-801bb18b011e.png)

<br>

- Hop back into the main editor
- Select your new material in the **Content Browser**
- Open **BP_MainPickup** (or whatever you've called your initial pickup BP)
- Tab over to the blueprint's **Viewport** so we can work with the mesh
- Select any *StaticMesh* component in your pickup
- In the **Materials** section of the **Details** panel, hit the left-pointing arrow to *Use Selected Asset from Content Browser*
- In this way, apply your material to other mesh components in your BP
- For each mesh component, uncheck **Cast Shadow** in the **Lighting** section of the **Details** panel
- Select the *root* scene component in the **Components** panel 
- Hit **Add Component** and search for **Point Light**
- Adjust the colour of the **Pointlight** to match your emissive colour 
> You may wish to return to the *Material Editor* and copy the *Hex sRGB* value for an exact match
- Consider reducing the Light's *Attenuation Radius* to something more like *500*
- **Compile**, **Save** and take a look atyour pickups in your level.. 
- Return to the **BP_MainPickup** viewport and *Material Editor* to tweak values as you see fit

<br>

![Glowy pickups in level](https://user-images.githubusercontent.com/36719180/95933733-c5cf1e80-0e2b-11eb-8943-3f8663a94511.png)

<br><br>

---

## 025.002 | Applying Post Processing effects

<br>

UE4 defaults to use certain post-processing effects (such as *bloom* - which makes emissive materials appear to glow) - but for more control over these effects and for access to others, we can add a 

<br>

- In the **Modes / Place Actors** panel, select the **Visual Effects** category
- Drag a **Post Process Volume** into the main viewport
- Scale this volume to encompass your level - ie. anywhere your player's camera can possibly go to
> Depending on the aesthetic you're going for, you may wish to place multple volumes in your level.. eg. perhaps your player passes through a 'black and white' zone.. and then a freaky 'chromatic aberration' zone.. Or perhaps (programmatically) you make a given volume 'Visible in Game' in response to a certain event.. 

<br><br>

---

## 025.003 | Destroy Actor on Overlap

<br>

We can use *Destroy Actor on Overlap* to create the illusion that the player has collected a pickup.




