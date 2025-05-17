To configure the **EvoFox Elite X Wireless Gaming Controller** for use in **Unity**, you need to ensure Unity can detect it and then map the buttons/axes correctly using Unity’s **Input System** or **legacy Input Manager**.

---

## ✅ Step-by-Step Guide to Set Up EvoFox Elite X in Unity

### 1. **Connect the Controller to Your PC**

* Plug the **USB dongle** of the EvoFox Elite X into your PC.
* Wait for Windows to detect and install it (it should show up as a generic gamepad).
* You can test it using **Windows Game Controller Settings**:

  * Press `Win + R` → type `joy.cpl` → press Enter.
  * You should see “Wireless Controller” or a similar name.
  * Click on "Properties" and press buttons to ensure they register.

---

### 2. **Set Up Input in Unity**

#### ✅ Option 1: **New Input System (Recommended)**

If you are using Unity 2020.1+ and have enabled the **Input System package**, follow this:

##### a. **Install Input System**

Go to `Window` → `Package Manager` → Install **Input System**.

##### b. **Enable Input System**

Go to `Edit` → `Project Settings` → `Player` → `Other Settings` → **Active Input Handling** → Select:

* **Input System Package (New)** or
* **Both** (if you want legacy support too).

Restart Unity.

##### c. **Create an Input Actions Asset**

1. Right-click in the `Assets` folder → `Create` → `Input Actions`.
2. Name it `GameControls.inputactions`.
3. Double-click it to open the Input Actions editor.
4. Add a new `Action Map` (e.g., "Player").
5. Add actions like `Move`, `Jump`, `Fire`.
6. Set bindings:

   * `Move`: Use a `2D Vector` composite with `Left Stick`.
   * `Jump`: Button South (A on Xbox-style).
   * `Fire`: Button West (X on Xbox-style).

##### d. **Use in Script**

```csharp
using UnityEngine;
using UnityEngine.InputSystem;

public class PlayerController : MonoBehaviour
{
    public InputAction move;
    public InputAction jump;

    void OnEnable()
    {
        move.Enable();
        jump.Enable();
    }

    void OnDisable()
    {
        move.Disable();
        jump.Disable();
    }

    void Update()
    {
        Vector2 movement = move.ReadValue<Vector2>();
        if (jump.triggered)
        {
            Debug.Log("Jump Pressed");
        }
    }
}
```

##### e. **Assign the Actions in Inspector**

* Drag the `Input Actions` asset onto the script field in Inspector or assign via code.

---

### 🕹 Gamepad Layout Ideas

* **D-Pad**: 4 buttons
* **ABXY**: 4 buttons
* **Joystick**: 2-axis analog input
* **L1, R1, L2, R2**
* **Start, Select, Home**

#### ✅ Option 2: **Legacy Input Manager (Not Recommended for New Projects)**

Go to `Edit` → `Project Settings` → `Input Manager`.

Typical Axis mappings:

* `Horizontal`/`Vertical`: Left stick.
* `Joystick Button 0`: A
* `Joystick Button 1`: B
* `Joystick Button 2`: X
* `Joystick Button 3`: Y

You can test button inputs in script:

```csharp
void Update()
{
    if (Input.GetKeyDown(KeyCode.JoystickButton0))
    {
        Debug.Log("A button pressed");
    }

    if (Input.GetKeyDown(KeyCode.JoystickButton1))
    {
        Debug.Log("B button pressed");
    }
    
    if (Input.GetKeyDown(KeyCode.JoystickButton2))
    {
        Debug.Log("x button pressed");
    }
    
    if (Input .GetKeyDown(KeyCode.JoystickButton3))
    {
        Debug.Log("y button pressed");
    }

    float moveX = Input.GetAxis("Horizontal");
    float moveY = Input.GetAxis("Vertical");
}
```

---

## 🧪 Testing & Debugging

Use Unity's **Input Debugger** (from the top menu: `Window → Analysis → Input Debugger`) to see if the controller is detected.

You can also install the free **"Input Debugger"** tool from the Unity Asset Store to visualize input in real-time.

---

## 📌 Notes

* EvoFox Elite X is likely recognized as a **DirectInput** device, not XInput (like Xbox controllers), which may affect compatibility.
* For full cross-platform support and button name mapping, use Unity’s **new Input System**.
* You may need to create custom control schemes if the controller reports unexpected button indices.

---

Would you like a Unity `.inputactions` file preset for this controller?
