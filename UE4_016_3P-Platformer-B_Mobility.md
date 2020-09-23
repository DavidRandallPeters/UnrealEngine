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

For Static Mesh Actors, this means they will have their shadows contribute to pre-calculated lightmaps using Lightmass to generate and process them. This mobility makes them ideal for structural or decorative meshes that never need to relocate during gameplay. Note, however, that their Materials can still be animated.

For Light Actors, this means it will contribute to pre-calculated lightmaps using Lightmass . They will illuminate the scene for Static and Stationary Actors and for Movable ones, use an indirect lighting method (like Indirect Lighting Samples or Volumetric Lightmaps ) to illuminate these dynamic objects.



