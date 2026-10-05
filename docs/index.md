
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#080808">
  <title>D.I.V.I.D.E. — Classified Database</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;500;600;700&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --bg:        #080808;
      --red:       #cc0000;
      --red-hot:   #ff2a2a;
      --red-dim:   #8b0000;
      --red-dark:  #3a0000;
      --red-faint: #1a0000;
      --ink:       #c0c0c0;
      --ink-dim:   #777;
      --ink-faint: #444;
      --panel:     rgba(13, 13, 13, 0.86);
      --hero:      url('https://github.com/user-attachments/assets/f0f5e73b-c5f5-4b3d-b1ef-b560a87e3bc5');
      --mx: 50%;
      --my: 25%;
    }

    html { scroll-behavior: smooth; }

    body {
      background-color: var(--bg);
      color: var(--ink);
      font-family: 'Share Tech Mono', monospace;
      min-height: 100vh;
      overflow-x: hidden;
      position: relative;
    }

    a { color: inherit; }
    :focus-visible { outline: 2px solid var(--red-hot); outline-offset: 2px; }

    /* ══════════════════════════════════
       BACKGROUND LAYERS
    ══════════════════════════════════ */
    #rain { position: fixed; inset: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none; opacity: 0.55; }

    .bg-grid {
      position: fixed; inset: 0; z-index: 1; pointer-events: none;
      background-image:
        linear-gradient(rgba(204,0,0,0.055) 1px, transparent 1px),
        linear-gradient(90deg, rgba(204,0,0,0.055) 1px, transparent 1px);
      background-size: 48px 48px;
    }
    .bg-spot {
      position: fixed; inset: 0; z-index: 1; pointer-events: none;
      background-image:
        linear-gradient(rgba(255,42,42,0.55) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,42,42,0.55) 1px, transparent 1px);
      background-size: 48px 48px;
      -webkit-mask-image: radial-gradient(circle 260px at var(--mx) var(--my), #000 0%, transparent 100%);
              mask-image: radial-gradient(circle 260px at var(--mx) var(--my), #000 0%, transparent 100%);
      opacity: 0.55;
    }
    .bg-vignette {
      position: fixed; inset: 0; z-index: 2; pointer-events: none;
      background: radial-gradient(ellipse at 50% 30%, transparent 40%, rgba(0,0,0,0.75) 100%);
    }
    body::after {
      content: ''; position: fixed; inset: 0; z-index: 999; pointer-events: none;
      background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(255,255,255,0.012) 3px, rgba(255,255,255,0.012) 4px);
    }

    /* ══════════════════════════════════
       WARNING BAR + TICKER
    ══════════════════════════════════ */
    .warning-bar {
      background: repeating-linear-gradient(135deg, #8b0000 0 18px, #7a0000 18px 36px);
      color: #fff; text-align: center; padding: 7px 10px;
      font-size: 11px; letter-spacing: 3px; text-transform: uppercase;
      border-bottom: 1px solid #ff0000;
      position: relative; z-index: 100;
      text-shadow: 0 1px 2px rgba(0,0,0,0.6);
    }

    .ticker {
      position: relative; z-index: 100; overflow: hidden;
      background: #0a0000; border-bottom: 1px solid var(--red-dark);
      height: 28px; display: flex; align-items: center;
    }
    .ticker-label {
      flex-shrink: 0; height: 100%; display: flex; align-items: center; gap: 6px;
      padding: 0 14px; background: var(--red-dim); color: #fff;
      font-size: 10px; letter-spacing: 3px; text-transform: uppercase; z-index: 2;
    }
    .ticker-label::before { content: ''; width: 6px; height: 6px; border-radius: 50%; background: #fff; animation: blink 1.2s steps(2) infinite; }
    @keyframes blink { 50% { opacity: 0.15; } }
    .ticker-viewport { overflow: hidden; flex: 1; }
    .ticker-track { display: inline-flex; white-space: nowrap; animation: tick 70s linear infinite; }
    .ticker:hover .ticker-track { animation-play-state: paused; }
    .ticker-item { font-size: 10px; letter-spacing: 2px; color: #a06060; padding: 0 22px; text-transform: uppercase; }
    .ticker-item b { color: var(--red); font-weight: 400; }
    .ticker-item::after { content: '◆'; margin-left: 44px; color: var(--red-dark); }
    @keyframes tick { from { transform: translateX(0); } to { transform: translateX(-50%); } }

    /* ══════════════════════════════════
       LAYOUT
    ══════════════════════════════════ */
    .container { max-width: 1100px; margin: 0 auto; padding: 40px 20px 30px; position: relative; z-index: 10; }

    .reveal { opacity: 0; transform: translateY(18px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .reveal.in { opacity: 1; transform: none; }

    /* ══════════════════════════════════
       HEADER
    ══════════════════════════════════ */
    .header {
      border: 1px solid var(--red-dark);
      padding: 38px 34px 34px; margin-bottom: 26px; position: relative; overflow: hidden;
      background: linear-gradient(180deg, rgba(15,0,0,0.92) 0%, rgba(8,8,8,0.92) 100%);
      box-shadow: inset 0 0 80px rgba(139,0,0,0.08), 0 0 50px rgba(139,0,0,0.08);
    }
    .header::before {
      content: '// CLASSIFIED //';
      position: absolute; top: -10px; left: 20px;
      background: var(--bg); padding: 0 10px;
      color: var(--red-dim); font-size: 11px; letter-spacing: 3px;
    }
    .header::after {
      content: ''; position: absolute; top: 0; right: 0; width: 46px; height: 46px;
      border-top: 2px solid var(--red-dim); border-right: 2px solid var(--red-dim);
    }
    .header-line {
      position: absolute; left: 0; bottom: 0; width: 100%; height: 2px;
      background: linear-gradient(90deg, transparent, var(--red), #ff8a8a, var(--red), transparent);
      background-size: 200% 100%; animation: slide 5s linear infinite;
    }
    @keyframes slide { from { background-position: 0 0; } to { background-position: 200% 0; } }

    .header-inner { display: flex; align-items: center; justify-content: space-between; gap: 30px; }
    .header-text { min-width: 0; }

    .site-title {
      position: relative; display: inline-block;
      font-family: 'Rajdhani', sans-serif; font-size: 64px; font-weight: 700;
      color: var(--red); letter-spacing: 10px; line-height: 1;
      text-shadow: 0 0 24px rgba(200,0,0,0.45);
      margin-bottom: 14px; cursor: default;
    }
    .site-title::before, .site-title::after {
      content: attr(data-text); position: absolute; left: 0; top: 0; width: 100%;
      opacity: 0; pointer-events: none; text-shadow: none;
    }
    .site-title::before { color: #00e5ff; clip-path: inset(0 0 58% 0); }
    .site-title::after  { color: #ff0040; clip-path: inset(58% 0 0 0); }
    .site-title.glitch { animation: titleJitter 0.4s steps(2) 1; }
    .site-title.glitch::before { opacity: 0.85; animation: gl1 0.4s steps(3) 1; }
    .site-title.glitch::after  { opacity: 0.85; animation: gl2 0.4s steps(3) 1; }
    @keyframes titleJitter { 0% { transform: translate(0,0); } 30% { transform: translate(2px,-1px); } 60% { transform: translate(-2px,1px); } 100% { transform: translate(0,0); } }
    @keyframes gl1 { 0% { transform: translate(-6px,0); } 50% { transform: translate(5px,-2px); } 100% { transform: translate(-3px,1px); } }
    @keyframes gl2 { 0% { transform: translate(6px,0); } 50% { transform: translate(-5px,2px); } 100% { transform: translate(3px,-1px); } }

    .site-subtitle {
      font-size: 12px; color: var(--ink-dim); letter-spacing: 2px;
      text-transform: uppercase; margin-bottom: 20px; line-height: 1.8;
    }
    .site-subtitle .ini { color: var(--red); text-shadow: 0 0 8px rgba(200,0,0,0.5); }

    .clearance-badge {
      display: inline-flex; align-items: center; gap: 10px;
      border: 1px solid var(--red-dim); color: var(--red-dim);
      font-size: 10px; letter-spacing: 3px; padding: 6px 14px;
      text-transform: uppercase; background: rgba(139,0,0,0.06);
    }
    .clearance-badge::before {
      content: ''; width: 9px; height: 11px; border: 1.5px solid var(--red); border-radius: 2px 2px 1px 1px; position: relative;
      box-shadow: 0 -5px 0 -2px var(--red);
    }

    .seal { width: 150px; height: 150px; flex-shrink: 0; position: relative; }
    .seal svg { width: 100%; height: 100%; overflow: visible; }
    .seal .ring-a { transform-origin: 75px 75px; animation: spin 40s linear infinite; }
    .seal .ring-b { transform-origin: 75px 75px; animation: spin 26s linear infinite reverse; }
    .seal .sweep  { transform-origin: 75px 75px; animation: spin 5s linear infinite; }
    @keyframes spin { to { transform: rotate(360deg); } }
    .seal .core { animation: coreglow 3s ease-in-out infinite; }
    @keyframes coreglow { 0%,100% { opacity: 1; } 50% { opacity: 0.55; } }
    @media (max-width: 760px) { .seal { display: none; } .site-title { font-size: 40px; letter-spacing: 5px; } .header { padding: 30px 20px 26px; } }

    /* ══════════════════════════════════
       HERO
    ══════════════════════════════════ */
    .hero { position: relative; border: 100% solid #2a0000; margin-bottom: 100%; overflow: hidden; background: #050505; }
    .hero-image { width: 100%; max-height: 100%; object-fit: cover; object-position: center; display: block; filter: contrast(1.1) saturate(0.8); }
    .hero-g { position: absolute; inset: 0; background: var(--hero) center / cover no-repeat; mix-blend-mode: screen; opacity: 0; pointer-events: none; }
    .hero-g.g1 { filter: hue-rotate(170deg) saturate(2.2); animation: hg1 9s infinite steps(1); }
    .hero-g.g2 { filter: saturate(3) hue-rotate(-20deg); animation: hg2 9s infinite steps(1); animation-delay: 4.2s; }
    @keyframes hg1 { 0%,91% { opacity: 0; } 92% { opacity: 0.5; clip-path: inset(10% 0 72% 0); transform: translateX(-8px); } 93% { opacity: 0.5; clip-path: inset(58% 0 22% 0); transform: translateX(8px); } 94%,100% { opacity: 0; } }
    @keyframes hg2 { 0%,91% { opacity: 0; } 92% { opacity: 0.45; clip-path: inset(34% 0 50% 0); transform: translateX(7px); } 93% { opacity: 0.45; clip-path: inset(70% 0 8% 0); transform: translateX(-7px); } 94%,100% { opacity: 0; } }
    .hero-scan {
      position: absolute; left: 100%; right: 10%0; top: 100%; height: 100%; pointer-events: none;
      background: linear-gradient(180deg, transparent, rgba(255,42,42,0.14), transparent);
      animation: scanmove 6.5s linear infinite;
    }
    @keyframes scanmove { from { transform: translateY(0); } to { transform: translateY(calc(100% + 760px)); } }
    .hero::after { content: ''; position: absolute; inset: 0; pointer-events: none; background: linear-gradient(180deg, transparent 55%, rgba(8,8,8,0.9) 100%); }
    .hud-c { position: absolute; width: 30px; height: 30px; border: 2px solid rgba(255,42,42,0.75); z-index: 3; pointer-events: none; }
    .hud-c.a { top: 10px; left: 10px; border-right: none; border-bottom: none; }
    .hud-c.b { top: 10px; right: 10px; border-left: none; border-bottom: none; }
    .hud-c.c { bottom: 10px; left: 10px; border-right: none; border-top: none; }
    .hud-c.d { bottom: 10px; right: 10px; border-left: none; border-top: none; }
    .hud-t { position: absolute; z-index: 3; font-size: 10px; letter-spacing: 3px; color: rgba(255,120,120,0.85); text-shadow: 0 0 6px #000; pointer-events: none; text-transform: uppercase; }
    .hud-t.tl { top: 16px; left: 50px; }
    .hud-t.tr { top: 16px; right: 50px; }
    .hud-t.bl { bottom: 16px; left: 50px; }
    .hud-t.br { bottom: 16px; right: 50px; }
    .hud-t .rec { display: inline-block; width: 7px; height: 7px; border-radius: 50%; background: #ff2a2a; margin-right: 7px; animation: blink 1.3s steps(2) infinite; }
    @media (max-width: 100%) { .hud-t.bl, .hud-t.br { display: none; } }

    /* ══════════════════════════════════
       STATUS BAR
    ══════════════════════════════════ */
    .status-bar {
      display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center; gap: 10px 18px;
      padding: 11px 18px; background: var(--panel); border: 1px solid var(--red-faint);
      margin-bottom: 36px; font-size: 10px; color: #666; letter-spacing: 1.5px;
    }
    .status-bar .grp { display: inline-flex; align-items: center; gap: 8px; }
    .status-bar .hi { color: #999; }
    .status-dot { display: inline-block; width: 7px; height: 7px; background: var(--red); border-radius: 50%; box-shadow: 0 0 8px var(--red); animation: pulse 2s infinite; }
    @keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: 0.3; } }
    .tmeter { display: inline-flex; gap: 3px; margin-left: 6px; }
    .tmeter i { width: 6px; height: 12px; background: #2a1a1a; display: block; }
    .tmeter i.on { background: #ff6a00; box-shadow: 0 0 6px rgba(255,106,0,0.6); }
    .tmeter i.on.hot { background: var(--red); box-shadow: 0 0 6px rgba(204,0,0,0.7); }
    .status-sep { color: #2a0000; }
    @media (max-width: 760px) { .status-sep { display: none; } .status-bar { justify-content: flex-start; } }

    /* ══════════════════════════════════
       SECTIONS
    ══════════════════════════════════ */
    .section { margin-bottom: 44px; }
    .section-label {
      font-size: 10px; letter-spacing: 4px; color: var(--red-dim); text-transform: uppercase;
      margin-bottom: 14px; padding-bottom: 7px; border-bottom: 1px solid var(--red-faint);
      display: flex; justify-content: space-between; align-items: center; gap: 12px;
    }
    .section-label .aside { color: #3a2a2a; letter-spacing: 2px; font-size: 9px; }

    /* ══════════════════════════════════
       NAV
    ══════════════════════════════════ */
    .nav-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
    @media (max-width: 700px) { .nav-grid { grid-template-columns: 1fr; } }

    .nav-link {
      position: relative; display: flex; align-items: center; gap: 16px;
      padding: 18px 22px; background-color: rgba(13,13,13,0.88);
      border: 1px solid #1a1a1a; border-left: 3px solid var(--red-dark);
      color: #aaa; text-decoration: none; letter-spacing: 1px; overflow: hidden;
      transition: border-color 0.25s ease, color 0.25s ease, transform 0.25s ease, background-color 0.25s ease;
      --cx: 50%; --cy: 50%;
    }
    .nav-link::before {
      content: ''; position: absolute; inset: 0; pointer-events: none; opacity: 0; transition: opacity 0.25s ease;
      background: radial-gradient(220px circle at var(--cx) var(--cy), rgba(204,0,0,0.20), transparent 70%);
    }
    .nav-link::after {
      content: ''; position: absolute; left: 0; bottom: 0; height: 2px; width: 0;
      background: linear-gradient(90deg, var(--red), transparent); transition: width 0.35s ease;
    }
    .nav-link:hover, .nav-link:focus-visible { border-left-color: var(--red); border-color: var(--red-dark); color: #fff; transform: translateX(3px); background-color: rgba(20,4,4,0.92); }
    .nav-link:hover::before, .nav-link:focus-visible::before { opacity: 1; }
    .nav-link:hover::after, .nav-link:focus-visible::after { width: 100%; }

    .nav-link .link-id { color: var(--red-dark); font-size: 10px; min-width: 40px; flex-shrink: 0; transition: color 0.25s; }
    .nav-link:hover .link-id { color: var(--red); }
    .nav-ico { width: 26px; height: 26px; flex-shrink: 0; color: var(--red-dim); transition: color 0.25s, transform 0.25s, filter 0.25s; }
    .nav-ico svg { width: 100%; height: 100%; fill: none; stroke: currentColor; stroke-width: 1.5; stroke-linecap: round; stroke-linejoin: round; }
    .nav-link:hover .nav-ico { color: var(--red-hot); transform: scale(1.12); filter: drop-shadow(0 0 6px rgba(255,42,42,0.7)); }
    .nav-body { display: flex; flex-direction: column; gap: 4px; min-width: 0; flex: 1; position: relative; }
    .nav-title { font-size: 14px; letter-spacing: 1.5px; }
    .nav-desc { font-size: 10px; letter-spacing: 1.5px; color: #4a4a4a; text-transform: uppercase; transition: color 0.25s; }
    .nav-link:hover .nav-desc { color: #8a6a6a; }
    .nav-go { font-size: 16px; color: var(--red-dark); transition: color 0.25s, transform 0.25s; position: relative; }
    .nav-link:hover .nav-go { color: var(--red-hot); transform: translateX(5px); }

    /* ══════════════════════════════════
       DISTRIBUTION
    ══════════════════════════════════ */
    .dist-box { background: var(--panel); border: 1px solid #1a1a1a; padding: 22px; }
    .dist-bar { display: flex; height: 34px; gap: 3px; margin-bottom: 20px; }
    .seg {
      position: relative; flex: 0 0 auto; width: 0; min-width: 0; background: var(--sc); border: none; cursor: default;
      transition: width 1.2s cubic-bezier(.2,.8,.2,1), filter 0.2s, transform 0.2s; box-shadow: 0 0 14px color-mix(in srgb, var(--sc) 35%, transparent);
    }
    .seg.has { cursor: pointer; }
    .seg:hover { filter: brightness(1.3); transform: scaleY(1.18); z-index: 3; }
    .seg .tip {
      position: absolute; bottom: calc(100% + 10px); left: 50%; transform: translateX(-50%);
      background: #0d0d0d; border: 1px solid var(--sc); color: #ddd; padding: 7px 10px; white-space: nowrap;
      font-size: 10px; letter-spacing: 1.5px; opacity: 0; pointer-events: none; transition: opacity 0.15s; z-index: 5;
    }
    .seg:hover .tip { opacity: 1; }
    .dist-legend { display: grid; grid-template-columns: repeat(auto-fit, minmax(190px, 1fr)); gap: 8px; }
    .lg {
      display: flex; align-items: center; gap: 12px; padding: 10px 12px; background: rgba(0,0,0,0.35);
      border: 1px solid #161616; border-left: 3px solid var(--sc); font-size: 11px; letter-spacing: 1px; color: #999;
    }
    .lg .sw { width: 10px; height: 10px; background: var(--sc); flex-shrink: 0; box-shadow: 0 0 8px var(--sc); }
    .lg .n { margin-left: auto; font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 18px; color: #e6e6e6; }
    .lg.classified { --sc: #3a0000; color: #5a3a3a; }
    .lg.classified .n { color: #3a2020; letter-spacing: 2px; font-size: 13px; }
    .dist-note { margin-top: 14px; font-size: 10px; letter-spacing: 2px; color: #444; text-align: center; text-transform: uppercase; }

    /* ══════════════════════════════════
       DIVISIONS
    ══════════════════════════════════ */
    .div-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
    @media (max-width: 860px) { .div-grid { grid-template-columns: 1fr 1fr; } }
    @media (max-width: 520px) { .div-grid { grid-template-columns: 1fr; } }
    .div-card {
      position: relative; display: block; padding: 18px 18px 16px; text-decoration: none;
      background: rgba(13,13,13,0.88); border: 1px solid #1a1a1a; border-top: 3px solid var(--dc);
      overflow: hidden; transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
    }
    .div-card::before { content: ''; position: absolute; inset: 0; background: linear-gradient(160deg, color-mix(in srgb, var(--dc) 14%, transparent), transparent 55%); opacity: 0.5; transition: opacity 0.25s; pointer-events: none; }
    .div-card:hover { transform: translateY(-4px); border-color: color-mix(in srgb, var(--dc) 60%, #111); box-shadow: 0 10px 30px rgba(0,0,0,0.5), 0 0 24px color-mix(in srgb, var(--dc) 28%, transparent); }
    .div-card:hover::before { opacity: 1; }
    .div-abbr { font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 26px; letter-spacing: 3px; color: var(--dc); text-shadow: 0 0 14px color-mix(in srgb, var(--dc) 45%, transparent); position: relative; }
    .div-name { font-size: 12px; letter-spacing: 1.5px; color: #cfcfcf; margin: 4px 0 6px; position: relative; }
    .div-desc { font-size: 10px; letter-spacing: 1.5px; color: #555; text-transform: uppercase; position: relative; }

    /* ══════════════════════════════════
       FILE GALLERY
    ══════════════════════════════════ */
    .gal-controls { display: flex; flex-wrap: wrap; gap: 10px; align-items: center; margin-bottom: 14px; }
    .search {
      flex: 1 1 260px; display: flex; align-items: center; gap: 10px; background: var(--panel);
      border: 1px solid #222; padding: 0 14px; transition: border-color 0.2s;
    }
    .search:focus-within { border-color: var(--red); box-shadow: 0 0 18px rgba(204,0,0,0.15); }
    .search span { color: var(--red-dim); font-size: 12px; }
    .search input {
      flex: 1; background: transparent; border: none; outline: none; color: #ddd; padding: 12px 0;
      font-family: 'Share Tech Mono', monospace; font-size: 12px; letter-spacing: 2px; text-transform: uppercase;
    }
    .search input::placeholder { color: #444; }
    .rand-btn {
      background: transparent; border: 1px solid var(--red-dim); color: var(--red); cursor: pointer;
      font-family: 'Share Tech Mono', monospace; font-size: 10px; letter-spacing: 3px; padding: 12px 16px; text-transform: uppercase; transition: all 0.2s;
    }
    .rand-btn:hover { background: var(--red); color: #080808; box-shadow: 0 0 20px rgba(204,0,0,0.5); }

    .chips { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 16px; }
    .chip {
      display: inline-flex; align-items: center; gap: 8px; cursor: pointer; background: rgba(13,13,13,0.9);
      border: 1px solid #222; color: #888; padding: 7px 12px; font-size: 10px; letter-spacing: 2px; text-transform: uppercase;
      font-family: 'Share Tech Mono', monospace; transition: all 0.2s;
    }
    .chip i { width: 8px; height: 8px; background: var(--cc, #888); border-radius: 50%; box-shadow: 0 0 8px var(--cc, #888); }
    .chip:hover { border-color: var(--cc, #666); color: #ddd; }
    .chip.active { border-color: var(--cc, var(--red)); color: #fff; background: color-mix(in srgb, var(--cc, #cc0000) 14%, #0d0d0d); }

    .gal-count { font-size: 10px; letter-spacing: 2px; color: #555; margin-bottom: 12px; text-transform: uppercase; }
    .file-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(230px, 1fr)); gap: 10px; }
    .file-card {
      position: relative; display: block; text-decoration: none; padding: 16px 16px 14px;
      background: rgba(13,13,13,0.9); border: 1px solid #1a1a1a; border-left: 3px solid var(--tc); overflow: hidden;
      transition: transform 0.25s, box-shadow 0.25s, border-color 0.25s; animation: cardin 0.4s ease both;
    }
    @keyframes cardin { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: none; } }
    .file-card::before { content: ''; position: absolute; right: -30px; top: -30px; width: 100px; height: 100px; border-radius: 50%; background: radial-gradient(circle, color-mix(in srgb, var(--tc) 30%, transparent), transparent 70%); opacity: 0.45; transition: opacity 0.25s, transform 0.25s; }
    .file-card:hover { transform: translateY(-3px); border-color: color-mix(in srgb, var(--tc) 55%, #111); box-shadow: 0 8px 26px rgba(0,0,0,0.5), 0 0 22px color-mix(in srgb, var(--tc) 25%, transparent); }
    .file-card:hover::before { opacity: 1; transform: scale(1.3); }
    .fc-id { font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 22px; letter-spacing: 3px; color: var(--tc); text-shadow: 0 0 12px color-mix(in srgb, var(--tc) 40%, transparent); position: relative; }
    .fc-name { font-size: 12px; color: #d0d0d0; letter-spacing: 1px; margin: 4px 0 10px; line-height: 1.4; position: relative; min-height: 34px; }
    .fc-tier { display: inline-block; font-size: 9px; letter-spacing: 3px; color: var(--tc); border: 1px solid color-mix(in srgb, var(--tc) 45%, transparent); padding: 3px 8px; text-transform: uppercase; position: relative; }
    .file-card.omega { box-shadow: 0 0 20px rgba(255,255,255,0.05); }
    .empty { grid-column: 1 / -1; text-align: center; padding: 40px 10px; font-size: 11px; letter-spacing: 3px; color: #555; border: 1px dashed #222; text-transform: uppercase; }
    .gal-foot { margin-top: 14px; text-align: center; font-size: 10px; letter-spacing: 3px; color: #3a2a2a; text-transform: uppercase; }

    /* ══════════════════════════════════
       FOOTER
    ══════════════════════════════════ */
    .end-line { display: flex; align-items: center; gap: 14px; margin: 10px 0 22px; color: #3a1a1a; font-size: 10px; letter-spacing: 4px; text-transform: uppercase; }
    .end-line::before, .end-line::after { content: ''; flex: 1; height: 1px; background: linear-gradient(90deg, transparent, #2a0000, transparent); }

    .footer { border-top: 1px solid var(--red-faint); padding-top: 20px; font-size: 10px; color: #333; letter-spacing: 1px; line-height: 1.8; text-align: center; }
    .footer a { color: #555; text-decoration: none; }

    /* Boot overlay */
    .boot {
      position: fixed; inset: 0; z-index: 10000; background: #050000; color: #ff3a3a;
      display: flex; flex-direction: column; justify-content: center; padding: 0 8vw; font-size: 13px; letter-spacing: 2px; line-height: 2;
      transition: opacity 0.6s ease; cursor: pointer; text-shadow: 0 0 8px rgba(255,40,40,0.6);
    }
    .boot.out { opacity: 0; pointer-events: none; }
    .boot .skip { position: absolute; bottom: 24px; left: 0; right: 0; text-align: center; font-size: 10px; color: #6a2a2a; letter-spacing: 4px; text-shadow: none; }
    .boot .caret { display: inline-block; width: 9px; height: 15px; background: #ff3a3a; vertical-align: -2px; margin-left: 4px; animation: blink 0.7s steps(2) infinite; }

    @media (prefers-reduced-motion: reduce) {
      .ticker-track, .hero-g, .hero-scan, .header-line, .seal .ring-a, .seal .ring-b, .seal .sweep, .seal .core, .site-title.glitch, .file-card { animation: none !important; }
      .reveal { opacity: 1; transform: none; transition: none; }
      #rain { display: none; }
    }
  </style>
</head>
<body>

  <!-- BACKGROUND -->
  <canvas id="rain" aria-hidden="true"></canvas>
  <div class="bg-grid"></div>
  <div class="bg-spot"></div>
  <div class="bg-vignette"></div>

  <div class="warning-bar">
    ⚠ RESTRICTED ACCESS — AUTHORIZED PERSONNEL ONLY — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="ticker" aria-label="Live alerts">
    <div class="ticker-label">Live Alerts</div>
    <div class="ticker-viewport">
      <div class="ticker-track" id="tickerTrack"></div>
    </div>
  </div>

  <div class="container">

    <!-- HEADER -->
    <div class="header reveal">
      <div class="header-line"></div>
      <div class="header-inner">
        <div class="header-text">
          <div class="site-title" id="siteTitle" data-text="D.I.V.I.D.E.">D.I.V.I.D.E.</div>
          <div class="site-subtitle"><span class="ini">D</span>epartment for <span class="ini">I</span>nternal <span class="ini">V</span>igilance, <span class="ini">I</span>ntervention, <span class="ini">D</span>estruction, and <span class="ini">E</span>rasure</div>
          <div class="clearance-badge">Clearance Level 1+ Required</div>
        </div>
        <div class="seal" aria-hidden="true">
          <svg viewBox="0 0 150 150" xmlns="http://www.w3.org/2000/svg">
            <defs>
              <linearGradient id="sweepG" x1="0" y1="0" x2="1" y2="0">
                <stop offset="0%" stop-color="#ff2a2a" stop-opacity="0"/>
                <stop offset="100%" stop-color="#ff2a2a" stop-opacity="0.55"/>
              </linearGradient>
            </defs>
            <circle cx="75" cy="75" r="72" fill="none" stroke="#3a0000" stroke-width="1"/>
            <g class="ring-a"><circle cx="75" cy="75" r="64" fill="none" stroke="#8b0000" stroke-width="2" stroke-dasharray="3 7"/></g>
            <g class="ring-b"><circle cx="75" cy="75" r="52" fill="none" stroke="#cc0000" stroke-width="1" stroke-dasharray="14 6"/></g>
            <circle cx="75" cy="75" r="40" fill="rgba(15,0,0,0.8)" stroke="#5a0000" stroke-width="1"/>
            <g class="sweep"><path d="M75 75 L75 35 A40 40 0 0 1 110 55 Z" fill="url(#sweepG)"/></g>
            <line x1="75" y1="3" x2="75" y2="12" stroke="#8b0000" stroke-width="1.5"/>
            <line x1="75" y1="138" x2="75" y2="147" stroke="#8b0000" stroke-width="1.5"/>
            <line x1="3" y1="75" x2="12" y2="75" stroke="#8b0000" stroke-width="1.5"/>
            <line x1="138" y1="75" x2="147" y2="75" stroke="#8b0000" stroke-width="1.5"/>
            <text class="core" x="75" y="90" text-anchor="middle" font-family="Rajdhani, sans-serif" font-weight="700" font-size="44" fill="#cc0000">D</text>
          </svg>
        </div>
      </div>
    </div>

    <!-- HERO -->
    <div class="hero reveal">
      <img class="hero-image" src="https://github.com/user-attachments/assets/f0f5e73b-c5f5-4b3d-b1ef-b560a87e3bc5" alt="D.I.V.I.D.E. Header" />
      <div class="hero-g g1"></div>
      <div class="hero-g g2"></div>
      <div class="hero-scan"></div>
      <div class="hud-c a"></div><div class="hud-c b"></div><div class="hud-c c"></div><div class="hud-c d"></div>
      <div class="hud-t tl"><span class="rec"></span>FEED 01 — HEADER</div>
      <div class="hud-t tr">SECURE CHANNEL</div>
      <div class="hud-t bl" id="hudCoord">LAT --.---- / LON --.----</div>
      <div class="hud-t br">D.I.V.I.D.E. // INTERNAL</div>
    </div>

    <!-- STATUS -->
    <div class="status-bar reveal">
      <span class="grp"><span class="status-dot"></span><span class="hi">DATABASE ONLINE</span></span>
      <span class="status-sep">//</span>
      <span class="grp">ACTIVE ANOMALIES: <span class="hi" id="anomCount">97</span></span>
      <span class="status-sep">//</span>
      <span class="grp">THREAT STATUS: <span class="hi">ELEVATED</span>
        <span class="tmeter"><i class="on"></i><i class="on"></i><i class="on"></i><i class="on hot"></i><i></i></span>
      </span>
      <span class="status-sep">//</span>
      <span class="grp">UTC <span class="hi" id="clock">--:--:--</span></span>
      <span class="status-sep">//</span>
      <span class="grp">SESSION <span class="hi" id="sess">------</span></span>
    </div>

    <!-- DATABASE INDEX -->
    <div class="section reveal">
      <div class="section-label">// Database Index — Select File //</div>

      <div class="nav-grid">
        <a href="timeline.html" class="nav-link">
          <span class="link-id">01 //</span>
          <span class="nav-ico"><svg viewBox="0 0 24 24"><path d="M2 12h20"/><circle cx="6" cy="12" r="2"/><circle cx="12" cy="12" r="2"/><circle cx="18" cy="12" r="2"/><path d="M6 6v4M12 4v6M18 7v3"/></svg></span>
          <span class="nav-body"><span class="nav-title">Timeline of Events</span><span class="nav-desc">Chronology of recorded incidents</span></span>
          <span class="nav-go">→</span>
        </a>
        <a href="anomaly_reports.html" class="nav-link">
          <span class="link-id">02 //</span>
          <span class="nav-ico"><svg viewBox="0 0 24 24"><path d="M6 2h9l4 4v16H6z"/><path d="M15 2v4h4M9 11h6M9 15h6M9 19h4"/></svg></span>
          <span class="nav-body"><span class="nav-title">Anomaly Reports</span><span class="nav-desc">Full catalogue of LD files</span></span>
          <span class="nav-go">→</span>
        </a>
        <a href="anomaly_threatlevel.html" class="nav-link">
          <span class="link-id">03 //</span>
          <span class="nav-ico"><svg viewBox="0 0 24 24"><path d="M12 3l10 18H2z"/><path d="M12 10v5M12 18v.5"/></svg></span>
          <span class="nav-body"><span class="nav-title">Anomaly Threat Levels</span><span class="nav-desc">Tier classification index</span></span>
          <span class="nav-go">→</span>
        </a>
        <a href="personal.html" class="nav-link">
          <span class="link-id">04 //</span>
          <span class="nav-ico"><svg viewBox="0 0 24 24"><circle cx="12" cy="8" r="4"/><path d="M4 21c1-5 5-7 8-7s7 2 8 7"/></svg></span>
          <span class="nav-body"><span class="nav-title">Personnel Files</span><span class="nav-desc">Divisions, units and task forces</span></span>
          <span class="nav-go">→</span>
        </a>
        <a href="servant_cards.html" class="nav-link">
          <span class="link-id">05 //</span>
          <span class="nav-ico"><svg viewBox="0 0 24 24"><rect x="5" y="3" width="14" height="18" rx="2"/><path d="M12 8l3 4-3 4-3-4z"/></svg></span>
          <span class="nav-body"><span class="nav-title">Servant Cards</span><span class="nav-desc">SYS-01 card registry</span></span>
          <span class="nav-go">→</span>
        </a>
        <a href="black_streets.html" class="nav-link">
          <span class="link-id">06 //</span>
          <span class="nav-ico"><svg viewBox="0 0 24 24"><path d="M3 21V9l9-6 9 6v12"/><path d="M9 21v-7h6v7"/></svg></span>
          <span class="nav-body"><span class="nav-title">Black Streets</span><span class="nav-desc">Unsanctioned market records</span></span>
          <span class="nav-go">→</span>
        </a>
        <a href="doro_sightings.html" class="nav-link">
          <span class="link-id">07 //</span>
          <span class="nav-ico"><svg viewBox="0 0 24 24"><path d="M2 12s4-7 10-7 10 7 10 7-4 7-10 7S2 12 2 12z"/><circle cx="12" cy="12" r="3"/></svg></span>
          <span class="nav-body"><span class="nav-title">Doro Sightings</span><span class="nav-desc">Logged encounters with LD-002</span></span>
          <span class="nav-go">→</span>
        </a>
        <a href="notes_from_inside.html" class="nav-link">
          <span class="link-id">08 //</span>
          <span class="nav-ico"><svg viewBox="0 0 24 24"><path d="M4 4h16v13H8l-4 4z"/><path d="M8 9h8M8 13h5"/></svg></span>
          <span class="nav-body"><span class="nav-title">Notes from Inside</span><span class="nav-desc">Anonymous internal disclosures</span></span>
          <span class="nav-go">→</span>
        </a>
      </div>
    </div>

    <!-- DISTRIBUTION -->
    <div class="section reveal">
      <div class="section-label"><span>// Anomaly Distribution — By Tier //</span><span class="aside">CLICK A SEGMENT TO FILTER FILES</span></div>
      <div class="dist-box">
        <div class="dist-bar" id="distBar"></div>
        <div class="dist-legend" id="distLegend"></div>
        <div class="dist-note">Tier V / VI / VII entries are not publicly indexed</div>
      </div>
    </div>

    <!-- DIVISIONS -->
    <div class="section reveal">
      <div class="section-label"><span>// Divisions & Task Forces //</span><span class="aside">PERSONNEL INDEX</span></div>
      <div class="div-grid">
        <a class="div-card" style="--dc:#4fc3f7" href="researchers.html"><div class="div-abbr">RES</div><div class="div-name">Research Division</div><div class="div-desc">Anomalous research and correlation</div></a>
        <a class="div-card" style="--dc:#4caf50" href="guards.html"><div class="div-abbr">SSO</div><div class="div-name">Security Personnel</div><div class="div-desc">Facility security forces</div></a>
        <a class="div-card" style="--dc:#b04bd0" href="special-individuals.html"><div class="div-abbr">S.I.</div><div class="div-name">Special Individuals</div><div class="div-desc">Level 7 — restricted</div></a>
        <a class="div-card" style="--dc:#9e9e9e" href="at-class.html"><div class="div-abbr">AT</div><div class="div-name">AT-Class</div><div class="div-desc">Expendable designation</div></a>
        <a class="div-card" style="--dc:#5aa9ff" href="apa.html"><div class="div-abbr">A.P.A.</div><div class="div-name">A.P.A. Task Force</div><div class="div-desc">Overview and unit profiles</div></a>
        <a class="div-card" style="--dc:#66bb6a" href="echo9.html"><div class="div-abbr">ECHO-9</div><div class="div-name">Phantom Sweepers</div><div class="div-desc">Sweep and cleanup unit</div></a>
        <a class="div-card" style="--dc:#f44336" href="viking.html"><div class="div-abbr">B.E.R.S.E.R.K.</div><div class="div-name">B.E.R.S.E.R.K.</div><div class="div-desc">Heavy response unit</div></a>
        <a class="div-card" style="--dc:#9c9cff" href="phantom.html"><div class="div-abbr">PHANTOM</div><div class="div-name">Phantom Division</div><div class="div-desc">Covert operations</div></a>
        <a class="div-card" style="--dc:#00bcd4" href="SORAD.html"><div class="div-abbr">SORAD</div><div class="div-name">Special Oceanic Retrieval</div><div class="div-desc">Deep-water recovery</div></a>
      </div>
    </div>

    <!-- FEATURED FILES -->
    <div class="section reveal" id="files">
      <div class="section-label"><span>// Featured Anomaly Files //</span><span class="aside" id="indexedCount">-- FILES INDEXED</span></div>

      <div class="gal-controls">
        <label class="search"><span>⌕</span><input id="q" type="text" autocomplete="off" spellcheck="false" placeholder="SEARCH — LD-### OR NAME" aria-label="Search anomaly files" /></label>
        <button class="rand-btn" id="randBtn" type="button">▶ Open random file</button>
      </div>
      <div class="chips" id="chips"></div>
      <div class="gal-count" id="galCount"></div>
      <div class="file-grid" id="fileGrid"></div>
      <div class="gal-foot">Remaining files are still being processed for declassification</div>
    </div>

    <div class="end-line">End of index</div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

  <script>
    (function () {
      var reduce = !!(window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches);
      var root = document.documentElement;

      /* ══ DATA ══ */
      var TIERS = {
        '0':        { label: 'Tier 0',    short: '0',        color: '#9e9e9e', n: 2 },
        '1':        { label: 'Tier I',    short: 'I',        color: '#4fc3f7', n: 8 },
        '2':        { label: 'Tier II',   short: 'II',       color: '#4caf50', n: 33 },
        '3':        { label: 'Tier III',  short: 'III',      color: '#ffd600', n: 29 },
        '4':        { label: 'Tier IV',   short: 'IV',       color: '#ff9800', n: 14 },
        'omega':    { label: 'Omega',     short: 'Ω',        color: '#f2f2f2', n: 1 },
        'redacted': { label: 'Redacted',  short: 'REDACTED', color: '#ff69b4', n: 10 }
      };
      var TIER_ORDER = ['0', '1', '2', '3', '4', 'omega', 'redacted'];

      var FILES = [
        { id: '000', name: 'D', tier: 'omega' },
        { id: '001', name: 'Lucas Devil', tier: 'redacted' },
        { id: '002', name: 'Doro', tier: 'redacted' },
        { id: '003', name: 'The Drowned Girl', tier: '3' },
        { id: '007', name: 'The Visitor\u2019s Folklore', tier: '2' },
        { id: '013', name: 'The Insect Matron', tier: '4' },
        { id: '014', name: 'The Knife That Loves Too Deeply', tier: '3' },
        { id: '015', name: '[REDACTED]', tier: 'redacted' },
        { id: '016', name: 'Andy\u2019s Revolver', tier: '2' },
        { id: '044', name: 'The Veiled Judgment', tier: 'redacted' },
        { id: '050', name: 'The Calamity Empress', tier: '4' },
        { id: '057', name: 'Egg of Concepts', tier: '2' },
        { id: '066', name: 'The Silent Executioner', tier: 'redacted' },
        { id: '068', name: 'The Absolute Zero Blade', tier: '4' },
        { id: '069', name: 'The Latex Lament', tier: '4' },
        { id: '072', name: 'The Finger Maiden', tier: '2' },
        { id: '079', name: 'The Crimson Witness', tier: 'redacted' },
        { id: '080', name: 'The Marionette', tier: '2' },
        { id: '082', name: 'The Mist Hound', tier: '4' },
        { id: '088', name: 'The Mercy of Life', tier: 'redacted' },
        { id: '089', name: 'The Missing', tier: '3' },
        { id: '091', name: 'I Love a Man in Uniform', tier: '3' },
        { id: '093', name: 'Don\u2019t Fear the Reaper', tier: '2' },
        { id: '095', name: 'Scythe of Sync', tier: '3' }
      ];

      var ALERTS = [
        ['LD-013', 'Thermal suppression — active'],
        ['LD-068', 'Retrieval operation — ongoing'],
        ['LD-066', 'Cooperative containment — if she asks to leave, open the door'],
        ['LD-082', 'Exclusion zone — unchanged'],
        ['LD-079', 'Uncontained by choice'],
        ['LD-000', 'Do not engage'],
        ['LD-095', 'Further testing has been prohibited'],
        ['PROTOCOL WINTER\u2019S END', 'Authorized — not enacted'],
        ['PROTOCOL BUTTERFLY', 'Standby'],
        ['\u0395\u03A4\u0394', 'Something is missing from the story']
      ];

      /* ══ TICKER ══ */
      (function () {
        var track = document.getElementById('tickerTrack');
        var html = '';
        for (var r = 0; r < 2; r++) {
          ALERTS.forEach(function (a) { html += '<span class="ticker-item"><b>' + a[0] + '</b> &nbsp;' + a[1] + '</span>'; });
        }
        track.innerHTML = html;
      })();

      /* ══ REVEAL ══ */
      (function () {
        var els = document.querySelectorAll('.reveal');
        if (!('IntersectionObserver' in window)) { els.forEach(function (e) { e.classList.add('in'); }); return; }
        var io = new IntersectionObserver(function (entries) {
          entries.forEach(function (en) { if (en.isIntersecting) { en.target.classList.add('in'); io.unobserve(en.target); } });
        }, { threshold: 0.08 });
        els.forEach(function (e) { io.observe(e); });
      })();

      /* ══ CLOCK / SESSION / COUNT-UP / COORDS ══ */
      (function () {
        var clock = document.getElementById('clock');
        function tick() {
          var d = new Date();
          function z(n) { return (n < 10 ? '0' : '') + n; }
          clock.textContent = z(d.getUTCHours()) + ':' + z(d.getUTCMinutes()) + ':' + z(d.getUTCSeconds());
        }
        tick(); setInterval(tick, 1000);

        var s = ''; for (var i = 0; i < 6; i++) s += '0123456789ABCDEF'[(Math.random() * 16) | 0];
        document.getElementById('sess').textContent = s;

        var el = document.getElementById('anomCount');
        if (!reduce) {
          var target = 97, start = performance.now(), dur = 1600;
          el.textContent = '0';
          (function step(now) {
            var t = Math.min(1, (now - start) / dur);
            el.textContent = Math.round(target * (1 - Math.pow(1 - t, 3)));
            if (t < 1) requestAnimationFrame(step);
          })(start);
        }

        var coord = document.getElementById('hudCoord');
        if (!reduce) {
          setInterval(function () {
            var lat = (Math.random() * 90).toFixed(4), lon = (Math.random() * 180).toFixed(4);
            coord.textContent = 'LAT ' + lat + ' / LON ' + lon;
          }, 900);
        }
      })();

      /* ══ TITLE GLITCH ══ */
      (function () {
        var t = document.getElementById('siteTitle');
        function fire() {
          if (reduce) return;
          t.classList.add('glitch');
          setTimeout(function () { t.classList.remove('glitch'); }, 420);
        }
        t.addEventListener('mouseenter', fire);
        (function loop() { setTimeout(function () { fire(); loop(); }, 4000 + Math.random() * 5000); })();
        setTimeout(fire, 1200);
      })();

      /* ══ CURSOR SPOTLIGHT + NAV GLOW ══ */
      (function () {
        var raf = null, px = 0, py = 0;
        window.addEventListener('pointermove', function (e) {
          px = e.clientX; py = e.clientY;
          if (raf) return;
          raf = requestAnimationFrame(function () {
            raf = null;
            root.style.setProperty('--mx', px + 'px');
            root.style.setProperty('--my', py + 'px');
          });
        }, { passive: true });

        document.querySelectorAll('.nav-link').forEach(function (a) {
          a.addEventListener('pointermove', function (e) {
            var r = a.getBoundingClientRect();
            a.style.setProperty('--cx', (e.clientX - r.left) + 'px');
            a.style.setProperty('--cy', (e.clientY - r.top) + 'px');
          });
        });
      })();

      /* ══ DISTRIBUTION ══ */
      var state = { filter: 'all', q: '' };
      var distBar = document.getElementById('distBar');
      var distLegend = document.getElementById('distLegend');
      var total = 0; TIER_ORDER.forEach(function (k) { total += TIERS[k].n; });

      function publishedCount(k) { return FILES.filter(function (f) { return f.tier === k; }).length; }

      (function () {
        var segs = [];
        TIER_ORDER.forEach(function (k) {
          var T = TIERS[k], pub = publishedCount(k);
          var seg = document.createElement('button');
          seg.type = 'button';
          seg.className = 'seg' + (pub ? ' has' : '');
          seg.style.setProperty('--sc', T.color);
          seg.setAttribute('aria-label', T.label + ': ' + T.n + ' anomalies');
          seg.innerHTML = '<span class="tip">' + T.label.toUpperCase() + ' — ' + T.n + ' ANOMALIES — ' + pub + ' PUBLISHED</span>';
          if (pub) seg.addEventListener('click', function () { setFilter(k); document.getElementById('files').scrollIntoView({ behavior: 'smooth', block: 'start' }); });
          distBar.appendChild(seg); segs.push({ el: seg, n: T.n });

          var lg = document.createElement('div');
          lg.className = 'lg'; lg.style.setProperty('--sc', T.color);
          lg.innerHTML = '<span class="sw"></span><span>' + T.label.toUpperCase() + '</span><span class="n">' + T.n + '</span>';
          distLegend.appendChild(lg);
        });
        var cl = document.createElement('div');
        cl.className = 'lg classified';
        cl.innerHTML = '<span class="sw"></span><span>TIER V / VI / VII</span><span class="n">[CLASSIFIED]</span>';
        distLegend.appendChild(cl);

        function size() {
          segs.forEach(function (s) { s.el.style.width = Math.max(10, (s.n / total) * 100) + '%'; s.el.style.flexBasis = 'auto'; });
        }
        if ('IntersectionObserver' in window && !reduce) {
          var io = new IntersectionObserver(function (en) { if (en[0].isIntersecting) { size(); io.disconnect(); } }, { threshold: 0.3 });
          io.observe(distBar);
        } else { size(); }
      })();

      /* ══ FILE GALLERY ══ */
      var grid = document.getElementById('fileGrid');
      var chipsEl = document.getElementById('chips');
      var countEl = document.getElementById('galCount');
      var qEl = document.getElementById('q');
      document.getElementById('indexedCount').textContent = FILES.length + ' FILES INDEXED';

      function buildChips() {
        chipsEl.innerHTML = '';
        var keys = ['all'].concat(['omega', 'redacted', '4', '3', '2'].filter(function (k) { return publishedCount(k) > 0; }));
        keys.forEach(function (k) {
          var b = document.createElement('button');
          b.type = 'button'; b.className = 'chip' + (state.filter === k ? ' active' : '');
          var c = k === 'all' ? '#cc0000' : TIERS[k].color;
          b.style.setProperty('--cc', c);
          var label = k === 'all' ? 'All files' : TIERS[k].short === 'REDACTED' ? 'Redacted' : (k === 'omega' ? 'Omega' : 'Tier ' + TIERS[k].short);
          b.innerHTML = '<i></i>' + label;
          b.addEventListener('click', function () { setFilter(k); });
          chipsEl.appendChild(b);
        });
      }

      function render() {
        var q = state.q.trim().toLowerCase();
        var list = FILES.filter(function (f) {
          if (state.filter !== 'all' && f.tier !== state.filter) return false;
          if (!q) return true;
          return ('ld-' + f.id).indexOf(q) > -1 || f.id.indexOf(q) > -1 || f.name.toLowerCase().indexOf(q) > -1;
        });
        grid.innerHTML = '';
        if (!list.length) {
          grid.innerHTML = '<div class="empty">No files match this query</div>';
        } else {
          list.forEach(function (f, i) {
            var T = TIERS[f.tier];
            var a = document.createElement('a');
            a.className = 'file-card' + (f.tier === 'omega' ? ' omega' : '');
            a.href = 'LD-' + f.id + '.html';
            a.style.setProperty('--tc', T.color);
            a.style.animationDelay = Math.min(i * 25, 400) + 'ms';
            a.innerHTML = '<div class="fc-id">LD-' + f.id + '</div><div class="fc-name">' + f.name + '</div><span class="fc-tier">' + (f.tier === 'omega' ? '\u03A9-Class' : T.label) + '</span>';
            grid.appendChild(a);
          });
        }
        countEl.textContent = 'Showing ' + list.length + ' of ' + FILES.length + ' indexed files';
      }

      function setFilter(k) { state.filter = k; buildChips(); render(); }

      qEl.addEventListener('input', function () { state.q = qEl.value; render(); });
      document.getElementById('randBtn').addEventListener('click', function () {
        var f = FILES[(Math.random() * FILES.length) | 0];
        window.location.href = 'LD-' + f.id + '.html';
      });
      window.addEventListener('keydown', function (e) {
        if (e.key === '/' && document.activeElement !== qEl) { e.preventDefault(); qEl.focus(); document.getElementById('files').scrollIntoView({ behavior: 'smooth' }); }
      });

      buildChips(); render();

      /* ══ DATA RAIN ══ */
      (function () {
        if (reduce) return;
        var cv = document.getElementById('rain');
        var ctx = cv.getContext('2d');
        var W, H, cols, drops, fs = 16;
        var GLYPHS = '01\u2588\u2593ABCDEF0123456789'.split('');
        var ETD = ['\u0395', '\u03A4', '\u0394'];
        var last = 0;

        function resize() {
          W = cv.width = window.innerWidth; H = cv.height = window.innerHeight;
          cols = Math.ceil(W / fs);
          drops = [];
          for (var i = 0; i < cols; i++) drops.push({ y: Math.random() * -H / fs, sp: 0.15 + Math.random() * 0.4, etd: -1 });
          ctx.fillStyle = '#080808'; ctx.fillRect(0, 0, W, H);
        }
        resize();
        window.addEventListener('resize', resize);

        function frame(t) {
          requestAnimationFrame(frame);
          if (t - last < 55) return;
          last = t;
          ctx.fillStyle = 'rgba(8,8,8,0.12)';
          ctx.fillRect(0, 0, W, H);
          ctx.font = fs + 'px "Share Tech Mono", monospace';
          for (var i = 0; i < cols; i++) {
            var d = drops[i];
            var ch;
            if (d.etd >= 0) { ch = ETD[d.etd]; d.etd = d.etd < 2 ? d.etd + 1 : -1; ctx.fillStyle = 'rgba(255,60,60,0.95)'; }
            else {
              ch = GLYPHS[(Math.random() * GLYPHS.length) | 0];
              if (Math.random() < 0.0025) { d.etd = 0; ch = ETD[0]; d.etd = 1; ctx.fillStyle = 'rgba(255,60,60,0.95)'; }
              else ctx.fillStyle = Math.random() < 0.06 ? 'rgba(255,70,70,0.6)' : 'rgba(150,10,10,0.38)';
            }
            ctx.fillText(ch, i * fs, d.y * fs);
            d.y += d.sp * 3;
            if (d.y * fs > H && Math.random() > 0.975) { d.y = 0; d.sp = 0.15 + Math.random() * 0.4; }
          }
        }
        requestAnimationFrame(frame);
      })();

      /* ══ BOOT SEQUENCE (once per session) ══ */
      (function () {
        if (reduce) return;
        var seen = false;
        try { seen = sessionStorage.getItem('dvdBoot') === '1'; } catch (e) {}
        if (seen) return;

        var LINES = [
          'D.I.V.I.D.E. SECURE TERMINAL',
          '> ESTABLISHING ENCRYPTED CHANNEL ............ OK',
          '> AUTHENTICATING OPERATOR ................... OK',
          '> CLEARANCE LEVEL 1 CONFIRMED',
          '> INDEXING ANOMALY RECORDS .................. 97',
          '> THREAT STATUS ............................. ELEVATED',
          '> WELCOME, OPERATOR.'
        ];
        var boot = document.createElement('div');
        boot.className = 'boot';
        boot.innerHTML = '<div id="bootText"></div><div class="skip">[ CLICK OR PRESS ANY KEY TO SKIP ]</div>';
        document.body.appendChild(boot);
        var out = boot.querySelector('#bootText');
        var done = false, li = 0, ci = 0, cur = '';

        function finish() {
          if (done) return; done = true;
          try { sessionStorage.setItem('dvdBoot', '1'); } catch (e) {}
          boot.classList.add('out');
          setTimeout(function () { boot.remove(); }, 700);
        }
        boot.addEventListener('click', finish);
        window.addEventListener('keydown', finish, { once: true });

        function type() {
          if (done) return;
          if (li >= LINES.length) { setTimeout(finish, 450); return; }
          var line = LINES[li];
          if (ci <= line.length) {
            out.innerHTML = cur + line.slice(0, ci) + '<span class="caret"></span>';
            ci++;
            setTimeout(type, 9);
          } else {
            cur += line + '<br>'; li++; ci = 0;
            setTimeout(type, 110);
          }
        }
        type();
      })();
    })();
  </script>

</body>
</html>
