# Unreal Engine | 016 | 3P / PLATFORMER B | Mobility

![Banner](https://user-images.githubusercontent.com/36719180/93958681-1a422980-fdab-11ea-8c2b-e665e08294da.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 016.001 | Mobility

<br>

![Mobility](https://user-images.githubusercontent.com/36719180/94083772-19b39c80-fe58-11ea-9432-ac00b579f386.png)

<br>

The Mobility setting controls whether an Actor will be allowed to move or change in some way during gameplay. This primarily applies to Static Mesh Actors and Light Actors.

When available, the Mobility property has 3 states: *Static*, *Stationary* and *Movable*.

It's pretty important to understand the differences between these:

<br><br>

### Static

	
This mobility is reserved for Actors that are *not intended* to move or update in any way during gameplay.

<br>

**For Static Mesh Actors**:

This means they will have their shadows contribute to pre-calculated lightmaps using Lightmass to generate and process them. This mobility makes them ideal for structural or decorative meshes that never need to relocate during gameplay.

> Note: their Materials can still be animated.

<br>

**For Light Actors**:

This means it will contribute to pre-calculated lightmaps using Lightmass. They will illuminate the scene for Static and Stationary Actors and for Movable ones, use an indirect lighting method (like Indirect Lighting Samples or Volumetric Lightmaps ) to illuminate these dynamic objects.

<br><br>

---

### Stationary


This mobility is reserved for Actors that can change during gameplay but not move.

<br>

**For Static Mesh Actors**: 

This means that they can be changed but not moved. They do not contribute to pre-calculated lightmaps using Lightmass and are lit like Movable Actors when lit by a Static or Stationary Light. However, when lit by a Movable Light, they will use a Cached Shadow Map to reuse for the next frame when the light is not moving, which can improve performance for projects using dynamic lighting.

<br>

For Light Actors, this means they can change in some way during gameplay, such as having their color changed or their intensity changed to be brighter or softer or even completely off. Stationary lights still contribute to pre-calculated lightmaps using Lightmass but can also cast dynamic shadows for moving objects. Note that care must be used to not have too many Stationary Lights affecting a given Actor. See Stationary Lights for more details.

<br>

---

### Moveable

This mobility is reserved for Actors that need to be added, removed, or moved during gameplay.

**For Static Mesh Actors**:

This means that they cast a fully dynamic shadow that does not cast pre-calculated shadows into the lightmap. When lit by Lights with Static mobility, they will use an indirect lighting method (like Indirect Lighting Samples or Volumetric Lightmaps ) to illuminate them. For Lights with Stationary or Movable mobility, they will only cast a dynamic shadow. This is the typical setting for any non-deforming mesh element that needs to added, removed, or moved in the scene. 

**For Light Actors**:

This means they can *only* cast dynamic shadows. In addition to being able to move the light during gameplay, they can also change their color and intensity during gameplay as well. However, care must be taken when making these lights cast shadows since their shadowing method is the most performance intensive. It should be noted that non-shadowing Movable Lights are very inexpensive to calculate due to Unreal Engine's Deferred rendering system.

<br><br>

---

