<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Heaven Sarder — Full Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,700;1,9..144,400&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #070a0f;
    --surface: #0d1117;
    --surface2: #161b22;
    --border: rgba(255,255,255,0.07);
    --accent: #00e5ff;
    --accent2: #ff4ecd;
    --accent3: #ffe066;
    --text: #e6edf3;
    --muted: #7d8590;
    --glow: 0 0 30px rgba(0,229,255,0.15);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,229,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* Radial glow blobs */
  .blob {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
    animation: drift 12s ease-in-out infinite alternate;
  }
  .blob-1 { width: 500px; height: 500px; background: rgba(0,229,255,0.07); top: -100px; left: -100px; }
  .blob-2 { width: 400px; height: 400px; background: rgba(255,78,205,0.06); bottom: 200px; right: -80px; animation-delay: -6s; }
  .blob-3 { width: 300px; height: 300px; background: rgba(255,224,102,0.05); top: 40%; left: 40%; animation-delay: -3s; }

  @keyframes drift {
    from { transform: translate(0, 0) scale(1); }
    to   { transform: translate(30px, 20px) scale(1.08); }
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* ─── HERO ─────────────────────────────── */
  .hero {
    text-align: center;
    padding-bottom: 56px;
    border-bottom: 1px solid var(--border);
    animation: fadeUp 0.8s ease both;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 11px;
    font-family: 'DM Mono', monospace;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent);
    background: rgba(0,229,255,0.07);
    border: 1px solid rgba(0,229,255,0.2);
    padding: 6px 16px;
    border-radius: 100px;
    margin-bottom: 28px;
  }
  .hero-badge::before { content: '◉'; font-size: 8px; animation: pulse 2s infinite; }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(36px, 6vw, 64px);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -0.02em;
    margin-bottom: 10px;
  }
  .hero h1 span {
    background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 60%, var(--accent3) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-family: 'Fraunces', serif;
    font-size: 18px;
    font-style: italic;
    color: var(--muted);
    margin-bottom: 28px;
  }

  .hero-desc {
    font-size: 14px;
    color: #8b949e;
    max-width: 520px;
    margin: 0 auto 36px;
    line-height: 1.7;
  }
  .hero-desc strong { color: var(--accent); font-weight: 500; }

  .cta-row {
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 22px;
    border-radius: 8px;
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    font-weight: 500;
    letter-spacing: 0.04em;
    text-decoration: none;
    transition: all 0.2s ease;
    cursor: pointer;
    border: none;
  }
  .btn-primary {
    background: var(--accent);
    color: #000;
  }
  .btn-primary:hover { background: #fff; transform: translateY(-2px); box-shadow: 0 8px 24px rgba(0,229,255,0.3); }
  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
  }
  .btn-ghost:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }

  /* ─── SECTIONS ──────────────────────────── */
  section {
    padding: 52px 0;
    border-bottom: 1px solid var(--border);
    animation: fadeUp 0.8s ease both;
  }

  .section-label {
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 32px;
    font-family: 'DM Mono', monospace;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, rgba(0,229,255,0.3), transparent);
  }

  /* ─── ABOUT GRID ─────────────────────────── */
  .about-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 16px;
  }

  .about-item {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 18px 20px;
    display: flex;
    align-items: flex-start;
    gap: 14px;
    transition: all 0.25s ease;
  }
  .about-item:hover {
    border-color: rgba(0,229,255,0.3);
    background: rgba(0,229,255,0.04);
    transform: translateY(-2px);
  }
  .about-icon {
    font-size: 20px;
    flex-shrink: 0;
    line-height: 1;
    margin-top: 2px;
  }
  .about-item p { font-size: 13px; color: #8b949e; line-height: 1.5; }
  .about-item strong { color: var(--text); font-weight: 500; display: block; margin-bottom: 2px; }

  /* ─── TECH STACK ─────────────────────────── */
  .stack-group { margin-bottom: 28px; }
  .stack-group:last-child { margin-bottom: 0; }

  .stack-group-title {
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .stack-group-title span { font-size: 14px; }

  .tag-row { display: flex; flex-wrap: wrap; gap: 8px; }

  .tag {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 14px;
    border-radius: 6px;
    font-size: 12px;
    font-family: 'DM Mono', monospace;
    border: 1px solid var(--border);
    background: var(--surface2);
    color: var(--text);
    transition: all 0.2s ease;
    cursor: default;
  }
  .tag:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(0,229,255,0.05);
    transform: translateY(-1px);
    box-shadow: 0 4px 12px rgba(0,229,255,0.1);
  }
  .tag .dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: currentColor;
    opacity: 0.6;
  }

  /* Color overrides by category */
  .tag.fe:hover { color: #61dafb; border-color: #61dafb; background: rgba(97,218,251,0.05); }
  .tag.be:hover { color: #68d391; border-color: #68d391; background: rgba(104,211,145,0.05); }
  .tag.db:hover { color: #f6ad55; border-color: #f6ad55; background: rgba(246,173,85,0.05); }
  .tag.ops:hover { color: #fc8181; border-color: #fc8181; background: rgba(252,129,129,0.05); }
  .tag.design:hover { color: #b794f4; border-color: #b794f4; background: rgba(183,148,244,0.05); }

  /* ─── STATS / STREAK ─────────────────────── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 16px;
    margin-bottom: 32px;
  }

  .stat-card {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px 20px;
    text-align: center;
    transition: all 0.25s ease;
  }
  .stat-card:hover {
    border-color: rgba(0,229,255,0.3);
    transform: translateY(-3px);
    box-shadow: var(--glow);
  }
  .stat-number {
    font-family: 'Syne', sans-serif;
    font-size: 36px;
    font-weight: 800;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1;
    margin-bottom: 6px;
  }
  .stat-label { font-size: 11px; color: var(--muted); letter-spacing: 0.08em; }

  .streak-wrap {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
    text-align: center;
  }
  .streak-wrap img {
    max-width: 100%;
    border-radius: 8px;
    filter: brightness(0.95);
  }

  /* ─── CONTACT ────────────────────────────── */
  .contact-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 16px;
  }

  .contact-card {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 18px 20px;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 12px;
    text-decoration: none;
    color: var(--text);
    transition: all 0.25s ease;
    font-size: 13px;
  }
  .contact-card:hover { transform: translateY(-2px); }
  .contact-card.web:hover { border-color: var(--accent); box-shadow: 0 8px 24px rgba(0,229,255,0.12); }
  .contact-card.email:hover { border-color: #fc8181; box-shadow: 0 8px 24px rgba(252,129,129,0.12); }
  .contact-card.linkedin:hover { border-color: #90cdf4; box-shadow: 0 8px 24px rgba(144,205,244,0.12); }

  .contact-icon {
    width: 40px; height: 40px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px;
    flex-shrink: 0;
  }
  .contact-card.web .contact-icon { background: rgba(0,229,255,0.1); color: var(--accent); }
  .contact-card.email .contact-icon { background: rgba(252,129,129,0.1); color: #fc8181; }
  .contact-card.linkedin .contact-icon { background: rgba(144,205,244,0.1); color: #90cdf4; }

  .contact-info { flex: 1; min-width: 0; }
  .contact-info strong { display: block; font-size: 13px; font-weight: 500; margin-bottom: 2px; }
  .contact-info span { font-size: 11px; color: var(--muted); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }

  /* ─── QUOTE ──────────────────────────────── */
  .quote-section {
    text-align: center;
    padding: 52px 0 0;
    border-bottom: none;
  }

  .quote-mark {
    font-family: 'Fraunces', serif;
    font-size: 80px;
    line-height: 0.5;
    color: rgba(0,229,255,0.15);
    display: block;
    margin-bottom: 24px;
  }

  .quote-text {
    font-family: 'Fraunces', serif;
    font-size: clamp(22px, 3.5vw, 32px);
    font-style: italic;
    font-weight: 300;
    color: var(--text);
    letter-spacing: -0.01em;
    line-height: 1.4;
    margin-bottom: 12px;
  }
  .quote-text strong {
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    font-style: normal;
    font-weight: 700;
  }

  .quote-author {
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 0.1em;
  }

  /* ─── FOOTER ─────────────────────────────── */
  .footer {
    text-align: center;
    padding-top: 36px;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.06em;
  }
  .footer a { color: var(--accent); text-decoration: none; }
  .footer a:hover { text-decoration: underline; }

  /* ─── ANIMATIONS ─────────────────────────── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  section:nth-child(2) { animation-delay: 0.1s; }
  section:nth-child(3) { animation-delay: 0.2s; }
  section:nth-child(4) { animation-delay: 0.3s; }
  section:nth-child(5) { animation-delay: 0.4s; }
  section:nth-child(6) { animation-delay: 0.5s; }

  /* ─── RESPONSIVE ─────────────────────────── */
  @media (max-width: 600px) {
    .hero { padding-bottom: 40px; }
    section { padding: 36px 0; }
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>

<div class="blob blob-1"></div>
<div class="blob blob-2"></div>
<div class="blob blob-3"></div>

<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-badge">Available for Work</div>
    <h1>Hi, I'm <span>Heaven Sarder</span></h1>
    <p class="hero-sub">Full Stack Developer · WordPress Expert · AI Builder</p>
    <p class="hero-desc">
      Passionate about building modern <strong>web applications</strong> and <strong>AI-powered solutions</strong>
      that are scalable, efficient, and user-friendly. 5+ years crafting real-world products
      with clean architecture and performance-focused design.
    </p>
    <div class="cta-row">
      <a class="btn btn-primary" href="https://www.heavensarder.com/" target="_blank">🌐 Visit Portfolio</a>
      <a class="btn btn-ghost" href="mailto:sarder.heaven@gmail.com">✉ Get In Touch</a>
      <a class="btn btn-ghost" href="https://www.linkedin.com/in/heaven-sarder-86b24a1b1/" target="_blank">🔗 LinkedIn</a>
    </div>
  </div>

  <!-- ABOUT -->
  <section>
    <div class="section-label">About Me</div>
    <div class="about-grid">
      <div class="about-item">
        <div class="about-icon">🇧🇩</div>
        <p><strong>Location</strong>Based in Bangladesh</p>
      </div>
      <div class="about-item">
        <div class="about-icon">💼</div>
        <p><strong>Role</strong>Full Stack Dev — MERN, Next.js, PHP, WordPress</p>
      </div>
      <div class="about-item">
        <div class="about-icon">🤖</div>
        <p><strong>Focus</strong>AI-powered applications & automation systems</p>
      </div>
      <div class="about-item">
        <div class="about-icon">🌐</div>
        <p><strong>Specialty</strong>Dynamic web apps & interactive UI/UX</p>
      </div>
      <div class="about-item">
        <div class="about-icon">⚡</div>
        <p><strong>Interest</strong>Performance optimization & scalable systems</p>
      </div>
      <div class="about-item">
        <div class="about-icon">🎯</div>
        <p><strong>Goal</strong>Build intelligent digital products that solve real-world problems</p>
      </div>
    </div>
  </section>

  <!-- TECH STACK -->
  <section>
    <div class="section-label">Tech Stack</div>

    <div class="stack-group">
      <div class="stack-group-title"><span>💻</span> Frontend</div>
      <div class="tag-row">
        <div class="tag fe"><div class="dot"></div>React</div>
        <div class="tag fe"><div class="dot"></div>Next.js</div>
        <div class="tag fe"><div class="dot"></div>JavaScript</div>
        <div class="tag fe"><div class="dot"></div>TailwindCSS</div>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-group-title"><span>⚙️</span> Backend</div>
      <div class="tag-row">
        <div class="tag be"><div class="dot"></div>Node.js</div>
        <div class="tag be"><div class="dot"></div>Express</div>
        <div class="tag be"><div class="dot"></div>PHP</div>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-group-title"><span>🗄️</span> Database</div>
      <div class="tag-row">
        <div class="tag db"><div class="dot"></div>MongoDB</div>
        <div class="tag db"><div class="dot"></div>MySQL</div>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-group-title"><span>☁️</span> Tools & DevOps</div>
      <div class="tag-row">
        <div class="tag ops"><div class="dot"></div>Vercel</div>
        <div class="tag ops"><div class="dot"></div>Cloudflare</div>
        <div class="tag ops"><div class="dot"></div>Docker</div>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-group-title"><span>🎨</span> Design</div>
      <div class="tag-row">
        <div class="tag design"><div class="dot"></div>Figma</div>
        <div class="tag design"><div class="dot"></div>Canva</div>
        <div class="tag design"><div class="dot"></div>Photoshop</div>
        <div class="tag design"><div class="dot"></div>Illustrator</div>
        <div class="tag design"><div class="dot"></div>Adobe XD</div>
        <div class="tag design"><div class="dot"></div>Premiere Pro</div>
        <div class="tag design"><div class="dot"></div>After Effects</div>
        <div class="tag design"><div class="dot"></div>Lightroom</div>
        <div class="tag design"><div class="dot"></div>InDesign</div>
        <div class="tag design"><div class="dot"></div>Framer</div>
        <div class="tag design"><div class="dot"></div>Webflow</div>
      </div>
    </div>
  </section>

  <!-- STATS -->
  <section>
    <div class="section-label">Stats & Activity</div>

    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-number">5+</div>
        <div class="stat-label">Years of Experience</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">3</div>
        <div class="stat-label">Core Stacks</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">20+</div>
        <div class="stat-label">Tools & Frameworks</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">∞</div>
        <div class="stat-label">Problems Solved</div>
      </div>
    </div>

    <div class="streak-wrap">
      <img src="https://streak-stats.demolab.com?user=heavensarder&theme=tokyonight&hide_border=true&background=0D1117&ring=00e5ff&fire=ff4ecd&currStreakLabel=00e5ff" alt="GitHub Streak" />
    </div>
  </section>

  <!-- CONTACT -->
  <section>
    <div class="section-label">Portfolio & Contact</div>
    <div class="contact-grid">
      <a class="contact-card web" href="https://www.heavensarder.com/" target="_blank">
        <div class="contact-icon">🌐</div>
        <div class="contact-info">
          <strong>Portfolio</strong>
          <span>heavensarder.com</span>
        </div>
      </a>
      <a class="contact-card email" href="mailto:sarder.heaven@gmail.com">
        <div class="contact-icon">✉</div>
        <div class="contact-info">
          <strong>Email</strong>
          <span>sarder.heaven@gmail.com</span>
        </div>
      </a>
      <a class="contact-card linkedin" href="https://www.linkedin.com/in/heaven-sarder-86b24a1b1/" target="_blank">
        <div class="contact-icon">🔗</div>
        <div class="contact-info">
          <strong>LinkedIn</strong>
          <span>heaven-sarder-86b24a1b1</span>
        </div>
      </a>
    </div>
  </section>

  <!-- QUOTE -->
  <section class="quote-section">
    <span class="quote-mark">"</span>
    <p class="quote-text"><strong>Code. Build. Scale.</strong> Repeat.</p>
    <p class="quote-author">— Heaven Sarder</p>
  </section>

  <!-- FOOTER -->
  <div class="footer">
    ⭐ From <a href="https://github.com/heavensarder" target="_blank">@heavensarder</a>
  </div>

</div>
</body>
</html>
