Sure! Here's a complete **README-style** guide that explains how to create a cube in Unity, attach the movement script, and use a game controller to move it with the analog stick.

---

# 🎮 Unity Cube Movement with Analog Controller

This guide will help you:

* Create a Cube in Unity
* Add movement using the left analog stick of a game controller (e.g., Xbox or PlayStation)
* Detect button presses (A, B, X, Y)

---

## ✅ Requirements

* Unity installed (any recent version)
* A connected game controller (e.g., Xbox or PS4/PS5 controller)

---

## 🧱 Step 1: Create a New Unity Project

1. Open Unity Hub
2. Click **New Project**
3. Choose **3D Core**
4. Name your project (e.g., `CubeController`)
5. Click **Create**

---

## 🟦 Step 2: Create a Cube

1. In the **Hierarchy** panel, right-click → `3D Object` → `Cube`
2. Rename the cube to `Player`
3. Optional: Reset the transform (`Right-click → Reset`)

---

## 🧾 Step 3: Create the Movement Script

1. In the **Project** panel:

   * Right-click in the `Assets` folder → `Create` → `C# Script`
   * Name it `CubeController`

2. Double-click the script to open it in your code editor

3. Replace the content with the following code:

```csharp
using UnityEngine;

public class CubeController : MonoBehaviour
{
    public float moveSpeed = 5f; // Speed of movement

    void Update()
    {
        // Joystick button press logging
        if (Input.GetKeyDown(KeyCode.JoystickButton0)) Debug.Log("A button pressed");
        if (Input.GetKeyDown(KeyCode.JoystickButton1)) Debug.Log("B button pressed");
        if (Input.GetKeyDown(KeyCode.JoystickButton2)) Debug.Log("X button pressed");
        if (Input.GetKeyDown(KeyCode.JoystickButton3)) Debug.Log("Y button pressed");

        // Read analog input
        float moveX = Input.GetAxis("Horizontal");
        float moveY = Input.GetAxis("Vertical");

        // Create movement vector
        Vector3 movement = new Vector3(moveX, 0f, moveY); // Movement on XZ plane

        // Apply movement
        transform.Translate(movement * moveSpeed * Time.deltaTime, Space.World);
    }
}
```

---

## 🧩 Step 4: Attach Script to Cube

1. Select the `Player` cube in the **Hierarchy**
2. In the **Inspector**, click `Add Component`
3. Search for `CubeController` and add it

---

## 🎮 Step 5: Test Controller Input

1. Plug in your game controller
2. Click the **Play** button in Unity
3. Move the **left analog stick** to move the cube
4. Press **A, B, X, Y** to see console logs

---

## 🛠️ Optional: Add Ground

* Right-click in the **Hierarchy** → `3D Object` → `Plane`
* Rename it `Ground`
* Scale or position it as needed

---

## 📌 Notes

* The cube moves on the **X-Z plane**
* `Horizontal` and `Vertical` axes are mapped to the **left analog stick** by default
* For smoother or physics-based movement, consider using `Rigidbody` with `AddForce` or `MovePosition`

---

Let me know if you'd like to include rotation, Rigidbody physics, or camera follow!


Here’s a **single Unity C# script** that combines:

✅ Analog stick movement (using `Rigidbody`)
✅ Right stick rotation
✅ Smooth camera follow

---

## 📜 Script: `CubeControllerFull.cs`

```csharp
using UnityEngine;

public class CubeControllerFull : MonoBehaviour
{
    [Header("Movement")]
    public float moveSpeed = 5f;
    private Rigidbody rb;

    [Header("Rotation")]
    public float rotationSpeed = 100f;

    [Header("Camera Follow")]
    public Transform cameraTransform;
    public Vector3 cameraOffset = new Vector3(0f, 5f, -10f);
    public float cameraSmoothSpeed = 0.125f;

    void Start()
    {
        rb = GetComponent<Rigidbody>();

        if (cameraTransform == null && Camera.main != null)
        {
            cameraTransform = Camera.main.transform;
        }
    }

    void FixedUpdate()
    {
        // Movement (left stick)
        float moveX = Input.GetAxis("Horizontal");
        float moveZ = Input.GetAxis("Vertical");
        Vector3 move = new Vector3(moveX, 0f, moveZ) * moveSpeed;
        Vector3 newVelocity = new Vector3(move.x, rb.velocity.y, move.z);
        rb.velocity = newVelocity;
    }

    void Update()
    {
        // Rotation (right stick)
        float rotateX = Input.GetAxis("RightStickHorizontal");
        float rotateY = Input.GetAxis("RightStickVertical");
        Vector3 rotation = new Vector3(rotateY, rotateX, 0f);
        transform.Rotate(rotation * rotationSpeed * Time.deltaTime);

        // Camera follow
        if (cameraTransform != null)
        {
            Vector3 desiredPos = transform.position + cameraOffset;
            Vector3 smoothedPos = Vector3.Lerp(cameraTransform.position, desiredPos, cameraSmoothSpeed);
            cameraTransform.position = smoothedPos;
            cameraTransform.LookAt(transform);
        }

        // Optional: Log button presses
        if (Input.GetKeyDown(KeyCode.JoystickButton0)) Debug.Log("A button pressed");
        if (Input.GetKeyDown(KeyCode.JoystickButton1)) Debug.Log("B button pressed");
        if (Input.GetKeyDown(KeyCode.JoystickButton2)) Debug.Log("X button pressed");
        if (Input.GetKeyDown(KeyCode.JoystickButton3)) Debug.Log("Y button pressed");
    }
}
```

---

## 🧩 Unity Setup

1. **Create a Cube**

   * Right-click → `3D Object` → `Cube`
   * Rename to `Player`

2. **Add Rigidbody**

   * Select cube → `Add Component` → `Rigidbody`

3. **Create/Adjust Camera**

   * Use Main Camera
   * No need for a separate script — this one handles following

4. **Attach Script**

   * Drag `CubeControllerFull.cs` to the Cube
   * Assign the `cameraTransform` (optional; will default to Main Camera)

5. **Input Manager (for right stick)**

   * Go to `Edit > Project Settings > Input Manager`
   * Duplicate `Horizontal` and `Vertical` axes:

     * Rename to `RightStickHorizontal` → Axis = `4th axis (Joystick Axis)`
     * Rename to `RightStickVertical` → Axis = `5th axis (Joystick Axis)`

---

Let me know if you want to add jumping, animations, or gamepad UI icons too!
