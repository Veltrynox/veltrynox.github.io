---
layout: default
title: Ivan Larinin | Technical Artist & Pipeline Tools Developer
---

<!-- Hero Section: Front-Loaded Value Proposition -->
<section class="hero">
  <h1 class="hero-title">
    <span class="hero-title-gradient">Unreal Engine Pipeline &amp; Editor Tools</span>
  </h1>
  <p class="hero-subtitle">
    <strong style="color: var(--text-primary); font-size: 1.25rem; display: block; margin-bottom: 0.5rem;">I build the systems that help teams ship.</strong>
    Specializing in custom Unreal Engine C++ editor plugins and pipeline tooling.
  </p>
  <div class="hero-links">
    <a href="https://github.com/Veltrynox" target="_blank" rel="noopener" class="btn btn-primary">📂 GitHub Profile</a>
    <a href="blog.html" class="btn btn-secondary">📝 Technical Blog</a>
    <a href="{{ '/assets/Ivan_Larinin_Resume.pdf' | relative_url }}" download="Ivan_Larinin_Resume.pdf" class="btn btn-secondary">📄 Download Resume (PDF)</a>
    <a href="mailto:ilarin75@gmail.com" class="btn btn-secondary">✉️ Get In Touch</a>
  </div>
</section>

<!-- SECTION 1: Tools & Engine Plugins -->
<section id="tools" style="margin-bottom: 4.5rem;">
  
  <div class="section-header">
    <h2 class="section-title">
      <span class="section-title-icon">🛠️</span> Core Tools &amp; Engine Plugins
    </h2>
  </div>

  <!-- Featured Project Banner: Quest System Plugin -->
  <div class="card featured-card" style="margin-bottom: 2rem;">
    <div class="card-body featured-grid">
      <div>
        <div class="card-media-badge">FEATURED UE5 PLUGIN</div>
        <h3 class="card-title" style="font-size: 1.6rem; margin-top: 0.5rem;">Quest System Plugin (UE5 C++)</h3>
        <p class="card-description">
          Custom C++ plugin for Unreal Engine 5 featuring an integrated Slate visual node graph editor toolkit, runtime quest manager subsystem (UWorldSubsystem), multi-root DAG execution, and JSON state serialization.
        </p>
        <div class="card-tags">
          <span class="tag tag-cpp">Unreal Engine 5</span>
          <span class="tag tag-csharp" style="color: #38bdf8; border-color: rgba(56, 189, 248, 0.3);">C++ Plugin</span>
          <span class="tag tag-unity">Slate UI</span>
          <span class="tag">Node Graph Editor</span>
        </div>
        <div class="card-footer" style="padding-top: 1rem;">
          <a href="questsystem.html" class="btn btn-primary btn-sm">📝 Read Technical Breakdown</a>
          <a href="https://github.com/Veltrynox/UE5-QuestSystem" target="_blank" rel="noopener" class="btn btn-secondary btn-sm">📂 View GitHub Repository</a>
        </div>
      </div>
      <div class="card-media" style="border-radius: var(--radius-md); box-shadow: 0 8px 25px rgba(0,0,0,0.4);">
        <img src="{{ '/assets/media/quest_system_graph.png' | relative_url }}" alt="Unreal Engine 5 Quest System Graph Editor" loading="lazy">
      </div>
    </div>
  </div>

  <!-- Tools Grid -->
  <div class="grid" style="margin-bottom: 0;">

    <!-- Unity Scatter Brush Tool -->
    <div class="card">
      <div class="card-media">
        <span class="card-media-badge">UNITY EDITOR EXTENSION</span>
        <img src="{{ '/assets/media/scattering_unity.gif' | relative_url }}" alt="Unity Scatter Brush Tool Demonstration" loading="lazy">
      </div>
      <div class="card-body">
        <h3 class="card-title">Scatter Brush Editor Tool</h3>
        <p class="card-description">
          Custom Unity EditorWindow tool for painting gameobject prefabs directly onto terrain in the Scene View with surface normal alignment, number key hotkeys, and full Undo support.
        </p>
        <div class="card-tags">
          <span class="tag tag-unity">Unity</span>
          <span class="tag tag-csharp">C#</span>
          <span class="tag tag-unity">Editor Tools</span>
        </div>
        <div class="card-footer">
          <a href="unityscatter.html" class="btn btn-primary btn-sm">📝 Read Blog Post</a>
        </div>
      </div>
    </div>

    <!-- Sand Dunes Simulation (Houdini C++ SOP) -->
    <div class="card">
      <div class="card-media">
        <span class="card-media-badge">HOUDINI C++ SOP</span>
        <img src="https://github.com/user-attachments/assets/b90e06e2-ef6f-41de-aba2-c4a26697257a" alt="Sand Dunes Simulation" loading="lazy">
      </div>
      <div class="card-body">
        <h3 class="card-title">Sand Dunes Simulation (Houdini C++ SOP)</h3>
        <p class="card-description">
          Custom C++ Houdini Surface Operator (SOP) node written for sand dune dynamics simulation on the feature film <em>Dune (Part One)</em>.
        </p>
        <div class="card-tags">
          <span class="tag tag-cpp">Houdini C++</span>
          <span class="tag tag-shader">Dune (Part One)</span>
          <span class="tag">VFX Simulation</span>
        </div>
        <div class="card-footer">
          <a href="sandpile.html" class="btn btn-primary btn-sm">📝 Read Blog Post</a>
          <a href="https://github.com/Veltrynox/misc_samples/tree/main/OpenCL/sandpile_algorithm" target="_blank" rel="noopener" class="btn btn-secondary btn-sm">📂 Source</a>
        </div>
      </div>
    </div>

    <!-- Procedural City Generator (Unreal Engine) -->
    <div class="card">
      <div class="card-media">
        <span class="card-media-badge">HOUDINI ENGINE</span>
        <img src="{{ '/assets/media/procedural_city.gif' | relative_url }}" alt="Procedural City Unreal Engine" loading="lazy">
      </div>
      <div class="card-body">
        <h3 class="card-title">Procedural Building &amp; City Generator</h3>
        <p class="card-description">
          Procedural building and city layout generator tool built using Houdini Engine for Unreal Engine. Generates modular architectural geometry and layout distributions interactively.
        </p>
        <div class="card-tags">
          <span class="tag tag-houdini">Houdini Engine</span>
          <span class="tag tag-csharp">Unreal Engine</span>
          <span class="tag">Procedural Tool</span>
        </div>
        <div class="card-footer">
          <a href="https://www.artstation.com/artwork/41bWB1" target="_blank" rel="noopener" class="btn btn-primary btn-sm">🎨 View on ArtStation</a>
        </div>
      </div>
    </div>

    <!-- Houdini Engine Environment Utilities (Rock Arch & Terrain Rocks) -->
    <div class="card">
      <div class="card-media">
        <span class="card-media-badge">HOUDINI ENGINE</span>
        <img src="{{ '/assets/media/rock_arch.jpg' | relative_url }}" alt="Procedural Rock Arch and Rocks" loading="lazy">
      </div>
      <div class="card-body">
        <h3 class="card-title">Houdini Engine Environment Utilities</h3>
        <p class="card-description">
          Procedural workflow tools built with Houdini Engine for Unity. Includes a Procedural Rock Arch Generator for natural formations and a Terrain Rocks scatter tool for automated environment dressing.
        </p>
        <div class="card-tags">
          <span class="tag tag-houdini">Houdini Engine</span>
          <span class="tag tag-unity">Unity</span>
          <span class="tag">Procedural HDA</span>
        </div>
        <div class="card-footer">
          <a href="https://youtu.be/U2MAFMaHZb4" target="_blank" rel="noopener" class="btn btn-primary btn-sm">📺 Watch Demo</a>
          <a href="https://github.com/Veltrynox/misc_samples" target="_blank" rel="noopener" class="btn btn-secondary btn-sm">📂 View Source</a>
        </div>
      </div>
    </div>

  </div>

</section>

<!-- SECTION 2: Real-Time Graphics & Technical Art -->
<section id="graphics" style="margin-bottom: 4.5rem;">
  
  <div class="section-header">
    <h2 class="section-title">
      <span class="section-title-icon">🌊</span> Real-Time Graphics &amp; Technical Art
    </h2>
  </div>

  <div class="grid" style="margin-bottom: 0;">

    <!-- Laminaria VAT GPU Instancing -->
    <div class="card">
      <div class="card-media">
        <span class="card-media-badge">TECH ART / SHADERS</span>
        <img src="{{ '/assets/media/laminaria.gif' | relative_url }}" alt="Laminaria VAT GPU Instancing Preview" loading="lazy">
      </div>
      <div class="card-body">
        <h3 class="card-title">Laminaria — GPU Instanced Procedural Tool (VAT)</h3>
        <p class="card-description">
          Unity-based GPU instanced procedural tool for generating scattered Laminaria prefabs. The system integrates Vertex Animation Textures (VAT) authored in Houdini FX for high-fidelity real-time deformation.
        </p>
        <div class="card-tags">
          <span class="tag tag-unity">Unity</span>
          <span class="tag tag-houdini">Houdini FX</span>
          <span class="tag tag-shader">VAT</span>
          <span class="tag">GPU Instancing</span>
        </div>
        <div class="card-footer">
          <a href="https://www.artstation.com/artwork/bg9Zym" target="_blank" rel="noopener" class="btn btn-primary btn-sm">🎨 View on ArtStation</a>
        </div>
      </div>
    </div>

    <!-- Ocean Shader Card -->
    <div class="card">
      <div class="card-media">
        <span class="card-media-badge">COMPUTE SHADER</span>
        <img src="https://github.com/user-attachments/assets/158e0db6-c761-473b-b1be-e137b3e6992d" alt="Ocean Shader Preview" loading="lazy">
      </div>
      <div class="card-body">
        <h3 class="card-title">Ocean Shader (Gerstner Waves)</h3>
        <p class="card-description">
          GPU ocean simulation moving Gerstner math from Vertex Shader to a Compute Shader. Decouples simulation cost from geometry, generates global displacement and normal maps, and includes distance-based Tessellation and near-plane split view.
        </p>
        <div class="card-tags">
          <span class="tag tag-shader">Compute Shader</span>
          <span class="tag tag-shader">HLSL</span>
          <span class="tag tag-unity">Unity</span>
          <span class="tag">Tessellation</span>
        </div>
        <div class="card-footer">
          <a href="oceanshader.html" class="btn btn-primary btn-sm">📝 Read Article</a>
          <a href="https://github.com/Veltrynox/plateau-steward/tree/main/Assets/Materials/FX/Ocean" target="_blank" rel="noopener" class="btn btn-secondary btn-sm">📂 Source</a>
        </div>
      </div>
    </div>

    <!-- Underwater Caustics Projector Shader -->
    <div class="card">
      <div class="card-media">
        <span class="card-media-badge">PROJECTOR SHADER</span>
        <img src="{{ '/assets/media/caustic_shader.gif' | relative_url }}" alt="Caustics Projector Shader" loading="lazy">
      </div>
      <div class="card-body">
        <h3 class="card-title">Caustics Projector Shader (URP)</h3>
        <p class="card-description">
          Custom Universal Render Pipeline (URP) ShaderLab &amp; HLSL caustics projector shader using depth reconstruction, projector box bounds clipping, wave normal distortion, and chromatic aberration.
        </p>
        <div class="card-tags">
          <span class="tag tag-shader">HLSL</span>
          <span class="tag tag-unity">Unity URP</span>
          <span class="tag">Projector Shader</span>
        </div>
        <div class="card-footer">
          <a href="caustics.html" class="btn btn-primary btn-sm">📝 Read Article</a>
        </div>
      </div>
    </div>

  </div>

</section>
