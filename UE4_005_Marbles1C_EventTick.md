# Unreal Engine | 005 | Marble Labyrinth 1C | Event Tick + Axis Events

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br>

---

## 005.001 | Mouse Input

<br>

We'll now make some changes so that we can control the *Floor* Actor smoothly - using mouse input.

<br>

- Go into your **Level Blueprint**
- Find some empty space in the graph under the *Key Input System* we built
- **Right-click** in empty graph space
- Scroll down the *Actions* menu and locate and expand **Input**
- Locate **Mouse Events** and expand it
- Select **Mouse X**

<br>

>We'll need *Mouse Y*, too:

- Either repeat the above steps to create a **Mouse Y** Action node, or
- **Right-click** in empty graph space and start typing **Mouse Y** (be sure to select the option that's in the *Mouse Events* section)

<br>

![MouseXandY](https://user-images.githubusercontent.com/36719180/90614958-7e7b4600-e25f-11ea-98ad-9159cbb91754.png)

<br>

- Drag **Mouse Y** downwards somewhere to make room for us to work on *Mouse X*
- Hover your cursor over the **Mouse X** node and read its tooltip:

![MouseEventTooltip](https://user-images.githubusercontent.com/36719180/90615373-255fe200-e260-11ea-91ab-119784c89088.png)

>It'll check where the mouse is (on this axis) on every frame - that value will be spat out of the node's lil' green pin

>Green pins indicate that a *float* (fractional) value will be returned (ie. has a decimal place)

<br>

Let's print that value to the screen:

- Right click in empty graph space and start typing **Print String**
- Connect the **Execution** pins
- Connect the **Mouse X** node's **Axis Value** to the **Print String** node's 







