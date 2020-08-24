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

<br><br>

### Clamping the X axis

<br>

- Go into your **Level Blueprint**
- Within your **Event Tick** sequence, locate the **float+float** node that handles the **Mouse X** values
- **Alt-click** the **float+float** node's **Return** pin to break the connection
- Click and drag off the **float+float** node's **Return** pin and release
- Drill down to **Math » Float** and select **Clamp (float)**
- Set the **Clamp (float)**'s **Min** value to **-20.0**
- Set the **Clamp (float)**'s **Max** value to **20.0**
- Reconnect the **Clamp (float)**'s **Return** node to the **Make Rotator** node's **X (Roll)** input

<br>

![ClampingX](https://user-images.githubusercontent.com/36719180/91009451-ba822280-e634-11ea-866c-a945d9df29bc.png)

<br><br>

### Clamping the Y axis

<br>

- Locate the **float+float** node that handles the **Mouse Y** values
- **Alt-click** that **float+float** node's **Return** pin to break the connection
- Select the existing **Clamp (float)** node and hit **Ctrl+W** to duplicate it
- Add it to the *Y-Axis* calculations as we did just now
- Maybe you'd like to rename the operation to **Mk.3 Mouse input control**?

<br>

![ClampingY](https://user-images.githubusercontent.com/36719180/91009620-0b921680-e635-11ea-9154-b7ece1e22656.png)


<br>

That's all there is to it!

<br>

- Compile and try it out

<br>

The *Floor* Actor's rotation is now limited - disallowing the player from completely inverting it.


