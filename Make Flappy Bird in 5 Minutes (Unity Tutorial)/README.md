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

# Import Sprites

Assets -> Sprites -> Import

# Go To Inspector

Sprite Mode -> Single

Pixels Per Unit -> 24

Advanced -> Wrap Mode -> Clamp

Advanced -> Filter Mode -> Point (no filter)

Default -> Max Size -> 256

Resize Algorithm -> Mitchell

Format -> RGBA 32 bit

Click -> Apply


# Create New Material 

Assets -> Materials -> Right Click -> Create -> Material -> New Material rename Background

Inspector -> Shader -> Unlit -> Texture -> Drag background.png to Base (RGB)

# Create Background GameObject

Hierarchy -> Right Click -> Create Empty -> GameObject -> rename to Background

# Add Mesh Filter to Background GameObject

Hierarchy -> Background -> Add Component -> Mesh Filter -> Mesh -> Quad

# Add Mesh Mesh Render to Background GameObject

Hierarchy -> Background -> Add Component -> Materials -> Select Background Material


# Change Background Sprite to Wrap Mode -> Repeat 

Assets -> Sprites -> Background -> Wrap Mode Repeat







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
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Parallax : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    private float animationSpeed = 1f;

    private void Awake()
    {
        meshRenderer = GetComponent<MeshRenderer>();
    }

    private void Update()
    {
        meshRenderer.material.mainTextureOffset += new Vector2(animationSpeed * Time.deltaTime, 0);
    }
}
```
