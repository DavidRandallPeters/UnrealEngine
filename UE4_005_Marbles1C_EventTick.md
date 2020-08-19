# Unreal Engine | 005 | Marble Labyrinth 1C | Event Tick + Axis Events

![UnrealEngineLogo002](https://user-images.githubusercontent.com/36719180/90347960-a4e68900-e087-11ea-9349-f5a59105b4d2.png)


Notes prepared by David Peters

Using: Unreal Engine 4.25.3 

<br><br>

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

<br>

>It'll check where the mouse is (on this axis) on every frame - that value will be spat out of the node's lil' green pin

>Green pins indicate that a *float* (fractional) value will be returned (ie. has a decimal place)

>Pink pins indicate that the value is a *string*

<br>

### Testing for mouse input

<br>

To test for input, let's print that float value to the screen as a string:

<br>

- Right click in empty graph space and start typing **Print String**
- Connect the **Execution** pins
- Connect the **Mouse X** node's **Axis Value** to the **Print String** node's **In String** pin - Unreal automatically converts the *float* value to a *string* value

<br>

![ConvertFloatToString](https://user-images.githubusercontent.com/36719180/90619208-0dd72800-e265-11ea-8a1a-55f00f176af3.png)

<br>

- Compile and head back to the editor viewport
- Hit **Play** to test it out (remember to click in the viewport to focus)

<br>

You should see a stream of axis values running down the left of the viewport. Moving the mouse left returns a negative value and moving it right returns a positive value.

![AxisValues](https://user-images.githubusercontent.com/36719180/90620437-8e4a5880-e266-11ea-9893-9c0fbfd77186.png)

<br>

Keep in mind that a value is returned on every frame - likely between 50 and 100 times every second. This will yield a very high resolution in terms of controller input - resulting in nice, smooth gameplay.

<br><br>

---

## 005.002 | Mouse Input

<br>

We'll

<br>

- Hop back into your **Level Blueprint**
- Delete the **Print String** node and its *Conversion* node
- Pan the graph up to your **Key Input System**
- Select a reference to **Floor**
- **Shift-select** an attached **AddActorWorldRotation** node - (both nodes should now be selected)
- Pan back down to your **Mouse X** node and hit **Ctrl+W** to duplicate the selected nodes
- Connect the **Execution** pins as you see below

<br>

![MouseRotation](https://user-images.githubusercontent.com/36719180/90622776-b4bdc300-e269-11ea-938f-861393f16caf.png)

<br><br>

### Splitting pins

Okay - we now want to plug the mouse's *Axis Value* (green pin) into the *Delta Rotation* pin.. but there are three axes to target.. and only one axis value..

How do we target a specific axis?

The solution is to *split* the pin.

<br>

- **Right-click** the **Delta Rotation** pin
- Choose **Split Struct Pin**

>We can now target individual axes.

- Connect the mouse's **Axis Value** to the **Delta Rotation X (Roll)** pin

<br>

![SplitStructPin](https://user-images.githubusercontent.com/36719180/90623654-e2efd280-e26a-11ea-8ebc-ffe0798810fd.png)

<br>

-







