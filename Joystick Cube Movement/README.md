To move a cube in Unity using an analog controller (e.g., Xbox or PlayStation joystick), you're already on the right track by reading the `Horizontal` and `Vertical` axes using:

```csharp
float moveX = Input.GetAxis("Horizontal");
float moveY = Input.GetAxis("Vertical");
```

Now, to make the cube actually move in your scene, you need to apply this movement to the cube’s `Transform`. Here's a complete example that moves a cube using the left analog stick:

### ✅ Final Working Script:

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

### 📌 Steps to Make It Work:

1. **Attach Script to Cube**:

   * Drag and drop this script onto the cube GameObject in the Unity Editor.

2. **Input Settings (if needed)**:

   * By default, Unity's Input Manager maps `Horizontal` and `Vertical` to analog stick movement (left stick). You can check this under:

     * `Edit > Project Settings > Input Manager`

3. **Test with Controller**:

   * Connect your game controller and enter Play mode. Move the left analog stick to move the cube.

Let me know if you want to use physics-based movement (with Rigidbody) or rotation too.
