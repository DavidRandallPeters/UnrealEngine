# Unreal Engine | 008 | Marble Labyrinth 1E | Clamping Values

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br><br>

---

## 008.001 | Limiting rotation

<br>

Currently, we can completely invert our playing board. It's probably better that we restrict the player from being able to turn the map upside-down.

We can achieve this by clamping values. 

This one's quick and easy. Let's go:

<br>

- Go into your **Level Blueprint**
- Within your **Event Tick** sequence, locate the **float+float** node that handles the **Mouse X** values
- **Alt-click** the **float+float** node's **Return** pin to break the connection
- Click and drag off the **float+float** node's **Return** pin and release
- Drill down to **Math » Float** and select **Clamp (float)**
- Set the **Clamp (float)**'s **Min** value to **-40.0**
- Set the **Clamp (float)**'s **Max** value to **40.0**
- Reconnect the **Clamp (float)**'s **Return** node to the **Make Rotator** node's **X (Roll)** input 

<br>



<br>

- 

