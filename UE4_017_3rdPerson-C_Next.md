# Unreal Engine | 017 | 3RD PERSON C | Setup

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 017.001 | Building Lighting

<br>

If you receive the message 'LIGHTING NEEDS TO BE REBUILT', this means that you've designated Mobility to *Light* or *Static Mesh* Actors that make them able to be added to the game's precaluclated lightmaps.

You can keep working while the the message displays for as long as you like, but should you want to do a build (and see things as they'd look in the game + get rid of the message):

<br>

- Use the **Build** dropdown above the main viewport and choose **Build Lighting Only**

> Note that you can use **Build » Lighting Quality** to determine the quality of the lighting build. During development, *Preview* quality will be fine.

<br><br>

---

## 017.002 | Lighting

<br>

We've covered mobility and touched on lightmaps - I don't think y'all need me to go over the types of lights available in Unreal in very much detail as they're essentially the same set that Unity makes available.

But I'll provide links below to the Unreal documentation, should you wish to know more. 

I would suggest taking a quick look at *Rect Lights* and *Sky Lights* - as these are a little bit special.

<br>

1. [Directional Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/Directional/index.html)
2. [Point Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/Point/index.html)
3. [Spot Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/Spot/index.html)
4. [Rect Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/RectLights/index.html)
5. [Sky Light](https://docs.unrealengine.com/en-US/Engine/Rendering/LightingAndShadows/LightTypes/SkyLight/index.html)

<br><br>

---

## 017.002 | Lighting

<br>


