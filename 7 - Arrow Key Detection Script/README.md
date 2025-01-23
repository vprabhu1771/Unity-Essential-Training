# ArrowKeyMovement.cs

```csharp
using UnityEngine;

public class ArrowKeyMovement : MonoBehaviour
{
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.UpArrow))
        {
            Debug.Log("Up Arrow Key Pressed");
        }
        if (Input.GetKeyDown(KeyCode.DownArrow))
        {
            Debug.Log("Down Arrow Key Pressed");
        }
        if (Input.GetKeyDown(KeyCode.LeftArrow))
        {
            Debug.Log("Left Arrow Key Pressed");
        }
        if (Input.GetKeyDown(KeyCode.RightArrow))
        {
            Debug.Log("Right Arrow Key Pressed");
        }
    }
}
```