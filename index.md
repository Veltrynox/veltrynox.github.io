---
layout: default
title: Portfolio
---

##### 📬 Contact & Links
**[Email Me](ilarin75@gmail.com)** | **[Download Resume (PDF)](#)** | **[GitHub](https://github.com/Veltrynox)**

---

#### 🌊 Ocean Shader
![shader_preview](https://github.com/user-attachments/assets/158e0db6-c761-473b-b1be-e137b3e6992d)  

<details markdown="1">
<summary><strong>📖 Read Technical Breakdown (Compute Shader, Split View, Tesselation)</strong></summary>

##### Gerstner Waves:
Instead of calculating Gerstner Wave math inside the Vertex Shader for every vertex, I moved the simulation to a Compute Shader.
The Compute Shader outputs a Displacement Map and NormalMap. These textures are set as global shader variables and act as a single source of truth.
* The Ocean Surface, Caustics, Post-Processing, Physics effects read them from one single source of truth.
* I can increase the complexity, add FFT waves etc, without touching the logic.

In the Vertex Shader, the GPU executes that math for every vertex in the mesh.
With Compute Shader, we calculate the waves once per pixel of the texture it just makes more sence for a flat surface like the ocean. By baking to a texture, we decouple the simulation cost from the geometry resolution. And because we dont target mobile devices we are safe to use the texture bandwidth.

##### The split view:
Initially, I attempted to render the split-view using geometric masking rendering a two sided shader for the above the water and underwater views. This resulted in code bloat and complex conditional logic to handle the "near-clip" plane artifacts. More than that we would have to override the material and render the ocean mesh again with a separate shader (with tesselation!) it proved to be very expensive. Eventually I switched to using the near plane of the camera frustrum, it make more sence, keeps code and logic clean and gives a pixel perfect result.

##### Tesselation:
To achieve realistic small-scale details (glitter, micro-waves) without destroying performance, I implemented distance-based Tessellation (Hull/Domain shaders). Mostly references from this tutorial. https://nedmakesgames.medium.com/mastering-tessellation-shaders-and-their-many-uses-in-unity-9caeb760150e

One thing I added is a displacement flattening out in the horizon. I helps with speculars and Zdepth tests and allows to have a shorter computed mesh.

| Pass | Preview |
| :--- | :--- |
| **Final** | <img src="https://github.com/user-attachments/assets/40d10fb1-da61-46a6-9839-a74e00fa5486" width="400"> |
| **Linear Depth** | <img src="https://github.com/user-attachments/assets/3a2126f8-67e6-466c-aea3-32a754918642" width="400"> |
| **Depth below Y** | <img src="https://github.com/user-attachments/assets/1e435222-ce6b-4bfe-b4fc-c3478528eea5" width="400"> |

</details>

[📂 View Source](https://github.com/Veltrynox/plateau-steward/tree/main/Assets/Materials/FX/Ocean)

---

#### Tower Defense Game
![tower_defence_preview](https://github.com/user-attachments/assets/29d94611-262b-4857-a648-915c840de7c9)  
A simple tower defence game using Unity. Featuring wave-based enemy spawning, tower building, upgrades, map progression, and persistent player data. All core game logic is implemented in C# across modular scripts organized under the TowerDefence namespace.  
* [View Source Code](https://github.com/Veltrynox/tower_defence)
* [Play the game](https://veltrynox.itch.io/ironclash-alpha)

#### Space Shooter  
![space shooter](https://github.com/Veltrynox/space_shooter/blob/main/media/output.gif)  
A 2D space shooter game prototype built with Unity. Featuring an HLSL background shader that follows the camera, Levels with enemies, asteroids, and debris spawners using simple Instantiate. A simple enemy sistem driven by "AI".
* [View Source Code](https://github.com/Veltrynox/space_shooter)

---

### Misc small projects
#### Unity Games
* [📂 View Source](https://github.com/Veltrynox/gamedev_course_homework_archive)  

| Project    | Preview                           | | |
| ---------- | --------------------------------- |-|-|
| Helix Jump | <img src="https://github.com/Veltrynox/gamedev_course_homework_archive/blob/main/helixjump/images/gameplay.gif" width="150" height="300" />   | Bass Blast | <img src="https://github.com/Veltrynox/gamedev_course_homework_archive/blob/main/ball_blast/content/gameplay.gif" width="400" height="250" /> |
| Adventure  | <img src="https://github.com/Veltrynox/gamedev_course_homework_archive/blob/main/content/adventure.gif" width="300" height="300" />           | | |

---

| Project | Preview | Project | Preview |
| :--- | :--- | :--- | :--- |
| **Pacman** (SFML) | ![](https://github.com/Veltrynox/gamedev_course_homework_archive/blob/main/content/pacman.gif) | **FindCouple** (SFML) | ![](https://github.com/Veltrynox/gamedev_course_homework_archive/blob/main/content/find_couple.gif) |
| **Arkanoid** (SFML) | ![](https://github.com/Veltrynox/gamedev_course_homework_archive/blob/main/content/arkanoid.gif) | **Pong Clone** (LOVE2D) | ![](https://github.com/Veltrynox/gamedev_course_homework_archive/blob/main/content/pong_banner.jpg) |
---

### 📬 Get In Touch
Feel free to reach out for collaborations or inquiries!
**[Email Me](ilarin75@gmail.com)** | **[Download Resume (PDF)](#)** | **[GitHub](https://github.com/Veltrynox)** | **[LinkedIn](#)**
