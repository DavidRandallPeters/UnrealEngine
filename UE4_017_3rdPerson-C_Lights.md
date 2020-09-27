# Unreal Engine | 017 | 3RD PERSON C | Lights in Unreal

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 017.001 | Lighting

<br>

We've covered mobility and touched on lightmaps - I don't think y'all need me to go over the types of lights available in Unreal in very much detail as they're essentially the same set that Unity makes available and are controlled in very similar ways.

I will provide links below to the Unreal documentation, should you wish to know more. 

I would suggest taking a quick look at *Rect Lights* and *Sky Lights* - as these are a little bit special.

<br>

1. [Directional Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/Directional/index.html)
2. [Point Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/Point/index.html)
3. [Spot Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/Spot/index.html)
4. [Rect Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/RectLights/index.html)
5. [Sky Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/SkyLight/index.html)

<br>

Lights can be added to your scene via the **Place Actors** / **Modes** panel.

<br><br>

---

## 017.002 | Adding a Cubemap to a Sky Light

<br>

![Sky Light](https://user-images.githubusercontent.com/36719180/94375288-26ddcd80-016f-11eb-9ed6-c3f3ebe24c51.png)

<br>

As you may have just read in the Unreal documentaion; the *Sky Light* captures the distant parts of your level and applies that to the scene as a light. That means the sky's appearance and its lighting/reflections will match, even if your sky is coming from atmosphere, or layered clouds on top of a skybox, or distant mountains. You can also manually specify a cubemap to use.

We don't have any distant objects or a sky to speak of, but Unreal provides us with a default Cubemap which can use to try this out. Maybe you'll want to keep this cubemap or maybe you'll want to import your own or one you've found online.

<br>

- Add a **Sky Light** to your scene
- In the **Light** section of the **Details** panel, set **Source Type** to **SLS Specified Cubemap**
- Set the **Cubemap** to **HDRI_Epic_Courtyard_Daylight** (or whichever HDRI map is availble to you personally)

<br>

You'll notice the ambient colours change in your scene.

<br><br>

---

## 017.003 | Building Lighting

<br>

If you receive the message 'LIGHTING NEEDS TO BE REBUILT', this means that you've designated Mobility to *Light* or *Static Mesh* Actors that make them able to be added to the game's precaluclated lightmaps.

You can keep working while the the message displays for as long as you like, but should you want to do a build (and see things as they'd look in the game + get rid of the message):

<br>

- Use the **Build** dropdown above the main viewport and choose **Build Lighting Only**

> Note that you can use **Build » Lighting Quality** to determine the quality of the lighting build. During development, *Preview* quality will be fine.

<br><br>

---

## 017.004 | Auto Exposure

<br>

You may notice that each time you adjust your main lights, Unreal adjusts them back again in the viewport.

By default, Unreal uses *Auto Exposure* to homogenise light intensity. Imagine a 1st person game in which you run from the interior of a cave out into bright sunshine - in that instance, this would be useful. 

While this is an often handy feature, this may become frustrating for us.

<br>

- Open **Project Settings** (in the main menu go to **Edit » Project Settings**)
- Locate **Engine » Rendering » Default Settings**
- In the **Default Settings** section, uncheck **Auto Exposure**

<br>

In our case, given the nature of our game, this will probably suit us better.

See what you think. You may wish to revert, depending on your level design.

<br><br>

---




