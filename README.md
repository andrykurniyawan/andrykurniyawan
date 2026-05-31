<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Andri Kurniyawan — Full Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700;800&family=Space+Grotesk:wght@300;400;500;700&display=swap" rel="stylesheet"/>
<style>
:root{
  --bg:#06060f;
  --bg2:#0d0d1f;
  --bg3:#12122a;
  --purple:#7c3aed;
  --purple2:#a78bfa;
  --blue:#3b82f6;
  --cyan:#06b6d4;
  --green:#10b981;
  --pink:#ec4899;
  --text:#e2e8f0;
  --muted:#64748b;
  --border:#1e1e3f;
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--text);font-family:'Space Grotesk',sans-serif;overflow-x:hidden}

/* CANVAS BG */
#bgCanvas{position:fixed;inset:0;z-index:0;pointer-events:none;opacity:.5}

/* NAVBAR */
nav{position:fixed;top:0;left:0;right:0;z-index:100;padding:16px 40px;display:flex;justify-content:space-between;align-items:center;background:rgba(6,6,15,.85);backdrop-filter:blur(12px);border-bottom:1px solid var(--border)}
.nav-logo{font-family:'JetBrains Mono',monospace;font-weight:800;font-size:18px;color:var(--purple2)}
.nav-links{display:flex;gap:24px}
.nav-links a{color:var(--muted);text-decoration:none;font-size:14px;transition:.2s;font-family:'JetBrains Mono',monospace}
.nav-links a:hover{color:var(--purple2)}

/* SECTIONS */
section{position:relative;z-index:1;padding:100px 40px}
.container{max-width:900px;margin:0 auto}

/* HERO */
#hero{min-height:100vh;display:flex;align-items:center;padding-top:80px;text-align:center}
#hero .container{width:100%}
.hero-tag{display:inline-block;font-family:'JetBrains Mono',monospace;font-size:13px;color:var(--cyan);background:rgba(6,182,212,.1);border:1px solid rgba(6,182,212,.3);padding:6px 16px;border-radius:999px;margin-bottom:24px}
.hero-name{font-size:clamp(42px,8vw,80px);font-weight:700;line-height:1.1;margin-bottom:16px}
.hero-name span{background:linear-gradient(135deg,var(--purple2),var(--cyan));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.hero-role{font-size:18px;color:var(--muted);margin-bottom:40px;font-family:'JetBrains Mono',monospace}
#typed{color:var(--purple2)}
#cursor{display:inline-block;width:3px;height:1.1em;background:var(--purple2);vertical-align:text-bottom;animation:blink .7s step-end infinite}
@keyframes blink{50%{opacity:0}}

.hero-btns{display:flex;gap:14px;justify-content:center;flex-wrap:wrap;margin-bottom:48px}
.btn{padding:12px 28px;border-radius:10px;font-weight:600;font-size:14px;cursor:pointer;transition:.2s;text-decoration:none;display:inline-flex;align-items:center;gap:8px;font-family:'Space Grotesk',sans-serif}
.btn-primary{background:var(--purple);color:#fff;border:none}
.btn-primary:hover{background:#6d28d9;transform:translateY(-2px)}
.btn-outline{background:transparent;color:var(--purple2);border:1px solid var(--purple);transition:.2s}
.btn-outline:hover{background:rgba(124,58,237,.15);transform:translateY(-2px)}

.scroll-hint{color:var(--muted);font-size:12px;font-family:'JetBrains Mono',monospace;animation:bounce 2s infinite}
@keyframes bounce{0%,100%{transform:translateY(0)}50%{transform:translateY(8px)}}

/* REVEAL ANIMATION */
.reveal{opacity:0;transform:translateY(40px);transition:opacity .7s ease,transform .7s ease}
.reveal.visible{opacity:1;transform:translateY(0)}
.reveal-left{opacity:0;transform:translateX(-40px);transition:opacity .7s ease,transform .7s ease}
.reveal-left.visible{opacity:1;transform:translateX(0)}
.reveal-right{opacity:0;transform:translateX(40px);transition:opacity .7s ease,transform .7s ease}
.reveal-right.visible{opacity:1;transform:translateX(0)}

/* SECTION TITLE */
.sec-title{font-size:13px;font-family:'JetBrains Mono',monospace;color:var(--cyan);margin-bottom:8px;letter-spacing:2px}
.sec-heading{font-size:36px;font-weight:700;margin-bottom:48px;position:relative;display:inline-block}
.sec-heading::after{content:'';position:absolute;bottom:-8px;left:0;width:60px;height:3px;background:linear-gradient(90deg,var(--purple),var(--cyan));border-radius:2px}

/* ABOUT */
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:40px;align-items:start}
.code-block{background:var(--bg2);border:1px solid var(--border);border-radius:14px;padding:24px;font-family:'JetBrains Mono',monospace;font-size:13px;line-height:1.9}
.code-block .kw{color:#f97316}
.code-block .str{color:#86efac}
.code-block .key{color:var(--purple2)}
.code-block .val{color:var(--cyan)}
.code-block .cm{color:var(--muted)}
.stat-pills{display:flex;flex-direction:column;gap:12px}
.stat-pill{background:var(--bg2);border:1px solid var(--border);border-radius:12px;padding:16px 20px;display:flex;align-items:center;gap:14px;transition:.2s}
.stat-pill:hover{border-color:var(--purple);transform:translateX(6px)}
.stat-pill .num{font-size:28px;font-weight:700;color:var(--purple2);font-family:'JetBrains Mono',monospace;min-width:60px}
.stat-pill .lbl{font-size:13px;color:var(--muted)}

/* SKILLS */
.skills-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:16px}
.skill-item{background:var(--bg2);border:1px solid var(--border);border-radius:12px;padding:16px 20px;transition:.2s}
.skill-item:hover{border-color:var(--purple);transform:translateY(-3px)}
.skill-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px}
.skill-name{font-size:14px;font-weight:600}
.skill-pct{font-size:12px;color:var(--purple2);font-family:'JetBrains Mono',monospace}
.skill-bar{height:6px;background:var(--bg3);border-radius:999px;overflow:hidden}
.skill-fill{height:100%;border-radius:999px;width:0;transition:width 1.2s cubic-bezier(.4,0,.2,1)}
.tag-grid{display:flex;flex-wrap:wrap;gap:8px;margin-top:32px}
.tag{padding:6px 14px;border-radius:999px;font-size:12px;font-family:'JetBrains Mono',monospace;border:1px solid var(--border);background:var(--bg2);transition:.2s}
.tag:hover{border-color:var(--purple2);color:var(--purple2)}

/* GAME */
#game{background:var(--bg2)}
.game-wrapper{background:var(--bg);border:1px solid var(--border);border-radius:18px;padding:24px;max-width:560px;margin:0 auto}
.game-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:16px}
.game-title{font-family:'JetBrains Mono',monospace;font-size:16px;font-weight:700;color:var(--purple2)}
.game-scores{display:flex;gap:20px}
.game-score-item{text-align:center}
.game-score-item .val{font-size:22px;font-weight:700;color:var(--cyan);font-family:'JetBrains Mono',monospace}
.game-score-item .lbl{font-size:10px;color:var(--muted);font-family:'JetBrains Mono',monospace}
#snakeCanvas{display:block;border-radius:10px;border:1px solid var(--border);background:#06060f}
.game-controls{display:flex;gap:10px;margin-top:16px;justify-content:center;flex-wrap:wrap}
.gc-btn{padding:10px 20px;border-radius:8px;border:1px solid var(--border);background:var(--bg2);color:var(--text);cursor:pointer;font-family:'JetBrains Mono',monospace;font-size:13px;transition:.2s}
.gc-btn:hover{border-color:var(--purple);color:var(--purple2)}
.gc-btn.active{background:var(--purple);border-color:var(--purple);color:#fff}
.dpad{display:grid;grid-template-columns:repeat(3,44px);grid-template-rows:repeat(3,44px);gap:4px;margin-top:12px;justify-content:center}
.dpad-btn{width:44px;height:44px;border-radius:8px;border:1px solid var(--border);background:var(--bg2);color:var(--text);cursor:pointer;font-size:18px;display:flex;align-items:center;justify-content:center;transition:.2s;user-select:none}
.dpad-btn:hover,.dpad-btn:active{background:var(--purple);border-color:var(--purple)}
.dpad-center{background:var(--bg3);cursor:default}
.dpad-center:hover{background:var(--bg3)}
.game-tip{text-align:center;font-size:11px;color:var(--muted);margin-top:10px;font-family:'JetBrains Mono',monospace}

/* PROJECTS */
.projects-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:20px}
.project-card{background:var(--bg2);border:1px solid var(--border);border-radius:14px;padding:22px;transition:.3s;position:relative;overflow:hidden}
.project-card::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(124,58,237,.06),rgba(6,182,212,.06));opacity:0;transition:.3s}
.project-card:hover{border-color:var(--purple);transform:translateY(-5px)}
.project-card:hover::before{opacity:1}
.project-icon{font-size:28px;margin-bottom:12px}
.project-title{font-size:16px;font-weight:700;margin-bottom:8px}
.project-desc{font-size:13px;color:var(--muted);line-height:1.6;margin-bottom:14px}
.project-tags{display:flex;flex-wrap:wrap;gap:6px}
.project-tag{padding:3px 10px;background:rgba(124,58,237,.15);color:var(--purple2);border-radius:999px;font-size:11px;font-family:'JetBrains Mono',monospace}

/* CONTACT */
.connect-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:14px}
.connect-card{display:flex;align-items:center;gap:14px;background:var(--bg2);border:1px solid var(--border);border-radius:12px;padding:16px 20px;text-decoration:none;color:var(--text);transition:.2s}
.connect-card:hover{border-color:var(--purple2);transform:translateY(-3px)}
.connect-icon{width:42px;height:42px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
.connect-info .name{font-weight:600;font-size:14px}
.connect-info .handle{font-size:12px;color:var(--muted);font-family:'JetBrains Mono',monospace}

/* FOOTER */
footer{text-align:center;padding:40px;border-top:1px solid var(--border);color:var(--muted);font-size:13px;font-family:'JetBrains Mono',monospace;position:relative;z-index:1}
footer span{color:var(--purple2)}

/* SCROLLBAR */
::-webkit-scrollbar{width:5px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--purple);border-radius:99px}

@media(max-width:640px){
  nav{padding:12px 20px}
  section{padding:80px 20px}
  .about-grid{grid-template-columns:1fr}
  .nav-links{display:none}
}
</style>
</head>
<body>

<canvas id="bgCanvas"></canvas>

<nav>
  <div class="nav-logo">AK.dev</div>
  <div class="nav-links">
    <a href="#about">about</a>
    <a href="#skills">skills</a>
    <a href="#game">game</a>
    <a href="#projects">projects</a>
    <a href="#contact">contact</a>
  </div>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="container">
    <div class="hero-tag">👋 Available for collaboration</div>
    <h1 class="hero-name">Andri<br/><span>Kurniyawan</span></h1>
    <p class="hero-role">&gt; <span id="typed"></span><span id="cursor"></span></p>
    <div class="hero-btns">
      <a href="#projects" class="btn btn-primary">🚀 Lihat Projects</a>
      <a href="#game" class="btn btn-outline">🐍 Main Snake Game</a>
      <a href="https://github.com/andrykurniyawan" target="_blank" class="btn btn-outline">⭐ GitHub</a>
    </div>
    <div class="scroll-hint">↓ scroll to explore ↓</div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="container">
    <p class="sec-title">// WHO I AM</p>
    <h2 class="sec-heading">About Me</h2>
    <div class="about-grid">
      <div class="code-block reveal-left">
        <div><span class="kw">class</span> <span class="val">AndriKurniyawan</span> {</div>
        <div>&nbsp;&nbsp;<span class="key">name</span> = <span class="str">"Andri Kurniyawan"</span></div>
        <div>&nbsp;&nbsp;<span class="key">base</span> = <span class="str">"Indonesia 🇮🇩"</span></div>
        <div>&nbsp;&nbsp;<span class="key">role</span> = <span class="str">"Full Stack Dev"</span></div>
        <br/>
        <div>&nbsp;&nbsp;<span class="cm">// Frontend</span></div>
        <div>&nbsp;&nbsp;<span class="key">html</span> = <span class="str">98</span><span class="cm">% mastery</span></div>
        <div>&nbsp;&nbsp;<span class="key">bootstrap</span> = <span class="str">92</span><span class="cm">% mastery</span></div>
        <div>&nbsp;&nbsp;<span class="key">javascript</span> = <span class="str">90</span><span class="cm">% mastery</span></div>
        <br/>
        <div>&nbsp;&nbsp;<span class="cm">// Backend</span></div>
        <div>&nbsp;&nbsp;<span class="key">php</span> = <span class="str">95</span><span class="cm">% mastery</span></div>
        <div>&nbsp;&nbsp;<span class="key">laravel</span> = <span class="str">95</span><span class="cm">% mastery</span></div>
        <div>&nbsp;&nbsp;<span class="key">cpp</span> = <span class="str">80</span><span class="cm">% mastery</span></div>
        <br/>
        <div>&nbsp;&nbsp;<span class="key">motto</span>() {</div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="kw">return</span> <span class="str">"Code is poetry 🎨"</span></div>
        <div>&nbsp;&nbsp;}</div>
        <div>}</div>
      </div>
      <div class="stat-pills reveal-right">
        <div class="stat-pill"><span class="num" data-target="420">0</span><span class="lbl">Total Commits</span></div>
        <div class="stat-pill"><span class="num" data-target="25">0</span><span class="lbl">Projects Completed</span></div>
        <div class="stat-pill"><span class="num" data-target="6">0</span><span class="lbl">Languages Known</span></div>
        <div class="stat-pill"><span class="num" data-target="3">0</span><span class="lbl">Years Experience</span></div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills" style="background:var(--bg2)">
  <div class="container">
    <p class="sec-title">// WHAT I KNOW</p>
    <h2 class="sec-heading">Tech Stack</h2>
    <div class="skills-grid">
      <div class="skill-item reveal" style="transition-delay:.0s"><div class="skill-top"><span class="skill-name">PHP / Laravel</span><span class="skill-pct">95%</span></div><div class="skill-bar"><div class="skill-fill" data-pct="95" style="background:linear-gradient(90deg,#7c3aed,#a78bfa)"></div></div></div>
      <div class="skill-item reveal" style="transition-delay:.1s"><div class="skill-top"><span class="skill-name">HTML / CSS</span><span class="skill-pct">98%</span></div><div class="skill-bar"><div class="skill-fill" data-pct="98" style="background:linear-gradient(90deg,#ea580c,#fb923c)"></div></div></div>
      <div class="skill-item reveal" style="transition-delay:.15s"><div class="skill-top"><span class="skill-name">JavaScript</span><span class="skill-pct">90%</span></div><div class="skill-bar"><div class="skill-fill" data-pct="90" style="background:linear-gradient(90deg,#ca8a04,#fbbf24)"></div></div></div>
      <div class="skill-item reveal" style="transition-delay:.2s"><div class="skill-top"><span class="skill-name">Bootstrap</span><span class="skill-pct">92%</span></div><div class="skill-bar"><div class="skill-fill" data-pct="92" style="background:linear-gradient(90deg,#6d28d9,#8b5cf6)"></div></div></div>
      <div class="skill-item reveal" style="transition-delay:.25s"><div class="skill-top"><span class="skill-name">C++</span><span class="skill-pct">80%</span></div><div class="skill-bar"><div class="skill-fill" data-pct="80" style="background:linear-gradient(90deg,#0e7490,#06b6d4)"></div></div></div>
      <div class="skill-item reveal" style="transition-delay:.3s"><div class="skill-top"><span class="skill-name">MySQL / PostgreSQL</span><span class="skill-pct">85%</span></div><div class="skill-bar"><div class="skill-fill" data-pct="85" style="background:linear-gradient(90deg,#065f46,#10b981)"></div></div></div>
      <div class="skill-item reveal" style="transition-delay:.35s"><div class="skill-top"><span class="skill-name">Python</span><span class="skill-pct">75%</span></div><div class="skill-bar"><div class="skill-fill" data-pct="75" style="background:linear-gradient(90deg,#1d4ed8,#3b82f6)"></div></div></div>
      <div class="skill-item reveal" style="transition-delay:.4s"><div class="skill-top"><span class="skill-name">Git & GitHub</span><span class="skill-pct">90%</span></div><div class="skill-bar"><div class="skill-fill" data-pct="90" style="background:linear-gradient(90deg,#9d174d,#ec4899)"></div></div></div>
    </div>
    <div class="tag-grid reveal" style="transition-delay:.5s">
      <span class="tag">PHP</span><span class="tag">Laravel</span><span class="tag">JavaScript</span>
      <span class="tag">Bootstrap</span><span class="tag">C++</span><span class="tag">Python</span>
      <span class="tag">MySQL</span><span class="tag">Node.js</span><span class="tag">REST API</span>
      <span class="tag">Git</span><span class="tag">VS Code</span><span class="tag">Postman</span>
      <span class="tag">jQuery</span><span class="tag">Tailwind</span><span class="tag">PostgreSQL</span>
    </div>
  </div>
</section>

<!-- SNAKE GAME -->
<section id="game">
  <div class="container">
    <p class="sec-title">// JUST FOR FUN</p>
    <h2 class="sec-heading">Snake Game 🐍</h2>
    <div class="game-wrapper reveal">
      <div class="game-header">
        <div class="game-title">🐍 Code Snake</div>
        <div class="game-scores">
          <div class="game-score-item"><div class="val" id="scoreVal">0</div><div class="lbl">SCORE</div></div>
          <div class="game-score-item"><div class="val" id="highVal">0</div><div class="lbl">BEST</div></div>
          <div class="game-score-item"><div class="val" id="levelVal">1</div><div class="lbl">LEVEL</div></div>
        </div>
      </div>
      <canvas id="snakeCanvas" width="504" height="336"></canvas>
      <div class="game-controls">
        <button class="gc-btn active" id="startBtn" onclick="toggleGame()">▶ Start</button>
        <button class="gc-btn" onclick="resetGame()">↺ Reset</button>
        <span style="font-size:12px;color:var(--muted);align-self:center;font-family:'JetBrains Mono',monospace">Speed: <span id="speedLbl">Normal</span></span>
      </div>
      <div class="dpad">
        <div></div>
        <button class="dpad-btn" onclick="setDir(0,-1)">▲</button>
        <div></div>
        <button class="dpad-btn" onclick="setDir(-1,0)">◀</button>
        <div class="dpad-btn dpad-center">●</div>
        <button class="dpad-btn" onclick="setDir(1,0)">▶</button>
        <div></div>
        <button class="dpad-btn" onclick="setDir(0,1)">▼</button>
        <div></div>
      </div>
      <p class="game-tip">⌨️ Arrow keys / WASD · Space = pause · Makan kata coding untuk poin!</p>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects" style="background:var(--bg2)">
  <div class="container">
    <p class="sec-title">// WHAT I BUILT</p>
    <h2 class="sec-heading">Projects</h2>
    <div class="projects-grid">
      <div class="project-card reveal" style="transition-delay:.0s"><div class="project-icon">🌐</div><div class="project-title">Portfolio Website</div><div class="project-desc">Personal portfolio dengan admin panel, dark mode, dan animasi scroll yang smooth.</div><div class="project-tags"><span class="project-tag">Laravel</span><span class="project-tag">Bootstrap</span><span class="project-tag">JS</span></div></div>
      <div class="project-card reveal" style="transition-delay:.1s"><div class="project-icon">🛒</div><div class="project-title">E-Commerce Platform</div><div class="project-desc">Platform belanja online full-stack dengan payment gateway, cart, dan dashboard admin.</div><div class="project-tags"><span class="project-tag">Laravel</span><span class="project-tag">MySQL</span><span class="project-tag">REST API</span></div></div>
      <div class="project-card reveal" style="transition-delay:.2s"><div class="project-icon">📊</div><div class="project-title">Analytics Dashboard</div><div class="project-desc">Dashboard analitik real-time dengan chart interaktif dan export data ke Excel/PDF.</div><div class="project-tags"><span class="project-tag">JavaScript</span><span class="project-tag">Chart.js</span><span class="project-tag">Bootstrap</span></div></div>
      <div class="project-card reveal" style="transition-delay:.3s"><div class="project-icon">🔐</div><div class="project-title">Auth & RBAC System</div><div class="project-desc">Sistem autentikasi berbasis JWT dengan role-based access control yang fleksibel.</div><div class="project-tags"><span class="project-tag">Laravel</span><span class="project-tag">Sanctum</span><span class="project-tag">JWT</span></div></div>
      <div class="project-card reveal" style="transition-delay:.4s"><div class="project-icon">📝</div><div class="project-title">Project Manager App</div><div class="project-desc">Aplikasi manajemen proyek & tugas dengan fitur kolaborasi tim dan notifikasi.</div><div class="project-tags"><span class="project-tag">Laravel</span><span class="project-tag">Bootstrap</span><span class="project-tag">MySQL</span></div></div>
      <div class="project-card reveal" style="transition-delay:.5s"><div class="project-icon">⚙️</div><div class="project-title">CLI Tools (C++)</div><div class="project-desc">Kumpulan tools command-line berbasis C++ untuk otomasi tugas-tugas developer.</div><div class="project-tags"><span class="project-tag">C++</span><span class="project-tag">Python</span><span class="project-tag">CLI</span></div></div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="container">
    <p class="sec-title">// GET IN TOUCH</p>
    <h2 class="sec-heading">Connect</h2>
    <div class="connect-grid">
      <a href="https://github.com/andrykurniyawan" target="_blank" class="connect-card reveal" style="transition-delay:.0s"><div class="connect-icon" style="background:rgba(255,255,255,.06)">🐙</div><div class="connect-info"><div class="name">GitHub</div><div class="handle">@andrykurniyawan</div></div></a>
      <a href="https://linkedin.com/in/andrykurniyawan" target="_blank" class="connect-card reveal" style="transition-delay:.1s"><div class="connect-icon" style="background:rgba(10,102,194,.15)">💼</div><div class="connect-info"><div class="name">LinkedIn</div><div class="handle">Andri Kurniyawan</div></div></a>
      <a href="https://instagram.com/andrykurniyawan" target="_blank" class="connect-card reveal" style="transition-delay:.2s"><div class="connect-icon" style="background:rgba(228,64,95,.15)">📸</div><div class="connect-info"><div class="name">Instagram</div><div class="handle">@andrykurniyawan</div></div></a>
      <a href="mailto:andrykurniyawan@gmail.com" class="connect-card reveal" style="transition-delay:.3s"><div class="connect-icon" style="background:rgba(234,67,53,.15)">✉️</div><div class="connect-info"><div class="name">Email</div><div class="handle">andrykurniyawan@gmail.com</div></div></a>
    </div>
  </div>
</section>

<footer>
  <p>Dibuat dengan <span>❤️</span> oleh <span>Andri Kurniyawan</span> · Full Stack Developer · Indonesia 🇮🇩</p>
  <p style="margin-top:8px;font-size:11px">© 2025 andrykurniyawan · Open to collaboration</p>
</footer>

<script>
/* ── BACKGROUND PARTICLE CANVAS ── */
const bgC=document.getElementById('bgCanvas');
const bgX=bgC.getContext('2d');
let particles=[];
function resizeBg(){bgC.width=window.innerWidth;bgC.height=window.innerHeight}
resizeBg();
window.addEventListener('resize',resizeBg);
for(let i=0;i<80;i++)particles.push({x:Math.random()*window.innerWidth,y:Math.random()*window.innerHeight,r:Math.random()*1.5+.3,dx:(Math.random()-.5)*.3,dy:(Math.random()-.5)*.3,o:Math.random()*.5+.1});
function drawBg(){
  bgX.clearRect(0,0,bgC.width,bgC.height);
  particles.forEach(p=>{
    bgX.beginPath();bgX.arc(p.x,p.y,p.r,0,Math.PI*2);
    bgX.fillStyle=`rgba(167,139,250,${p.o})`;bgX.fill();
    p.x+=p.dx;p.y+=p.dy;
    if(p.x<0||p.x>bgC.width)p.dx*=-1;
    if(p.y<0||p.y>bgC.height)p.dy*=-1;
  });
  requestAnimationFrame(drawBg);
}
drawBg();

/* ── TYPING ANIMATION ── */
const phrases=['Full Stack Developer','Laravel Expert','PHP & JS Engineer','C++ Programmer','Bootstrap Master','Problem Solver'];
let pi=0,ci=0,del=false;
const tel=document.getElementById('typed');
function typeLoop(){
  const cur=phrases[pi];
  if(!del){tel.textContent=cur.slice(0,++ci);if(ci===cur.length){del=true;setTimeout(typeLoop,1400);return;}}
  else{tel.textContent=cur.slice(0,--ci);if(ci===0){del=false;pi=(pi+1)%phrases.length;}}
  setTimeout(typeLoop,del?45:85);
}
typeLoop();

/* ── SCROLL REVEAL ── */
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.classList.add('visible');
      /* skill bars */
      e.target.querySelectorAll('.skill-fill').forEach(b=>{b.style.width=b.dataset.pct+'%'});
      /* counters */
      e.target.querySelectorAll('[data-target]').forEach(el=>{
        let v=0,t=+el.dataset.target;
        const s=setInterval(()=>{v=Math.min(v+Math.ceil(t/50),t);el.textContent=v;if(v>=t)clearInterval(s);},30);
      });
    }
  });
},{threshold:.15});
document.querySelectorAll('.reveal,.reveal-left,.reveal-right').forEach(el=>obs.observe(el));

/* ── SNAKE GAME ── */
const sc=document.getElementById('snakeCanvas');
const cx=sc.getContext('2d');
const CELL=24,COLS=Math.floor(sc.width/CELL),ROWS=Math.floor(sc.height/CELL);
const WORDS=['PHP','Laravel','JS','CSS','C++','MySQL','Git','HTML','API','Python','Node','Boot'];
const COLORS=['#a78bfa','#06b6d4','#10b981','#fbbf24','#f87171','#ec4899','#34d399','#60a5fa'];

let snake,dir,nextDir,food,score,hiScore=0,level,gameInterval,running=false,paused=false;

function initSnake(){
  snake=[{x:10,y:7},{x:9,y:7},{x:8,y:7}];
  dir={x:1,y:0};nextDir={x:1,y:0};
  score=0;level=1;
  document.getElementById('scoreVal').textContent=0;
  document.getElementById('levelVal').textContent=1;
  spawnFood();
}

function spawnFood(){
  let pos;
  do{pos={x:Math.floor(Math.random()*COLS),y:Math.floor(Math.random()*ROWS)}}
  while(snake.some(s=>s.x===pos.x&&s.y===pos.y));
  const w=WORDS[Math.floor(Math.random()*WORDS.length)];
  const c=COLORS[Math.floor(Math.random()*COLORS.length)];
  food={...pos,word:w,color:c,pts:w.length*10};
}

function gameStep(){
  if(paused)return;
  dir={...nextDir};
  const head={x:snake[0].x+dir.x,y:snake[0].y+dir.y};
  if(head.x<0||head.x>=COLS||head.y<0||head.y>=ROWS||snake.some(s=>s.x===head.x&&s.y===head.y)){
    endGame();return;
  }
  snake.unshift(head);
  if(head.x===food.x&&head.y===food.y){
    score+=food.pts;
    level=Math.floor(score/200)+1;
    document.getElementById('scoreVal').textContent=score;
    document.getElementById('levelVal').textContent=level;
    document.getElementById('speedLbl').textContent=level<=2?'Normal':level<=4?'Fast':'Turbo';
    if(score>hiScore){hiScore=score;document.getElementById('highVal').textContent=hiScore;}
    spawnFood();
    clearInterval(gameInterval);
    gameInterval=setInterval(gameStep,Math.max(80,200-level*25));
  } else {
    snake.pop();
  }
  draw();
}

function draw(){
  cx.fillStyle='#06060f';cx.fillRect(0,0,sc.width,sc.height);
  /* grid */
  cx.strokeStyle='rgba(30,30,63,.6)';cx.lineWidth=.5;
  for(let x=0;x<=COLS;x++){cx.beginPath();cx.moveTo(x*CELL,0);cx.lineTo(x*CELL,sc.height);cx.stroke();}
  for(let y=0;y<=ROWS;y++){cx.beginPath();cx.moveTo(0,y*CELL);cx.lineTo(sc.width,y*CELL);cx.stroke();}

  /* food */
  cx.fillStyle=food.color;
  cx.font=`bold 11px 'JetBrains Mono'`;cx.textAlign='center';cx.textBaseline='middle';
  const fw=cx.measureText(food.word).width+12;
  const fh=18;const fx=food.x*CELL+CELL/2,fy=food.y*CELL+CELL/2;
  cx.beginPath();cx.roundRect(fx-fw/2,fy-fh/2,fw,fh,4);cx.fill();
  cx.fillStyle='#06060f';cx.fillText(food.word,fx,fy);

  /* snake */
  snake.forEach((s,i)=>{
    const alpha=1-i/(snake.length+5);
    cx.fillStyle=i===0?'#a78bfa':`rgba(124,58,237,${alpha})`;
    cx.beginPath();cx.roundRect(s.x*CELL+1,s.y*CELL+1,CELL-2,CELL-2,i===0?5:3);cx.fill();
    if(i===0){cx.fillStyle='#fff';cx.fillRect(s.x*CELL+6,s.y*CELL+6,4,4);cx.fillRect(s.x*CELL+14,s.y*CELL+6,4,4);}
  });

  if(paused){
    cx.fillStyle='rgba(6,6,15,.7)';cx.fillRect(0,0,sc.width,sc.height);
    cx.fillStyle='#a78bfa';cx.font="bold 24px 'JetBrains Mono'";cx.textAlign='center';cx.textBaseline='middle';
    cx.fillText('⏸ PAUSED',sc.width/2,sc.height/2);
  }
}

function drawIdle(){
  cx.fillStyle='#06060f';cx.fillRect(0,0,sc.width,sc.height);
  cx.fillStyle='rgba(30,30,63,.6)';cx.lineWidth=.5;cx.strokeStyle='rgba(30,30,63,.6)';
  for(let x=0;x<=COLS;x++){cx.beginPath();cx.moveTo(x*CELL,0);cx.lineTo(x*CELL,sc.height);cx.stroke();}
  for(let y=0;y<=ROWS;y++){cx.beginPath();cx.moveTo(0,y*CELL);cx.lineTo(sc.width,y*CELL);cx.stroke();}
  cx.fillStyle='#a78bfa';cx.font="bold 22px 'JetBrains Mono'";cx.textAlign='center';cx.textBaseline='middle';
  cx.fillText('🐍 Press Start to Play!',sc.width/2,sc.height/2-16);
  cx.fillStyle='#64748b';cx.font="13px 'JetBrains Mono'";
  cx.fillText('Makan kata coding untuk poin!',sc.width/2,sc.height/2+20);
}

function endGame(){
  clearInterval(gameInterval);running=false;paused=false;
  cx.fillStyle='rgba(6,6,15,.85)';cx.fillRect(0,0,sc.width,sc.height);
  cx.textAlign='center';cx.textBaseline='middle';
  cx.fillStyle='#f87171';cx.font="bold 26px 'JetBrains Mono'";cx.fillText('GAME OVER!',sc.width/2,sc.height/2-36);
  cx.fillStyle='#a78bfa';cx.font="16px 'JetBrains Mono'";cx.fillText(`Score: ${score}`,sc.width/2,sc.height/2+2);
  cx.fillStyle='#06b6d4';cx.font="14px 'JetBrains Mono'";cx.fillText(`Best: ${hiScore}`,sc.width/2,sc.height/2+30);
  cx.fillStyle='#64748b';cx.font="12px 'JetBrains Mono'";cx.fillText('Klik Reset untuk main lagi',sc.width/2,sc.height/2+58);
  document.getElementById('startBtn').textContent='▶ Start';
}

function toggleGame(){
  if(!running){
    initSnake();running=true;paused=false;
    gameInterval=setInterval(gameStep,200);
    document.getElementById('startBtn').textContent='⏸ Pause';
  } else {
    paused=!paused;
    document.getElementById('startBtn').textContent=paused?'▶ Resume':'⏸ Pause';
    if(!paused)draw();
  }
}
function resetGame(){
  clearInterval(gameInterval);running=false;paused=false;
  document.getElementById('startBtn').textContent='▶ Start';
  document.getElementById('scoreVal').textContent=0;
  document.getElementById('levelVal').textContent=1;
  document.getElementById('speedLbl').textContent='Normal';
  drawIdle();
}
function setDir(dx,dy){
  if(dx!==0&&dir.x!==0)return;
  if(dy!==0&&dir.y!==0)return;
  nextDir={x:dx,y:dy};
}

document.addEventListener('keydown',e=>{
  if(['ArrowUp','ArrowDown','ArrowLeft','ArrowRight','w','a','s','d','W','A','S','D',' '].includes(e.key))e.preventDefault();
  if(e.key==='ArrowUp'||e.key==='w'||e.key==='W')setDir(0,-1);
  if(e.key==='ArrowDown'||e.key==='s'||e.key==='S')setDir(0,1);
  if(e.key==='ArrowLeft'||e.key==='a'||e.key==='A')setDir(-1,0);
  if(e.key==='ArrowRight'||e.key==='d'||e.key==='D')setDir(1,0);
  if(e.key===' ')toggleGame();
});

drawIdle();
</script>
</body>
</html>
