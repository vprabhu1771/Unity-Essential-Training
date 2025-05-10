# Make Flappy Bird in 5 Minutes (Unity Tutorial)
```
https://www.youtube.com/watch?v=hKGzSYXPQwY
```
```
https://www.youtube.com/watch?v=ihvBiJ1oC9U
```

# Download The TileSet
```
https://www.spriters-resource.com/mobile/flappybird/sheet/59894/
```

# Download The Flappy Bird font
```
https://www.dafont.com/04b-19.font
```

# Folder Setup 

Assets -> Fonts

Assets -> Materials

Assets -> Prefabs

Assets -> Scripts

Assets -> Sprites


# Create New Material 

Assets -> Materials -> Right Click -> Create -> Material -> New Material rename Background

Inspector -> Shader -> Unit -> Texture -> Drag background.png to Base (RGB)

# Import Sprites

Assets -> Sprites -> Import

# Go To Inspector

Sprite Mode -> Multiple

Advanced -> Filter Mode -> Point (no filter)

Advanced -> Default -> Compression -> None

Click -> Apply

Click -> Sprite Editor





```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerBehaviour : MonoBehaviour
{
    private Vector3 direction;

    public float gravity = -9.8f;

    public float strength = 5f;

    private void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space) || Input.GetMouseButtonDown(0) )
        {
            direction = Vector3.up * strength;
        }

        if(Input.touchCount > 0)
        {
            Touch touch = Input.GetTouch(0);

            if (touch.phase == TouchPhase.Began)
            {
                direction = Vector3.up * strength;
            }
        }

        direction.y += gravity * Time.deltaTime;

        transform.position += direction * Time.deltaTime;
    }
}
```
