```
https://www.youtube.com/watch?v=a-rogIWEJlY
```

# move a player in Unity 3D

```
Unity Hub -> New project -> All templates -> 3D Core 
```

Project name
3D Fun

Location
Select Location

Create project

--------------------

```
Hierarchy -> Right Click -> 3D Object -> Terrain
```

```
Hierarchy -> Right Click -> 3D Object -> Cube
```

OR

```
Hierarchy -> Terrain -> Right Click -> Cube
```

---------------------

Folder Setup

```
Project -> Assets -> Right Click -> Create -> Folder -> Scripts
```

```
Project -> Assets -> Scripts -> Right Click -> Create -> C# Script -> PlayerMovement
```

`PlayerMovement.cs`

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float speed = 5.0f; // Added a speed variable for movement

    public float horizontalInput;
    public float verticalInput;

    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        // Read Values from keyboard
        horizontalInput = Input.GetAxis("Horizontal");
        verticalInput = Input.GetAxis("Vertical");

        // Move the object
        transform.Translate(Vector3.forward * Time.deltaTime * speed * verticalInput);
        transform.Translate(Vector3.right * Time.deltaTime * speed * horizontalInput);
    }
}
```