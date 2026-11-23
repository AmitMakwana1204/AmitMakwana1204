<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pure CSS 3D Cybernetic Core Animation</title>
  <style>
    /* =========================================
       1. RESET & COSMIC BACKGROUND
       ========================================= */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      background: radial-gradient(circle at center, #090d16 0%, #020408 100%);
      font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
      overflow: hidden;
      color: #e2e8f0;
    }

    /* Animated Perspective Cyber Grid Floor */
    .cyber-grid {
      position: fixed;
      inset: -50%;
      background-image: 
        linear-gradient(to right, rgba(56, 189, 248, 0.08) 1px, transparent 1px),
        linear-gradient(to bottom, rgba(56, 189, 248, 0.08) 1px, transparent 1px);
      background-size: 60px 60px;
      transform: perspective(600px) rotateX(65deg);
      animation: gridScroll 8s linear infinite;
      pointer-events: none;
      z-index: 0;
    }

    @keyframes gridScroll {
      0% {
        transform: perspective(600px) rotateX(65deg) translateY(0);
      }
      100% {
        transform: perspective(600px) rotateX(65deg) translateY(60px);
      }
    }

    /* =========================================
       2. 3D STAGE & SCENE CONTAINER
       ========================================= */
    .stage {
      position: relative;
      width: 380px;
      height: 380px;
      display: flex;
      justify-content: center;
      align-items: center;
      perspective: 1200px;
      z-index: 2;
      cursor: pointer;
    }

    /* Ambient Neon Aura */
    .ambient-glow {
      position: absolute;
      width: 260px;
      height: 260px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(56, 189, 248, 0.35), rgba(168, 85, 247, 0.15), transparent 70%);
      filter: blur(25px);
      animation: pulseAura 4s ease-in-out infinite alternate;
    }

    @keyframes pulseAura {
      0% {
        transform: scale(0.85);
        opacity: 0.6;
      }
      100% {
        transform: scale(1.25);
        opacity: 1;
      }
    }

    /* =========================================
       3. MULTI-AXIS 3D GYROSCOPE RINGS
       ========================================= */
    .gyroscope {
      position: relative;
      width: 100%;
      height: 100%;
      transform-style: preserve-3d;
      display: flex;
      justify-content: center;
      align-items: center;
      transition: transform 0.6s cubic-bezier(0.23, 1, 0.32, 1);
    }

    /* Interactive Overdrive Mode on Hover */
    .stage:hover .ring-1 { animation-duration: 2.5s; }
    .stage:hover .ring-2 { animation-duration: 3s; }
    .stage:hover .ring-3 { animation-duration: 2s; }
    .stage:hover .core-sphere {
      transform: scale(1.2);
      box-shadow:
        0 0 35px #38bdf8,
        0 0 70px #a855f7,
        inset 0 0 25px #ffffff;
    }

    .ring {
      position: absolute;
      border-radius: 50%;
      transform-style: preserve-3d;
    }

    /* Outer Dashed Cyber Ring */
    .ring-1 {
      width: 340px;
      height: 340px;
      border: 3px dashed rgba(56, 189, 248, 0.75);
      box-shadow: 0 0 25px rgba(56, 189, 248, 0.3), inset 0 0 25px rgba(56, 189, 248, 0.2);
      animation: rotateRing1 10s linear infinite;
    }

    /* Middle Dual-Arc Purple Ring */
    .ring-2 {
      width: 270px;
      height: 270px;
      border: 4px solid transparent;
      border-top: 4px solid #a855f7;
      border-bottom: 4px solid #ec4899;
      box-shadow: 0 0 30px rgba(168, 85, 247, 0.5);
      animation: rotateRing2 7s linear infinite;
    }

    /* Inner High-Speed Cyan Ring */
    .ring-3 {
      width: 200px;
      height: 200px;
      border: 3px solid transparent;
      border-left: 4px solid #22d3ee;
      border-right: 4px solid #38bdf8;
      box-shadow: 0 0 20px rgba(34, 211, 238, 0.6);
      animation: rotateRing3 5s linear infinite;
    }

    /* 4th Tilted Orbital Ring with Glowing Electron */
    .ring-4 {
      width: 310px;
      height: 310px;
      border: 1px solid rgba(255, 255, 255, 0.15);
      animation: rotateRing4 6s linear infinite;
    }

    .ring-4::before {
      content: '';
      position: absolute;
      top: -6px;
      left: 50%;
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: #fff;
      box-shadow: 0 0 15px #38bdf8, 0 0 30px #38bdf8;
    }

    @keyframes rotateRing1 {
      0%   { transform: rotateX(65deg) rotateY(15deg) rotateZ(0deg); }
      100% { transform: rotateX(65deg) rotateY(15deg) rotateZ(360deg); }
    }

    @keyframes rotateRing2 {
      0%   { transform: rotateX(-55deg) rotateY(35deg) rotateZ(0deg); }
      100% { transform: rotateX(-55deg) rotateY(35deg) rotateZ(-360deg); }
    }

    @keyframes rotateRing3 {
      0%   { transform: rotateX(35deg) rotateY(-60deg) rotateZ(0deg); }
      100% { transform: rotateX(35deg) rotateY(-60deg) rotateZ(360deg); }
    }

    @keyframes rotateRing4 {
      0%   { transform: rotateX(75deg) rotateY(-25deg) rotateZ(0deg); }
      100% { transform: rotateX(75deg) rotateY(-25deg) rotateZ(360deg); }
    }

    /* =========================================
       4. MORPHING ENERGY CORE SPHERE
       ========================================= */
    .core-sphere {
      position: relative;
      width: 95px;
      height: 95px;
      border-radius: 42% 58% 70% 30% / 45% 45% 55% 55%;
      background: conic-gradient(from 0deg, #38bdf8, #a855f7, #ec4899, #22d3ee, #38bdf8);
      box-shadow:
        0 0 25px rgba(56, 189, 248, 0.8),
        0 0 55px rgba(168, 85, 247, 0.6),
        inset 0 0 20px rgba(255, 255, 255, 0.9);
      animation: 
        morphCore 6s ease-in-out infinite alternate,
        spinCore 4s linear infinite;
      transition: transform 0.4s ease, box-shadow 0.4s ease;
    }

    /* Inner White-Hot Singularity */
    .core-sphere::after {
      content: '';
      position: absolute;
      inset: 22px;
      border-radius: 50%;
      background: #ffffff;
      filter: blur(4px);
      animation: coreHeartbeat 1.5s ease-in-out infinite alternate;
    }

    @keyframes morphCore {
      0%   { border-radius: 42% 58% 70% 30% / 45% 45% 55% 55%; }
      33%  { border-radius: 70% 30% 46% 54% / 30% 29% 71% 70%; }
      66%  { border-radius: 100% 60% 60% 100% / 100% 100% 60% 60%; }
      100% { border-radius: 42% 58% 70% 30% / 45% 45% 55% 55%; }
    }

    @keyframes spinCore {
      0%   { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    @keyframes coreHeartbeat {
      0%   { transform: scale(0.75); opacity: 0.7; }
      100% { transform: scale(1.15); opacity: 1; }
    }

    /* =========================================
       5. SHOCKWAVE RIPPLES & FLOATING PARTICLES
       ========================================= */
    .shockwave {
      position: absolute;
      width: 100px;
      height: 100px;
      border-radius: 50%;
      border: 2px solid rgba(56, 189, 248, 0.6);
      animation: rippleWave 3.5s cubic-bezier(0.16, 1, 0.3, 1) infinite;
      pointer-events: none;
    }

    .shockwave:nth-child(2) {
      animation-delay: 1.75s;
      border-color: rgba(168, 85, 247, 0.6);
    }

    @keyframes rippleWave {
      0% {
        transform: scale(0.8);
        opacity: 0.9;
      }
      100% {
        transform: scale(3.6);
        opacity: 0;
      }
    }

    /* Floating Energy Sparks */
    .particles span {
      position: absolute;
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: #38bdf8;
      box-shadow: 0 0 10px #38bdf8;
      animation: floatParticle 5s ease-in-out infinite;
    }

    .particles span:nth-child(1) { top: 10%; left: 20%; animation-delay: 0s; }
    .particles span:nth-child(2) { top: 80%; left: 15%; animation-delay: 1s; background: #a855f7; }
    .particles span:nth-child(3) { top: 20%; right: 15%; animation-delay: 2s; background: #ec4899; }
    .particles span:nth-child(4) { bottom: 15%; right: 20%; animation-delay: 1.5s; }
    .particles span:nth-child(5) { top: 50%; left: 5%; animation-delay: 2.5s; background: #22d3ee; }
    .particles span:nth-child(6) { top: 45%; right: 5%; animation-delay: 0.5s; background: #a855f7; }

    @keyframes floatParticle {
      0%, 100% {
        transform: translateY(0) scale(1);
        opacity: 0.3;
      }
      50% {
        transform: translateY(-28px) scale(1.6);
        opacity: 1;
      }
    }

    /* =========================================
       6. HUD STATUS LABEL
       ========================================= */
    .hud-panel {
      margin-top: 24px;
      text-align: center;
      z-index: 2;
      letter-spacing: 3px;
      text-transform: uppercase;
    }

    .hud-title {
      font-size: 1.1rem;
      font-weight: 700;
      background: linear-gradient(90deg, #38bdf8, #a855f7, #ec4899, #38bdf8);
      background-size: 200% auto;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      animation: textShimmer 3s linear infinite;
    }

    .hud-sub {
      margin-top: 6px;
      font-size: 0.75rem;
      color: #94a3b8;
    }

    @keyframes textShimmer {
      to { background-position: 200% center; }
    }
  </style>
</head>
<body>

  <!-- Infinite Scrolling 3D Perspective Grid -->
  <div class="cyber-grid"></div>

  <!-- Interactive 3D Animation Stage -->
  <div class="stage" title="Hover to activate Overdrive">
    <div class="ambient-glow"></div>

    <!-- Expanding Energy Shockwaves -->
    <div class="shockwave"></div>
    <div class="shockwave"></div>

    <!-- Floating Particle Nodes -->
    <div class="particles">
      <span></span><span></span><span></span>
      <span></span><span></span><span></span>
    </div>

    <!-- 3D Gyroscope Assembly -->
    <div class="gyroscope">
      <div class="ring ring-1"></div>
      <div class="ring ring-2"></div>
      <div class="ring ring-3"></div>
      <div class="ring ring-4"></div>
      <div class="core-sphere"></div>
    </div>
  </div>

  <!-- Minimal HUD Text -->
  <div class="hud-panel">
    <div class="hud-title">Quantum Core Active</div>
    <div class="hud-sub">Hover Core For Overdrive • Pure HTML & CSS Keyframes</div>
  </div>

</body>
</html>
