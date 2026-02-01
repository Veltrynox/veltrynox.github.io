---
layout: default
title: Portfolio
---

<div style="text-align: center; margin-bottom: 40px;">
  <h5>📬 Contact & Links</h5>
  <p>
    <a href="mailto:ilarin75@gmail.com" style="margin-right: 15px;"><strong>✉️ Email Me</strong></a>
    <a href="#" style="margin-right: 15px;"><strong>📄 Download Resume (PDF)</strong></a>
    <a href="https://github.com/Veltrynox"><strong>GitHub</strong></a>
  </p>
</div>

<hr>

<h2>🎮 Games</h2>

<div style="display: flex; flex-wrap: wrap; gap: 30px; margin-bottom: 40px; align-items: start;">
  <div style="flex: 1; min-width: 300px;">
    <a href="https://github.com/user-attachments/assets/29d94611-262b-4857-a648-915c840de7c9">
      <img src="https://github.com/user-attachments/assets/29d94611-262b-4857-a648-915c840de7c9" style="width: 100%; border-radius: 8px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
    </a>
  </div>
  <div style="flex: 1; min-width: 300px;">
    <h3>Tower Defense</h3>
    <p><strong>Core Systems:</strong> Wave spawning, building, upgrades, and persistent data.</p>
    <p>
      <a href="https://github.com/Veltrynox/tower_defence">📂 <strong>Source Code</strong></a> | 
      <a href="https://veltrynox.itch.io/ironclash-alpha">🎮 <strong>Play Game</strong></a>
    </p>
  </div>
</div>

<div style="display: flex; flex-wrap: wrap; gap: 30px; margin-bottom: 40px; align-items: start;">
  <div style="flex: 1; min-width: 300px;">
    <a href="https://raw.githubusercontent.com/Veltrynox/space_shooter/main/media/output.gif">
      <img src="https://raw.githubusercontent.com/Veltrynox/space_shooter/main/media/output.gif" style="width: 100%; border-radius: 8px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
    </a>
  </div>
  <div style="flex: 1; min-width: 300px;">
    <h3>Space Shooter</h3>
    <p><strong>2D Prototype:</strong> Features smooth player movement, projectile pooling, and enemy patterns.</p>
    <p>
      <a href="https://github.com/Veltrynox/space_shooter">📂 <strong>Source Code</strong></a>
    </p>
  </div>
</div>

<br>

<details>
<summary style="cursor: pointer; font-size: 1.1em;"><strong>🕹️ Archive: Full Project History (Click to Expand)</strong></summary>
<br>

<p><a href="https://github.com/Veltrynox/gamedev_course_homework_archive">📂 <strong>View Source Code Repository</strong></a></p>

<div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(160px, 1fr)); gap: 20px; text-align: center;">
  
  <div>
    <img src="https://raw.githubusercontent.com/Veltrynox/gamedev_course_homework_archive/main/helixjump/images/gameplay.gif" style="width: 100%; border-radius: 6px;">
    <p><strong>Helix Jump</strong></p>
  </div>
  
  <div>
    <img src="https://raw.githubusercontent.com/Veltrynox/gamedev_course_homework_archive/main/ball_blast/content/gameplay.gif" style="width: 100%; border-radius: 6px;">
    <p><strong>Ball Blast</strong></p>
  </div>

  <div>
    <img src="https://raw.githubusercontent.com/Veltrynox/gamedev_course_homework_archive/main/content/adventure.gif" style="width: 100%; border-radius: 6px;">
    <p><strong>Adventure</strong></p>
  </div>

  <div>
    <img src="https://raw.githubusercontent.com/Veltrynox/gamedev_course_homework_archive/main/content/pacman.gif" style="width: 100%; border-radius: 6px;">
    <p><strong>Pacman</strong></p>
  </div>

  <div>
    <img src="https://raw.githubusercontent.com/Veltrynox/gamedev_course_homework_archive/main/content/arkanoid.gif" style="width: 100%; border-radius: 6px;">
    <p><strong>Arkanoid</strong></p>
  </div>

  <div>
    <img src="https://raw.githubusercontent.com/Veltrynox/gamedev_course_homework_archive/main/content/find_couple.gif" style="width: 100%; border-radius: 6px;">
    <p><strong>FindCouple</strong></p>
  </div>

  <div>
    <img src="https://raw.githubusercontent.com/Veltrynox/gamedev_course_homework_archive/main/content/pong_banner.jpg" style="width: 100%; border-radius: 6px;">
    <p><strong>Pong Clone</strong></p>
  </div>
</div>
</details>

<hr>

<h2>🎨 Shaders & Graphics</h2>

<h3>Ocean Shader</h3>
<img src="https://github.com/user-attachments/assets/158e0db6-c761-473b-b1be-e137b3e6992d" style="width: 100%; border-radius: 8px; margin-bottom: 15px;">

<p><a href="https://github.com/Veltrynox/plateau-steward/tree/main/Assets/Materials/FX/Ocean"><strong>📂 View Source Code</strong></a></p>

<details>
<summary style="cursor: pointer;"><strong>📖 Read Technical Breakdown (Compute Shader, Split View, Tessellation)</strong></summary>
<div style="margin-top: 15px; padding-left: 10px; border-left: 3px solid #ddd;">

<h5>Gerstner Waves (Compute Shader):</h5>
<p>Optimized simulation by moving Gerstner math from the Vertex Shader to a Compute Shader.</p>
<ul>
  <li>Outputs Displacement and Normal Maps as global shader variables.</li>
  <li>Decouples simulation cost from geometry resolution.</li>
</ul>

<h5>The Split View & Tessellation:</h5>
<ul>
  <li><strong>Split View:</strong> Switched from geometric masking to camera near-plane logic for a pixel-perfect water line.</li>
  <li><strong>Tessellation:</strong> Implemented distance-based Hull/Domain shaders for micro-detail without a performance hit.</li>
</ul>

<div style="display: flex; gap: 10px; flex-wrap: wrap;">
  <div style="flex: 1; min-width: 250px;">
    <p><strong>Final Render</strong></p>
    <img src="https://github.com/user-attachments/assets/40d10fb1-da61-46a6-9839-a74e00fa5486" style="width: 100%; border-radius: 6px;">
  </div>
  <div style="flex: 1; min-width: 250px;">
    <p><strong>Linear Depth</strong></p>
    <img src="https://github.com/user-attachments/assets/3a2126f8-67e6-466c-aea3-32a754918642" style="width: 100%; border-radius: 6px;">
  </div>
</div>

</div>
</details>

<hr>
<h2>🛠️ Tools</h2>

<div style="display: flex; flex-wrap: wrap; gap: 20px; margin-bottom: 30px; align-items: center;">
  <div style="flex: 1; min-width: 300px;">
    <h3>Procedural Rock Arch Generator</h3>
    <p><strong>Unity & Houdini:</strong> A procedural tool for generating complex rock arches and natural formations directly within Unity using Houdini Engine.</p>
    <a href="https://youtu.be/U2MAFMaHZb4" style="margin-right: 15px;">📺 Watch Demo</a>
    <a href="https://github.com/Veltrynox/misc_samples">📂 View Source</a>
  </div>
  <div style="flex: 1; min-width: 300px;">
    <img src="https://github.com/user-attachments/assets/13191263-b3d9-480b-8201-2f62d315451c" style="width: 100%; border-radius: 6px;" alt="Procedural Rock Arch Generator Screenshot">
  </div>
</div>

<div style="display: flex; flex-wrap: wrap; gap: 20px; margin-bottom: 30px; align-items: center;">
  <div style="flex: 1; min-width: 300px;">
    <h3>SandPile (C++)</h3>
    <p><strong>Cellular Automata:</strong> A C++ implementation of the Abelian Sandpile Model.</p>
    <a href="https://github.com/Veltrynox/misc_samples/tree/main/OpenCL/sandpile_algorithm">📂 View Source</a>
  </div>
  <div style="flex: 1; min-width: 300px;">
    <img src="https://github.com/user-attachments/assets/b90e06e2-ef6f-41de-aba2-c4a26697257a" style="width: 100%; border-radius: 6px;">
  </div>
</div>

<div style="display: flex; flex-wrap: wrap; gap: 20px; margin-bottom: 30px; align-items: center;">
  <div style="flex: 1; min-width: 300px;">
    <h3>Houdini Rocks Generator</h3>
    <p>Houdini Unity Engine procedural rocks generator that uses Unity's terrain.</p>
    <a href="https://github.com/Veltrynox/misc_samples/blob/main/houdini/sop_ps.terraingeo.1.0.hdalc">📂 View Source</a>  
  </div>
  <div style="flex: 1; min-width: 300px;">
    <img src="https://github.com/user-attachments/assets/05bc4baf-3e63-4303-b1c2-be1ea4deb0f3" style="width: 100%; border-radius: 6px;">
  </div>
</div>

<div style="display: flex; flex-wrap: wrap; gap: 20px; margin-bottom: 30px; align-items: center;">
  <div style="flex: 1; min-width: 300px;">
    <h3>Houdini Tunnel Generator</h3>
    <p>Houdini Python State tool for generating tunnel skeletons.</p>
    <a href="https://github.com/Veltrynox/misc_samples/blob/main/houdini/houdiniTonnelGeneratorState">📂 View Source</a>  
  </div>
  <div style="flex: 1; min-width: 300px;">
    <img src="https://github.com/user-attachments/assets/415a7b56-7b06-491f-b6a9-4298a1622b28" style="width: 100%; border-radius: 6px;">
  </div>
</div>

<hr>

<div style="text-align: center; margin-top: 40px; margin-bottom: 60px;">
  <h3>📬 Get In Touch</h3>
  <p>
    <a href="mailto:ilarin75@gmail.com" style="margin-right: 15px;"><strong>Email Me</strong></a> | 
    <a href="#" style="margin-right: 15px;"><strong>Download Resume (PDF)</strong></a> | 
    <a href="https://github.com/Veltrynox"><strong>GitHub</strong></a>
  </p>
</div>


