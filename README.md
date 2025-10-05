<!--
  yubbiXploit GitHub profile / landing page
  - Ultra hacker neon red theme
  - Removes white background from the provided PNG on-the-fly using an SVG filter
  - Single-file HTML (no external dependencies)

  Usage: save as yubbiXploit_github_profile.html and open in browser.
--><!doctype html>

<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>yubbiXploit</title>
  <style>
    :root{
      --bg:#050406;
      --panel:rgba(255,255,255,0.03);
      --neon:#ff0033;
      --glass:rgba(255,255,255,0.04);
      --accent:rgba(255,0,51,0.12);
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, "Roboto Mono", monospace;
      background: radial-gradient(1200px 600px at 10% 20%, rgba(255,0,51,0.03), transparent),
                  radial-gradient(900px 400px at 90% 80%, rgba(255,0,51,0.02), transparent),
                  var(--bg);
      color:#e6e6e6;
      -webkit-font-smoothing:antialiased;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:40px;
    }.card{
  width:980px;
  max-width:96vw;
  background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
  border-radius:18px;
  padding:28px;
  box-shadow: 0 10px 40px rgba(0,0,0,0.6), 0 0 40px rgba(255,0,51,0.06) inset;
  border: 1px solid rgba(255,0,51,0.06);
  position:relative;
  overflow:hidden;
}

/* subtle grid */
.card::before{
  content:'';
  position:absolute;
  inset:0;
  background-image:linear-gradient(rgba(255,255,255,0.008) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.008) 1px, transparent 1px);
  background-size: 40px 40px, 40px 40px;
  pointer-events:none;
  mix-blend-mode:overlay;
  opacity:0.6;
}

.header{
  display:flex;
  gap:22px;
  align-items:center;
}

/* logo container uses SVG filter to turn white -> transparent */
.logo-wrap{
  width:160px;
  height:160px;
  min-width:160px;
  border-radius:12px;
  display:grid;
  place-items:center;
  background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,0,51,0.02));
  box-shadow: 0 8px 30px rgba(255,0,51,0.06);
  position:relative;
  overflow:visible;
  filter:drop-shadow(0 10px 30px rgba(255,0,51,0.06));
}

/* neon glow behind the logo */
.logo-wrap::after{
  content:'';
  position:absolute;
  inset:auto -20px -20px -20px;
  background:radial-gradient(closest-side, rgba(255,0,51,0.14), transparent);
  transform:rotate(6deg);
  filter:blur(18px);
  z-index:0;
  pointer-events:none;
}

.title{
  z-index:2;
}

h1{font-size:32px;margin:0 0 6px 0;letter-spacing:1px}
p.lead{margin:0;color:rgba(255,255,255,0.65)}

.actions{
  margin-left:auto;
  display:flex;
  gap:12px;
  align-items:center;
}
.btn{
  padding:10px 14px;border-radius:10px;border:1px solid rgba(255,255,255,0.06);background:var(--glass);backdrop-filter:blur(6px);cursor:pointer;font-weight:600
}
.btn.ghost{background:transparent;border-color:rgba(255,255,255,0.04)}
.btn.neon{
  background:linear-gradient(90deg, rgba(255,0,51,0.12), rgba(255,0,51,0.08));
  box-shadow:0 6px 30px rgba(255,0,51,0.08);
  border:1px solid rgba(255,0,51,0.25);
  color:#fff;
}

/* stats row */
.stats{display:flex;gap:12px;margin-top:18px}
.stat{padding:12px 14px;background:rgba(0,0,0,0.18);border-radius:10px;min-width:110px;text-align:center}
.stat strong{display:block;font-size:18px}
.stat small{color:rgba(255,255,255,0.6)}

/* bio + code area */
.main{
  margin-top:20px;
  display:grid;
  grid-template-columns:1fr 360px;
  gap:22px;
}
.bio{
  background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.005));
  padding:18px;border-radius:12px;border:1px solid rgba(255,0,51,0.04);
  min-height:220px;position:relative;overflow:hidden
}

/* fake terminal */
.terminal{
  background:linear-gradient(180deg, rgba(0,0,0,0.5), rgba(0,0,0,0.35));
  padding:16px;border-radius:10px;color:#f3f3f3;font-size:13px;line-height:1.45;height:220px;overflow:auto;font-family:ui-monospace,monospace
}
.line{opacity:0.95}
.muted{color:rgba(255,255,255,0.5)}

/* sidebar */
.sidebar{display:flex;flex-direction:column;gap:14px}
.card-panel{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:12px;border-radius:10px;border:1px solid rgba(255,0,51,0.04)}

/* footer effect */
.scanline{
  position:absolute;inset:0;pointer-events:none;background-image:linear-gradient(180deg, rgba(255,255,255,0.02) 1px, transparent 1px);background-size:100% 40px;mix-blend-mode:overlay;opacity:0.25
}

/* small responsive */
@media (max-width:880px){
  .main{grid-template-columns:1fr}
  .logo-wrap{width:120px;height:120px;min-width:120px}
}

/* subtle animation for neon title */
@keyframes neonPulse{0%{text-shadow:0 0 6px rgba(255,0,51,0.08)}50%{text-shadow:0 0 18px rgba(255,0,51,0.28)}100%{text-shadow:0 0 6px rgba(255,0,51,0.08)}}
h1 span.neon{color:var(--neon);animation:neonPulse 2s ease-in-out infinite}

  </style>
</head>
<body>
  <div class="card">
    <div class="header">
      <div class="logo-wrap" aria-hidden="true">
        <!-- Inline SVG that loads the remote PNG and converts white -> transparent via filter -->
        <svg width="140" height="140" viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid meet" style="z-index:2">
          <defs>
            <filter id="whiteToAlpha">
              <!-- turn luminance into alpha (white -> 1) -->
              <feColorMatrix type="luminanceToAlpha"/>
              <!-- invert alpha so white -> 0 (transparent), dark -> opaque -->
              <feComponentTransfer>
                <feFuncA type="table" tableValues="1 0"/>
              </feComponentTransfer>
            </filter>
            <!-- small blur to avoid harsh edges -->
            <filter id="soften" x="-20%" y="-20%" width="140%" height="140%">
              <feGaussianBlur stdDeviation="0.6"/>
            </filter>
          </defs><!-- glow circles for extra neon effect -->
      <circle cx="256" cy="256" r="220" fill="none" stroke="rgba(255,0,51,0.06)" stroke-width="40" filter="url(#soften)" />

      <!-- the provided PNG (remote). It will be filtered so white becomes transparent -->
      <image href="https://g.top4top.io/p_35655q4ql0.png" x="56" y="56" width="400" height="400" preserveAspectRatio="xMidYMid meet" style="filter:url(#whiteToAlpha) drop-shadow(0 10px 20px rgba(255,0,51,0.12))" />

    </svg>
  </div>

  <div class="title">
    <h1>yubbiXploit <span class="neon">●</span></h1>
    <p class="lead">Hacker aesthetic · neon red · repositories & tools</p>
    <div class="stats">
      <div class="stat"><strong>128</strong><small>Repos</small></div>
      <div class="stat"><strong>4.2k</strong><small>Commits</small></div>
      <div class="stat"><strong>999</strong><small>Followers</small></div>
    </div>
  </div>

  <div class="actions">
    <button class="btn ghost">Follow</button>
    <button class="btn neon">View Repos</button>
  </div>
</div>

<div class="main">
  <div class="bio">
    <div class="terminal" id="terminal">
      <div class="line">$ git clone https://github.com/yubbiXploit/repo-ghost</div>
      <div class="line muted">Cloning into 'repo-ghost'...</div>
      <div class="line">Resolving deltas: 100% (512/512), done.</div>
      <div class="line">$ ./deploy.sh --stealth --neon</div>
      <div class="line muted">[ OK ] deploy completed — neon mode: activated</div>
      <div class="line">$ cat README.md | grep "yubbi"</div>
      <div class="line">## yubbiXploit — Tools, scripts, and leaked</div>
    </div>
  </div>

  <aside class="sidebar">
    <div class="card-panel">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
        <strong>Top Languages</strong>
        <small class="muted">weighted</small>
      </div>
      <div style="display:flex;gap:8px;flex-wrap:wrap">
        <span style="padding:6px 8px;border-radius:8px;background:rgba(255,255,255,0.02);font-weight:600">Python</span>
        <span style="padding:6px 8px;border-radius:8px;background:rgba(255,255,255,0.02);font-weight:600">Bash</span>
        <span style="padding:6px 8px;border-radius:8px;background:rgba(255,255,255,0.02);font-weight:600">HTML</span>
        <span style="padding:6px 8px;border-radius:8px;background:rgba(255,255,255,0.02);font-weight:600">JavaScript</span>
      </div>
    </div>

    <div class="card-panel">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
        <strong>Latest Release</strong>
        <small class="muted">v2.1</small>
      </div>
      <div class="muted">yubbiXploit-locker-prank · 2 days ago</div>
    </div>

    <div class="card-panel">
      <strong>Contact</strong>
      <div class="muted" style="margin-top:8px;">github.com/yubbiXploit</div>
    </div>
  </aside>
</div>

<div class="scanline"></div>

  </div>
</body>
</html>
