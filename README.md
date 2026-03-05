<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>3d0hidayat — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=VT323:wght@400&display=swap" rel="stylesheet">
<style>
  :root {
    --pixel-green: #00ff88;
    --pixel-blue: #00cfff;
    --pixel-yellow: #ffe600;
    --pixel-red: #ff4444;
    --pixel-purple: #b86fff;
    --bg-dark: #0a0a0f;
    --bg-panel: #0d1117;
    --bg-card: #161b22;
    --border: #30363d;
    --text: #e6edf3;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg-dark);
    font-family: 'Press Start 2P', monospace;
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Scanlines overlay */
  body::after {
    content: '';
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.15) 2px,
      rgba(0,0,0,0.15) 4px
    );
    pointer-events: none;
    z-index: 9999;
  }

  /* Stars background */
  .stars {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    z-index: 0;
  }

  .star {
    position: absolute;
    width: 2px;
    height: 2px;
    background: white;
    animation: twinkle 3s infinite;
  }

  @keyframes twinkle {
    0%, 100% { opacity: 0.2; }
    50% { opacity: 1; }
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 20px;
    position: relative;
    z-index: 1;
  }

  /* ===== HEADER ===== */
  .header {
    text-align: center;
    padding: 30px 0 20px;
    position: relative;
  }

  .header-title {
    font-size: 11px;
    color: var(--pixel-green);
    text-shadow: 0 0 20px var(--pixel-green), 0 0 40px var(--pixel-green);
    letter-spacing: 2px;
    animation: glow 2s ease-in-out infinite alternate;
    margin-bottom: 8px;
  }

  @keyframes glow {
    from { text-shadow: 0 0 10px var(--pixel-green); }
    to   { text-shadow: 0 0 30px var(--pixel-green), 0 0 60px var(--pixel-green); }
  }

  .header-sub {
    font-size: 7px;
    color: var(--pixel-blue);
    letter-spacing: 3px;
    animation: blink 1.5s step-end infinite;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  /* ===== PIXEL BORDER ===== */
  .pixel-box {
    border: 2px solid var(--border);
    background: var(--bg-card);
    position: relative;
    margin-bottom: 16px;
    image-rendering: pixelated;
  }

  .pixel-box::before {
    content: '';
    position: absolute;
    top: -1px; left: 4px; right: 4px;
    height: 1px;
    background: var(--pixel-green);
    opacity: 0.6;
  }

  .pixel-box-title {
    font-size: 7px;
    color: var(--pixel-yellow);
    padding: 10px 14px 6px;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 8px;
    letter-spacing: 1px;
  }

  .pixel-box-title span.icon {
    font-size: 10px;
  }

  /* ===== CHARACTER CARD ===== */
  .char-card {
    display: grid;
    grid-template-columns: 140px 1fr;
    gap: 0;
  }

  .char-sprite {
    padding: 16px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border-right: 1px solid var(--border);
    background: linear-gradient(135deg, #0d1117, #161b22);
  }

  /* Pixel art character made with CSS */
  .pixel-char {
    width: 64px;
    height: 64px;
    image-rendering: pixelated;
    position: relative;
    margin-bottom: 8px;
  }

  .pixel-char canvas {
    width: 64px;
    height: 64px;
    image-rendering: pixelated;
  }

  .char-name {
    font-size: 6px;
    color: var(--pixel-green);
    text-align: center;
    margin-top: 4px;
  }

  .char-class {
    font-size: 5px;
    color: var(--pixel-blue);
    text-align: center;
    margin-top: 3px;
    font-family: 'VT323', monospace;
    font-size: 14px;
  }

  .char-info {
    padding: 14px;
  }

  .char-quote {
    font-size: 6px;
    color: #8b949e;
    font-family: 'VT323', monospace;
    font-size: 15px;
    line-height: 1.6;
    border-left: 2px solid var(--pixel-purple);
    padding-left: 10px;
    margin-bottom: 12px;
    font-style: italic;
  }

  /* ===== STAT BARS ===== */
  .stat-row {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 8px;
  }

  .stat-label {
    font-size: 5px;
    color: #8b949e;
    width: 70px;
    flex-shrink: 0;
    letter-spacing: 1px;
  }

  .stat-bar-wrap {
    flex: 1;
    height: 10px;
    background: #0d1117;
    border: 1px solid #30363d;
    position: relative;
    overflow: hidden;
  }

  .stat-bar-fill {
    height: 100%;
    position: relative;
    transition: width 1.5s cubic-bezier(0.23, 1, 0.32, 1);
    animation: barLoad 1.5s ease-out forwards;
  }

  .stat-bar-fill::after {
    content: '';
    position: absolute;
    right: 0;
    top: 0;
    width: 3px;
    height: 100%;
    background: white;
    opacity: 0.8;
  }

  .stat-val {
    font-size: 5px;
    color: var(--pixel-yellow);
    width: 30px;
    text-align: right;
  }

  @keyframes barLoad {
    from { width: 0; }
  }

  /* ===== LEVEL / XP ===== */
  .level-row {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 10px;
  }

  .level-badge {
    background: var(--pixel-yellow);
    color: #000;
    font-size: 5px;
    padding: 3px 6px;
    flex-shrink: 0;
  }

  .xp-bar-wrap {
    flex: 1;
    height: 12px;
    background: #0d1117;
    border: 1px solid #30363d;
    overflow: hidden;
    position: relative;
  }

  .xp-bar-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--pixel-green), var(--pixel-blue));
    width: 35%;
    animation: barLoad 2s ease-out forwards;
    position: relative;
  }

  .xp-bar-fill::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background: repeating-linear-gradient(
      90deg,
      transparent,
      transparent 6px,
      rgba(255,255,255,0.1) 6px,
      rgba(255,255,255,0.1) 7px
    );
  }

  .xp-label {
    font-size: 5px;
    color: #8b949e;
  }

  /* ===== QUEST LOG ===== */
  .quest-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    padding: 10px 14px;
    border-bottom: 1px solid #1c2128;
  }

  .quest-item:last-child { border-bottom: none; }

  .quest-status {
    font-size: 10px;
    flex-shrink: 0;
    margin-top: 1px;
  }

  .quest-status.done { color: var(--pixel-green); }
  .quest-status.active { color: var(--pixel-yellow); animation: blink 1s step-end infinite; }
  .quest-status.locked { color: #30363d; }

  .quest-text {
    font-size: 5.5px;
    color: var(--text);
    line-height: 2;
    font-family: 'VT323', monospace;
    font-size: 15px;
  }

  .quest-reward {
    font-size: 5px;
    color: var(--pixel-purple);
    margin-top: 2px;
    font-size: 11px;
    font-family: 'VT323', monospace;
  }

  /* ===== TECH INVENTORY ===== */
  .inventory-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
    gap: 8px;
    padding: 12px 14px;
  }

  .inv-item {
    border: 1px solid var(--border);
    padding: 8px 4px;
    text-align: center;
    cursor: default;
    transition: all 0.1s;
    position: relative;
    background: #0d1117;
  }

  .inv-item:hover {
    border-color: var(--pixel-green);
    background: rgba(0,255,136,0.05);
    transform: translateY(-2px);
    box-shadow: 0 4px 0 rgba(0,255,136,0.3);
  }

  .inv-item .inv-icon {
    font-size: 20px;
    display: block;
    margin-bottom: 5px;
  }

  .inv-item .inv-name {
    font-size: 4px;
    color: var(--pixel-blue);
    letter-spacing: 0.5px;
  }

  .inv-item .inv-rarity {
    position: absolute;
    top: 3px;
    right: 3px;
    width: 5px;
    height: 5px;
    border-radius: 0;
  }

  .rarity-common { background: #8b949e; }
  .rarity-uncommon { background: var(--pixel-green); }
  .rarity-rare { background: var(--pixel-blue); }
  .rarity-epic { background: var(--pixel-purple); }

  /* ===== STATS GRID ===== */
  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: var(--border);
  }

  .stat-cell {
    background: var(--bg-card);
    padding: 14px;
    text-align: center;
  }

  .stat-cell .num {
    font-size: 18px;
    color: var(--pixel-green);
    display: block;
    margin-bottom: 6px;
    font-family: 'VT323', monospace;
    text-shadow: 0 0 10px var(--pixel-green);
  }

  .stat-cell .lbl {
    font-size: 5px;
    color: #8b949e;
    letter-spacing: 1px;
  }

  /* ===== FOOTER ===== */
  .footer {
    text-align: center;
    padding: 20px;
    font-size: 5px;
    color: #30363d;
    letter-spacing: 2px;
  }

  /* Floating pixel particles */
  .pixel-particle {
    position: fixed;
    width: 4px;
    height: 4px;
    pointer-events: none;
    z-index: 2;
    animation: floatUp 8s linear infinite;
    opacity: 0;
  }

  @keyframes floatUp {
    0%   { transform: translateY(100vh) rotate(0deg); opacity: 0; }
    10%  { opacity: 1; }
    90%  { opacity: 0.5; }
    100% { transform: translateY(-100px) rotate(360deg); opacity: 0; }
  }

  /* Glitch effect on hover */
  .glitch {
    position: relative;
  }
  .glitch:hover {
    animation: glitch 0.3s step-end;
  }
  @keyframes glitch {
    0%   { clip-path: inset(20% 0 60% 0); transform: translate(-4px, 0); }
    20%  { clip-path: inset(50% 0 30% 0); transform: translate(4px, 0); }
    40%  { clip-path: inset(10% 0 80% 0); transform: translate(0, 0); }
    60%  { clip-path: inset(70% 0 10% 0); transform: translate(-2px, 0); }
    80%  { clip-path: inset(40% 0 40% 0); transform: translate(2px, 0); }
    100% { clip-path: inset(0); transform: translate(0, 0); }
  }

  .console-line {
    font-family: 'VT323', monospace;
    font-size: 15px;
    color: var(--pixel-green);
    padding: 4px 14px;
    border-bottom: 1px solid #1c2128;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .console-line .prompt { color: var(--pixel-blue); }
  .console-line .cmd { color: var(--text); }
  .console-line .out { color: var(--pixel-yellow); }

  .cursor-blink {
    display: inline-block;
    width: 8px;
    height: 14px;
    background: var(--pixel-green);
    animation: blink 0.8s step-end infinite;
    vertical-align: bottom;
  }
</style>
</head>
<body>

<!-- Stars -->
<div class="stars" id="stars"></div>

<!-- Pixel particles -->
<div id="particles"></div>

<div class="container">

  <!-- HEADER -->
  <div class="header">
    <div style="font-size:9px; color:#30363d; letter-spacing:3px; margin-bottom:8px;">▓░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░▓</div>
    <div class="header-title glitch">⚔ &nbsp;3D0HIDAYAT&nbsp; ⚔</div>
    <div style="margin:8px 0; font-size:8px; color:var(--pixel-purple);">[ WEB DEVELOPER EXPLORER ]</div>
    <div class="header-sub">▶ PRESS START TO VIEW PROFILE ◀</div>
    <div style="font-size:9px; color:#30363d; letter-spacing:3px; margin-top:8px;">▓░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░▓</div>
  </div>

  <!-- CHARACTER CARD -->
  <div class="pixel-box">
    <div class="pixel-box-title">
      <span class="icon">🧙</span> CHARACTER PROFILE
    </div>
    <div class="char-card">
      <div class="char-sprite">
        <canvas class="pixel-char" id="charCanvas" width="32" height="32"></canvas>
        <div class="char-name">3D0HIDAYAT</div>
        <div class="char-class">Web Explorer</div>
        <br>
        <div class="level-row" style="flex-direction:column; gap:4px;">
          <div style="display:flex;gap:6px;align-items:center;">
            <div class="level-badge">LV.1</div>
            <span class="xp-label" style="font-size:5px;">XP: 350/1000</span>
          </div>
          <div class="xp-bar-wrap" style="width:100%;">
            <div class="xp-bar-fill" style="width:35%;"></div>
          </div>
        </div>
      </div>

      <div class="char-info">
        <div class="char-quote">"Every line of code that finally runs feels like a small victory."</div>

        <div class="stat-row">
          <div class="stat-label">HTML/CSS</div>
          <div class="stat-bar-wrap">
            <div class="stat-bar-fill" style="width:75%; background: linear-gradient(90deg, #e34f26, #ff7043);"></div>
          </div>
          <div class="stat-val">75</div>
        </div>

        <div class="stat-row">
          <div class="stat-label">JAVASCRIPT</div>
          <div class="stat-bar-wrap">
            <div class="stat-bar-fill" style="width:55%; background: linear-gradient(90deg, #f7df1e, #ffcc02); animation-delay:0.1s;"></div>
          </div>
          <div class="stat-val">55</div>
        </div>

        <div class="stat-row">
          <div class="stat-label">PYTHON</div>
          <div class="stat-bar-wrap">
            <div class="stat-bar-fill" style="width:50%; background: linear-gradient(90deg, #3670a0, #4a90d9); animation-delay:0.2s;"></div>
          </div>
          <div class="stat-val">50</div>
        </div>

        <div class="stat-row">
          <div class="stat-label">LARAVEL</div>
          <div class="stat-bar-wrap">
            <div class="stat-bar-fill" style="width:40%; background: linear-gradient(90deg, #ff2d20, #ff6b6b); animation-delay:0.3s;"></div>
          </div>
          <div class="stat-val">40</div>
        </div>

        <div class="stat-row">
          <div class="stat-label">NODE.JS</div>
          <div class="stat-bar-wrap">
            <div class="stat-bar-fill" style="width:35%; background: linear-gradient(90deg, #6da55f, #8bc34a); animation-delay:0.4s;"></div>
          </div>
          <div class="stat-val">35</div>
        </div>
      </div>
    </div>
  </div>

  <!-- QUEST LOG -->
  <div class="pixel-box">
    <div class="pixel-box-title">
      <span class="icon">📜</span> QUEST LOG — CURRENT JOURNEY
    </div>

    <div class="quest-item">
      <div class="quest-status done">✔</div>
      <div>
        <div class="quest-text">QUEST: Master the Basics of HTML & CSS</div>
        <div class="quest-reward">+50 XP · REWARD: [ LAYOUT SKILLS UNLOCKED ]</div>
      </div>
    </div>
    <div class="quest-item">
      <div class="quest-status done">✔</div>
      <div>
        <div class="quest-text">QUEST: Build Your First Web Project</div>
        <div class="quest-reward">+80 XP · REWARD: [ BUILDER TITLE UNLOCKED ]</div>
      </div>
    </div>
    <div class="quest-item">
      <div class="quest-status active">►</div>
      <div>
        <div class="quest-text">QUEST: Tame the JavaScript Dragon 🐉</div>
        <div class="quest-reward">+120 XP · REWARD: [ JS WARRIOR BADGE ]  ← IN PROGRESS</div>
      </div>
    </div>
    <div class="quest-item">
      <div class="quest-status active">►</div>
      <div>
        <div class="quest-text">QUEST: Defeat the Laravel Dungeon Boss</div>
        <div class="quest-reward">+150 XP · REWARD: [ BACKEND TITLE ]  ← IN PROGRESS</div>
      </div>
    </div>
    <div class="quest-item">
      <div class="quest-status locked">🔒</div>
      <div>
        <div class="quest-text" style="color:#30363d;">QUEST: ??? Full Stack Mastery ???</div>
        <div class="quest-reward" style="color:#21262d;">[ LOCKED — KEEP LEVELING UP ]</div>
      </div>
    </div>
  </div>

  <!-- INVENTORY / TECH STACK -->
  <div class="pixel-box">
    <div class="pixel-box-title">
      <span class="icon">🎒</span> INVENTORY — TECH STACK
      <span style="margin-left:auto; font-size:5px; color:#8b949e;">9/20 SLOTS</span>
    </div>
    <div class="inventory-grid">
      <div class="inv-item">
        <div class="inv-rarity rarity-uncommon"></div>
        <span class="inv-icon">🔥</span>
        <div class="inv-name">HTML5</div>
      </div>
      <div class="inv-item">
        <div class="inv-rarity rarity-uncommon"></div>
        <span class="inv-icon">💎</span>
        <div class="inv-name">CSS3</div>
      </div>
      <div class="inv-item">
        <div class="inv-rarity rarity-rare"></div>
        <span class="inv-icon">⚡</span>
        <div class="inv-name">JAVASCRIPT</div>
      </div>
      <div class="inv-item">
        <div class="inv-rarity rarity-rare"></div>
        <span class="inv-icon">🐍</span>
        <div class="inv-name">PYTHON</div>
      </div>
      <div class="inv-item">
        <div class="inv-rarity rarity-uncommon"></div>
        <span class="inv-icon">🌊</span>
        <div class="inv-name">TAILWIND</div>
      </div>
      <div class="inv-item">
        <div class="inv-rarity rarity-uncommon"></div>
        <span class="inv-icon">🅱</span>
        <div class="inv-name">BOOTSTRAP</div>
      </div>
      <div class="inv-item">
        <div class="inv-rarity rarity-epic"></div>
        <span class="inv-icon">🔴</span>
        <div class="inv-name">LARAVEL</div>
      </div>
      <div class="inv-item">
        <div class="inv-rarity rarity-rare"></div>
        <span class="inv-icon">🟢</span>
        <div class="inv-name">NODE.JS</div>
      </div>
      <div class="inv-item">
        <div class="inv-rarity rarity-common"></div>
        <span class="inv-icon">✏️</span>
        <div class="inv-name">SKETCH</div>
      </div>
    </div>
    <div style="padding: 6px 14px 10px; display:flex; gap:12px;">
      <span style="font-size:5px; color:#8b949e;">◼ COMMON</span>
      <span style="font-size:5px; color:var(--pixel-green);">◼ UNCOMMON</span>
      <span style="font-size:5px; color:var(--pixel-blue);">◼ RARE</span>
      <span style="font-size:5px; color:var(--pixel-purple);">◼ EPIC</span>
    </div>
  </div>

  <!-- TERMINAL / ABOUT -->
  <div class="pixel-box">
    <div class="pixel-box-title">
      <span class="icon">💻</span> TERMINAL — ./about.sh
    </div>
    <div class="console-line"><span class="prompt">$&gt;</span> <span class="cmd">cat /profile/about.txt</span></div>
    <div class="console-line"><span class="out">→ Explorer on a journey into web development</span></div>
    <div class="console-line"><span class="out">→ Not an expert — still learning, still trying</span></div>
    <div class="console-line"><span class="out">→ Errors = XP. Failures = Tutorials in disguise.</span></div>
    <div class="console-line"><span class="out">→ Building my foundation, one step at a time</span></div>
    <div class="console-line"><span class="out">→ The road is long. The grind is real. Let's go.</span></div>
    <div class="console-line"><span class="prompt">$&gt;</span> <span class="cmd">_</span><span class="cursor-blink"></span></div>
  </div>

  <!-- GITHUB STATS -->
  <div class="pixel-box">
    <div class="pixel-box-title">
      <span class="icon">📊</span> BATTLE STATS
    </div>
    <div class="stats-grid">
      <div class="stat-cell">
        <span class="num">116</span>
        <span class="lbl">CONTRIBUTIONS</span>
      </div>
      <div class="stat-cell">
        <span class="num">6</span>
        <span class="lbl">REPOS CREATED</span>
      </div>
      <div class="stat-cell">
        <span class="num">124</span>
        <span class="lbl">TOTAL COMMITS</span>
      </div>
      <div class="stat-cell">
        <span class="num">7</span>
        <span class="lbl">LONGEST STREAK</span>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░<br><br>
    [ GAME IN PROGRESS — SAVE FILE: 3d0hidayat ]<br>
    PLAYTIME: JUST STARTED ∙ DIFFICULTY: LEARNING MODE<br><br>
    ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
  </div>

</div>

<script>
// Generate stars
const starsEl = document.getElementById('stars');
for (let i = 0; i < 80; i++) {
  const s = document.createElement('div');
  s.className = 'star';
  s.style.cssText = `
    left: ${Math.random()*100}%;
    top: ${Math.random()*100}%;
    animation-delay: ${Math.random()*3}s;
    animation-duration: ${2+Math.random()*3}s;
    opacity: ${Math.random()*0.5};
    width: ${Math.random()<0.2 ? 3 : 2}px;
    height: ${Math.random()<0.2 ? 3 : 2}px;
  `;
  starsEl.appendChild(s);
}

// Pixel particles
const particlesEl = document.getElementById('particles');
const colors = ['#00ff88','#00cfff','#ffe600','#b86fff','#ff4444'];
for (let i = 0; i < 15; i++) {
  const p = document.createElement('div');
  p.className = 'pixel-particle';
  p.style.cssText = `
    left: ${Math.random()*100}%;
    background: ${colors[Math.floor(Math.random()*colors.length)]};
    animation-delay: ${Math.random()*8}s;
    animation-duration: ${6+Math.random()*4}s;
    width: ${2+Math.floor(Math.random()*3)*2}px;
    height: ${2+Math.floor(Math.random()*3)*2}px;
  `;
  particlesEl.appendChild(p);
}

// Draw pixel art character on canvas
const canvas = document.getElementById('charCanvas');
const ctx = canvas.getContext('2d');
ctx.imageSmoothingEnabled = false;

const P = '#b86fff'; // purple robe
const S = '#ffe600'; // skin
const W = '#00cfff'; // wand/magic
const H = '#333';    // dark
const G = '#00ff88'; // green accent
const _ = null;

const sprite = [
  [_,_,_,S,S,S,S,_,_,_,_,_,_,_,_,_],
  [_,_,S,S,S,S,S,S,_,_,_,_,_,_,_,_],
  [_,_,S,H,S,S,H,S,_,_,_,_,_,_,_,_],
  [_,_,S,S,S,S,S,S,_,_,_,_,_,_,W,_],
  [_,P,P,P,P,P,P,P,P,_,_,_,_,_,W,_],
  [P,P,P,P,P,P,P,P,P,P,_,_,_,W,W,_],
  [P,P,G,P,P,P,P,P,G,P,_,_,W,W,_,_],
  [_,P,P,P,P,P,P,P,P,_,_,W,W,_,_,_],
  [_,P,P,P,P,P,P,P,P,_,_,W,_,_,_,_],
  [_,_,P,P,_,_,P,P,_,_,_,_,_,_,_,_],
  [_,_,P,P,_,_,P,P,_,_,_,_,_,_,_,_],
  [_,_,H,H,_,_,H,H,_,_,_,_,_,_,_,_],
];

const scale = 2;
sprite.forEach((row, y) => {
  row.forEach((color, x) => {
    if (color) {
      ctx.fillStyle = color;
      ctx.fillRect(x*scale, y*scale, scale, scale);
    }
  });
});

// Add glow around character
let frame = 0;
function animateChar() {
  ctx.clearRect(0, 0, 64, 64);
  
  // Glow effect
  const glow = Math.sin(frame * 0.05) * 0.5 + 0.5;
  ctx.shadowColor = '#b86fff';
  ctx.shadowBlur = 4 + glow * 8;
  
  sprite.forEach((row, y) => {
    row.forEach((color, x) => {
      if (color) {
        ctx.fillStyle = color;
        ctx.fillRect(x*scale, y*scale, scale, scale);
      }
    });
  });

  // Wand sparkle
  if (frame % 30 < 15) {
    ctx.fillStyle = '#fff';
    ctx.shadowColor = '#00cfff';
    ctx.shadowBlur = 8;
    ctx.fillRect(26, 0, 2, 2);
  }

  frame++;
  requestAnimationFrame(animateChar);
}
animateChar();
</script>
</body>
</html>
