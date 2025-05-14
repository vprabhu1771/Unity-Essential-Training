Here's a **complete step-by-step guide and README-style instructions** for creating a Unity project with a `MonoBehaviour` script that displays `x`, `y`, and `result` values on a UI Text element.

---

## ✅ Project Summary

This Unity app uses a simple `MonoBehaviour` script that holds `x`, `y`, and `result` float values and displays them on a UI Text component in the format:

```
x = <value>
y = <value>
result = <value>
```

---

## 📁 Folder Structure

```
Assets/
├── Scripts/
│   └── App.cs
└── UI/
    └── Canvas with Text (Unity UI)
```

---

## 🧾 Step-by-Step Instructions

### 1. Create a New Unity Project

* Open Unity Hub.
* Click on **New Project** → Choose **2D Core** (or 3D if preferred).
* Name it: `DisplayValuesApp`.
* Click **Create**.

---

### 2. Create the Script

#### 📄 Assets > Scripts > App.cs

```csharp
using UnityEngine;
using UnityEngine.UI;

public class App : MonoBehaviour
{
    public float x = 10f;
    public float y = 20f;
    public float result;

    public Text displayText; // Reference to the UI Text component

    void Start()
    {
        result = x + y;
        UpdateDisplay();
    }

    void UpdateDisplay()
    {
        displayText.text = $"x = {x}\ny = {y}\nresult = {result}";
    }
}
```

---

### 3. Set Up the UI

#### 🧱 Create Canvas and Text

1. Right-click in **Hierarchy** → `UI > Canvas`
2. Right-click on **Canvas** → `UI > Text - TextMeshPro` (or `UI > Text` for legacy).
3. Rename it to `DisplayText`.

#### 🧰 Adjust Text Properties

* Set **Font Size**: 24 or above
* Set **Alignment**: Top Left or Center
* Adjust size/position as needed

---

### 4. Connect Script to UI

1. Drag the `App.cs` script onto a GameObject (e.g., an empty GameObject or Canvas).
2. Select the GameObject with `App` script attached.
3. In the Inspector, drag the `DisplayText` UI element to the `Display Text` field in the script.

---

### 5. Run the App

Click **Play** in Unity Editor. You should see something like:

```
x = 10
y = 20
result = 30
```

---

## 📝 README.md (For Your Project)

```markdown
# Unity Float Display App

This is a simple Unity project that shows how to:

- Use a MonoBehaviour script with public float variables (`x`, `y`, `result`)
- Perform a calculation (`x + y = result`)
- Display the result in a UI Text element at runtime

## 🎮 How to Use

1. Set values for `x` and `y` in the Inspector.
2. The script auto-calculates `result = x + y`.
3. UI text displays:  
```

x = <value>
y = <value>
result = <value>

```

## 📂 Folder Structure

- `Assets/Scripts/App.cs` — MonoBehaviour script
- `Assets/UI/Canvas` — Contains UI Text

## 🔧 Requirements

- Unity 2020.3 or later
- TextMeshPro package (optional, if using `TextMeshProUGUI`)

## 🖥️ Setup Steps

1. Open Unity and create a new project.
2. Add a Canvas and Text.
3. Attach `App.cs` to a GameObject.
4. Link the Text UI to the script.
5. Press Play to see results.

## 📷 Screenshot

*(Add screenshot here if needed)*

---

Enjoy coding with Unity! 🎮
```

---

Would you like a Unity package or .zip of the project structure to go along with it?
