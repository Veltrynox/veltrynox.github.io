---
layout: post
title: "Gerstner Waves Unity"
---

# UNITY. The Waterline & Underwater Effect
![shader_preview](https://github.com/user-attachments/assets/158e0db6-c761-473b-b1be-e137b3e6992d)  
[📂 View Source](https://github.com/Veltrynox/plateau-steward/tree/main/Assets/Materials/FX/Ocean)

## Gerstner Waves:
Instead of calculating Gerstner Wave math inside the Vertex Shader for every vertex, I moved the simulation to a Compute Shader.
The Compute Shader outputs a RenderTexture (Displacement Map) and NormalMap. These textures are set as global shader variables and act as a single source of truth.
* The Ocean Surface reads them to displace vertices.
* The Post-Processing Effect reads them to calculate the waterline.
* Caustics can read it as well
* The C# Physics System can read the buffer for buoyancy.
* I can easily increase the complexity, add FFT waves etc, without touching the logic.

In the Vertex Shader, the GPU executes that math for every vertex in the mesh.
With Compute Shader, we calculate the waves once per pixel of the texture it just makes more sence for a flat surface like the ocean. By baking to a texture, we decouple the simulation cost from the geometry resolution. And because we dont target mobile devices we are safe to use the texture bandwidth.

## The split view:
Initially, I attempted to render the split-view using geometric masking rendering a two sided shader for the above the water and underwater views. This resulted in code bloat and complex conditional logic to handle the "near-clip" plane artifacts. More than that we would have to override the material and render the ocean mesh again with a separate shader (with tesselation!) it proved to be very very expensive. Eventually I switched to using the near plane of the camera frustrum, it make more sence, keeps code and logic clean and gives a pixel perfect result. I sample a shader ocean water mesh.

## Tesselation:
To achieve realistic small-scale details (glitter, micro-waves) without destroying performance, I implemented distance-based Tessellation (Hull/Domain shaders). Mostly references from this tutorial. https://nedmakesgames.medium.com/mastering-tessellation-shaders-and-their-many-uses-in-unity-9caeb760150e

One thing I added is a displacement flattening out in the horizon. I helps with speculars and Zdepth tests and allows to have a shorter computed mesh.

The depth pass is pretty streightforward and consists only of two main layers:
<img width="1467" height="828" alt="Screenshot 2025-12-30 at 11 16 00 AM" src="https://github.com/user-attachments/assets/40d10fb1-da61-46a6-9839-a74e00fa5486" />

1. The Scene Linear Depth layer
<img width="1467" height="828" alt="Screenshot 2025-12-30 at 11 15 53 AM" src="https://github.com/user-attachments/assets/3a2126f8-67e6-466c-aea3-32a754918642" />

3. The Scene Depth Below the Y axis
<img width="1467" height="828" alt="Screenshot 2025-12-30 at 11 16 40 AM" src="https://github.com/user-attachments/assets/1e435222-ce6b-4bfe-b4fc-c3478528eea5" />
