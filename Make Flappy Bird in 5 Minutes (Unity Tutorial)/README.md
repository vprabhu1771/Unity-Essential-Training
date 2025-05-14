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


# Create New Material for Background

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





Here's a **formatted README-style guide** based on your instructions for creating a repeating background in Unity using a material and mesh:

---

# 🎮 Setting Up a Repeating Background in Unity

This guide walks you through the steps to create a repeating background using a material, quad mesh, and custom texture.

---

## 🧱 Step 1: Create a New Material for the Background

1. Navigate to: `Assets`
2. Right-click → **Create** → **Material**
3. Rename the material to: `Background`
4. In the **Inspector**, set:

   * `Shader` → **Unlit** → **Texture**
   * Drag and drop your `background.png` into the `Base (RGB)` texture slot

---

## 🏗️ Step 2: Create the Background GameObject

1. In the **Hierarchy**, right-click → **Create Empty**
2. Rename it to: `Background`

---

## 🧩 Step 3: Add Mesh Filter to Background

1. Select the `Background` GameObject
2. In the **Inspector**, click **Add Component**
3. Search and add: **Mesh Filter**
4. Set `Mesh` to: **Quad**

---

## 🎨 Step 4: Add Mesh Renderer with Background Material

1. With `Background` still selected, click **Add Component**
2. Add: **Mesh Renderer**
3. In the **Mesh Renderer** component:

   * Under `Materials`, assign your `Background` material

---

## 🖼️ Step 5: Set Texture Wrap Mode to Repeat

1. Navigate to your texture: `Assets` → `Sprites` → `Background`
2. Select the texture and look at the **Inspector**
3. Change:

   * `Wrap Mode` → **Repeat**
   * Click **Apply**

---

✅ Now your background texture will tile properly across the quad using the repeat wrap mode. You can control tiling via the material’s texture scale settings.

Let me know if you want a parallax background or to animate the texture offset!

Sure! Here's a **README-style guide** to **set up a repeating ground** texture in Unity, just like the background:

---

# 🛤️ Setting Up a Repeating Ground in Unity

This guide helps you create a **repeating ground texture** using a material and quad mesh.

---

## 🧱 Step 1: Create a New Material for the Ground

1. Go to: `Assets`
2. Right-click → **Create** → **Material**
3. Rename the material to: `Ground`
4. In the **Inspector**, set:

   * `Shader` → **Unlit** → **Texture**
   * Drag and drop your `ground.png` into the `Base (RGB)` texture slot

---

## 🏗️ Step 2: Create the Ground GameObject

1. In the **Hierarchy**, right-click → **Create Empty**
2. Rename it to: `Ground`

---

## 🧩 Step 3: Add Mesh Filter to Ground

1. Select the `Ground` GameObject
2. In the **Inspector**, click **Add Component**
3. Search and add: **Mesh Filter**
4. Set `Mesh` to: **Quad**

---

## 🎨 Step 4: Add Mesh Renderer with Ground Material

1. With `Ground` selected, click **Add Component**
2. Add: **Mesh Renderer**
3. In the **Mesh Renderer** component:

   * Under `Materials`, assign your `Ground` material

---

## 🖼️ Step 5: Set Ground Texture Wrap Mode to Repeat

1. Navigate to: `Assets` → `Sprites` → `Ground`
2. Select the texture and go to the **Inspector**
3. Change:

   * `Wrap Mode` → **Repeat**
   * Click **Apply**

---

✅ Your **ground texture** is now set up to repeat across a quad. You can adjust the tiling by modifying the **material’s texture scale** in the material inspector.

Need help with positioning or animating the ground? Just ask!



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

Add Score Text

Hierarchy -> Right Click -> UI -> Text

or

Hierarchy -> Right Click -> UI -> Legacy -> Text


# Config Score Text Canvas 

Canvas Scaler -> UI Scale Mode -> Constant Pixel Size

# Rename Text to Score

Select Text -> Rename to Score

# Config Score Text

Pos X 0

Pos Y -25

Pos Z 0

Width 250

Height 30


# Text Style

Font Size -> 35

