
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#080808">
  <title>D.I.V.I.D.E. — Anomaly Reports</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;500;600;700&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --bg: #080808; --red: #cc0000; --red-hot: #ff2a2a; --red-dim: #8b0000; --red-dark: #3a0000; --red-faint: #1a0000;
      --panel: rgba(13,13,13,0.88);
      --mx: 50%; --my: 20%;
    }

    html { scroll-behavior: smooth; }

    body {
      background-color: var(--bg); color: #c0c0c0;
      font-family: 'Share Tech Mono', monospace; min-height: 100vh; overflow-x: hidden; position: relative;
    }
    a { color: inherit; }
    :focus-visible { outline: 2px solid var(--red-hot); outline-offset: 2px; }

    /* ══ BACKGROUND ══ */
    #rain { position: fixed; inset: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none; opacity: 0.45; }
    .bg-grid { position: fixed; inset: 0; z-index: 1; pointer-events: none; background-image: linear-gradient(rgba(204,0,0,0.05) 1px, transparent 1px), linear-gradient(90deg, rgba(204,0,0,0.05) 1px, transparent 1px); background-size: 48px 48px; }
    .bg-spot { position: fixed; inset: 0; z-index: 1; pointer-events: none; opacity: 0.55; background-image: linear-gradient(rgba(255,42,42,0.55) 1px, transparent 1px), linear-gradient(90deg, rgba(255,42,42,0.55) 1px, transparent 1px); background-size: 48px 48px; -webkit-mask-image: radial-gradient(circle 240px at var(--mx) var(--my), #000 0%, transparent 100%); mask-image: radial-gradient(circle 240px at var(--mx) var(--my), #000 0%, transparent 100%); }
    .bg-vignette { position: fixed; inset: 0; z-index: 2; pointer-events: none; background: radial-gradient(ellipse at 50% 30%, transparent 40%, rgba(0,0,0,0.78) 100%); }
    body::after { content: ''; position: fixed; inset: 0; z-index: 999; pointer-events: none; background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(255,255,255,0.012) 3px, rgba(255,255,255,0.012) 4px); }

    /* ══ TOP BARS ══ */
    .warning-bar {
      background: repeating-linear-gradient(135deg, #8b0000 0 18px, #7a0000 18px 36px);
      color: #fff; text-align: center; padding: 7px 10px; font-size: 11px; letter-spacing: 3px; text-transform: uppercase;
      border-bottom: 1px solid #ff0000; position: relative; z-index: 100; text-shadow: 0 1px 2px rgba(0,0,0,0.6);
    }
    .ticker { position: relative; z-index: 100; overflow: hidden; background: #0a0000; border-bottom: 1px solid var(--red-dark); height: 28px; display: flex; align-items: center; }
    .ticker-label { flex-shrink: 0; height: 100%; display: flex; align-items: center; gap: 6px; padding: 0 14px; background: var(--red-dim); color: #fff; font-size: 10px; letter-spacing: 3px; text-transform: uppercase; z-index: 2; }
    .ticker-label::before { content: ''; width: 6px; height: 6px; border-radius: 50%; background: #fff; animation: blink 1.2s steps(2) infinite; }
    @keyframes blink { 50% { opacity: 0.15; } }
    .ticker-viewport { overflow: hidden; flex: 1; }
    .ticker-track { display: inline-flex; white-space: nowrap; animation: tick 90s linear infinite; }
    .ticker:hover .ticker-track { animation-play-state: paused; }
    .ticker-item { font-size: 10px; letter-spacing: 2px; color: #a06060; padding: 0 22px; text-transform: uppercase; text-decoration: none; transition: color 0.2s; }
    .ticker-item b { color: var(--red); font-weight: 400; margin-right: 6px; }
    .ticker-item:hover { color: #fff; }
    .ticker-item::after { content: '◆'; margin-left: 44px; color: var(--red-dark); }
    @keyframes tick { from { transform: translateX(0); } to { transform: translateX(-50%); } }

    .container { max-width: 1100px; margin: 0 auto; padding: 36px 20px 30px; position: relative; z-index: 10; }

    .back-link { display: inline-flex; align-items: center; gap: 8px; color: #666; text-decoration: none; font-size: 11px; letter-spacing: 2px; margin-bottom: 20px; transition: color 0.2s, gap 0.2s; }
    .back-link:hover { color: var(--red-hot); gap: 14px; }

    .reveal { opacity: 0; transform: translateY(16px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .reveal.in { opacity: 1; transform: none; }

    /* ══ HEADER ══ */
    .header {
      border: 1px solid var(--red-dark); padding: 34px 32px 30px; margin-bottom: 22px; position: relative; overflow: hidden;
      background: linear-gradient(180deg, rgba(15,0,0,0.92) 0%, rgba(8,8,8,0.92) 100%);
      box-shadow: inset 0 0 80px rgba(139,0,0,0.08), 0 0 50px rgba(139,0,0,0.08);
    }
    .header::before { content: '// CLASSIFIED //'; position: absolute; top: -10px; left: 20px; background: var(--bg); padding: 0 10px; color: var(--red-dim); font-size: 11px; letter-spacing: 3px; }
    .header::after { content: ''; position: absolute; top: 0; right: 0; width: 44px; height: 44px; border-top: 2px solid var(--red-dim); border-right: 2px solid var(--red-dim); }
    .header-line { position: absolute; left: 0; bottom: 0; width: 100%; height: 2px; background: linear-gradient(90deg, transparent, var(--red), #ff8a8a, var(--red), transparent); background-size: 200% 100%; animation: slide 5s linear infinite; }
    @keyframes slide { from { background-position: 0 0; } to { background-position: 200% 0; } }
    .header-inner { display: flex; align-items: center; justify-content: space-between; gap: 28px; }

    .site-title { position: relative; display: inline-block; font-family: 'Rajdhani', sans-serif; font-size: 58px; font-weight: 700; color: var(--red); letter-spacing: 8px; line-height: 1; text-shadow: 0 0 24px rgba(200,0,0,0.45); margin-bottom: 12px; cursor: default; }
    .site-title::before, .site-title::after { content: attr(data-text); position: absolute; left: 0; top: 0; width: 100%; opacity: 0; pointer-events: none; text-shadow: none; }
    .site-title::before { color: #00e5ff; clip-path: inset(0 0 58% 0); }
    .site-title::after { color: #ff0040; clip-path: inset(58% 0 0 0); }
    .site-title.glitch { animation: tj 0.4s steps(2) 1; }
    .site-title.glitch::before { opacity: 0.85; animation: g1 0.4s steps(3) 1; }
    .site-title.glitch::after { opacity: 0.85; animation: g2 0.4s steps(3) 1; }
    @keyframes tj { 0% { transform: translate(0,0); } 30% { transform: translate(2px,-1px); } 60% { transform: translate(-2px,1px); } 100% { transform: translate(0,0); } }
    @keyframes g1 { 0% { transform: translate(-6px,0); } 50% { transform: translate(5px,-2px); } 100% { transform: translate(-3px,1px); } }
    @keyframes g2 { 0% { transform: translate(6px,0); } 50% { transform: translate(-5px,2px); } 100% { transform: translate(3px,-1px); } }

    .site-subtitle { font-size: 12px; color: #666; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 18px; }
    .clearance-badge { display: inline-flex; align-items: center; gap: 10px; border: 1px solid var(--red-dim); color: var(--red-dim); font-size: 10px; letter-spacing: 3px; padding: 6px 14px; text-transform: uppercase; background: rgba(139,0,0,0.06); }
    .clearance-badge::before { content: ''; width: 9px; height: 11px; border: 1.5px solid var(--red); border-radius: 2px 2px 1px 1px; box-shadow: 0 -5px 0 -2px var(--red); }

    .donut-wrap { width: 170px; height: 170px; flex-shrink: 0; position: relative; }
    .donut-wrap svg { width: 100%; height: 100%; overflow: visible; }
    .donut-seg { transition: stroke-dasharray 1.4s cubic-bezier(.2,.8,.2,1); }
    .donut-sweep { transform-origin: 85px 85px; animation: spin 6s linear infinite; }
    @keyframes spin { to { transform: rotate(360deg); } }
    .donut-num { position: absolute; inset: 0; display: flex; flex-direction: column; align-items: center; justify-content: center; pointer-events: none; }
    .donut-num b { font-family: 'Rajdhani', sans-serif; font-size: 40px; font-weight: 700; color: #eee; line-height: 1; text-shadow: 0 0 18px rgba(204,0,0,0.6); }
    .donut-num span { font-size: 8px; letter-spacing: 3px; color: #666; margin-top: 2px; }
    @media (max-width: 760px) { .donut-wrap { display: none; } .site-title { font-size: 36px; letter-spacing: 4px; } .header { padding: 28px 18px 24px; } }

    /* ══ STATUS ══ */
    .status-bar { display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center; gap: 10px 18px; padding: 11px 18px; background: var(--panel); border: 1px solid var(--red-faint); margin-bottom: 22px; font-size: 10px; color: #666; letter-spacing: 1.5px; }
    .status-bar .grp { display: inline-flex; align-items: center; gap: 8px; }
    .status-bar .hi { color: #aaa; }
    .status-dot { display: inline-block; width: 7px; height: 7px; background: var(--red); border-radius: 50%; margin-right: 0; box-shadow: 0 0 8px var(--red); animation: pulse 2s infinite; }
    @keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: 0.3; } }
    .status-sep { color: #2a0000; }
    @media (max-width: 760px) { .status-sep { display: none; } .status-bar { justify-content: flex-start; } }

    /* ══ LEGEND / FILTER CHIPS ══ */
    .legend { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 18px; padding: 14px; background: var(--panel); border: 1px solid #1a1a1a; }
    .legend-item {
      display: flex; align-items: center; gap: 8px; font-size: 10px; letter-spacing: 1.5px; padding: 6px 12px;
      border: 1px solid #1c1c1c; background: rgba(0,0,0,0.35); cursor: pointer; user-select: none;
      transition: border-color 0.2s, background 0.2s, transform 0.2s, color 0.2s; color: #999; position: relative;
    }
    .legend-item:hover { border-color: var(--cc); color: #fff; transform: translateY(-2px); }
    .legend-item.active { border-color: var(--cc); background: color-mix(in srgb, var(--cc) 16%, #0d0d0d); color: #fff; box-shadow: 0 0 16px color-mix(in srgb, var(--cc) 35%, transparent); }
    .legend-item.empty { opacity: 0.45; }
    .legend-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; box-shadow: 0 0 8px currentColor; }
    .legend-count { font-family: 'Rajdhani', sans-serif; font-size: 14px; font-weight: 700; color: #ddd; margin-left: 2px; }
    .legend-item.empty .legend-count { color: #555; }

    .dot-0 { background: #8a8a8a; color: #8a8a8a; } .dot-1 { background: #4fc3f7; color: #4fc3f7; } .dot-2 { background: #4caf50; color: #4caf50; }
    .dot-3 { background: #ffd600; color: #ffd600; } .dot-4 { background: #ff6a1a; color: #ff6a1a; } .dot-5 { background: #f44336; color: #f44336; }
    .dot-6 { background: #b04bd0; color: #b04bd0; } .dot-7 { background: #e020e0; color: #e020e0; } .dot-omega { background: #fff; color: #fff; }
    .dot-redacted { background: #ff69b4; color: #ff69b4; }

    .t0 { --tc: #8a8a8a; } .t1 { --tc: #4fc3f7; } .t2 { --tc: #4caf50; } .t3 { --tc: #ffd600; } .t4 { --tc: #ff6a1a; }
    .t5 { --tc: #f44336; } .t6 { --tc: #b04bd0; } .t7 { --tc: #e020e0; } .tomega { --tc: #ffffff; } .tredacted { --tc: #ff69b4; }

    /* ══ CONTROLS ══ */
    .controls { display: flex; flex-wrap: wrap; gap: 10px; align-items: stretch; margin-bottom: 12px; }
    .search { flex: 1 1 280px; display: flex; align-items: center; gap: 10px; background: var(--panel); border: 1px solid #1a0000; border-left: 3px solid var(--red-dim); padding: 0 14px; transition: border-color 0.2s, box-shadow 0.2s; }
    .search:focus-within { border-color: var(--red); box-shadow: 0 0 22px rgba(204,0,0,0.18); }
    .search .ico { color: var(--red-dim); font-size: 14px; }
    .search-bar { flex: 1; width: 100%; background: transparent; border: none; color: #c0c0c0; font-family: 'Share Tech Mono', monospace; font-size: 13px; padding: 13px 0; outline: none; letter-spacing: 1px; }
    .search-bar::placeholder { color: #444; }
    .kbd { font-size: 9px; letter-spacing: 1px; color: #555; border: 1px solid #2a2a2a; padding: 2px 6px; border-radius: 3px; }

    .seg-group { display: flex; border: 1px solid #1f1f1f; background: var(--panel); }
    .seg-btn { background: transparent; border: none; border-right: 1px solid #1f1f1f; color: #777; font-family: 'Share Tech Mono', monospace; font-size: 10px; letter-spacing: 2px; padding: 0 14px; cursor: pointer; text-transform: uppercase; transition: all 0.2s; min-height: 44px; display: flex; align-items: center; gap: 7px; }
    .seg-btn:last-child { border-right: none; }
    .seg-btn svg { width: 14px; height: 14px; fill: none; stroke: currentColor; stroke-width: 1.6; stroke-linecap: round; }
    .seg-btn:hover { color: #fff; background: rgba(204,0,0,0.1); }
    .seg-btn.active { background: var(--red-dim); color: #fff; box-shadow: inset 0 0 14px rgba(255,42,42,0.3); }

    .sel { background: var(--panel); border: 1px solid #1f1f1f; color: #aaa; font-family: 'Share Tech Mono', monospace; font-size: 10px; letter-spacing: 2px; padding: 0 12px; min-height: 44px; text-transform: uppercase; cursor: pointer; outline: none; }
    .sel:hover, .sel:focus { border-color: var(--red-dim); color: #fff; }
    .sel option { background: #0d0d0d; }

    .act-btn { background: transparent; border: 1px solid var(--red-dim); color: var(--red); cursor: pointer; font-family: 'Share Tech Mono', monospace; font-size: 10px; letter-spacing: 3px; padding: 0 16px; min-height: 44px; text-transform: uppercase; transition: all 0.2s; }
    .act-btn:hover { background: var(--red); color: #080808; box-shadow: 0 0 22px rgba(204,0,0,0.5); }
    .act-btn.ghost { border-color: #2a2a2a; color: #777; }
    .act-btn.ghost:hover { background: #222; color: #fff; box-shadow: none; }

    .info-line { display: flex; flex-wrap: wrap; justify-content: space-between; gap: 8px 16px; font-size: 10px; letter-spacing: 2px; color: #555; text-transform: uppercase; margin-bottom: 22px; }
    .info-line b { color: #bbb; font-weight: 400; }
    .info-line .keys span { color: #888; }

    /* ══ SECTIONS ══ */
    .section-label { font-size: 10px; letter-spacing: 4px; color: var(--red-dim); text-transform: uppercase; margin-bottom: 14px; padding-bottom: 7px; border-bottom: 1px solid var(--red-faint); display: flex; justify-content: space-between; align-items: center; gap: 12px; }
    .section-label .aside { color: #3a2a2a; letter-spacing: 2px; font-size: 9px; }
    .section-label button { background: none; border: none; color: #5a3a3a; font-family: inherit; font-size: 9px; letter-spacing: 2px; cursor: pointer; text-transform: uppercase; }
    .section-label button:hover { color: var(--red-hot); }

    /* ══ MAP ══ */
    .map-wrap { margin-bottom: 36px; }
    .map { display: grid; grid-template-columns: repeat(auto-fill, minmax(42px, 1fr)); gap: 4px; padding: 14px; background: var(--panel); border: 1px solid #1a1a1a; }
    .map.closed { display: none; }
    .mcell {
      position: relative; aspect-ratio: 1; display: flex; align-items: center; justify-content: center; text-decoration: none;
      font-size: 10px; letter-spacing: 0.5px; color: color-mix(in srgb, var(--tc) 85%, #fff);
      background: color-mix(in srgb, var(--tc) 14%, #0d0d0d); border: 1px solid color-mix(in srgb, var(--tc) 40%, #111);
      transition: transform 0.18s, box-shadow 0.18s, opacity 0.25s, background 0.18s; animation: cellin 0.5s ease both;
    }
    @keyframes cellin { from { opacity: 0; transform: scale(0.6); } to { opacity: 1; transform: none; } }
    .mcell.sub { font-size: 8px; }
    .mcell:hover, .mcell.selected { transform: scale(1.35); z-index: 5; background: color-mix(in srgb, var(--tc) 38%, #0d0d0d); box-shadow: 0 0 20px color-mix(in srgb, var(--tc) 70%, transparent); color: #fff; }
    .mcell.dim { opacity: 0.12; }
    .mcell.hide { display: none; }
    .tip { position: fixed; z-index: 700; pointer-events: none; background: #0d0d0d; border: 1px solid var(--tc, #555); padding: 9px 12px; min-width: 190px; opacity: 0; transform: translateY(6px); transition: opacity 0.12s, transform 0.12s; box-shadow: 0 8px 30px rgba(0,0,0,0.7), 0 0 20px color-mix(in srgb, var(--tc, #555) 30%, transparent); }
    .tip.on { opacity: 1; transform: none; }
    .tip .tid { font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 20px; letter-spacing: 3px; color: var(--tc, #fff); }
    .tip .tname { font-size: 12px; color: #ddd; margin: 2px 0 6px; letter-spacing: 1px; }
    .tip .tcls { font-size: 9px; letter-spacing: 3px; color: var(--tc, #aaa); text-transform: uppercase; }

    /* ══ VIEWS ══ */
    .views { position: relative; }
    .views.flash::after { content: ''; position: absolute; left: 0; right: 0; top: 0; height: 70px; pointer-events: none; background: linear-gradient(180deg, transparent, rgba(255,42,42,0.16), transparent); animation: sweep 0.7s ease-out 1; z-index: 4; }
    @keyframes sweep { from { transform: translateY(-70px); opacity: 1; } to { transform: translateY(100%); opacity: 0; } }
    .view { display: none; }
    .view.on { display: flex; }
    #gridView.on { display: grid; }

    .anomaly-list { flex-direction: column; gap: 4px; margin-bottom: 30px; }

    .anomaly-link {
      position: relative; display: flex; align-items: center; gap: 12px; padding: 11px 16px; overflow: hidden;
      background-color: rgba(13,13,13,0.9); border: 1px solid #1a1a1a; border-left: 3px solid color-mix(in srgb, var(--tc) 35%, #111);
      color: #888; text-decoration: none; font-size: 12px; letter-spacing: 0.5px;
      transition: border-color 0.18s, color 0.18s, background-color 0.18s, transform 0.18s; --cx: 50%; --cy: 50%;
      animation: rowin 0.35s ease both;
    }
    @keyframes rowin { from { opacity: 0; transform: translateX(-8px); } to { opacity: 1; transform: none; } }
    .anomaly-link::before { content: ''; position: absolute; inset: 0; pointer-events: none; opacity: 0; transition: opacity 0.2s; background: radial-gradient(240px circle at var(--cx) var(--cy), color-mix(in srgb, var(--tc) 18%, transparent), transparent 70%); }
    .anomaly-link:hover, .anomaly-link.sel-on { border-left-color: var(--tc); color: color-mix(in srgb, var(--tc) 55%, #fff); background-color: color-mix(in srgb, var(--tc) 7%, #0a0a0a); transform: translateX(4px); }
    .anomaly-link:hover::before, .anomaly-link.sel-on::before { opacity: 1; }
    .anomaly-link.sel-on { outline: 1px solid color-mix(in srgb, var(--tc) 50%, transparent); }
    .anomaly-link.hide { display: none; }
    .tier-dot { width: 7px; height: 7px; border-radius: 50%; flex-shrink: 0; box-shadow: 0 0 8px currentColor; position: relative; }
    .lid { font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 15px; letter-spacing: 2px; color: color-mix(in srgb, var(--tc) 80%, #888); min-width: 70px; position: relative; }
    .dash { color: #3a3a3a; position: relative; }
    .lname { flex: 1; position: relative; min-width: 0; }
    .badge { font-size: 9px; letter-spacing: 3px; color: var(--tc); border: 1px solid color-mix(in srgb, var(--tc) 40%, transparent); padding: 2px 8px; text-transform: uppercase; position: relative; margin-left: auto; white-space: nowrap; opacity: 0.8; }
    .go { color: #2a2a2a; font-size: 15px; transition: color 0.2s, transform 0.2s; position: relative; }
    .anomaly-link:hover .go, .anomaly-link.sel-on .go { color: var(--tc); transform: translateX(5px); }
    @media (max-width: 600px) { .badge { display: none; } }
    mark { background: rgba(255,42,42,0.35); color: #fff; padding: 0 1px; }

    .tomega { box-shadow: 0 0 18px rgba(255,255,255,0.04); }
    .tomega:hover .lid, .tomega .lid { text-shadow: 0 0 12px rgba(255,255,255,0.6); }
    .tredacted:hover .lname, .tredacted.sel-on .lname { animation: rgbs 0.5s steps(2) 2; }
    @keyframes rgbs { 0% { text-shadow: -2px 0 #00e5ff, 2px 0 #ff0040; } 50% { text-shadow: 2px 0 #00e5ff, -2px 0 #ff0040; } 100% { text-shadow: none; } }

    /* grid */
    #gridView { grid-template-columns: repeat(auto-fill, minmax(230px, 1fr)); gap: 10px; margin-bottom: 30px; }
    .gcard {
      position: relative; display: flex; flex-direction: column; justify-content: flex-end; min-height: 130px; padding: 16px; overflow: hidden; text-decoration: none;
      background: rgba(13,13,13,0.9); border: 1px solid #1a1a1a; border-top: 3px solid var(--tc); --cx: 50%; --cy: 50%;
      transition: transform 0.22s, box-shadow 0.22s, border-color 0.22s; animation: cardin 0.4s ease both;
    }
    @keyframes cardin { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: none; } }
    .gcard::before { content: ''; position: absolute; inset: 0; pointer-events: none; opacity: 0.55; transition: opacity 0.2s; background: radial-gradient(260px circle at var(--cx) var(--cy), color-mix(in srgb, var(--tc) 22%, transparent), transparent 70%); }
    .gcard:hover, .gcard.sel-on { transform: translateY(-4px); border-color: color-mix(in srgb, var(--tc) 50%, #111); box-shadow: 0 10px 30px rgba(0,0,0,0.55), 0 0 26px color-mix(in srgb, var(--tc) 28%, transparent); }
    .gcard:hover::before, .gcard.sel-on::before { opacity: 1; }
    .gcard.hide { display: none; }
    .gnum { position: absolute; right: 8px; top: -2px; font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 84px; line-height: 1; color: transparent; -webkit-text-stroke: 1px color-mix(in srgb, var(--tc) 38%, transparent); letter-spacing: -2px; pointer-events: none; }
    .gcard .lid { font-size: 22px; position: relative; display: block; margin-bottom: 4px; }
    .gname { font-size: 13px; color: #ddd; line-height: 1.4; position: relative; min-height: 36px; letter-spacing: 0.5px; }
    .gname.sub { color: #555; font-size: 10px; letter-spacing: 3px; }
    .gcard .badge { align-self: flex-start; margin: 8px 0 0; }

    /* terminal */
    #termView { flex-direction: column; gap: 0; margin-bottom: 30px; background: rgba(5,5,5,0.92); border: 1px solid #1a1a1a; padding: 14px 6px; font-size: 12px; }
    .trow { position: relative; display: flex; align-items: baseline; gap: 10px; padding: 5px 14px; text-decoration: none; color: #777; letter-spacing: 1px; transition: background 0.12s, color 0.12s; }
    .trow.hide { display: none; }
    .tpre { color: transparent; width: 12px; flex-shrink: 0; }
    .trow:hover, .trow.sel-on { background: color-mix(in srgb, var(--tc) 10%, transparent); color: color-mix(in srgb, var(--tc) 40%, #fff); }
    .trow:hover .tpre, .trow.sel-on .tpre { color: var(--tc); }
    .trow .lid { font-size: 13px; min-width: 70px; }
    .leader { flex: 1; border-bottom: 1px dotted #2a2a2a; min-width: 12px; transform: translateY(-3px); }
    .tcls { font-size: 10px; letter-spacing: 3px; color: var(--tc); min-width: 92px; text-align: right; opacity: 0.85; }
    @media (max-width: 600px) { .tcls { display: none; } }
    .term-end { padding: 8px 14px 2px; color: var(--red); font-size: 12px; }
    .term-end::after { content: ''; display: inline-block; width: 8px; height: 14px; background: var(--red); vertical-align: -2px; margin-left: 4px; animation: blink 0.8s steps(2) infinite; }

    .empty-msg { display: none; text-align: center; padding: 50px 14px; border: 1px dashed #2a2a2a; margin-bottom: 30px; font-size: 11px; letter-spacing: 3px; color: #666; text-transform: uppercase; line-height: 2; }
    .empty-msg.on { display: block; }
    .empty-msg b { display: block; font-family: 'Rajdhani', sans-serif; font-size: 28px; color: var(--red-dim); letter-spacing: 6px; }

    /* ══ FOOTER ══ */
    .end-line { display: flex; align-items: center; gap: 14px; margin: 10px 0 22px; color: #3a1a1a; font-size: 10px; letter-spacing: 4px; text-transform: uppercase; }
    .end-line::before, .end-line::after { content: ''; flex: 1; height: 1px; background: linear-gradient(90deg, transparent, #2a0000, transparent); }
    .footer { border-top: 1px solid var(--red-faint); padding-top: 20px; font-size: 10px; color: #333; letter-spacing: 1px; line-height: 1.8; text-align: center; }

    @media (prefers-reduced-motion: reduce) {
      .ticker-track, .header-line, .donut-sweep, .site-title.glitch, .anomaly-link, .gcard, .mcell, .views.flash::after { animation: none !important; }
      .reveal { opacity: 1; transform: none; transition: none; }
      #rain { display: none; }
    }
  </style>
</head>
<body>

  <canvas id="rain" aria-hidden="true"></canvas>
  <div class="bg-grid"></div>
  <div class="bg-spot"></div>
  <div class="bg-vignette"></div>

  <div class="warning-bar">
    ⚠ RESTRICTED ACCESS — AUTHORIZED PERSONNEL ONLY — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="ticker" aria-label="Recently updated files">
    <div class="ticker-label">Recently Updated</div>
    <div class="ticker-viewport"><div class="ticker-track" id="tickerTrack"></div></div>
  </div>

  <div class="container">

    <a href="index.html" class="back-link">← RETURN TO DATABASE INDEX</a>

    <div class="header reveal">
      <div class="header-line"></div>
      <div class="header-inner">
        <div>
          <div class="site-title" id="siteTitle" data-text="ANOMALY REPORTS">ANOMALY REPORTS</div>
          <div class="site-subtitle">Liminal Division — Active Case Files</div>
          <div class="clearance-badge">Clearance Level 1+ Required</div>
        </div>
        <div class="donut-wrap" aria-hidden="true">
          <svg viewBox="0 0 170 170" id="donut">
            <defs>
              <linearGradient id="swG" x1="0" y1="0" x2="1" y2="0"><stop offset="0" stop-color="#ff2a2a" stop-opacity="0"/><stop offset="1" stop-color="#ff2a2a" stop-opacity="0.5"/></linearGradient>
            </defs>
            <circle cx="85" cy="85" r="80" fill="none" stroke="#2a0000" stroke-width="1"/>
            <circle cx="85" cy="85" r="50" fill="rgba(10,0,0,0.85)" stroke="#2a0000" stroke-width="1"/>
            <g id="donutSegs"></g>
            <g class="donut-sweep"><path d="M85 85 L85 12 A73 73 0 0 1 140 37 Z" fill="url(#swG)"/></g>
          </svg>
          <div class="donut-num"><b id="donutCount">0</b><span>FILES</span></div>
        </div>
      </div>
    </div>

    <div class="status-bar reveal">
      <span class="grp"><span class="status-dot"></span><span class="hi">DATABASE ONLINE</span></span>
      <span class="status-sep">//</span>
      <span class="grp"><span class="hi">TOTAL DOCUMENTED: 97 ANOMALIES</span></span>
      <span class="status-sep">//</span>
      <span class="grp">THREAT STATUS: <span class="hi">ELEVATED</span></span>
      <span class="status-sep">//</span>
      <span class="grp">FILES LISTED <span class="hi" id="listedCount">--</span></span>
      <span class="status-sep">//</span>
      <span class="grp">UTC <span class="hi" id="clock">--:--:--</span></span>
    </div>

    <div class="legend reveal" id="legend">
      <div class="legend-item" data-tier="0"><div class="legend-dot dot-0"></div> CLASS 0</div>
      <div class="legend-item" data-tier="1"><div class="legend-dot dot-1"></div> CLASS I</div>
      <div class="legend-item" data-tier="2"><div class="legend-dot dot-2"></div> CLASS II</div>
      <div class="legend-item" data-tier="3"><div class="legend-dot dot-3"></div> CLASS III</div>
      <div class="legend-item" data-tier="4"><div class="legend-dot dot-4"></div> CLASS IV</div>
      <div class="legend-item" data-tier="5"><div class="legend-dot dot-5"></div> CLASS V</div>
      <div class="legend-item" data-tier="6"><div class="legend-dot dot-6"></div> CLASS VI</div>
      <div class="legend-item" data-tier="7"><div class="legend-dot dot-7"></div> CLASS VII</div>
      <div class="legend-item" data-tier="omega"><div class="legend-dot dot-omega"></div> CLASS Ω</div>
      <div class="legend-item" data-tier="redacted"><div class="legend-dot dot-redacted"></div> REDACTED</div>
    </div>

    <div class="controls reveal">
      <label class="search">
        <span class="ico">⌕</span>
        <input class="search-bar" type="text" placeholder="// SEARCH ANOMALY FILES..." id="searchInput" onkeyup="filterAnomalies()" autocomplete="off" spellcheck="false" />
        <span class="kbd">/</span>
      </label>
      <div class="seg-group" id="viewGroup">
        <button class="seg-btn" type="button" data-view="list"><svg viewBox="0 0 16 16"><path d="M2 4h12M2 8h12M2 12h12"/></svg>List</button>
        <button class="seg-btn" type="button" data-view="grid"><svg viewBox="0 0 16 16"><rect x="2" y="2" width="5" height="5"/><rect x="9" y="2" width="5" height="5"/><rect x="2" y="9" width="5" height="5"/><rect x="9" y="9" width="5" height="5"/></svg>Grid</button>
        <button class="seg-btn" type="button" data-view="term"><svg viewBox="0 0 16 16"><path d="M3 4l4 4-4 4M9 12h4"/></svg>Terminal</button>
      </div>
      <select class="sel" id="sortSel" aria-label="Sort files">
        <option value="idasc">File no. ↑</option>
        <option value="iddesc">File no. ↓</option>
        <option value="classasc">Class ↑</option>
        <option value="classdesc">Class ↓</option>
        <option value="name">Name A–Z</option>
      </select>
      <button class="act-btn" type="button" id="randBtn">▶ Random file</button>
      <button class="act-btn ghost" type="button" id="clearBtn">Reset</button>
    </div>

    <div class="info-line reveal">
      <span>SHOWING <b id="shownCount">0</b> OF <b id="totalCount">0</b> FILES</span>
      <span class="keys"><span>/</span> SEARCH · <span>↑ ↓ ← →</span> NAVIGATE · <span>ENTER</span> OPEN · <span>R</span> RANDOM · <span>ESC</span> RESET</span>
    </div>

    <div class="map-wrap reveal">
      <div class="section-label"><span>// File Map //</span><span class="aside">HOVER FOR DETAILS — CLICK TO OPEN</span><button type="button" id="mapToggle">▾ HIDE MAP</button></div>
      <div class="map" id="mapView"></div>
    </div>

    <div class="section-label reveal"><span>// Active Case Files — LD Series //</span><span class="aside" id="viewAside">LIST VIEW</span></div>

    <div class="views" id="views">
    <div class="anomaly-list view on" id="anomalyGrid">

      <a href="LD-000.html" class="anomaly-link tomega"><div class="tier-dot dot-omega"></div>LD-000 — [REDACTED]</a>
      <a href="LD-001.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-001 — Lucas Devil</a>
      <a href="LD-002.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-002 — Doro</a>
      <a href="LD-003.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-003 — The Drowned Girl</a>
      <a href="LD-004.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-004 — The Swine Hybrid</a>
      <a href="LD-005.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-005 — The Hollow Plaything</a>
      <a href="LD-006.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-006 — The Oracle Terminal</a>
      <a href="LD-007.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-007 — The Visitor's Folklore</a>
      <a href="LD-008.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-008 — Laughtrack</a>
      <a href="LD-009.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-009 — The Endless Lift</a>
      <a href="LD-009.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-009.5</a>
      <a href="LD-010.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-010 — The Pactbound</a>
      <a href="LD-011.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-011 — The Echo-Faced</a>
      <a href="LD-012.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-012 — The Molded</a>
      <a href="LD-013.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-013 — The Insect Matron</a>
      <a href="LD-014.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-014 — The Knife That Loves Too Deeply</a>
      <a href="LD-015.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-015 — REDACTED</a>
      <a href="LD-016.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-016 — Andy's Revolver</a>
      <a href="LD-017.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-017 — The Pactbound Trinket</a>
      <a href="LD-018.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-018 — REDACTED Neutralized</a>
      <a href="LD-019.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-019 — The House Always Wins</a>
      <a href="LD-020.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-020 — The Finder's Shard</a>
      <a href="LD-021.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-021 — Velocity Pills</a>
      <a href="LD-021.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-021.5</a>
      <a href="LD-022.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-022 — RedSap</a>
      <a href="LD-023.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-023 — The Kindler's Box</a>
      <a href="LD-023.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-023.5</a>
      <a href="LD-024.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-024 — The Hunting Slide</a>
      <a href="LD-025.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-025 — The Red Stalker</a>
      <a href="LD-026.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-026 — The Perfect Wife</a>
      <a href="LD-027.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-027 — Angel Terminal</a>
      <a href="LD-028.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-028 — It's a Fking UFO</a>
      <a href="LD-029.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-029 — Flashbang Lens</a>
      <a href="LD-030.html" class="anomaly-link t0"><div class="tier-dot dot-0"></div>LD-030 — Infinite Pizza Slice</a>
      <a href="LD-031.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-031 — First Bottle's Free</a>
      <a href="LD-032.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-032 — Free Parking</a>
      <a href="LD-033.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-033 — Black Backseat</a>
      <a href="LD-034.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-034 — The Pale Man</a>
      <a href="LD-035.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-035 — The Wishing Matron</a>
      <a href="LD-035.5.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-035.5</a>
      <a href="LD-036.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-036 — The Hunters</a>
      <a href="LD-036.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-036.5</a>
      <a href="LD-037.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-037 — The Lost Episode</a>
      <a href="LD-037.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-037.5</a>
      <a href="LD-038.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-038 — The All-Brewer</a>
      <a href="LD-039.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-039 — The Suicide Line</a>
      <a href="LD-040.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-040 — Calcium Devourers</a>
      <a href="LD-041.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-041 — The Crow Guard</a>
      <a href="LD-042.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-042 — The Earth Devourers</a>
      <a href="LD-043.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-043 — The Crimson Judgement</a>
      <a href="LD-044.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-044 — The Veiled Judgment</a>
      <a href="LD-045.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-045 — DIVA</a>
      <a href="LD-046.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-046 — Gloom Smoking Tube</a>
      <a href="LD-047.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-047 — Fragment of One's Imagination</a>
      <a href="LD-048.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-048 — Price of Immortality</a>
      <a href="LD-049.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-049 — RAGE</a>
      <a href="LD-050.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-050 — The Calamity Empress</a>
      <a href="LD-051.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-051 — Remnants of Ash</a>
      <a href="LD-052.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-052 — Judgement Coin</a>
      <a href="LD-053.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-053 — The Crimson Impaler</a>
      <a href="LD-054.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-054 — The Sailor's Lullaby</a>
      <a href="LD-055.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-055 — The Drowned Shepherd</a>
      <a href="LD-056.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-056 — The Hollow Seraph</a>
      <a href="LD-057.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-057 — Egg of Concepts</a>
      <a href="LD-058.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-058 — The Hunter Tribes</a>
      <a href="LD-059.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-059 — The Murder Bucket</a>
      <a href="LD-060.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-060 — The Timekeeper's Pocket Watch</a>

      <a href="LD-061.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-061 — The Gravebound Colossus</a>
      <a href="LD-062.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-062 — The Hollow Farm</a>
      <a href="LD-063.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-063 — The Hollow Stag</a>
      <a href="LD-064.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-064 — The Veiled Queen &amp; The Devourer</a>
      <a href="LD-065.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-065 — The Rabbit Mother</a>
      <a href="LD-066.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-066 — The Silent Executioner</a>
      <a href="LD-067.html" class="anomaly-link t0"><div class="tier-dot dot-0"></div>LD-067 — The Attempted Entertainer</a>
      <a href="LD-068.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-068 — The Absolute Zero Blade</a>
      <a href="LD-069.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-069 — The Latex Lament</a>
      <a href="LD-070.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-070 — There's A Devil In My Heart</a>
      <a href="LD-071.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-071 — Killstreak</a>
      <a href="LD-072.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-072 — The Finger Maiden</a>
      <a href="LD-073.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-073 — The Watchers</a>
      <a href="LD-074.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-074 — Dominance</a>
      <a href="LD-075.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-075 — Phantom Edge</a>
      <a href="LD-076.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-076 — The Silent Queen</a>
      <a href="LD-077.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-077 — The White Maiden</a>
      <a href="LD-078.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-078 — The Golden-Eyed Lord</a>
      <a href="LD-079.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-079 — The Crimson Witness</a>
      <a href="LD-080.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-080 — The Marionette</a>
      <a href="LD-081.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-081 — The Corrosive Drake</a>
      <a href="LD-082.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-082 — The Mist Hound</a>
      <a href="LD-083.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-083 — The HellBreaker</a>
      <a href="LD-084.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-084 — The Mourning Coffin</a>
      <a href="LD-085.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-085 — Eclipse</a>
      <a href="LD-086.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-086 — The Hook Embrace</a>
      <a href="LD-087.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-087 — The Second Skin</a>
      <a href="LD-088.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-088 — The Mercy of Life</a>
      <a href="LD-089.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-089 — The Missing</a>
      <a href="LD-090.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-090 — Forever Diamonds</a>
      <a href="LD-091.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-091 — I Love A Man In Uniform</a>
      <a href="LD-092.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-092 — The Last Wonderer</a>
      <a href="LD-093.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-093 — Don't Fear The Reaper</a>
      <a href="LD-094.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-094 — The Last Oath</a>
      <a href="LD-095.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-095 — Scythe of Sync</a>
      <a href="LD-096.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-096 — The Candle Maiden</a>
      <a href="LD-097.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-097 — The Cannibalistic Meat Cleaver</a>
    </div>

    <div class="view" id="gridView"></div>
    <div class="view" id="termView"></div>
    </div>

    <div class="empty-msg" id="emptyMsg"><b>NO FILES</b><span id="emptyTxt">No files match the current filters</span></div>

    <div class="end-line">End of index</div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

  <div class="tip" id="tip"><div class="tid"></div><div class="tname"></div><div class="tcls"></div></div>

  <script>
    /* original hook — kept so the inline onkeyup handler still works */
    function filterAnomalies() {
      if (window.__dvdFilter) window.__dvdFilter(document.getElementById('searchInput').value);
    }

    (function () {
      var reduce = !!(window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches);
      var root = document.documentElement;
      function $(id) { return document.getElementById(id); }
      function esc(s) { return String(s).replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;'); }

      var TIERS = {
        '0':       { label: 'CLASS 0',   color: '#8a8a8a', ord: 0 },
        '1':       { label: 'CLASS I',   color: '#4fc3f7', ord: 1 },
        '2':       { label: 'CLASS II',  color: '#4caf50', ord: 2 },
        '3':       { label: 'CLASS III', color: '#ffd600', ord: 3 },
        '4':       { label: 'CLASS IV',  color: '#ff6a1a', ord: 4 },
        '5':       { label: 'CLASS V',   color: '#f44336', ord: 5 },
        '6':       { label: 'CLASS VI',  color: '#b04bd0', ord: 6 },
        '7':       { label: 'CLASS VII', color: '#e020e0', ord: 7 },
        'omega':   { label: 'CLASS \u03A9', color: '#ffffff', ord: 8 },
        'redacted':{ label: 'REDACTED',  color: '#ff69b4', ord: 9 }
      };
      var ORDER = ['0', '1', '2', '3', '4', '5', '6', '7', 'omega', 'redacted'];

      var listEl = $('anomalyGrid'), gridEl = $('gridView'), termEl = $('termView'), mapEl = $('mapView');
      var viewsEl = $('views');

      /* ══ READ DATA FROM THE EXISTING LINKS ══ */
      var anchors = Array.prototype.slice.call(listEl.querySelectorAll('.anomaly-link'));
      var DATA = anchors.map(function (a, i) {
        var txt = a.textContent.trim(), cut = txt.indexOf(' \u2014 ');
        var id = cut > -1 ? txt.slice(0, cut) : txt, name = cut > -1 ? txt.slice(cut + 3) : '';
        var cls = ''; for (var k = 0; k < a.classList.length; k++) if (/^t(\d|omega|redacted)$/.test(a.classList[k])) cls = a.classList[k];
        var tier = cls.replace(/^t/, '');
        return { i: i, el: a, href: a.getAttribute('href'), id: id, name: name, tier: tier, cls: cls, num: parseFloat(id.replace('LD-', '')), text: txt, vis: true };
      });
      var count = {}; ORDER.forEach(function (k) { count[k] = 0; });
      DATA.forEach(function (d) { count[d.tier]++; });

      /* ══ ENHANCE LIST ROWS ══ */
      DATA.forEach(function (d) {
        var dot = d.el.querySelector('.tier-dot');
        var html = '<span class="lid">' + esc(d.id) + '</span>';
        if (d.name) html += '<span class="dash"> \u2014 </span><span class="lname">' + esc(d.name) + '</span>';
        else html += '<span class="lname"></span>';
        html += '<span class="badge">' + TIERS[d.tier].label + '</span><span class="go">\u2192</span>';
        var keep = dot; d.el.innerHTML = ''; d.el.appendChild(keep); d.el.insertAdjacentHTML('beforeend', html);
        d.el.setAttribute('data-i', d.i);
        d.el.style.animationDelay = Math.min(d.i * 12, 500) + 'ms';
        d.hlList = [{ el: d.el.querySelector('.lid'), t: d.id }]; if (d.name) d.hlList.push({ el: d.el.querySelector('.lname'), t: d.name });
      });

      /* ══ BUILD GRID / TERMINAL / MAP ══ */
      function mk(tag, cls, html) { var e = document.createElement(tag); if (cls) e.className = cls; if (html != null) e.innerHTML = html; return e; }
      DATA.forEach(function (d) {
        var T = TIERS[d.tier], pad = d.id.replace('LD-', '');
        var g = mk('a', 'gcard ' + d.cls);
        g.href = d.href; g.setAttribute('data-i', d.i); g.style.animationDelay = Math.min(d.i * 10, 400) + 'ms';
        g.innerHTML = '<span class="gnum">' + esc(pad.split('.')[0]) + '</span><span class="lid">' + esc(d.id) + '</span><span class="gname' + (d.name ? '' : ' sub') + '">' + (d.name ? esc(d.name) : 'SUB-ENTRY') + '</span><span class="badge">' + T.label + '</span>';
        d.g = g; d.gId = g.querySelector('.lid'); d.gName = g.querySelector('.gname');
        d.hlList.push({ el: d.gId, t: d.id }); if (d.name) d.hlList.push({ el: d.gName, t: d.name });

        var t = mk('a', 'trow ' + d.cls);
        t.href = d.href; t.setAttribute('data-i', d.i);
        t.innerHTML = '<span class="tpre">&gt;</span><span class="lid">' + esc(d.id) + '</span><span class="leader"></span><span class="tn">' + (d.name ? esc(d.name) : '\u2014') + '</span><span class="leader"></span><span class="tcls">' + T.label + '</span>';
        d.t = t; d.tId = t.querySelector('.lid'); d.tName = t.querySelector('.tn');
        d.hlList.push({ el: d.tId, t: d.id }); if (d.name) d.hlList.push({ el: d.tName, t: d.name });

        var m = mk('a', 'mcell ' + d.cls + (d.name ? '' : ' sub'));
        m.href = d.href; m.setAttribute('data-i', d.i); m.textContent = pad; m.style.animationDelay = Math.min(d.i * 8, 700) + 'ms';
        m.setAttribute('aria-label', d.text);
        d.m = m;

        gridEl.appendChild(g); termEl.appendChild(t); mapEl.appendChild(m);
        [g, t, m].forEach(function (x) { /* hover glow tracking */
          if (x === m) return;
          x.addEventListener('pointermove', function (e) { var r = x.getBoundingClientRect(); x.style.setProperty('--cx', (e.clientX - r.left) + 'px'); x.style.setProperty('--cy', (e.clientY - r.top) + 'px'); });
        });
        d.el.addEventListener('pointermove', function (e) { var r = d.el.getBoundingClientRect(); d.el.style.setProperty('--cx', (e.clientX - r.left) + 'px'); d.el.style.setProperty('--cy', (e.clientY - r.top) + 'px'); });
      });
      termEl.appendChild(mk('div', 'term-end', '&gt; END OF LISTING'));

      /* ══ MAP TOOLTIP ══ */
      var tip = $('tip');
      function showTip(d, ev) {
        tip.style.setProperty('--tc', TIERS[d.tier].color);
        tip.querySelector('.tid').textContent = d.id;
        tip.querySelector('.tname').textContent = d.name || 'Sub-entry';
        tip.querySelector('.tcls').textContent = TIERS[d.tier].label;
        tip.classList.add('on'); moveTip(ev);
      }
      function moveTip(ev) {
        var x = ev.clientX + 16, y = ev.clientY + 16, w = tip.offsetWidth, h = tip.offsetHeight;
        if (x + w > window.innerWidth - 8) x = ev.clientX - w - 16;
        if (y + h > window.innerHeight - 8) y = ev.clientY - h - 16;
        tip.style.left = x + 'px'; tip.style.top = y + 'px';
      }
      DATA.forEach(function (d) {
        d.m.addEventListener('mouseenter', function (e) { showTip(d, e); });
        d.m.addEventListener('mousemove', moveTip);
        d.m.addEventListener('mouseleave', function () { tip.classList.remove('on'); });
      });

      /* ══ STATE ══ */
      var state = { q: '', tiers: {}, view: 'list', sort: 'idasc', sel: -1, map: true };
      try { var sv = localStorage.getItem('dvdArView'), ss = localStorage.getItem('dvdArSort'); if (sv) state.view = sv; if (ss) state.sort = ss; } catch (e) {}

      function readHash() {
        var h = location.hash.replace(/^#/, ''); if (!h) return;
        h.split('&').forEach(function (p) {
          var kv = p.split('='), k = kv[0], v = decodeURIComponent(kv[1] || '');
          if (k === 'q') state.q = v;
          else if (k === 't') v.split(',').forEach(function (x) { if (TIERS[x]) state.tiers[x] = true; });
          else if (k === 'v' && (v === 'list' || v === 'grid' || v === 'term')) state.view = v;
          else if (k === 's') state.sort = v;
        });
      }
      function writeHash() {
        var parts = [];
        if (state.q) parts.push('q=' + encodeURIComponent(state.q));
        var ts = ORDER.filter(function (k) { return state.tiers[k]; }); if (ts.length) parts.push('t=' + ts.join(','));
        if (state.view !== 'list') parts.push('v=' + state.view);
        if (state.sort !== 'idasc') parts.push('s=' + state.sort);
        try { history.replaceState(null, '', parts.length ? '#' + parts.join('&') : location.pathname + location.search); } catch (e) {}
        try { localStorage.setItem('dvdArView', state.view); localStorage.setItem('dvdArSort', state.sort); } catch (e) {}
      }

      /* ══ SORT / FILTER ══ */
      function cmp(a, b) {
        var s = state.sort, oa = TIERS[a.tier].ord, ob = TIERS[b.tier].ord;
        if (s === 'iddesc') return b.num - a.num;
        if (s === 'classasc') return (oa - ob) || (a.num - b.num);
        if (s === 'classdesc') return (ob - oa) || (a.num - b.num);
        if (s === 'name') { if (!a.name && b.name) return 1; if (a.name && !b.name) return -1; return a.name.toLowerCase().localeCompare(b.name.toLowerCase()) || (a.num - b.num); }
        return a.num - b.num;
      }
      function applySort() {
        var arr = DATA.slice().sort(cmp);
        var tEnd = termEl.querySelector('.term-end');
        arr.forEach(function (d) { listEl.appendChild(d.el); gridEl.appendChild(d.g); termEl.insertBefore(d.t, tEnd); mapEl.appendChild(d.m); });
        return arr;
      }
      function matches(d) {
        var anyT = ORDER.some(function (k) { return state.tiers[k]; });
        if (anyT && !state.tiers[d.tier]) return false;
        if (!state.q) return true;
        var q = state.q.toLowerCase();
        return d.text.toLowerCase().indexOf(q) > -1 || TIERS[d.tier].label.toLowerCase().indexOf(q) > -1 || d.id.toLowerCase().replace('ld-', '').indexOf(q) > -1;
      }
      function hl(text, q) {
        if (!q) return esc(text);
        var low = text.toLowerCase(), ql = q.toLowerCase(), out = '', pos = 0, ix;
        while ((ix = low.indexOf(ql, pos)) > -1) { out += esc(text.slice(pos, ix)) + '<mark>' + esc(text.slice(ix, ix + q.length)) + '</mark>'; pos = ix + q.length; }
        return out + esc(text.slice(pos));
      }

      var shownEl = $('shownCount'), emptyMsg = $('emptyMsg'), emptyTxt = $('emptyTxt');
      function apply(flash) {
        var vis = 0;
        DATA.forEach(function (d) {
          d.vis = matches(d); if (d.vis) vis++;
          d.el.classList.toggle('hide', !d.vis); d.g.classList.toggle('hide', !d.vis); d.t.classList.toggle('hide', !d.vis);
          d.m.classList.toggle('dim', !d.vis);
          d.hlList.forEach(function (h) { h.el.innerHTML = hl(h.t, state.q); });
        });
        shownEl.textContent = vis;
        var anyT = ORDER.some(function (k) { return state.tiers[k]; });
        emptyMsg.classList.toggle('on', vis === 0);
        if (vis === 0) emptyTxt.textContent = (anyT && !state.q) ? 'No files at this classification are publicly indexed' : 'No files match the current filters';
        document.querySelectorAll('#legend .legend-item').forEach(function (it) { it.classList.toggle('active', !!state.tiers[it.getAttribute('data-tier')]); });
        state.sel = -1; clearSel();
        if (flash && !reduce) { viewsEl.classList.remove('flash'); void viewsEl.offsetWidth; viewsEl.classList.add('flash'); }
        writeHash();
      }

      function setView(v) {
        state.view = v;
        listEl.classList.toggle('on', v === 'list'); gridEl.classList.toggle('on', v === 'grid'); termEl.classList.toggle('on', v === 'term');
        document.querySelectorAll('#viewGroup .seg-btn').forEach(function (b) { b.classList.toggle('active', b.getAttribute('data-view') === v); });
        $('viewAside').textContent = (v === 'list' ? 'LIST' : v === 'grid' ? 'GRID' : 'TERMINAL') + ' VIEW';
        state.sel = -1; clearSel(); writeHash();
      }

      /* ══ SELECTION / KEYBOARD ══ */
      function activeContainer() { return state.view === 'list' ? listEl : state.view === 'grid' ? gridEl : termEl; }
      function visibleEls() { return Array.prototype.filter.call(activeContainer().children, function (e) { return e.hasAttribute('data-i') && !e.classList.contains('hide'); }); }
      function clearSel() {
        document.querySelectorAll('.sel-on').forEach(function (e) { e.classList.remove('sel-on'); });
        document.querySelectorAll('.mcell.selected').forEach(function (e) { e.classList.remove('selected'); });
      }
      function setSel(n, scroll) {
        var els = visibleEls(); if (!els.length) return;
        n = Math.max(0, Math.min(els.length - 1, n)); state.sel = n; clearSel();
        var el = els[n]; el.classList.add('sel-on');
        var d = DATA[parseInt(el.getAttribute('data-i'), 10)]; d.m.classList.add('selected');
        if (scroll !== false) el.scrollIntoView({ block: 'nearest', behavior: reduce ? 'auto' : 'smooth' });
      }
      function colsOf(els) { if (state.view !== 'grid' || !els.length) return 1; var top = els[0].offsetTop, c = 0; for (var i = 0; i < els.length; i++) { if (els[i].offsetTop === top) c++; else break; } return Math.max(1, c); }
      function openSel() { var els = visibleEls(); if (state.sel > -1 && els[state.sel]) window.location.href = els[state.sel].getAttribute('href'); else if (els.length === 1) window.location.href = els[0].getAttribute('href'); }

      var qInput = $('searchInput');
      document.addEventListener('keydown', function (e) {
        var typing = document.activeElement === qInput;
        if (e.key === '/' && !typing) { e.preventDefault(); qInput.focus(); qInput.select(); return; }
        if (e.key === 'Escape') { if (typing) qInput.blur(); resetAll(); return; }
        if (e.key === 'Enter' && (typing || state.sel > -1)) { if (document.activeElement && document.activeElement.tagName === 'A') return; e.preventDefault(); openSel(); return; }
        if (typing && !(e.key === 'ArrowDown' || e.key === 'ArrowUp')) return;
        if (!typing && (e.key === 'r' || e.key === 'R') && !e.ctrlKey && !e.metaKey) { randomFile(); return; }
        var els = visibleEls(), c = colsOf(els);
        if (e.key === 'ArrowDown') { e.preventDefault(); setSel(state.sel < 0 ? 0 : state.sel + c); }
        else if (e.key === 'ArrowUp') { e.preventDefault(); setSel(state.sel < 0 ? 0 : state.sel - c); }
        else if (e.key === 'ArrowRight' && state.view === 'grid') { e.preventDefault(); setSel(state.sel < 0 ? 0 : state.sel + 1); }
        else if (e.key === 'ArrowLeft' && state.view === 'grid') { e.preventDefault(); setSel(state.sel < 0 ? 0 : state.sel - 1); }
      });

      /* ══ CONTROLS ══ */
      function setQuery(v) { state.q = (v || '').trim(); apply(true); }
      window.__dvdFilter = function (v) { if (qInput.value !== v) qInput.value = v; setQuery(v); };
      qInput.addEventListener('input', function () { setQuery(qInput.value); });

      document.querySelectorAll('#legend .legend-item').forEach(function (it) {
        var k = it.getAttribute('data-tier');
        it.style.setProperty('--cc', TIERS[k].color);
        it.setAttribute('role', 'button'); it.setAttribute('tabindex', '0');
        it.insertAdjacentHTML('beforeend', '<span class="legend-count">' + count[k] + '</span>');
        if (!count[k]) it.classList.add('empty');
        function tog() { state.tiers[k] = !state.tiers[k]; apply(true); }
        it.addEventListener('click', tog);
        it.addEventListener('keydown', function (e) { if (e.key === 'Enter' || e.key === ' ') { e.preventDefault(); tog(); } });
      });

      document.querySelectorAll('#viewGroup .seg-btn').forEach(function (b) { b.addEventListener('click', function () { setView(b.getAttribute('data-view')); }); });
      var sortSel = $('sortSel');
      sortSel.addEventListener('change', function () { state.sort = sortSel.value; applySort(); apply(true); });

      function resetAll() { state.q = ''; state.tiers = {}; qInput.value = ''; apply(true); }
      $('clearBtn').addEventListener('click', resetAll);

      var rolling = false;
      function randomFile() {
        if (rolling) return;
        var els = visibleEls(); if (!els.length) { els = Array.prototype.slice.call(activeContainer().children).filter(function (e) { return e.hasAttribute('data-i'); }); }
        var target = els[(Math.random() * els.length) | 0];
        if (reduce) { window.location.href = target.getAttribute('href'); return; }
        rolling = true; var steps = 0, total = 16;
        (function step() {
          var cur = els[(Math.random() * els.length) | 0]; if (steps === total) cur = target;
          clearSel(); cur.classList.add('sel-on'); cur.scrollIntoView({ block: 'nearest' });
          var d = DATA[parseInt(cur.getAttribute('data-i'), 10)]; d.m.classList.add('selected');
          steps++;
          if (steps > total) { setTimeout(function () { window.location.href = target.getAttribute('href'); }, 350); return; }
          setTimeout(step, 40 + steps * steps * 1.6);
        })();
      }
      $('randBtn').addEventListener('click', randomFile);

      $('mapToggle').addEventListener('click', function () {
        state.map = !state.map; mapEl.classList.toggle('closed', !state.map); this.textContent = state.map ? '\u25BE HIDE MAP' : '\u25B8 SHOW MAP';
      });

      /* ══ HEADER DONUT / COUNTS / CLOCK / TICKER ══ */
      (function () {
        var total = DATA.length, C = 2 * Math.PI * 65, off = 0, g = $('donutSegs'), html = '', segs = [];
        ORDER.forEach(function (k) {
          if (!count[k]) return;
          var len = count[k] / total * C;
          html += '<circle class="donut-seg" cx="85" cy="85" r="65" fill="none" stroke="' + TIERS[k].color + '" stroke-width="11" stroke-dasharray="0 ' + C + '" stroke-dashoffset="' + (-off) + '" transform="rotate(-90 85 85)" data-len="' + len + '"/>';
          off += len;
        });
        g.innerHTML = html;
        var segsEls = g.querySelectorAll('circle');
        function grow() { segsEls.forEach(function (c) { var len = parseFloat(c.getAttribute('data-len')); c.setAttribute('stroke-dasharray', Math.max(0, len - 2.5) + ' ' + (C - len + 2.5)); }); }
        if (reduce) grow(); else setTimeout(grow, 400);

        $('totalCount').textContent = total; $('listedCount').textContent = total;
        var el = $('donutCount');
        if (reduce) el.textContent = total;
        else { var t0 = performance.now(); (function step(now) { var t = Math.min(1, (now - t0) / 1600); el.textContent = Math.round(total * (1 - Math.pow(1 - t, 3))); if (t < 1) requestAnimationFrame(step); })(t0); }

        var clock = $('clock');
        function tick() { var d = new Date(); function z(n) { return (n < 10 ? '0' : '') + n; } clock.textContent = z(d.getUTCHours()) + ':' + z(d.getUTCMinutes()) + ':' + z(d.getUTCSeconds()); }
        tick(); setInterval(tick, 1000);

        var recent = ['097', '096', '095', '093', '091', '089', '088', '082', '080', '079', '072', '069', '068', '066', '057', '050', '044', '016', '014', '013'];
        var th = '';
        for (var r = 0; r < 2; r++) recent.forEach(function (n) {
          var d = DATA.filter(function (x) { return x.id === 'LD-' + n; })[0]; if (!d) return;
          th += '<a class="ticker-item" href="' + d.href + '"><b>' + d.id + '</b>' + esc(d.name || '') + '</a>';
        });
        $('tickerTrack').innerHTML = th;
      })();

      /* ══ TITLE GLITCH / SPOTLIGHT / REVEAL ══ */
      (function () {
        var t = $('siteTitle');
        function fire() { if (reduce) return; t.classList.add('glitch'); setTimeout(function () { t.classList.remove('glitch'); }, 420); }
        t.addEventListener('mouseenter', fire);
        (function loop() { setTimeout(function () { fire(); loop(); }, 4500 + Math.random() * 5000); })();
        setTimeout(fire, 1200);

        var raf = null, px = 0, py = 0;
        window.addEventListener('pointermove', function (e) {
          px = e.clientX; py = e.clientY; if (raf) return;
          raf = requestAnimationFrame(function () { raf = null; root.style.setProperty('--mx', px + 'px'); root.style.setProperty('--my', py + 'px'); });
        }, { passive: true });

        var els = document.querySelectorAll('.reveal');
        if (!('IntersectionObserver' in window)) { els.forEach(function (e) { e.classList.add('in'); }); return; }
        var io = new IntersectionObserver(function (en) { en.forEach(function (x) { if (x.isIntersecting) { x.target.classList.add('in'); io.unobserve(x.target); } }); }, { threshold: 0.06 });
        els.forEach(function (e) { io.observe(e); });
      })();

      /* ══ DATA RAIN ══ */
      (function () {
        if (reduce) return;
        var cv = $('rain'), ctx = cv.getContext('2d'), W, H, cols, drops, fs = 16, last = 0;
        var GL = '01\u2588\u2593ABCDEF0123456789'.split(''), ETD = ['\u0395', '\u03A4', '\u0394'];
        function resize() {
          W = cv.width = window.innerWidth; H = cv.height = window.innerHeight; cols = Math.ceil(W / fs); drops = [];
          for (var i = 0; i < cols; i++) drops.push({ y: Math.random() * -H / fs, sp: 0.15 + Math.random() * 0.4, etd: -1 });
          ctx.fillStyle = '#080808'; ctx.fillRect(0, 0, W, H);
        }
        resize(); window.addEventListener('resize', resize);
        function frame(t) {
          requestAnimationFrame(frame); if (t - last < 55) return; last = t;
          ctx.fillStyle = 'rgba(8,8,8,0.12)'; ctx.fillRect(0, 0, W, H); ctx.font = fs + 'px "Share Tech Mono", monospace';
          for (var i = 0; i < cols; i++) {
            var d = drops[i], ch;
            if (d.etd >= 0) { ch = ETD[d.etd]; d.etd = d.etd < 2 ? d.etd + 1 : -1; ctx.fillStyle = 'rgba(255,60,60,0.95)'; }
            else {
              ch = GL[(Math.random() * GL.length) | 0];
              if (Math.random() < 0.0025) { ch = ETD[0]; d.etd = 1; ctx.fillStyle = 'rgba(255,60,60,0.95)'; }
              else ctx.fillStyle = Math.random() < 0.06 ? 'rgba(255,70,70,0.6)' : 'rgba(150,10,10,0.38)';
            }
            ctx.fillText(ch, i * fs, d.y * fs); d.y += d.sp * 3;
            if (d.y * fs > H && Math.random() > 0.975) { d.y = 0; d.sp = 0.15 + Math.random() * 0.4; }
          }
        }
        requestAnimationFrame(frame);
      })();

      /* ══ INIT ══ */
      readHash();
      sortSel.value = ['idasc', 'iddesc', 'classasc', 'classdesc', 'name'].indexOf(state.sort) > -1 ? state.sort : 'idasc';
      state.sort = sortSel.value;
      qInput.value = state.q;
      applySort(); setView(state.view); apply(false);
    })();
  </script>

</body>
</html>
