<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Khawaja Absar Ali — GitHub Profile</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet" />
<style>
  /* ── TOKENS ── */
  :root {
    --bg:       #0d1117;
    --surface:  #111827;
    --border:   #1f2d45;
    --navy:     #0a1628;
    --blue:     #1a3a6e;
    --accent:   #8ab4f8;
    --soft:     #c2d9ff;
    --text:     #c9d1d9;
    --muted:    #6e7f96;
    --white:    #f0f6ff;
    --green:    #3fb950;
    --r:        12px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── ANIMATED BACKGROUND ── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background:
      radial-gradient(ellipse 60% 40% at 20% 10%, rgba(26,58,110,.18) 0%, transparent 70%),
      radial-gradient(ellipse 40% 50% at 80% 90%, rgba(138,180,248,.07) 0%, transparent 60%);
    pointer-events: none; z-index: 0;
  }

  .page { position: relative; z-index: 1; max-width: 900px; margin: 0 auto; padding: 0 20px 60px; }

  /* ══════════════════ HEADER ══════════════════ */
  .header {
    position: relative;
    text-align: center;
    padding: 70px 20px 56px;
    overflow: hidden;
  }
  .header::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(160deg, #0a1628 0%, #1a3a6e 50%, #0a1628 100%);
    border-radius: 0 0 40px 40px;
    z-index: 0;
  }
  /* grid mesh overlay */
  .header::after {
    content: '';
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(138,180,248,.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(138,180,248,.04) 1px, transparent 1px);
    background-size: 32px 32px;
    border-radius: 0 0 40px 40px;
    z-index: 0;
  }
  .header-inner { position: relative; z-index: 1; }

  .header-subtitle {
    font-size: 11px;
    letter-spacing: .25em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
    opacity: 0;
    animation: fadeUp .6s .2s forwards;
  }
  .header-name {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(36px, 7vw, 62px);
    color: var(--white);
    line-height: 1.05;
    letter-spacing: -.02em;
    opacity: 0;
    animation: fadeUp .7s .4s forwards;
  }
  .header-name span { color: var(--accent); }
  .header-desc {
    margin-top: 14px;
    font-size: 14px;
    color: var(--muted);
    letter-spacing: .05em;
    opacity: 0;
    animation: fadeUp .6s .6s forwards;
  }
  .header-badges {
    margin-top: 28px;
    display: flex; justify-content: center; gap: 10px; flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp .6s .8s forwards;
  }
  .badge {
    display: inline-flex; align-items: center; gap: 6px;
    background: rgba(26,58,110,.5);
    border: 1px solid rgba(138,180,248,.2);
    border-radius: 20px;
    padding: 5px 14px;
    font-size: 11px;
    color: var(--accent);
    backdrop-filter: blur(8px);
  }
  .badge .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--green); box-shadow: 0 0 6px var(--green); }

  /* ══════════════════ DIVIDER ══════════════════ */
  .divider {
    position: relative; height: 6px; margin: 40px 0; border-radius: 3px; overflow: visible;
  }
  .divider svg { display: block; width: 100%; height: 6px; }

  /* ══════════════════ SECTIONS ══════════════════ */
  .section { margin-bottom: 48px; }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 700;
    letter-spacing: .2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 22px;
    display: flex; align-items: center; gap: 10px;
  }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, rgba(138,180,248,.3), transparent);
  }

  /* ── about ── */
  .quote-block {
    border-left: 3px solid var(--accent);
    padding: 12px 18px;
    margin-bottom: 22px;
    background: rgba(138,180,248,.05);
    border-radius: 0 8px 8px 0;
    font-style: italic;
    color: var(--soft);
    font-size: 13px;
    line-height: 1.7;
  }

  .about-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 10px;
  }
  @media(max-width:600px){ .about-grid { grid-template-columns: 1fr; } }

  .about-row {
    display: flex; align-items: flex-start; gap: 10px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px 14px;
    font-size: 12px;
    transition: border-color .2s, transform .2s;
  }
  .about-row:hover { border-color: rgba(138,180,248,.4); transform: translateY(-2px); }
  .about-row .icon { font-size: 16px; flex-shrink: 0; margin-top: 1px; }
  .about-row .label { color: var(--muted); font-size: 10px; letter-spacing: .05em; margin-bottom: 2px; }
  .about-row .val   { color: var(--text); line-height: 1.4; }
  .about-row a { color: var(--accent); text-decoration: none; }
  .about-row a:hover { text-decoration: underline; }

  /* ── journey ── */
  .journey-list { list-style: none; display: flex; flex-direction: column; gap: 14px; }
  .journey-item {
    display: flex; align-items: flex-start; gap: 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px 18px;
    position: relative;
    overflow: hidden;
    transition: border-color .2s, transform .2s;
  }
  .journey-item::before {
    content: '';
    position: absolute; left: 0; top: 0; bottom: 0; width: 3px;
    background: linear-gradient(180deg, var(--blue), var(--accent));
    border-radius: 3px 0 0 3px;
    opacity: 0;
    transition: opacity .2s;
  }
  .journey-item:hover { border-color: rgba(138,180,248,.35); transform: translateX(4px); }
  .journey-item:hover::before { opacity: 1; }
  .journey-icon { font-size: 20px; flex-shrink: 0; margin-top: 1px; }
  .journey-text { font-size: 13px; line-height: 1.6; color: var(--text); }
  .journey-text strong { color: var(--accent); }

  /* ── tech stack ── */
  .stack-group { margin-bottom: 20px; }
  .stack-group-label {
    font-size: 10px; letter-spacing: .18em; text-transform: uppercase;
    color: var(--muted); margin-bottom: 10px;
  }
  .stack-pills { display: flex; flex-wrap: wrap; gap: 8px; }
  .pill {
    display: inline-flex; align-items: center; gap: 7px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 7px 13px;
    font-size: 11px; font-weight: 600;
    color: var(--text);
    transition: border-color .2s, transform .2s, box-shadow .2s;
    cursor: default;
  }
  .pill:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
    box-shadow: 0 4px 14px rgba(138,180,248,.15);
    color: var(--white);
  }
  .pill-dot { width: 8px; height: 8px; border-radius: 2px; flex-shrink: 0; }

  /* ── stats ── */
  .stats-row {
    display: grid; grid-template-columns: repeat(3, 1fr); gap: 14px; margin-bottom: 20px;
  }
  @media(max-width:560px){ .stats-row { grid-template-columns: 1fr 1fr; } }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    text-align: center;
    transition: border-color .2s, transform .2s;
  }
  .stat-card:hover { border-color: rgba(138,180,248,.4); transform: translateY(-3px); }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 28px; font-weight: 800;
    color: var(--accent);
    display: block;
  }
  .stat-label { font-size: 10px; color: var(--muted); letter-spacing: .1em; text-transform: uppercase; margin-top: 4px; }

  .stat-img-row {
    display: grid; grid-template-columns: 1fr 1fr; gap: 14px; margin-bottom: 20px;
  }
  @media(max-width:560px){ .stat-img-row { grid-template-columns: 1fr; } }

  .stat-img-row img, .streak-wrap img, .graph-wrap img {
    width: 100%; border-radius: 12px; display: block;
  }
  .streak-wrap { text-align: center; margin-bottom: 20px; }
  .streak-wrap img { max-width: 580px; margin: 0 auto; }
  .graph-wrap img { border-radius: 12px; }

  /* ── trophies ── */
  .trophy-wrap { text-align: center; }
  .trophy-wrap img { max-width: 100%; border-radius: 10px; }

  /* ── connect ── */
  .connect-grid { display: flex; flex-wrap: wrap; gap: 12px; justify-content: center; }
  .connect-card {
    display: flex; align-items: center; gap: 10px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px 22px;
    text-decoration: none;
    color: var(--text);
    font-size: 13px;
    transition: border-color .2s, transform .2s, box-shadow .2s;
  }
  .connect-card:hover {
    border-color: var(--accent);
    transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(138,180,248,.12);
    color: var(--white);
  }
  .connect-card .ci { font-size: 18px; }

  /* ── footer ── */
  .footer {
    margin-top: 60px;
    text-align: center;
    padding: 40px 20px;
    position: relative;
    overflow: hidden;
  }
  .footer::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(160deg, #0a1628 0%, #1a3a6e 50%, #0a1628 100%);
    border-radius: 40px 40px 0 0;
  }
  .footer::after {
    content: '';
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(138,180,248,.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(138,180,248,.04) 1px, transparent 1px);
    background-size: 32px 32px;
    border-radius: 40px 40px 0 0;
  }
  .footer-inner { position: relative; z-index: 1; }
  .footer-text { font-size: 12px; color: var(--muted); margin-top: 8px; }
  .footer-star { font-size: 13px; color: var(--accent); margin-top: 10px; }

  /* ── animations ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ── typing cursor ── */
  .typing-wrap {
    text-align: center; margin: 20px 0;
  }
  .typing {
    font-size: 16px; color: var(--accent); font-weight: 600;
    border-right: 2px solid var(--accent);
    padding-right: 4px;
    white-space: nowrap; overflow: hidden;
    display: inline-block;
    animation: blink .7s step-end infinite;
  }
  @keyframes blink { 50% { border-color: transparent; } }

  /* ── scroll reveal ── */
  .reveal {
    opacity: 0; transform: translateY(24px);
    transition: opacity .6s ease, transform .6s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
</style>
</head>
<body>

<div class="page">

  <!-- ════ HEADER ════ -->
  <header class="header">
    <div class="header-inner">
      <div class="header-subtitle">GitHub Profile · Pakistan 🇵🇰</div>
      <h1 class="header-name">Khawaja <span>Absar</span> Ali</h1>
      <p class="header-desc">Software Engineer &nbsp;·&nbsp; Web Developer &nbsp;·&nbsp; UI/UX Designer</p>
      <div class="header-badges">
        <span class="badge"><span class="dot"></span> Open to Work</span>
        <span class="badge">⚡ Web Development</span>
        <span class="badge">🎯 Becoming a Software Engineer</span>
        <span class="badge">🌱 Advanced WordPress &amp; AI</span>
      </div>
    </div>
  </header>

  <!-- Typing row -->
  <div class="typing-wrap reveal">
    <span class="typing" id="typer"></span>
  </div>

  <!-- ════ DIVIDER ════ -->
  <div class="divider reveal">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 6" preserveAspectRatio="none">
      <defs>
        <style>
          .trk { animation: pulse 3s ease-in-out infinite; }
          .shn { animation: sweep 3s ease-in-out infinite; }
          @keyframes pulse { 0%,100%{opacity:.25} 50%{opacity:.65} }
          @keyframes sweep {
            0%   { opacity:0; transform:translateX(-400px); }
            30%  { opacity:1; }
            70%  { opacity:1; }
            100% { opacity:0; transform:translateX(1200px); }
          }
        </style>
        <linearGradient id="trk" x1="0%" x2="100%">
          <stop offset="0%"   stop-color="#0d1117"/>
          <stop offset="30%"  stop-color="#1a3a6e"/>
          <stop offset="50%"  stop-color="#4a7abf"/>
          <stop offset="70%"  stop-color="#1a3a6e"/>
          <stop offset="100%" stop-color="#0d1117"/>
        </linearGradient>
        <linearGradient id="shn" x1="0%" x2="100%">
          <stop offset="0%"   stop-color="#0d1117"  stop-opacity="0"/>
          <stop offset="40%"  stop-color="#8ab4f8"  stop-opacity="1"/>
          <stop offset="60%"  stop-color="#c2d9ff"  stop-opacity="1"/>
          <stop offset="100%" stop-color="#0d1117"  stop-opacity="0"/>
        </linearGradient>
      </defs>
      <rect class="trk" width="1200" height="6" rx="3" fill="url(#trk)"/>
      <rect class="shn" width="400"  height="6" rx="3" fill="url(#shn)"/>
    </svg>
  </div>

  <!-- ════ ABOUT ════ -->
  <section class="section reveal">
    <h2 class="section-title">🧑‍💻 About Me</h2>
    <div class="quote-block">
      "I am on a mission to become a Software Engineer — building meaningful digital products, one clean commit at a time."
    </div>
    <div class="about-grid">
      <div class="about-row"><span class="icon">🔭</span><div><div class="label">Currently</div><div class="val">Building conversion-optimised web solutions</div></div></div>
      <div class="about-row"><span class="icon">🌱</span><div><div class="label">Learning</div><div class="val">Advanced WordPress · AI Integration · SEO</div></div></div>
      <div class="about-row"><span class="icon">🤝</span><div><div class="label">Looking For</div><div class="val">Open-source &amp; freelance collaboration</div></div></div>
      <div class="about-row"><span class="icon">💬</span><div><div class="label">Ask Me About</div><div class="val">WordPress · PHP · Elementor · Front-End</div></div></div>
      <div class="about-row"><span class="icon">📬</span><div><div class="label">Email</div><div class="val"><a href="mailto:khabsarali@gmail.com">khabsarali@gmail.com</a></div></div></div>
      <div class="about-row"><span class="icon">🌍</span><div><div class="label">Based In</div><div class="val">Pakistan 🇵🇰</div></div></div>
    </div>
  </section>

  <!-- DIVIDER -->
  <div class="divider reveal"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 6" preserveAspectRatio="none"><defs><style>.trk2{animation:pulse 3s ease-in-out infinite}.shn2{animation:sweep 3s .6s ease-in-out infinite}@keyframes pulse{0%,100%{opacity:.25}50%{opacity:.65}}@keyframes sweep{0%{opacity:0;transform:translateX(-400px)}30%{opacity:1}70%{opacity:1}100%{opacity:0;transform:translateX(1200px)}}</style><linearGradient id="trk2" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117"/><stop offset="30%" stop-color="#1a3a6e"/><stop offset="50%" stop-color="#4a7abf"/><stop offset="70%" stop-color="#1a3a6e"/><stop offset="100%" stop-color="#0d1117"/></linearGradient><linearGradient id="shn2" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117" stop-opacity="0"/><stop offset="40%" stop-color="#8ab4f8" stop-opacity="1"/><stop offset="60%" stop-color="#c2d9ff" stop-opacity="1"/><stop offset="100%" stop-color="#0d1117" stop-opacity="0"/></linearGradient></defs><rect class="trk2" width="1200" height="6" rx="3" fill="url(#trk2)"/><rect class="shn2" width="400" height="6" rx="3" fill="url(#shn2)"/></svg></div>

  <!-- ════ JOURNEY ════ -->
  <section class="section reveal">
    <h2 class="section-title">🚀 My Journey to Become a Software Engineer</h2>
    <ul class="journey-list">
      <li class="journey-item"><span class="journey-icon">🎓</span><div class="journey-text">Started with <strong>HTML, CSS &amp; the fundamentals</strong> — felt the joy of seeing a webpage come alive for the first time</div></li>
      <li class="journey-item"><span class="journey-icon">💡</span><div class="journey-text">Discovered a <strong>passion for solving real problems</strong> through code — logic became a creative tool</div></li>
      <li class="journey-item"><span class="journey-icon">🛠️</span><div class="journey-text"><strong>Built projects, broke things, fixed them</strong> — grew stronger and sharper with every bug and deploy</div></li>
      <li class="journey-item"><span class="journey-icon">🌐</span><div class="journey-text">Expanded into <strong>full-stack web development</strong> — PHP, JavaScript, WordPress, Python — building real client solutions</div></li>
      <li class="journey-item"><span class="journey-icon">🎨</span><div class="journey-text">Added <strong>UI/UX &amp; graphic design</strong> to the toolkit — bridging the gap between engineering and human experience</div></li>
      <li class="journey-item"><span class="journey-icon">📈</span><div class="journey-text">Now sharpening skills in <strong>AI tooling, SEO systems &amp; scalable web architecture</strong> for professional-grade products</div></li>
      <li class="journey-item"><span class="journey-icon">🌟</span><div class="journey-text"><strong>Next milestone:</strong> ship products used by thousands — the journey continues, always learning, always building</div></li>
    </ul>
  </section>

  <!-- DIVIDER -->
  <div class="divider reveal"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 6" preserveAspectRatio="none"><defs><style>.trk3{animation:pulse 3s ease-in-out infinite}.shn3{animation:sweep 3s 1.2s ease-in-out infinite}@keyframes pulse{0%,100%{opacity:.25}50%{opacity:.65}}@keyframes sweep{0%{opacity:0;transform:translateX(-400px)}30%{opacity:1}70%{opacity:1}100%{opacity:0;transform:translateX(1200px)}}</style><linearGradient id="trk3" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117"/><stop offset="30%" stop-color="#1a3a6e"/><stop offset="50%" stop-color="#4a7abf"/><stop offset="70%" stop-color="#1a3a6e"/><stop offset="100%" stop-color="#0d1117"/></linearGradient><linearGradient id="shn3" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117" stop-opacity="0"/><stop offset="40%" stop-color="#8ab4f8" stop-opacity="1"/><stop offset="60%" stop-color="#c2d9ff" stop-opacity="1"/><stop offset="100%" stop-color="#0d1117" stop-opacity="0"/></linearGradient></defs><rect class="trk3" width="1200" height="6" rx="3" fill="url(#trk3)"/><rect class="shn3" width="400" height="6" rx="3" fill="url(#shn3)"/></svg></div>

  <!-- ════ TECH STACK ════ -->
  <section class="section reveal">
    <h2 class="section-title">🛠 Tech Stack</h2>

    <div class="stack-group">
      <div class="stack-group-label">⚙️ Languages</div>
      <div class="stack-pills">
        <span class="pill"><span class="pill-dot" style="background:#e34f26"></span>HTML5</span>
        <span class="pill"><span class="pill-dot" style="background:#1572b6"></span>CSS3</span>
        <span class="pill"><span class="pill-dot" style="background:#f7df1e"></span>JavaScript</span>
        <span class="pill"><span class="pill-dot" style="background:#777bb4"></span>PHP</span>
        <span class="pill"><span class="pill-dot" style="background:#3776ab"></span>Python</span>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-group-label">🌐 CMS &amp; Platforms</div>
      <div class="stack-pills">
        <span class="pill"><span class="pill-dot" style="background:#21759b"></span>WordPress</span>
        <span class="pill"><span class="pill-dot" style="background:#92003b"></span>Elementor</span>
        <span class="pill"><span class="pill-dot" style="background:#96588a"></span>WooCommerce</span>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-group-label">🎨 Design Tools</div>
      <div class="stack-pills">
        <span class="pill"><span class="pill-dot" style="background:#f24e1e"></span>Figma</span>
        <span class="pill"><span class="pill-dot" style="background:#31a8ff"></span>Photoshop</span>
        <span class="pill"><span class="pill-dot" style="background:#ff9a00"></span>Illustrator</span>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-group-label">🔧 Developer Tools</div>
      <div class="stack-pills">
        <span class="pill"><span class="pill-dot" style="background:#f05032"></span>Git</span>
        <span class="pill"><span class="pill-dot" style="background:#181717"></span>GitHub</span>
        <span class="pill"><span class="pill-dot" style="background:#007acc"></span>VS Code</span>
      </div>
    </div>
  </section>

  <!-- DIVIDER -->
  <div class="divider reveal"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 6" preserveAspectRatio="none"><defs><style>.trk4{animation:pulse 3s ease-in-out infinite}.shn4{animation:sweep 3s 1.8s ease-in-out infinite}@keyframes pulse{0%,100%{opacity:.25}50%{opacity:.65}}@keyframes sweep{0%{opacity:0;transform:translateX(-400px)}30%{opacity:1}70%{opacity:1}100%{opacity:0;transform:translateX(1200px)}}</style><linearGradient id="trk4" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117"/><stop offset="30%" stop-color="#1a3a6e"/><stop offset="50%" stop-color="#4a7abf"/><stop offset="70%" stop-color="#1a3a6e"/><stop offset="100%" stop-color="#0d1117"/></linearGradient><linearGradient id="shn4" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117" stop-opacity="0"/><stop offset="40%" stop-color="#8ab4f8" stop-opacity="1"/><stop offset="60%" stop-color="#c2d9ff" stop-opacity="1"/><stop offset="100%" stop-color="#0d1117" stop-opacity="0"/></linearGradient></defs><rect class="trk4" width="1200" height="6" rx="3" fill="url(#trk4)"/><rect class="shn4" width="400" height="6" rx="3" fill="url(#shn4)"/></svg></div>

  <!-- ════ STATS ════ -->
  <section class="section reveal">
    <h2 class="section-title">📊 GitHub Stats</h2>

    <div class="stat-img-row">
      <img src="https://github-readme-stats.vercel.app/api?username=khabsarali&show_icons=true&count_private=true&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=8ab4f8&icon_color=8ab4f8&text_color=c9d1d9&rank_icon=github" alt="GitHub Stats" />
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=khabsarali&layout=compact&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=8ab4f8&text_color=c9d1d9&langs_count=8" alt="Top Languages" />
    </div>

    <div class="streak-wrap">
      <img src="https://github-readme-streak-stats.herokuapp.com?user=khabsarali&theme=github-dark-blue&hide_border=true&background=0d1117&ring=8ab4f8&fire=8ab4f8&currStreakLabel=8ab4f8" alt="GitHub Streak" />
    </div>

    <div class="graph-wrap">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=khabsarali&theme=github-compact&hide_border=true&bg_color=0d1117&color=8ab4f8&line=1a3a6e&point=8ab4f8&area=true&area_color=1a3a6e" alt="Activity Graph" />
    </div>
  </section>

  <!-- DIVIDER -->
  <div class="divider reveal"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 6" preserveAspectRatio="none"><defs><style>.trk5{animation:pulse 3s ease-in-out infinite}.shn5{animation:sweep 3s 2.4s ease-in-out infinite}@keyframes pulse{0%,100%{opacity:.25}50%{opacity:.65}}@keyframes sweep{0%{opacity:0;transform:translateX(-400px)}30%{opacity:1}70%{opacity:1}100%{opacity:0;transform:translateX(1200px)}}</style><linearGradient id="trk5" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117"/><stop offset="30%" stop-color="#1a3a6e"/><stop offset="50%" stop-color="#4a7abf"/><stop offset="70%" stop-color="#1a3a6e"/><stop offset="100%" stop-color="#0d1117"/></linearGradient><linearGradient id="shn5" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117" stop-opacity="0"/><stop offset="40%" stop-color="#8ab4f8" stop-opacity="1"/><stop offset="60%" stop-color="#c2d9ff" stop-opacity="1"/><stop offset="100%" stop-color="#0d1117" stop-opacity="0"/></linearGradient></defs><rect class="trk5" width="1200" height="6" rx="3" fill="url(#trk5)"/><rect class="shn5" width="400" height="6" rx="3" fill="url(#shn5)"/></svg></div>

  <!-- ════ TROPHIES ════ -->
  <section class="section reveal">
    <h2 class="section-title">🏆 Achievements</h2>
    <div class="trophy-wrap">
      <img src="https://github-profile-trophy.vercel.app/?username=khabsarali&theme=algolia&no-frame=true&no-bg=true&margin-w=8&column=7" alt="Trophies" />
    </div>
  </section>

  <!-- DIVIDER -->
  <div class="divider reveal"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 6" preserveAspectRatio="none"><defs><style>.trk6{animation:pulse 3s ease-in-out infinite}.shn6{animation:sweep 3s 3s ease-in-out infinite}@keyframes pulse{0%,100%{opacity:.25}50%{opacity:.65}}@keyframes sweep{0%{opacity:0;transform:translateX(-400px)}30%{opacity:1}70%{opacity:1}100%{opacity:0;transform:translateX(1200px)}}</style><linearGradient id="trk6" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117"/><stop offset="30%" stop-color="#1a3a6e"/><stop offset="50%" stop-color="#4a7abf"/><stop offset="70%" stop-color="#1a3a6e"/><stop offset="100%" stop-color="#0d1117"/></linearGradient><linearGradient id="shn6" x1="0%" x2="100%"><stop offset="0%" stop-color="#0d1117" stop-opacity="0"/><stop offset="40%" stop-color="#8ab4f8" stop-opacity="1"/><stop offset="60%" stop-color="#c2d9ff" stop-opacity="1"/><stop offset="100%" stop-color="#0d1117" stop-opacity="0"/></linearGradient></defs><rect class="trk6" width="1200" height="6" rx="3" fill="url(#trk6)"/><rect class="shn6" width="400" height="6" rx="3" fill="url(#shn6)"/></svg></div>

  <!-- ════ CONNECT ════ -->
  <section class="section reveal">
    <h2 class="section-title">🤝 Connect With Me</h2>
    <div class="connect-grid">
      <a class="connect-card" href="mailto:khabsarali@gmail.com"><span class="ci">📧</span> khabsarali@gmail.com</a>
      <a class="connect-card" href="https://github.com/khabsarali" target="_blank"><span class="ci">🐙</span> github.com/khabsarali</a>
      <a class="connect-card" href="#"><span class="ci">💼</span> Upwork Profile</a>
    </div>
  </section>

  <!-- ════ FOOTER ════ -->
  <footer class="footer">
    <div class="footer-inner">
      <div style="font-family:'Syne',sans-serif;font-size:20px;font-weight:800;color:var(--white)">Khawaja Absar Ali</div>
      <div class="footer-text">Software Engineer · Web Developer · Designer · Pakistan 🇵🇰</div>
      <div class="footer-star">⭐ If you find my work useful, a star goes a long way — thank you!</div>
    </div>
  </footer>

</div>

<script>
  /* ── Typing animation ── */
  const lines = [
    "Building the Web, One Line at a Time 🚀",
    "WordPress · PHP · JavaScript · Python",
    "Turning Ideas into Digital Products 💡",
    "From Pakistan 🇵🇰 to the World 🌍",
    "On a Mission to Become a Software Engineer 🎯"
  ];
  const el = document.getElementById('typer');
  let li = 0, ci = 0, deleting = false;
  function tick() {
    const cur = lines[li];
    if (!deleting) {
      el.textContent = cur.slice(0, ++ci);
      if (ci === cur.length) { deleting = true; setTimeout(tick, 2000); return; }
    } else {
      el.textContent = cur.slice(0, --ci);
      if (ci === 0) { deleting = false; li = (li + 1) % lines.length; }
    }
    setTimeout(tick, deleting ? 40 : 70);
  }
  tick();

  /* ── Scroll reveal ── */
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); obs.unobserve(e.target); } });
  }, { threshold: 0.12 });
  document.querySelectorAll('.reveal').forEach(el => obs.observe(el));
</script>
</body>
</html>
