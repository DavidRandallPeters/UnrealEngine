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
> Note: Another way of creating a *Constant3Vector* is to hold *3* and *left-click* in the graph.
- Connect the **Constant3Vector** node's output to the **Emissive Color** output
- Either use the **Constant** swatch in the **Details** panel or double-click the **Constant3Vector** node to change the RGB values to make a colour you're into
> For the colour to actually display, slide the **Value** slider up from its default (black) position.

<br>

![Choose a colour](https://user-images.githubusercontent.com/36719180/95931333-581ff400-0e25-11eb-85d0-e316f82edaf7.png)

<br>

- Hold **M** and **left-click** to create a *multiply* node - we'll use this to amplify the colour - essentially making it glow more
- Connect the **Constant3Vector** node's output to the **Multiply** node's **A** input
- Connect the **Multiply** node's output to **Emissive Color** - (replacing the existing input)
> We're currently multiplying by *1* - which has no effect - we now need to provide a higher value to multiply by.
- With the **Multply** node selected, adjust the value of **Const B** in the **Details** panel to your liking
> For now, I'm going with *40*.
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
> We're adding one of these because emissive materials don't actually emit light - they only look like they do.
- Adjust the colour of the **Pointlight** to match your emissive colour 
> You may wish to return to the *Material Editor* and copy the *Hex sRGB* value for an exact match.
- Consider reducing the Light's *Attenuation Radius* to something more like *500*
- **Compile**, **Save** and take a look atyour pickups in your level.. 
- Return to the **BP_MainPickup** viewport and *Material Editor* to tweak values as you see fit

<br>

![Glowy pickups in level](https://user-images.githubusercontent.com/36719180/95933733-c5cf1e80-0e2b-11eb-8943-3f8663a94511.png)

<br><br>

---

## 025.002 | Applying Post Processing effects

<br>

UE4 defaults to use certain post-processing effects (such as *bloom* - which makes emissive materials appear to glow) - but for more control over these effects and for access to others, we can add a *Post Process Volume* to our levels.

<br>

- In the **Modes / Place Actors** panel, select the **Visual Effects** category
- Drag a **Post Process Volume** into the main viewport
- Scale this volume to encompass your level - ie. anywhere your player's camera can possibly go to
> Depending on the aesthetic you're going for, you may wish to place multiple volumes in your level.. eg. perhaps your player passes through a 'black and white' zone.. and then a freaky 'chromatic aberration' zone.. Or perhaps (programmatically) you make a given volume 'Visible in Game' in response to a certain event..
- With the **PostProcessVolume** still selected, play around with the various effects in the **Details** panel.

<br>

![Post Process Volume added](https://user-images.githubusercontent.com/36719180/95935449-c964a480-0e2f-11eb-8b04-9630f8f119a2.png)

<br>

The above example has:

> *Depth of Field* applied with a *Focal Distance* of *100* and *Depth Blur Radius* of *100* (*Depth Blur km for 50%* is not activated) - notice that objects in the distance are out of focus.

> *Lens Flares* activated (adjust values to suit your environment and aesthetic).

> *Bloom* activated (adjust values to suit your environment and aesthetic).

<br><br>

---

## 025.003 | Destroy Actor on Overlap

<br>

We can use *Destroy Actor on Overlap* to create the illusion that the player has collected a pickup.

Currently, when we roll into our pickups, we just hit them. This is because their *Collision Preset* is set to *BlockAllDynamic*.

Let's start by removing these collisions - we'll allow a single encompassing collision event that ultimately destroys the entire blueprint.

<br>

- Within the **BP_MainPickup** blueprint (or whatever you called it), **ctrl-select** all mesh components
- Locate the **Collision** section of the **Details** panel
- Set **Collision Presets** to **NoCollision** - the player can now roll straight through the pickups
- In the **Components** panel, add a **Sphere Collision** component
- Rename the *Sphere Collision* to *SphereTrigger*
- Drag **SphereTrigger** onto the current scene root to make it the new scene root 

<br>

Your component hierarchy should look *something* like this:

<br>

![Components hierarchy](https://user-images.githubusercontent.com/36719180/95936267-a9ce7b80-0e31-11eb-8d3c-0dc4fcdc6c16.png)

<br>

- Tab over to this blueprint's **Event Graph**
- Delete **Event Tick** and **Event BeginPlay**

> The remaining Event node - **ActorBeginOverlap** will fire when any Actor overlaps with *any* of the the components within this blueprint - except we've disabled collisions on everything except the *SphereTrigger* - so that's the only thing that will activate this Event node.

> As we've done before, we'll run a check to see if the *Other Actor* is the *PlayerPawn* and, if it is, we'll then destroy this blueprint

- Drag off **OtherActor** and find **Equal (Object)**
- **Right-click** in empty space and **Get Player Pawn**
- Connect the **object** pins
- Hold **B** and **left-click** to create a *Branch*
- Connect the **bool** and **execution** pins
- Drag off **True** and **DestroyActor**

<br>

![Destroy Actor](https://user-images.githubusercontent.com/36719180/95937380-26faf000-0e34-11eb-8aae-ea512ec8b481.png)

<br>

- **Compile**, **Save** and go test it out

<br>

Your pickups should now disappear when rolled into.

<br><br>

---

## 025.004 | Animating objects using Timelines

<br>

Next, we'll create a neat lil' animation using *Timelines* that runs when the player gets within range of a pickup. At a certain distance, the pickup will appear to gravitate toward the player before being destroyed.

To do this, we'll update the pickup's location upon overlap.

<br>

- Hop back into the **Event Graph** of your pickup blueprint
- Break the input **Execution** link to **DestroyActor** (**alt-click**) - we'll add code before it in the sequence
- Move the **DestroyActor** node off to the right to make space
- **Right-cick** in empty graph space and **SetActorLocation**
> If we use *New Location* as it is, we'll simply teleport the pickup Actor to that location.. but we want to interpolate between locations..
- Drag off the **New Location** pin and **Lerp (Vector)** 

<br>

![Lerp (Vector)](https://user-images.githubusercontent.com/36719180/95941612-a2ad6a80-0e3d-11eb-85a2-5752e4827eb2.png)

<br>

> Lerp is an abbrevation of *'Linear Interpolation'*

> This node allows us to provide two vectors (for location) and 'lerp' (linearly interpolate) between the two.

> The *Alpha* float input allows us to provide a location where the object should be - at any given time

- **Right-click** in empty graph space and **Add Timeline** - name it *Alpha blend*

<br>

![Timeline node](https://user-images.githubusercontent.com/36719180/95941448-46e2e180-0e3d-11eb-9356-32e251ab78c3.png)

<br>

> The *Update* execution pin will fire constantly *until* the timeline has finished playing

> The *Finished* execution pin will fire once that timeline has finished playing

- Double-click on the **Alpha blend** timeline to open it up

> In the top-left of this viewport, there's an *Add Float Track* button. This will allow us to animate a float value over time.

> *Length* determines the duration of the timeline (in seconds)

- Give **Length** a value of **0.7** seconds

- Hit **Add Float Track** and name the new track *PickupPosition*

- Hold **Shift** and **left-click** anywhere in the timeline to create a 'key' that we can apply values to

- Give the new key a **Time** value of **0.0** and a **Value** value of **0.0**

- Add a second key, as before

- Give the second key a **Time** value of **0.7** and a **Value** value of **1.0**

- To see your entire curve, hit the lil' arrow buttons to the left of the fields in which you've just entered values

<br>

![Alpha blend timeline](https://user-images.githubusercontent.com/36719180/95941283-dfc52d00-0e3c-11eb-87b2-e7b75d768548.png)

<br>

- Tab back over to the **Event Graph**

> Notice that the *Alpha blend* timeline now has a *Pickup Position* float output - that's the *Float Track* we just made

- Connect **Pickup Position** to the **Alpha** input in the **Lerp (Vector)** node

- Connect the **Alpha Blend** node's **Update** execution pin to the **SetActorLocation** node

<br>

![Connecting timeline](https://user-images.githubusercontent.com/36719180/95943673-f1a9ce80-0e42-11eb-88b2-3fff5c5f6b3b.png)

<br>

We've now supplied values between 0 and 1 (start and finish) and the speed (essentially) at which to interpolate - but we still need to provide vector locations for the pickup to move between.

<br>

- **Right-click** the **A** input pin in the **Lerp (Vector)** node and choose **Promote to Variable**
> This is a means by which we can take an incidental value and promote that value to a variable that can be reused in all the normal ways.
- Name the new variable *LerpStartLocation*
- **Right-click** in empty graph space and **GetPlayerPawn**
- Drag off its **Return Value** and **GetActorLocation**
- Connect the vector **Return Value** to the **B** input of the **Lerp (Vector)** node

<br>

![Vectors connected](https://user-images.githubusercontent.com/36719180/95945882-e9a05d80-0e47-11eb-82db-de24c84b103c.png)

<br>

So, now we know where the player is and are using that vector3 as the destination location.

The observant among you might have noticed that we also promoted a vector (that has no value) to a variable .. and plugged it into itself. Pointless.

It's not quite true that it has no value - its value is (0,0,0) - that's origin.

If we left it like this, the lerp would interpolate between origin (probably the start of your level) and wherever the player is on the map - that's not what we're intending here.

Let's rectify that.

<br>

- Drag the **LerpStartLocation** variable out from the **My Blueprint** panel and into the graph
- Instead of *getting* it, this time choose **Set LerpStartLocation**
- Add this node to the sequence between the **Branch** and the **Alpha blend** timeline
- **Right-click** in empty graph space and **GetActorLocation**
> This node's target is itself, so it will return the current location of *THIS* instance of the blueprint
- Connect the **GetActorLocation** node's **Return Value** to the **SET** input
> *LerpStartLocation* will now have a useful value by the time the variable is used in the lerp
- Finally, connect **DestroyActor** to the **Finished** execution pin of the timeline

<br>

![Finished lerp sequence](https://user-images.githubusercontent.com/36719180/95947215-a0054200-0e4a-11eb-9621-868943b74266.png)

<br>

- Check your sequence against the above image and hope into this blueprint's **Viewport** when you're satisfied everything's in order
- Select the **SphereTrigger** in the **Components** panel
- In the **Shape** section of the **Details** panel, set the **Sphere Radius** to about **220**
- **Compile**, **Save** and go test it out

<br>

Pickups should now animate as you approach them, moving from their current position to yours over the course of 0.7 seconds.

<br><br>

---

## 025.005 | Blueprint Functions

<br>

The code we've just finished writing is kinda freaky. We haven't commented it and it's otherwise wild and wooly.

At a glance, it's pretty hard to see what it does (due to so many nodes and wires) and its reusability is.. average.

We're just gonna take a minute to encapsulate parts of our code into functions that can be far more easily read and managed.

In fact, we're already using functions - *DestroyActor* and *SetActorLocation* are both functions - as indicated by their blue tone and the **f** symbol next to their name. As you can imagine, there's more going on under the hood, here, that we're not privy to.

<br>

- In the **Event Graph** of your pickup blueprint, select all nodes highlighted below:

<br>

![Pre-collapse / selected nodes](https://user-images.githubusercontent.com/36719180/95961512-a357f800-0e61-11eb-9ce1-8100a7421fa0.png)

<br>

- **Right-click** any one of those nodes and choose **Collapse to Function** - name the function *MoveTowardsPlayer*

<br>

![Collapsed](https://user-images.githubusercontent.com/36719180/95961894-2ed18900-0e62-11eb-9416-6c7b503f817a.png)

<br>

> The new function has been added to the *My Blueprint* panel for later deployment

> Those nodes have all been encapsulated within this function

> We can view and edit its contents by double-clicking it

- **Double-click** the **MoveTowardsPlayer** function to open it
> Unreal tends to make a mess of your sequences when collapsing to functions - feel free to tidy up
- Once you've explored what Unreal's done to your code, hop back over to the **Event Graph**
- Select the **GetActorLocation** and **SET** nodes
- Collapse these into a function called *StoreInitialValues*
- Open the function and tidy things up - we'll be adding to these functions shortly

<br>

![Tidied sequence](https://user-images.githubusercontent.com/36719180/95963961-cc2dbc80-0e64-11eb-8644-906ed93f7404.png)

<br>

- **Compile**, **Save** and go test your game again to make sure nothing got broken - there's no reason it should (functions are trusty and safe) but there's no harm in checking.

<br><br>

---

## 025.006 | Animating pickup scale

<br>

We can add some polish to our pickup animations by adding a 'shrinking' animation to the existing timeline.

We'll build on our fancy new functions to achieve this.

<br>

- Open your **Store Initial Values** function
- **Right-click** in empty graph space and **Get Actor Scale 3D**
- Promote the **Get Actor Scale 3D** node's **Return Value** output to a variable called **InitialScale**
- To keep things consistent, rename **LerpStartLocation** to *InitialLocation*

<br>

![Storing initial values](https://user-images.githubusercontent.com/36719180/95967478-ca65f800-0e68-11eb-9e9b-9ab239a7dca2.png)

<br>

- Hop back into the **Event Graph**

<br>

We'll now hit this home - won't take long. And this is good practice for animating all manner of things in your game, including light intensity, moving platforms.. all sorts.

<br>

- **Right-click** in empty space and **Set Actor Scale 3D**
- Add this node just after **Move Towards Player** in the execution sequence
- As before, to create a lerp, drag out from the vector input pin and **Lerp (Vector)
- Drag **Initial Scale** out from the **My Blueprint** panel and drop it on the **A** input of the **Lerp (Vector)** node

> The aim is to make the pickup shink into nothing.. so we don't need to provide a *B* input, as it's already set to (0.0,0.0,0.0)

> We'll reuse the float output from our timeline.. but our names could be more descriptive..

- Select the **Alpha blend** timeline and rename it to *Pickup Timeline*
- Open **Pickup Timeline**, **right-click** in the blank space to the left of the graph and **Rename** the float track to *PickupProgress*
- Hop back into the **Event Graph**
- Connect the **Pickup Progress** float output to the new **Lerp (Vector)** node's **Alpha** input
> HOT TIP! You can double-click wires to add *Reroute* nodes for organisational purposes

<br>

![Second Lerp node added](https://user-images.githubusercontent.com/36719180/95970421-6cd3aa80-0e6c-11eb-91c9-12f8060ebf97.png)

<br>

- Select the nodes indicated above and collapse them to a function called *ScalePickup*

<br>

![Scale pickup function](https://user-images.githubusercontent.com/36719180/95970469-7c52f380-0e6c-11eb-9a5b-8371ef80b93c.png)

<br>

- **Compile**, **Save** and go test this out

<br>

Pickups should now shrink down to nothing as they approach the Player Pawn.

<br><br>

---


















