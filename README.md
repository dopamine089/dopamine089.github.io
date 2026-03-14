<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Shouket Ali — Freelancer</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --bg: #0a0a0c;
      --bg2: #111116;
      --bg3: #18181f;
      --accent: #c8f04a;
      --accent2: #7ee8a2;
      --text: #e8e8f0;
      --muted: #6b6b80;
      --border: rgba(255,255,255,0.07);
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      line-height: 1.6;
      overflow-x: hidden;
      cursor: none;
    }

    /* Custom Cursor */
    .cursor {
      width: 12px; height: 12px;
      background: var(--accent);
      border-radius: 50%;
      position: fixed; top: 0; left: 0;
      pointer-events: none;
      z-index: 9999;
      transition: transform 0.15s ease, width 0.2s, height 0.2s, background 0.2s;
      transform: translate(-50%, -50%);
    }
    .cursor-ring {
      width: 36px; height: 36px;
      border: 1.5px solid rgba(200,240,74,0.4);
      border-radius: 50%;
      position: fixed; top: 0; left: 0;
      pointer-events: none;
      z-index: 9998;
      transition: transform 0.35s ease;
      transform: translate(-50%, -50%);
    }
    body:hover .cursor { transform: translate(-50%, -50%) scale(1); }

    /* Noise overlay */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none; z-index: 0; opacity: 0.4;
    }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.5rem 4rem;
      background: rgba(10,10,12,0.8);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
    }
    .nav-logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800; font-size: 1.1rem;
      letter-spacing: -0.03em;
      color: var(--text);
      text-decoration: none;
    }
    .nav-logo span { color: var(--accent); }
    .nav-links { display: flex; gap: 2.5rem; list-style: none; }
    .nav-links a {
      color: var(--muted); text-decoration: none;
      font-size: 0.85rem; letter-spacing: 0.05em; text-transform: uppercase;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--accent); }
    .nav-cta {
      background: var(--accent); color: #0a0a0c;
      padding: 0.55rem 1.4rem; border-radius: 2px;
      font-family: 'Syne', sans-serif; font-weight: 700;
      font-size: 0.8rem; letter-spacing: 0.06em; text-transform: uppercase;
      text-decoration: none;
      transition: background 0.2s, transform 0.2s;
    }
    .nav-cta:hover { background: #d9ff55; transform: translateY(-1px); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex; flex-direction: column; justify-content: center;
      padding: 8rem 4rem 4rem;
      position: relative; overflow: hidden;
    }
    .hero-grid-bg {
      position: absolute; inset: 0;
      background-image:
        linear-gradient(rgba(200,240,74,0.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(200,240,74,0.04) 1px, transparent 1px);
      background-size: 60px 60px;
      mask-image: radial-gradient(ellipse 80% 70% at 50% 50%, black 20%, transparent 100%);
    }
    .hero-tag {
      display: inline-flex; align-items: center; gap: 0.5rem;
      background: rgba(200,240,74,0.08);
      border: 1px solid rgba(200,240,74,0.2);
      padding: 0.4rem 1rem; border-radius: 100px;
      font-size: 0.78rem; letter-spacing: 0.1em; text-transform: uppercase;
      color: var(--accent); margin-bottom: 2rem;
      width: fit-content;
      animation: fadeUp 0.8s ease both;
    }
    .hero-tag::before {
      content: ''; width: 6px; height: 6px;
      background: var(--accent); border-radius: 50%;
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.4; transform: scale(0.7); }
    }
    .hero h1 {
      font-family: 'Syne', sans-serif;
      font-weight: 800; font-size: clamp(3.5rem, 8vw, 7.5rem);
      line-height: 0.95; letter-spacing: -0.04em;
      margin-bottom: 1.5rem;
      animation: fadeUp 0.8s 0.1s ease both;
    }
    .hero h1 .line2 { color: var(--accent); display: block; }
    .hero h1 .line3 {
      display: block;
      -webkit-text-stroke: 1px rgba(232,232,240,0.3);
      color: transparent;
    }
    .hero-sub {
      max-width: 480px; color: var(--muted);
      font-size: 1.05rem; line-height: 1.7;
      margin-bottom: 2.5rem;
      animation: fadeUp 0.8s 0.2s ease both;
    }
    .hero-actions {
      display: flex; align-items: center; gap: 1.5rem;
      animation: fadeUp 0.8s 0.3s ease both;
    }
    .btn-primary {
      background: var(--accent); color: #0a0a0c;
      padding: 0.9rem 2rem; border-radius: 2px;
      font-family: 'Syne', sans-serif; font-weight: 700;
      font-size: 0.9rem; letter-spacing: 0.05em; text-transform: uppercase;
      text-decoration: none; display: inline-flex; align-items: center; gap: 0.5rem;
      transition: all 0.2s;
    }
    .btn-primary:hover { background: #d9ff55; transform: translateY(-2px); box-shadow: 0 12px 40px rgba(200,240,74,0.25); }
    .btn-secondary {
      color: var(--text); text-decoration: none;
      font-size: 0.9rem; display: inline-flex; align-items: center; gap: 0.5rem;
      border-bottom: 1px solid var(--border); padding-bottom: 2px;
      transition: color 0.2s, border-color 0.2s;
    }
    .btn-secondary:hover { color: var(--accent); border-color: var(--accent); }
    .hero-stats {
      display: flex; gap: 3rem; margin-top: 5rem;
      border-top: 1px solid var(--border); padding-top: 2rem;
      animation: fadeUp 0.8s 0.4s ease both;
    }
    .stat-num {
      font-family: 'Syne', sans-serif; font-weight: 800;
      font-size: 2rem; letter-spacing: -0.04em; color: var(--text);
    }
    .stat-num span { color: var(--accent); }
    .stat-label { font-size: 0.78rem; color: var(--muted); letter-spacing: 0.05em; text-transform: uppercase; margin-top: 0.2rem; }

    /* Floating badge */
    .hero-badge {
      position: absolute; right: 6rem; top: 50%;
      transform: translateY(-50%);
      width: 160px; height: 160px;
      animation: spin 20s linear infinite, fadeUp 1s 0.5s ease both;
    }
    .hero-badge svg { width: 100%; height: 100%; }
    .hero-badge-center {
      position: absolute; inset: 0;
      display: flex; align-items: center; justify-content: center;
      font-family: 'Syne', sans-serif; font-size: 2.5rem; font-weight: 800;
      color: var(--accent);
    }
    @keyframes spin { to { transform: translateY(-50%) rotate(360deg); } }

    /* SERVICES */
    section { padding: 6rem 4rem; position: relative; }
    .section-label {
      font-size: 0.75rem; letter-spacing: 0.15em; text-transform: uppercase;
      color: var(--accent); margin-bottom: 1rem;
      display: flex; align-items: center; gap: 0.75rem;
    }
    .section-label::before {
      content: ''; display: block; width: 30px; height: 1px; background: var(--accent);
    }
    .section-title {
      font-family: 'Syne', sans-serif; font-weight: 800;
      font-size: clamp(2rem, 4vw, 3.2rem); letter-spacing: -0.03em;
      line-height: 1.1; margin-bottom: 3.5rem;
    }
    .services-grid {
      display: grid; grid-template-columns: repeat(3, 1fr); gap: 1px;
      background: var(--border); border: 1px solid var(--border);
    }
    .service-card {
      background: var(--bg2); padding: 2.5rem;
      transition: background 0.3s;
      position: relative; overflow: hidden;
    }
    .service-card::after {
      content: ''; position: absolute;
      bottom: 0; left: 0; right: 0; height: 2px;
      background: var(--accent);
      transform: scaleX(0); transform-origin: left;
      transition: transform 0.3s ease;
    }
    .service-card:hover { background: var(--bg3); }
    .service-card:hover::after { transform: scaleX(1); }
    .service-num {
      font-family: 'Syne', sans-serif; font-weight: 800;
      font-size: 0.7rem; color: var(--accent); letter-spacing: 0.1em;
      margin-bottom: 1.5rem;
    }
    .service-icon { font-size: 2rem; margin-bottom: 1rem; }
    .service-card h3 {
      font-family: 'Syne', sans-serif; font-weight: 700;
      font-size: 1.15rem; margin-bottom: 0.75rem;
    }
    .service-card p { color: var(--muted); font-size: 0.9rem; line-height: 1.65; }

    /* PORTFOLIO */
    .portfolio-grid {
      display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem;
      margin-top: 0;
    }
    .project-card {
      background: var(--bg2); border: 1px solid var(--border);
      border-radius: 4px; overflow: hidden;
      transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
      cursor: pointer;
    }
    .project-card:hover {
      transform: translateY(-6px);
      border-color: rgba(200,240,74,0.2);
      box-shadow: 0 20px 60px rgba(0,0,0,0.4);
    }
    .project-thumb {
      height: 200px;
      display: flex; align-items: center; justify-content: center;
      font-size: 3.5rem; position: relative; overflow: hidden;
    }
    .project-thumb::after {
      content: ''; position: absolute; inset: 0;
      background: linear-gradient(to bottom, transparent 50%, var(--bg2));
    }
    .p1 { background: linear-gradient(135deg, #1a1a2e, #16213e); }
    .p2 { background: linear-gradient(135deg, #0d1b2a, #1b263b); }
    .p3 { background: linear-gradient(135deg, #1c1c1c, #2d2d2d); }
    .p4 { background: linear-gradient(135deg, #0f2027, #203a43); }
    .project-info { padding: 1.5rem; }
    .project-tags { display: flex; gap: 0.5rem; flex-wrap: wrap; margin-bottom: 0.75rem; }
    .tag {
      font-size: 0.7rem; letter-spacing: 0.08em; text-transform: uppercase;
      padding: 0.25rem 0.7rem; border-radius: 2px;
      background: rgba(200,240,74,0.08); color: var(--accent);
      border: 1px solid rgba(200,240,74,0.15);
    }
    .project-info h3 {
      font-family: 'Syne', sans-serif; font-weight: 700;
      font-size: 1.1rem; margin-bottom: 0.5rem;
    }
    .project-info p { color: var(--muted); font-size: 0.88rem; }
    .project-link {
      display: inline-flex; align-items: center; gap: 0.4rem;
      color: var(--accent); font-size: 0.82rem; margin-top: 1rem;
      text-decoration: none; letter-spacing: 0.05em;
      transition: gap 0.2s;
    }
    .project-link:hover { gap: 0.7rem; }

    /* ABOUT */
    .about-inner {
      display: grid; grid-template-columns: 1fr 1fr; gap: 6rem; align-items: center;
    }
    .about-img-wrap {
      position: relative;
    }
    .about-img-placeholder {
      width: 100%; aspect-ratio: 4/5;
      background: var(--bg3); border: 1px solid var(--border);
      border-radius: 4px;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      gap: 1rem;
    }
    .about-img-placeholder .avatar {
      width: 100px; height: 100px; border-radius: 50%;
      background: linear-gradient(135deg, var(--bg2), var(--bg3));
      border: 2px solid rgba(200,240,74,0.3);
      display: flex; align-items: center; justify-content: center;
      font-size: 2.5rem;
    }
    .about-img-placeholder p { color: var(--muted); font-size: 0.8rem; }
    .about-img-corner {
      position: absolute; bottom: -1.5rem; right: -1.5rem;
      background: var(--accent); color: #0a0a0c;
      padding: 1.2rem 1.5rem; border-radius: 4px;
    }
    .about-img-corner strong {
      font-family: 'Syne', sans-serif; font-weight: 800; font-size: 1.8rem;
      display: block; line-height: 1;
    }
    .about-img-corner span { font-size: 0.72rem; letter-spacing: 0.08em; text-transform: uppercase; }
    .about-text p { color: var(--muted); line-height: 1.8; margin-bottom: 1.2rem; font-size: 0.95rem; }
    .skills-list {
      display: flex; flex-wrap: wrap; gap: 0.6rem; margin: 2rem 0;
    }
    .skill-pill {
      padding: 0.4rem 1rem; background: var(--bg3);
      border: 1px solid var(--border); border-radius: 2px;
      font-size: 0.8rem; color: var(--text);
      transition: border-color 0.2s, color 0.2s;
    }
    .skill-pill:hover { border-color: var(--accent); color: var(--accent); }

    /* CONTACT */
    #contact { background: var(--bg2); }
    .contact-inner {
      max-width: 680px; margin: 0 auto; text-align: center;
    }
    .contact-inner .section-label { justify-content: center; }
    .contact-inner .section-label::before { display: none; }
    .contact-big {
      font-family: 'Syne', sans-serif; font-weight: 800;
      font-size: clamp(2.5rem, 5vw, 4.5rem);
      letter-spacing: -0.04em; line-height: 1.05;
      margin-bottom: 1.5rem;
    }
    .contact-big span { color: var(--accent); }
    .contact-sub { color: var(--muted); font-size: 1rem; margin-bottom: 2.5rem; }
    .contact-email {
      display: inline-flex; align-items: center; gap: 0.75rem;
      background: var(--bg3); border: 1px solid var(--border);
      padding: 1rem 1.8rem; border-radius: 2px;
      color: var(--text); text-decoration: none; font-size: 1rem;
      transition: border-color 0.2s, color 0.2s;
      margin-bottom: 2.5rem;
    }
    .contact-email:hover { border-color: var(--accent); color: var(--accent); }
    .social-links { display: flex; justify-content: center; gap: 1.5rem; }
    .social-link {
      width: 44px; height: 44px;
      background: var(--bg3); border: 1px solid var(--border);
      border-radius: 2px; display: flex; align-items: center; justify-content: center;
      color: var(--muted); text-decoration: none; font-size: 1.1rem;
      transition: border-color 0.2s, color 0.2s, transform 0.2s;
    }
    .social-link:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-3px); }

    /* FOOTER */
    footer {
      padding: 2rem 4rem;
      border-top: 1px solid var(--border);
      display: flex; align-items: center; justify-content: space-between;
    }
    footer p { color: var(--muted); font-size: 0.8rem; }
    footer a { color: var(--accent); text-decoration: none; }

    /* ANIMATIONS */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .reveal {
      opacity: 0; transform: translateY(40px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible { opacity: 1; transform: none; }

    /* RESPONSIVE */
    @media (max-width: 900px) {
      nav { padding: 1.2rem 1.5rem; }
      .nav-links { display: none; }
      .hero { padding: 7rem 1.5rem 3rem; }
      .hero-badge { display: none; }
      .hero-stats { gap: 1.5rem; }
      section { padding: 4rem 1.5rem; }
      .services-grid { grid-template-columns: 1fr; }
      .portfolio-grid { grid-template-columns: 1fr; }
      .about-inner { grid-template-columns: 1fr; gap: 3rem; }
      footer { flex-direction: column; gap: 1rem; text-align: center; }
    }
  </style>
</head>
<body>

  <div class="cursor" id="cursor"></div>
  <div class="cursor-ring" id="cursorRing"></div>

  <!-- NAV -->
  <nav>
    <a href="#" class="nav-logo">Zeeshan<span>.</span></a>
    <ul class="nav-links">
      <li><a href="#services">Services</a></li>
      <li><a href="#work">Work</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <a href="#contact" class="nav-cta">Hire Me</a>
  </nav>

  <!-- HERO -->
  <section class="hero" id="home">
    <div class="hero-grid-bg"></div>
    <div class="hero-tag">Available for freelance work</div>
    <h1>
      Zeeshan<br>
      <span class="line2">Ali</span>
      <span class="line3">Freelancer</span>
    </h1>
    <p class="hero-sub">
      I craft digital experiences that help businesses grow — from sleek websites to powerful web applications. Let's build something great together.
    </p>
    <div class="hero-actions">
      <a href="#work" class="btn-primary">View My Work →</a>
      <a href="#contact" class="btn-secondary">Get in touch ↓</a>
    </div>
    <div class="hero-stats">
      <div>
        <div class="stat-num">3<span>+</span></div>
        <div class="stat-label">Years Experience</div>
      </div>
      <div>
        <div class="stat-num">40<span>+</span></div>
        <div class="stat-label">Projects Done</div>
      </div>
      <div>
        <div class="stat-num">25<span>+</span></div>
        <div class="stat-label">Happy Clients</div>
      </div>
    </div>

    <!-- Rotating badge -->
    <div class="hero-badge">
      <svg viewBox="0 0 160 160" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path id="circle-text" d="M 80,80 m -60,0 a 60,60 0 1,1 120,0 a 60,60 0 1,1 -120,0" fill="none"/>
        <text font-family="Syne" font-size="11.5" font-weight="600" fill="rgba(200,240,74,0.6)" letter-spacing="3">
          <textPath href="#circle-text">FREELANCER • WEB DEV • DESIGNER • </textPath>
        </text>
      </svg>
      <div class="hero-badge-center">✦</div>
    </div>
  </section>

  <!-- SERVICES -->
  <section id="services">
    <div class="section-label reveal">What I Do</div>
    <h2 class="section-title reveal">Services I <br>Specialize In</h2>
    <div class="services-grid reveal">
      <div class="service-card">
        <div class="service-num">01</div>
        <div class="service-icon">🌐</div>
        <h3>Web Development</h3>
        <p>Fast, responsive websites and web apps built with modern technologies. Clean code, great performance.</p>
      </div>
      <div class="service-card">
        <div class="service-num">02</div>
        <div class="service-icon">🎨</div>
        <h3>UI / UX Design</h3>
        <p>Beautiful, user-friendly interfaces that convert visitors into customers. From wireframe to final design.</p>
      </div>
      <div class="service-card">
        <div class="service-num">03</div>
        <div class="service-icon">🛒</div>
        <h3>E-Commerce Stores</h3>
        <p>Complete online stores with payments, inventory, and everything your business needs to sell online.</p>
      </div>
      <div class="service-card">
        <div class="service-num">04</div>
        <div class="service-icon">⚡</div>
        <h3>Speed Optimization</h3>
        <p>Make your existing website faster, better ranked on Google, and more enjoyable for users.</p>
      </div>
      <div class="service-card">
        <div class="service-num">05</div>
        <div class="service-icon">📱</div>
        <h3>Mobile-First Design</h3>
        <p>Every project I build looks and works perfectly on phones, tablets, and desktops.</p>
      </div>
      <div class="service-card">
        <div class="service-num">06</div>
        <div class="service-icon">🔧</div>
        <h3>Maintenance & Support</h3>
        <p>Ongoing updates, bug fixes, and technical support so your site always runs smoothly.</p>
      </div>
    </div>
  </section>

  <!-- PORTFOLIO -->
  <section id="work" style="background: var(--bg2);">
    <div class="section-label reveal">Portfolio</div>
    <h2 class="section-title reveal">Selected <br>Projects</h2>
    <div class="portfolio-grid reveal">
      <div class="project-card">
        <div class="project-thumb p1">🛍️</div>
        <div class="project-info">
          <div class="project-tags"><span class="tag">E-Commerce</span><span class="tag">UI/UX</span></div>
          <h3>Online Clothing Store</h3>
          <p>A fully responsive e-commerce store with cart, payments, and admin dashboard.</p>
          <a href="#" class="project-link">View Project →</a>
        </div>
      </div>
      <div class="project-card">
        <div class="project-thumb p2">💼</div>
        <div class="project-info">
          <div class="project-tags"><span class="tag">Web App</span><span class="tag">Dashboard</span></div>
          <h3>Business Dashboard</h3>
          <p>Analytics and management dashboard for a local services company.</p>
          <a href="#" class="project-link">View Project →</a>
        </div>
      </div>
      <div class="project-card">
        <div class="project-thumb p3">🍕</div>
        <div class="project-info">
          <div class="project-tags"><span class="tag">Landing Page</span><span class="tag">Design</span></div>
          <h3>Restaurant Website</h3>
          <p>A beautiful landing page with online menu, booking system, and gallery.</p>
          <a href="#" class="project-link">View Project →</a>
        </div>
      </div>
      <div class="project-card">
        <div class="project-thumb p4">📚</div>
        <div class="project-info">
          <div class="project-tags"><span class="tag">Portfolio</span><span class="tag">Blog</span></div>
          <h3>Personal Blog Platform</h3>
          <p>Custom blog with CMS, dark mode, newsletter signup and SEO optimization.</p>
          <a href="#" class="project-link">View Project →</a>
        </div>
      </div>
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about">
    <div class="about-inner">
      <div class="about-img-wrap reveal">
        <div class="about-img-placeholder">
          <div class="avatar">👨‍💻</div>
          <p>Replace with your photo</p>
        </div>
        <div class="about-img-corner">
          <strong>3+</strong>
          <span>Yrs of Experience</span>
        </div>
      </div>
      <div class="about-text reveal">
        <div class="section-label">About Me</div>
        <h2 class="section-title" style="margin-bottom:1.5rem;">The Person<br>Behind the Work</h2>
        <p>
          Hi, I'm <strong style="color:var(--text)">zee Ali</strong> — a freelance web developer and designer based in Pakistan. I help startups, small businesses, and individuals build their digital presence from scratch.
        </p>
        <p>
          I care deeply about writing clean code, designing intuitive interfaces, and delivering on time. Every project I take on is treated with full attention and dedication.
        </p>
        <div class="skills-list">
          <span class="skill-pill">HTML / CSS</span>
          <span class="skill-pill">JavaScript</span>
          <span class="skill-pill">React</span>
          <span class="skill-pill">Node.js</span>
          <span class="skill-pill">WordPress</span>
          <span class="skill-pill">Figma</span>
          <span class="skill-pill">Git & GitHub</span>
          <span class="skill-pill">Shopify</span>
        </div>
        <a href="#contact" class="btn-primary" style="margin-top:0.5rem; display:inline-flex;">Let's Talk →</a>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <div class="contact-inner reveal">
      <div class="section-label">Contact</div>
      <h2 class="contact-big">Got a project<br>in <span>mind?</span></h2>
      <p class="contact-sub">I'm currently open to new freelance projects. Let's discuss your idea.</p>
      <a href="mailto:se@example.com" class="contact-email">
        ✉️ se@example.com
      </a>
      <div class="social-links">
        <a href="https://github.com/dopamine089" class="social-link" title="GitHub">⌨</a>
        <a href="#" class="social-link" title="LinkedIn">in</a>
        <a href="#" class="social-link" title="Twitter / X">𝕏</a>
        <a href="#" class="social-link" title="Upwork">⚡</a>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <p>© 2025 <a href="#">Zeeshan w</a>. All rights reserved.</p>
    <p style="color:var(--muted); font-size:0.78rem;">Built with ❤️ & deployed on GitHub Pages</p>
  </footer>

  <script>
    // Custom cursor
    const cursor = document.getElementById('cursor');
    const ring = document.getElementById('cursorRing');
    document.addEventListener('mousemove', e => {
      cursor.style.left = e.clientX + 'px';
      cursor.style.top = e.clientY + 'px';
      setTimeout(() => {
        ring.style.left = e.clientX + 'px';
        ring.style.top = e.clientY + 'px';
      }, 80);
    });
    document.querySelectorAll('a, button').forEach(el => {
      el.addEventListener('mouseenter', () => { cursor.style.transform = 'translate(-50%,-50%) scale(2.5)'; cursor.style.background = 'rgba(200,240,74,0.5)'; });
      el.addEventListener('mouseleave', () => { cursor.style.transform = 'translate(-50%,-50%) scale(1)'; cursor.style.background = 'var(--accent)'; });
    });

    // Scroll reveal
    const revealEls = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver(entries => {
      entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); } });
    }, { threshold: 0.12 });
    revealEls.forEach(el => observer.observe(el));
  </script>
</body>
</html>
