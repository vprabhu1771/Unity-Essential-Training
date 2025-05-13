Here’s a comprehensive **Unity 2D Physics Components & Topics** list that covers what you need to know when working with 2D physics in Unity:

---

## 🧩 **Unity Physics 2D Components**

### 🔹 **RigidBody2D**

* Adds physics behavior to 2D objects
* Types: Dynamic, Kinematic, Static
* Key properties:

  * `mass`, `gravityScale`, `drag`, `angularDrag`
  * `bodyType` (Dynamic/Kinematic/Static)
  * `freezeRotation`, `constraints`

### 🔹 **Collider2D Types**

Used for detecting collisions and triggers. Must be used with a Rigidbody2D to move correctly with physics.

| Component               | Description                                                          |
| ----------------------- | -------------------------------------------------------------------- |
| **BoxCollider2D**       | Rectangle collider                                                   |
| **CircleCollider2D**    | Circle collider                                                      |
| **CapsuleCollider2D**   | Capsule-shaped collider                                              |
| **PolygonCollider2D**   | Custom polygon shape collider                                        |
| **EdgeCollider2D**      | Line segments for terrains or edges                                  |
| **CompositeCollider2D** | Combines multiple colliders into one (used with Tilemaps or Terrain) |
| **TilemapCollider2D**   | Collider for grid-based tilemaps                                     |

### 🔹 **Effector2D Types**

Modifiers for how physics interacts through colliders:

| Component              | Description                         |
| ---------------------- | ----------------------------------- |
| **PlatformEffector2D** | One-way platforms, surface arc      |
| **PointEffector2D**    | Attraction or repulsion to a point  |
| **SurfaceEffector2D**  | Move objects along a surface        |
| **AreaEffector2D**     | Forces applied inside a volume area |
| **BuoyancyEffector2D** | Simulates floating in water         |

---

## 📚 **Unity Physics 2D Topics**

### 🔸 1. **Physics Settings**

* Set in **Edit → Project Settings → Physics 2D**
* Gravity (usually -9.81 on Y-axis)
* Layer collision matrix
* Velocity iterations / Position iterations

---

### 🔸 2. **Collision Detection**

* `OnCollisionEnter2D()`
* `OnCollisionStay2D()`
* `OnCollisionExit2D()`
* Physics Material 2D (friction, bounciness)

---

### 🔸 3. **Triggers**

* `isTrigger` enabled on Collider2D
* Use `OnTriggerEnter2D()`, `OnTriggerStay2D()`, `OnTriggerExit2D()`

---

### 🔸 4. **Forces & Movement**

* `Rigidbody2D.AddForce()` (impulse, force, etc.)
* `velocity` and `angularVelocity`
* `MovePosition()` and `MoveRotation()` (for Kinematic bodies)

---

### 🔸 5. **Raycasting**

* `Physics2D.Raycast()`
* `RaycastHit2D` struct
* Used for line-of-sight, shooting, ground checks, etc.

---

### 🔸 6. **Physics Layers and Collision Filtering**

* Assign layers to GameObjects
* Use layer collision matrix to define which layers interact
* Use `Physics2D.IgnoreCollision()` or `Physics2D.IgnoreLayerCollision()`

---

### 🔸 7. **Joints (2D)**

Used to link objects together:

| Joint Type          | Use Case                                             |
| ------------------- | ---------------------------------------------------- |
| **DistanceJoint2D** | Keep objects a fixed distance apart                  |
| **HingeJoint2D**    | Rotates around a pivot (like doors, wheels)          |
| **FixedJoint2D**    | Rigidly attaches two objects                         |
| **SpringJoint2D**   | Applies spring force between objects                 |
| **TargetJoint2D**   | Moves an object to a target position (like dragging) |
| **RelativeJoint2D** | Maintains relative position/rotation                 |
| **SliderJoint2D**   | Movement constrained to a line                       |

---

### 🔸 8. **Sleep and Wake States**

* Rigidbody2D can sleep when idle
* Use `WakeUp()` or `IsSleeping()` to control states

---

### 🔸 9. **Performance Tips**

* Use Static colliders for non-moving objects
* Use Rigidbody2D only when movement is needed
* Avoid overly complex polygon colliders

---

Would you like hands-on tutorials for these, such as:

* Player movement with Rigidbody2D
* Jump with ground check using Raycast2D
* One-way platforms with PlatformEffector2D

Let me know and I can provide step-by-step guides or code!
