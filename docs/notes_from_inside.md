
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#080808">
  <title>D.I.V.I.D.E. — Classification System</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;500;600;700&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    :root { --tc: 204,0,0; --bg: #070709; --ink: #c0c0c0; --panel: rgba(10,10,13,0.88); }

    html { scroll-behavior: smooth; }

    body { background: var(--bg); color: var(--ink); font-family: 'Share Tech Mono', monospace; min-height: 100vh; overflow-x: hidden; position: relative; }
    :focus-visible { outline: 2px solid rgb(var(--tc)); outline-offset: 2px; }

    #bg, #wave { position: fixed; inset: 0; width: 100%; height: 100%; pointer-events: none; }
    #bg { z-index: 0; } #wave { z-index: 60; }
    .ov-vig { position: fixed; inset: 0; z-index: 2; pointer-events: none; background: radial-gradient(ellipse at 50% 40%, transparent 45%, rgba(0,0,0,0.82) 100%); }
    .ov-edge { position: fixed; inset: 0; z-index: 3; pointer-events: none; box-shadow: inset 0 0 160px rgba(var(--tc), 0.16); transition: box-shadow 0.6s; }
    .ov-void { position: fixed; inset: 0; z-index: 4; pointer-events: none; background: radial-gradient(circle at 50% 50%, transparent 40%, rgba(255,255,255,0.22) 100%); opacity: var(--vw, 0); }
    body::after { content: ''; position: fixed; inset: 0; z-index: 90; pointer-events: none; background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(255,255,255,0.011) 3px, rgba(255,255,255,0.011) 4px); }
    .omega-msg { position: fixed; inset: 0; z-index: 95; display: flex; align-items: center; justify-content: center; pointer-events: none; font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: clamp(34px, 9vw, 110px); letter-spacing: 14px; color: #fff; background: radial-gradient(circle, rgba(255,255,255,0.55), rgba(255,255,255,0) 70%); opacity: 0; text-shadow: 0 0 40px #fff; }
    .omega-msg.go { animation: omg 3.2s ease-out forwards; }
    @keyframes omg { 0% { opacity: 0; } 15% { opacity: 1; } 70% { opacity: 1; } 100% { opacity: 0; } }

    .warning-bar { background: repeating-linear-gradient(135deg, #8b0000 0 18px, #7a0000 18px 36px); color: #fff; text-align: center; padding: 7px 10px; font-size: 11px; letter-spacing: 3px; text-transform: uppercase; border-bottom: 1px solid #ff0000; position: relative; z-index: 100; text-shadow: 0 1px 2px rgba(0,0,0,0.6); }
    .container { max-width: 1000px; margin: 0 auto; padding: 36px 20px 30px; position: relative; z-index: 10; }
    .back-link { display: inline-flex; align-items: center; gap: 8px; color: #666; text-decoration: none; font-size: 11px; letter-spacing: 2px; margin-bottom: 20px; transition: color 0.2s, gap 0.2s; }
    .back-link:hover { color: #cc0000; gap: 14px; }
    .reveal { opacity: 0; transform: translateY(18px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .reveal.in { opacity: 1; transform: none; }

    /* header */
    .header { border: 1px solid #3a0000; padding: 36px 32px 30px; margin-bottom: 30px; position: relative; overflow: hidden; background: linear-gradient(180deg, rgba(15,0,0,0.92) 0%, rgba(8,8,8,0.94) 100%); box-shadow: inset 0 0 80px rgba(139,0,0,0.08), 0 0 50px rgba(139,0,0,0.08); }
    .header::before { content: '// CLASSIFIED //'; position: absolute; top: -10px; left: 20px; background: var(--bg); padding: 0 10px; color: #8b0000; font-size: 11px; letter-spacing: 3px; }
    .header::after { content: ''; position: absolute; top: 0; right: 0; width: 44px; height: 44px; border-top: 2px solid #8b0000; border-right: 2px solid #8b0000; }
    .hline { position: absolute; left: 0; bottom: 0; width: 100%; height: 2px; background: linear-gradient(90deg, #4fc3f7, #4caf50, #ffd600, #e65100, #f44336, #9c27b0, #cc00cc, #fff, #ff69b4); }
    .hspec { display: flex; gap: 6px; margin: 18px 0 4px; flex-wrap: wrap; }
    .hspec i { width: 38px; height: 6px; background: var(--c); box-shadow: 0 0 10px var(--c); display: block; opacity: 0.9; transition: transform 0.2s; }
    .hspec i:hover { transform: scaleY(2.2); }
    .site-title { position: relative; display: inline-block; font-family: 'Rajdhani', sans-serif; font-size: 60px; font-weight: 700; color: #cc0000; letter-spacing: 7px; line-height: 1.02; text-shadow: 0 0 24px rgba(200,0,0,0.45); margin-bottom: 8px; cursor: default; }
    .site-title::before, .site-title::after { content: attr(data-text); position: absolute; left: 0; top: 0; width: 100%; opacity: 0; pointer-events: none; text-shadow: none; }
    .site-title::before { color: #00e5ff; clip-path: inset(0 0 58% 0); } .site-title::after { color: #ff0040; clip-path: inset(58% 0 0 0); }
    .site-title.glitch { animation: tj 0.4s steps(2) 1; } .site-title.glitch::before { opacity: 0.85; animation: g1 0.4s steps(3) 1; } .site-title.glitch::after { opacity: 0.85; animation: g2 0.4s steps(3) 1; }
    @keyframes tj { 0% { transform: translate(0,0); } 30% { transform: translate(2px,-1px); } 60% { transform: translate(-2px,1px); } 100% { transform: none; } }
    @keyframes g1 { 0% { transform: translate(-6px,0); } 50% { transform: translate(5px,-2px); } 100% { transform: translate(-3px,1px); } }
    @keyframes g2 { 0% { transform: translate(6px,0); } 50% { transform: translate(-5px,2px); } 100% { transform: translate(3px,-1px); } }
    @media (max-width: 700px) { .site-title { font-size: 32px; letter-spacing: 3px; } .header { padding: 26px 18px 22px; } }
    .site-subtitle { font-size: 12px; color: #6a6a6a; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 16px; }
    .clearance-badge { display: inline-flex; align-items: center; gap: 10px; border: 1px solid #8b0000; color: #8b0000; font-size: 10px; letter-spacing: 3px; padding: 6px 14px; text-transform: uppercase; background: rgba(139,0,0,0.06); }
    .clearance-badge::before { content: ''; width: 9px; height: 11px; border: 1.5px solid #cc0000; border-radius: 2px 2px 1px 1px; box-shadow: 0 -5px 0 -2px #cc0000; }

    .section-label { font-size: 10px; letter-spacing: 4px; color: #8b0000; text-transform: uppercase; margin-bottom: 16px; margin-top: 44px; padding-bottom: 7px; border-bottom: 1px solid #1a0000; display: flex; justify-content: space-between; align-items: center; gap: 12px; position: relative; }
    .section-label::after { content: ''; position: absolute; left: 0; bottom: -1px; width: 90px; height: 2px; background: linear-gradient(90deg, rgb(var(--tc)), transparent); }
    .section-label button { background: none; border: none; color: #5a3a3a; font-family: inherit; font-size: 9px; letter-spacing: 2px; cursor: pointer; text-transform: uppercase; } .section-label button:hover { color: #ff2a2a; }

    /* class cards */
    .class-card { --cc: 150,150,150; position: relative; border: 1px solid #1c1c1c; border-left: 4px solid rgb(var(--cc)); margin-bottom: 12px; overflow: hidden; background: var(--panel); backdrop-filter: blur(2px); transition: box-shadow 0.3s, border-color 0.3s, transform 0.3s; --cx: 50%; --cy: 50%; }
    .class-card::before { content: attr(data-n); position: absolute; right: 12px; top: -22px; font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 140px; line-height: 1; color: transparent; -webkit-text-stroke: 1px rgba(var(--cc), 0.16); pointer-events: none; }
    .class-card::after { content: ''; position: absolute; inset: 0; pointer-events: none; opacity: 0; transition: opacity 0.3s; background: radial-gradient(300px circle at var(--cx) var(--cy), rgba(var(--cc), 0.14), transparent 70%); }
    .class-card:hover { box-shadow: 0 0 36px rgba(var(--cc), 0.16); transform: translateX(3px); } .class-card:hover::after { opacity: 1; }
    .class-card.active { box-shadow: 0 0 44px rgba(var(--cc), 0.22), inset 0 0 40px rgba(var(--cc), 0.05); }
    .class-header { position: relative; z-index: 2; display: flex; align-items: center; gap: 16px; padding: 14px 18px; cursor: pointer; transition: background 0.2s; user-select: none; }
    .class-header:hover { background: rgba(255,255,255,0.025); }
    .class-badge { font-family: 'Rajdhani', sans-serif; font-size: 26px; font-weight: 700; letter-spacing: 2px; min-width: 64px; color: rgb(var(--cc)); text-shadow: 0 0 14px rgba(var(--cc), 0.5); }
    .class-name { font-family: 'Rajdhani', sans-serif; font-size: 15px; font-weight: 600; letter-spacing: 3px; text-transform: uppercase; flex: 1; color: rgb(var(--cc)); }
    .glyph { width: 46px; height: 46px; flex-shrink: 0; color: rgb(var(--cc)); filter: drop-shadow(0 0 6px rgba(var(--cc), 0.7)); overflow: visible; }
    .gauge { display: flex; gap: 3px; } .gauge i { width: 14px; height: 6px; background: #1a1a1a; display: block; } .gauge i.on { background: rgb(var(--cc)); box-shadow: 0 0 8px rgb(var(--cc)); }
    .chev { color: #555; font-size: 12px; transition: transform 0.3s; margin-left: 4px; } .collapsed .chev { transform: rotate(-90deg); }
    @media (max-width: 640px) { .gauge { display: none; } .glyph { width: 34px; height: 34px; } }
    .cb-wrap { display: grid; grid-template-rows: 1fr; transition: grid-template-rows 0.4s ease; position: relative; z-index: 2; }
    .collapsed .cb-wrap { grid-template-rows: 0fr; }
    .class-body { min-height: 0; overflow: hidden; padding: 0 18px 16px 18px; font-size: 12px; line-height: 1.9; color: #8a8a8a; border-top: 1px solid #141414; }
    .collapsed .class-body { padding-bottom: 0; border-top-color: transparent; }
    .class-body p { margin-top: 10px; }
    .class-body .example { margin-top: 12px; padding: 11px 15px; background: rgba(5,5,7,0.8); border-left: 2px solid rgba(var(--cc), 0.5); font-size: 11px; color: #6c6c6c; font-style: italic; }
    .class-body strong.k { color: #cfcfcf; }

    .c0 { --cc: 136,136,136; } .c1 { --cc: 79,195,247; } .c2 { --cc: 76,175,80; } .c3 { --cc: 255,214,0; } .c4 { --cc: 255,110,20; }
    .c5 { --cc: 244,67,54; } .c6 { --cc: 190,80,220; } .c7 { --cc: 220,20,220; } .comega { --cc: 255,255,255; } .credacted { --cc: 255,105,180; }
    .c7 .class-name { animation: gl7 4s steps(1) infinite; }
    @keyframes gl7 { 0%,92%,100% { transform: none; text-shadow: none; } 93% { transform: translateX(4px); text-shadow: -3px 0 #00e5ff, 3px 0 #ff0040; } 95% { transform: translateX(-4px); } 96% { transform: none; } }
    .comega { background: rgba(2,2,3,0.94); border-color: #333; box-shadow: 0 0 60px rgba(255,255,255,0.06); }
    .comega .class-body p:first-child { font-family: 'Rajdhani', sans-serif; font-size: 24px; letter-spacing: 3px; color: #fff; text-shadow: 0 0 20px rgba(255,255,255,0.6); line-height: 1.4; }
    .credacted .class-body .example { letter-spacing: 3px; }

    /* glyph animations */
    .gy-spin { transform-box: fill-box; transform-origin: center; animation: spin 14s linear infinite; } .gy-spin.r { animation-direction: reverse; animation-duration: 9s; }
    @keyframes spin { to { transform: rotate(360deg); } }
    .gy-br { transform-box: fill-box; transform-origin: center; animation: breathe 3.6s ease-in-out infinite; } @keyframes breathe { 50% { transform: scale(1.18); opacity: 0.7; } }
    .gy-gl { animation: gyg 2.2s steps(1) infinite; } @keyframes gyg { 0%,80% { transform: none; } 85% { transform: translate(3px,-2px); } 90% { transform: translate(-3px,2px); } 95% { transform: none; } }
    .gy-sk { transform-box: fill-box; transform-origin: center; animation: sk 4s ease-in-out infinite; } @keyframes sk { 0%,100% { transform: skew(0,0); } 50% { transform: skew(14deg, 6deg); } }

    /* info boxes */
    .info-box { background: var(--panel); border: 1px solid #1a1a1a; border-left: 3px solid #8b0000; padding: 20px 22px; margin-bottom: 12px; font-size: 12px; line-height: 1.9; color: #8a8a8a; position: relative; backdrop-filter: blur(2px); transition: border-left-color 0.25s, box-shadow 0.25s; }
    .info-box:hover { border-left-color: rgb(var(--tc)); box-shadow: 0 0 28px rgba(var(--tc), 0.1); }
    .info-box h3 { font-family: 'Rajdhani', sans-serif; font-size: 16px; letter-spacing: 3px; color: #bbb; margin-bottom: 10px; text-transform: uppercase; }
    .info-box ul { padding-left: 18px; color: #7a7a7a; } .info-box ul li { margin-bottom: 6px; transition: color 0.2s, transform 0.2s; cursor: default; }
    .info-box ul li:hover { color: #ddd; transform: translateX(4px); }
    .info-box strong.k { color: #cfcfcf; }
    .ldx { font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 44px; letter-spacing: 4px; color: #fff; margin: 4px 0 12px; text-shadow: 0 0 20px rgba(var(--tc), 0.6); display: flex; flex-wrap: wrap; align-items: baseline; }
    .ldx .r { display: inline-block; max-width: 0; overflow: hidden; white-space: nowrap; color: #aaa; font-size: 32px; transition: max-width 1.6s ease 0.5s; } .ldx.in .r { max-width: 6em; } .ldx .sp { width: 0.4em; }
    .reg { display: grid; grid-template-columns: repeat(20, 1fr); gap: 3px; margin: 14px 0 4px; }
    @media (max-width: 640px) { .reg { grid-template-columns: repeat(10, 1fr); } }
    .reg i { aspect-ratio: 1; background: rgba(120,140,170,0.25); display: block; transition: background 0.3s, box-shadow 0.3s, transform 0.3s; }
    .reg i.m { background: transparent; border: 1px dashed #333; }
    .reg i.hot { transform: scale(1.35); z-index: 2; position: relative; }
    .reg i.hot.r0 { background: #ff3a3a; box-shadow: 0 0 10px #ff3a3a; } .reg i.hot.r1 { background: #b0b0ff; box-shadow: 0 0 10px #b0b0ff; } .reg i.hot.r2 { background: #ffd600; box-shadow: 0 0 10px #ffd600; } .reg i.hot.r3 { background: #4fc3f7; box-shadow: 0 0 10px #4fc3f7; }
    .regcap { font-size: 9px; letter-spacing: 3px; color: #555; text-transform: uppercase; }

    /* pulses */
    .psim { padding: 22px 24px; margin: 6px 0 16px; background: var(--panel); border: 1px solid #1a2a3a; border-left: 3px solid rgb(var(--pc, 79,195,247)); position: relative; }
    .psim::before { content: 'PULSE SEISMOGRAPH — SIMULATION'; position: absolute; top: -9px; left: 18px; background: var(--bg); padding: 0 10px; color: rgb(var(--pc, 79,195,247)); font-size: 10px; letter-spacing: 3px; }
    #seis { width: 100%; height: 190px; display: block; background: rgba(3,6,10,0.85); border: 1px solid #14202c; margin-bottom: 14px; }
    .lvls { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 12px; }
    .btn { background: rgba(10,10,14,0.92); color: #aaa; border: 1px solid #2a2a33; font-family: 'Share Tech Mono', monospace; font-size: 11px; letter-spacing: 2px; padding: 10px 16px; cursor: pointer; text-transform: uppercase; transition: all 0.22s; }
    .btn:hover:not(:disabled) { color: #fff; border-color: rgb(var(--bc, 200,200,200)); box-shadow: 0 0 18px rgba(var(--bc, 200,200,200), 0.35); transform: translateY(-1px); }
    .btn.on { background: rgba(var(--bc), 0.2); color: #fff; border-color: rgb(var(--bc)); }
    .btn.pri { border-color: rgb(var(--pc, 79,195,247)); color: #fff; background: rgba(var(--pc, 79,195,247), 0.2); }
    .btn.dng { border-color: #6a0000; color: #ff6a6a; } .btn:disabled { opacity: 0.4; cursor: default; }
    .pbtns { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 12px; }
    .plog { font-size: 12px; line-height: 1.8; min-height: 96px; color: #7a8aa0; border-left: 2px solid #1a2a3a; padding-left: 12px; }
    .plog div { animation: logIn 0.4s ease both; } .plog .r { color: #ff6a6a; } .plog .g { color: #8affb0; }
    @keyframes logIn { from { opacity: 0; transform: translateX(-6px); } to { opacity: 1; transform: none; } }

    .pulse-card { --pc: 150,150,150; position: relative; display: flex; gap: 18px; align-items: center; padding: 14px 18px; border: 1px solid #1a1a1a; border-left: 4px solid rgb(var(--pc)); margin-bottom: 8px; font-size: 12px; background: var(--panel); overflow: hidden; transition: transform 0.25s, box-shadow 0.25s; }
    .pulse-card:hover { transform: translateX(5px); box-shadow: 0 0 30px rgba(var(--pc), 0.18); }
    .pulse-card .body { flex: 1; min-width: 0; }
    .pulse-level { font-family: 'Rajdhani', sans-serif; font-size: 34px; font-weight: 700; min-width: 40px; letter-spacing: 1px; color: rgb(var(--pc)); text-shadow: 0 0 14px rgba(var(--pc), 0.6); line-height: 1; }
    .pulse-name { font-size: 12px; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 4px; color: rgb(var(--pc)); }
    .pulse-desc { color: #7a7a7a; font-size: 11px; line-height: 1.7; }
    .mw { width: 130px; height: 44px; flex-shrink: 0; overflow: visible; } @media (max-width: 640px) { .mw { display: none; } }
    .mw path { fill: none; stroke: rgb(var(--pc)); stroke-width: 1.6; stroke-linejoin: round; filter: drop-shadow(0 0 4px rgb(var(--pc))); stroke-dasharray: 260; animation: mwd 3.2s linear infinite; }
    @keyframes mwd { from { stroke-dashoffset: 260; } to { stroke-dashoffset: -260; } }
    .p1 { --pc: 79,195,247; } .p2 { --pc: 76,175,80; } .p3 { --pc: 255,214,0; } .p4 { --pc: 255,110,20; } .p5 { --pc: 244,67,54; } .p6 { --pc: 190,80,220; } .pomega { --pc: 255,255,255; }
    .pomega { background: rgba(2,2,3,0.95); }

    /* clearance */
    .cterm { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; margin-bottom: 14px; padding: 14px 16px; background: var(--panel); border: 1px solid #2a1010; }
    .cterm .lbl { font-size: 10px; letter-spacing: 3px; color: #7a5a5a; text-transform: uppercase; margin-right: 8px; }
    .cterm .btn { padding: 8px 14px; --bc: 255,60,60; }
    .clearance-card { --lv: 0; position: relative; display: flex; gap: 18px; padding: 16px 20px; border: 1px solid #1a1a1a; border-left: 3px solid #3a0000; margin-bottom: 7px; align-items: flex-start; background: var(--panel); transition: border-color 0.25s, background 0.25s, transform 0.25s; overflow: hidden; }
    .clearance-card:hover { border-left-color: #cc0000; background: rgba(20,0,0,0.9); transform: translateX(5px); }
    .clearance-card::before { content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: calc(var(--lv) * 12.5%); background: linear-gradient(90deg, rgba(204,0,0,0.12), transparent); pointer-events: none; }
    .clearance-level { font-family: 'Rajdhani', sans-serif; font-size: 40px; font-weight: 700; color: #cc0000; min-width: 40px; line-height: 1; text-shadow: 0 0 14px rgba(204,0,0,0.5); }
    .clearance-title { font-size: 13px; letter-spacing: 2px; color: #cc0000; text-transform: uppercase; margin-bottom: 5px; }
    .clearance-desc { font-size: 11px; color: #7a7a7a; line-height: 1.8; transition: filter 0.4s; }
    .clearance-card.locked .clearance-desc, .clearance-card.locked .clearance-title { filter: blur(5px); }
    .clearance-card.locked::after { content: 'ACCESS DENIED'; position: absolute; right: 16px; top: 50%; transform: translateY(-50%); font-size: 12px; letter-spacing: 6px; color: #ff4444; border: 2px solid #ff4444; padding: 4px 12px; background: rgba(20,0,0,0.85); font-family: 'Rajdhani', sans-serif; font-weight: 700; }
    .dcard { border-left-color: #cc0000; background: rgba(13,0,0,0.9); box-shadow: 0 0 40px rgba(204,0,0,0.12); flex-wrap: wrap; }
    .dcard .clearance-level { color: #ff4444; font-size: 20px; letter-spacing: 1px; padding-top: 6px; min-width: 100px; }
    .dcard .clearance-title { color: #ff4444; }
    .nuke { width: 100%; padding-top: 14px; margin-top: 4px; border-top: 1px solid #2a0000; }
    .wh { display: grid; grid-template-columns: repeat(25, 1fr); gap: 4px; margin-bottom: 12px; }
    @media (max-width: 640px) { .wh { grid-template-columns: repeat(10, 1fr); } }
    .wh i { aspect-ratio: 1 / 1.6; background: #1a0808; clip-path: polygon(50% 0, 100% 40%, 100% 100%, 0 100%, 0 40%); display: block; transition: background 0.2s, box-shadow 0.2s; }
    .wh.armed i { background: #ff2a2a; animation: whl 0.5s ease both; animation-delay: calc(var(--i) * 40ms); }
    @keyframes whl { from { background: #1a0808; } to { background: #ff2a2a; } }
    .hold { position: relative; overflow: hidden; border-color: #8b0000; color: #ff6a6a; user-select: none; touch-action: none; }
    .hold .fill { position: absolute; left: 0; top: 0; bottom: 0; width: 0; background: rgba(255,40,40,0.5); }
    .hold span { position: relative; }
    .nmsg { font-size: 11px; letter-spacing: 2px; color: #a06060; margin-top: 10px; min-height: 18px; text-transform: uppercase; }

    /* ladder + hud */
    .ladder { position: fixed; right: 14px; top: 50%; transform: translateY(-50%); z-index: 700; display: flex; flex-direction: column; gap: 9px; }
    @media (max-width: 1100px) { .ladder { display: none; } }
    .ladder a { position: relative; width: 12px; height: 12px; border-radius: 50%; background: rgba(var(--dc), 0.35); border: 1px solid rgba(var(--dc), 0.8); display: block; transition: transform 0.2s, background 0.2s, box-shadow 0.2s; }
    .ladder a:hover { transform: scale(1.5); background: rgb(var(--dc)); }
    .ladder a.on { background: rgb(var(--dc)); box-shadow: 0 0 14px rgb(var(--dc)); transform: scale(1.4); }
    .ladder a span { position: absolute; right: 22px; top: 50%; transform: translateY(-50%); white-space: nowrap; font-size: 10px; letter-spacing: 2px; color: rgb(var(--dc)); background: rgba(5,5,7,0.92); padding: 3px 8px; border: 1px solid rgba(var(--dc), 0.5); opacity: 0; pointer-events: none; transition: opacity 0.2s; text-transform: uppercase; }
    .ladder a:hover span { opacity: 1; }
    .hud-r { position: fixed; right: 14px; bottom: 14px; z-index: 700; width: 176px; padding: 8px 10px 8px; background: rgba(6,6,8,0.9); border: 1px solid rgba(var(--tc), 0.35); text-align: center; }
    .hud-r svg { width: 100%; height: auto; display: block; overflow: visible; }
    .hud-r .lab { font-size: 9px; letter-spacing: 2px; color: rgb(var(--tc)); text-transform: uppercase; margin-top: 2px; min-height: 24px; line-height: 1.3; }
    @media (max-width: 700px) { .hud-r { display: none; } }
    .needle { transform-origin: 70px 70px; transition: transform 0.9s cubic-bezier(.3,1.4,.4,1); }
    .hud-l { position: fixed; left: 14px; bottom: 14px; z-index: 700; }
    .hud-l button { background: rgba(6,6,8,0.9); color: #aaa; border: 1px solid #333; padding: 7px 12px; font-family: inherit; font-size: 10px; letter-spacing: 2px; cursor: pointer; text-transform: uppercase; }
    .hud-l button:hover { color: #fff; border-color: rgb(var(--tc)); }

    .end-line { display: flex; align-items: center; gap: 14px; margin: 16px 0 20px; color: #3a1a1a; font-size: 10px; letter-spacing: 4px; text-transform: uppercase; }
    .end-line::before, .end-line::after { content: ''; flex: 1; height: 1px; background: linear-gradient(90deg, transparent, #2a0000, transparent); }
    .footer { border-top: 1px solid #1a0000; padding-top: 20px; margin-top: 30px; font-size: 10px; color: #333; letter-spacing: 1px; line-height: 1.8; text-align: center; }

    @media (prefers-reduced-motion: reduce) { .gy-spin, .gy-br, .gy-gl, .gy-sk, .c7 .class-name, .mw path { animation: none !important; } .reveal { opacity: 1; transform: none; transition: none; } }
  </style>
</head>
<body>

  <canvas id="bg" aria-hidden="true"></canvas>
  <canvas id="wave" aria-hidden="true"></canvas>
  <div class="ov-vig"></div><div class="ov-edge"></div><div class="ov-void"></div>
  <div class="omega-msg" id="omegaMsg">THE END WAVE</div>
  <div class="hud-l"><button id="fxBtn" type="button">&#9680; Effects: full</button></div>
  <nav class="ladder" id="ladder" aria-label="Section ladder"></nav>
  <div class="hud-r">
    <svg viewBox="0 0 140 82" aria-hidden="true">
      <path d="M12 70 A58 58 0 0 1 128 70" fill="none" stroke="#222" stroke-width="8"/>
      <path id="dialArc" d="M12 70 A58 58 0 0 1 128 70" fill="none" stroke="rgb(204,0,0)" stroke-width="8" stroke-dasharray="182" stroke-dashoffset="182" style="transition: stroke-dashoffset 0.9s ease, stroke 0.6s"/>
      <g class="needle" id="needle" style="transform: rotate(-90deg)"><line x1="70" y1="70" x2="70" y2="20" stroke="#fff" stroke-width="2.5" stroke-linecap="round"/><circle cx="70" cy="70" r="5" fill="#fff"/></g>
    </svg>
    <div class="lab" id="hudLab">CLASSIFICATION SYSTEM</div>
  </div>

  <div class="warning-bar">
    ⚠ RESTRICTED ACCESS — AUTHORIZED PERSONNEL ONLY — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="container">

    <a href="index.html" class="back-link">← RETURN TO DATABASE INDEX</a>

    <div class="header reveal" data-th="base" data-lab="Top" id="top">
      <div class="hline"></div>
      <div class="site-title" id="siteTitle" data-text="CLASSIFICATION SYSTEM">CLASSIFICATION SYSTEM</div>
      <div class="site-subtitle">Anomaly Threat Levels, Pulse Ratings &amp; Clearance Protocols</div>
      <div class="clearance-badge">Clearance Level 1+ Required</div>
      <div class="hspec" aria-hidden="true"><i style="--c:#4fc3f7"></i><i style="--c:#4caf50"></i><i style="--c:#ffd600"></i><i style="--c:#e65100"></i><i style="--c:#f44336"></i><i style="--c:#9c27b0"></i><i style="--c:#cc00cc"></i><i style="--c:#fff"></i><i style="--c:#ff69b4"></i></div>
    </div>

    <!-- ANOMALY CLASSES -->
    <div class="section-label reveal"><span>// Anomaly Threat Classification //</span><button type="button" id="toggleAll">▾ Collapse all</button></div>

    <div class="class-card c1 reveal" data-th="1" data-lab="Class I" data-n="I" data-gi="1">
      <div class="class-header"><div class="class-badge">I</div><div class="class-name">Low Threat</div></div>
      <div class="cb-wrap"><div class="class-body">
        <p>Minimal risk. Typically stable and harmless anomalies that do not alter their environment or pose significant danger unless provoked.</p>
        <div class="example">Example: A sentient entity that remains passive under standard conditions and exhibits no environmental manipulation.</div>
      </div></div>
    </div>

    <div class="class-card c2 reveal" data-th="2" data-lab="Class II" data-n="II" data-gi="2">
      <div class="class-header"><div class="class-badge">II</div><div class="class-name">Moderate Threat</div></div>
      <div class="cb-wrap"><div class="class-body">
        <p>Some risk, though manageable with standard containment procedures. These anomalies exhibit defensive or reactive behavior under specific circumstances.</p>
        <div class="example">Example: An entity that becomes hostile when approached, but can be stabilized with standard containment protocols.</div>
      </div></div>
    </div>

    <div class="class-card c3 reveal" data-th="3" data-lab="Class III" data-n="III" data-gi="3">
      <div class="class-header"><div class="class-badge">III</div><div class="class-name">High Threat</div></div>
      <div class="cb-wrap"><div class="class-body">
        <p>Potential for significant danger if mishandled. Requires strict monitoring and specialized safety protocols. These anomalies are capable of direct harm or environmental manipulation.</p>
        <div class="example">Example: An entity capable of causing casualties through direct action or reality-adjacent manipulation of its immediate environment.</div>
      </div></div>
    </div>

    <div class="class-card c4 reveal" data-th="4" data-lab="Class IV" data-n="IV" data-gi="4">
      <div class="class-header"><div class="class-badge">IV</div><div class="class-name">Extreme Threat</div></div>
      <div class="cb-wrap"><div class="class-body">
        <p>Significant risk to personnel and surrounding environment. Requires specialized containment and constant monitoring. These anomalies can alter environmental factors or reality within a confined space.</p>
        <div class="example">Example: An anomaly capable of altering local reality, warping physical laws, or neutralizing standard containment measures.</div>
      </div></div>
    </div>

    <div class="class-card c5 reveal" data-th="5" data-lab="Class V" data-n="V" data-gi="5">
      <div class="class-header"><div class="class-badge">V</div><div class="class-name">Catastrophic Threat</div></div>
      <div class="cb-wrap"><div class="class-body">
        <p>Large-scale destructive potential. Full understanding of the entity may not be possible. These anomalies can erase or alter memories, timelines, or existence on a grand scale.</p>
        <div class="example">Example: A reality-warping entity capable of erasing localized existence or restructuring physical and metaphysical elements across wide areas.</div>
      </div></div>
    </div>

    <div class="class-card c6 reveal" data-th="6" data-lab="Class VI" data-n="VI" data-gi="6">
      <div class="class-header"><div class="class-badge">VI</div><div class="class-name">Omega-Class Threat</div></div>
      <div class="cb-wrap"><div class="class-body">
        <p>The most extreme threats known to D.I.V.I.D.E. These entities are capable of overwhelming large-scale destruction, manipulating fundamental aspects of reality, and causing chaos across dimensions. Their power is limitless and exceeds the scope of all standard classification systems.</p>
        <div class="example">Example: An entity whose presence destabilizes entire dimensional strata, rendering standard containment protocols irrelevant.</div>
      </div></div>
    </div>

    <div class="class-card c7 reveal" data-th="7" data-lab="Class VII" data-n="VII" data-gi="7">
      <div class="class-header"><div class="class-badge">VII</div><div class="class-name">[DATA EXPUNGED]</div></div>
      <div class="cb-wrap"><div class="class-body">
        <p>[REDACTED — DIVIDE LEVEL CLEARANCE REQUIRED]</p>
        <div class="example">[ACCESS DENIED]</div>
      </div></div>
    </div>

    <div class="class-card comega reveal" data-th="omega" data-lab="Class Ω" data-n="Ω" data-gi="8">
      <div class="class-header"><div class="class-badge">Ω</div><div class="class-name">The End</div></div>
      <div class="cb-wrap"><div class="class-body">
        <p>There is nothing you can do. We are all dead.</p>
        <p>Ω-Class anomalies are uncontainable, capable of reshaping time, space, and reality itself. Their influence extends far beyond the physical realm. They are often considered apocalyptic in nature. These anomalies exist beyond all known physical or metaphysical constraints — capable of manipulating and controlling life, death, and reality itself.</p>
        <p><strong class="k">Containment:</strong> Impossible. These anomalies defy the fundamental laws of the universe. No measures exist or are theorized to be achievable.</p>
        <div class="example">Anomaly Ω-01: A being whose presence can collapse entire galaxies, alter timelines, or erase life from existence.<br><br>Anomaly Ω-02: A cosmic entity that governs life and death across multiple dimensions, able to create and destroy universes with a single action.</div>
      </div></div>
    </div>

    <div class="class-card credacted reveal" data-th="redacted" data-lab="Redacted" data-n="—" data-gi="9">
      <div class="class-header"><div class="class-badge">—</div><div class="class-name">Redacted Anomalies</div></div>
      <div class="cb-wrap"><div class="class-body">
        <p>Entities that are either too dangerous, unknown, or classified as too great a threat to disclose. These anomalies are beyond containment and may fall under Ω-Class, but their exact nature remains sealed by the highest authorities of D.I.V.I.D.E.</p>
        <p><strong class="k">Access:</strong> D.I.V.I.D.E. Level clearance required. No exceptions.</p>
        <div class="example">[ALL FURTHER DATA SUPPRESSED]</div>
      </div></div>
    </div>

    <!-- HOW ANOMALIES WORK -->
    <div data-th="how" data-lab="How anomalies work">
      <div class="section-label reveal">// How Anomalies Work //</div>

      <div class="info-box reveal">
        <h3>What Does "LD" Stand For?</h3>
        <div class="ldx" id="ldx" aria-hidden="true"><span>L</span><span class="r">iminal</span><span class="sp"></span><span>D</span><span class="r">ivision</span></div>
        <p>The classification code "LD" stands for <strong class="k">Liminal Division</strong> — the division responsible for locating, documenting, and (if possible) containing or neutralizing supernatural, reality-bending, or otherwise anomalous entities and objects. Each anomaly is assigned a unique LD ID number for cataloging and identification.</p>
      </div>

      <div class="info-box reveal">
        <h3>Why Are Some Anomalies Missing?</h3>
        <ul id="whyList">
          <li data-r="0"><strong class="k">Terminated Cases:</strong> Some anomalies were permanently destroyed or neutralized and removed from active records.</li>
          <li data-r="1"><strong class="k">Undiscovered Anomalies:</strong> The world is vast — many anomalies remain hidden or misunderstood. Reports come in daily from across the globe.</li>
          <li data-r="2"><strong class="k">Withheld or Stolen:</strong> Certain individuals have discovered powerful anomalies and taken them for personal use — rogue agents, civilians, and corporate interests.</li>
          <li data-r="3"><strong class="k">Task Force Suppression:</strong> The APA Task Force actively hunts, retrieves, or destroys anomalies before they spread. Some slip through.</li>
        </ul>
        <div class="reg" id="reg" aria-hidden="true"></div>
        <div class="regcap">Illustrative registry — hover a reason to see where records go missing</div>
      </div>

      <div class="info-box reveal">
        <h3>What Qualifies as an Anomaly?</h3>
        <p>Any object, creature, location, or substance that breaks known scientific laws or causes extreme psychological, physical, or dimensional effects. Most anomalies:</p>
        <ul>
          <li>Defy conventional physics or biology</li>
          <li>Exhibit sentience, manipulation, or hostile traits</li>
          <li>Cannot be safely explained or reproduced</li>
          <li>Must be handled under strict containment protocols</li>
        </ul>
      </div>
    </div>

    <!-- PULSES -->
    <div data-th="pulse" data-lab="Pulse system">
      <div class="section-label reveal">// Anomaly Pulse System //</div>

      <div class="info-box reveal" style="margin-bottom: 16px;">
        <h3>What Are Pulses?</h3>
        <p>Pulses are intense bursts of reality distortion that occur exclusively when an anomaly first manifests or breaches into our reality — a signature "rip" in the fabric of space-time. Each anomaly generates exactly one Pulse at the moment of arrival. The magnitude directly reflects the threat level. Pulses are rare, one-time events that cannot be replicated.</p>
      </div>

      <div class="psim reveal" id="psim">
        <canvas id="seis"></canvas>
        <div class="lvls" id="lvls"></div>
        <div class="pbtns">
          <button class="btn pri" id="bManifest" type="button">&#9889; Manifest anomaly</button>
          <button class="btn dng" id="bRep" type="button">&#8635; Replicate pulse</button>
        </div>
        <div class="plog" id="plog"></div>
      </div>

      <div class="pulse-card p1 reveal"><div><div class="pulse-level">1</div></div><div class="body"><div class="pulse-name">Minor Distortion — Class I</div><div class="pulse-desc">Slight, barely noticeable ripples in reality. Often detected only by sensitive instruments. No immediate danger.</div></div></div>
      <div class="pulse-card p2 reveal"><div><div class="pulse-level">2</div></div><div class="body"><div class="pulse-name">Noticeable Ripple — Class II</div><div class="pulse-desc">Detectable dimensional pulses causing mild spatial disturbances. Usually stable but signals an active anomaly.</div></div></div>
      <div class="pulse-card p3 reveal"><div><div class="pulse-level">3</div></div><div class="body"><div class="pulse-name">Severe Fluctuation — Class III</div><div class="pulse-desc">Strong reality disruptions manifesting as visible distortions or auditory anomalies. Can cause environmental interference and requires caution.</div></div></div>
      <div class="pulse-card p4 reveal"><div><div class="pulse-level">4</div></div><div class="body"><div class="pulse-name">Critical Tear — Class IV</div><div class="pulse-desc">Intense, violent rips in space-time. These pulses cause hazardous phenomena around the anomaly's vicinity. Immediate containment necessary.</div></div></div>
      <div class="pulse-card p5 reveal"><div><div class="pulse-level">5</div></div><div class="body"><div class="pulse-name">Catastrophic Rend — Class V</div><div class="pulse-desc">Massive reality ruptures capable of large-scale destruction and erasure of physical or metaphysical elements. Signals an anomaly of global or universal threat.</div></div></div>
      <div class="pulse-card p6 reveal"><div><div class="pulse-level">6</div></div><div class="body"><div class="pulse-name">Omega Surge — Class VI</div><div class="pulse-desc">Uncontainable and omnipresent pulses disrupting multiple dimensions. These surges often precede apocalyptic events or interdimensional collapse.</div></div></div>
      <div class="pulse-card pomega reveal"><div><div class="pulse-level">Ω</div></div><div class="body"><div class="pulse-name">The End Wave — Class Ω</div><div class="pulse-desc">The final, unstoppable pulse signaling total annihilation. All known laws break down. No containment or resistance possible.</div></div></div>
    </div>

    <!-- CLEARANCE LEVELS -->
    <div data-th="clear" data-lab="Clearance levels">
      <div class="section-label reveal">// Clearance Levels //</div>

      <div class="cterm reveal" id="cterm"><span class="lbl">Your clearance</span></div>

      <div class="clearance-card reveal" data-lvl="1" style="--lv:1"><div class="clearance-level">1</div><div><div class="clearance-title">Entry-Level Access</div><div class="clearance-desc">Basic security access. Non-sensitive anomalies and public records only. General staff, researchers, and new personnel.</div></div></div>
      <div class="clearance-card reveal" data-lvl="2" style="--lv:2"><div class="clearance-level">2</div><div><div class="clearance-title">Restricted Access</div><div class="clearance-desc">Specific anomalies and sensitive areas. Limited access to dangerous or volatile entities. Security personnel and authorized technicians.</div></div></div>
      <div class="clearance-card reveal" data-lvl="3" style="--lv:3"><div class="clearance-level">3</div><div><div class="clearance-title">Intermediate Access</div><div class="clearance-desc">Common research and standard containment protocols. Full access to classified anomalies at moderate clearance. Containment staff and researchers on routine high-risk cases.</div></div></div>
      <div class="clearance-card reveal" data-lvl="4" style="--lv:4"><div class="clearance-level">4</div><div><div class="clearance-title">Advanced Access</div><div class="clearance-desc">High-risk anomalies, restricted data, and classified operations. Senior researchers, top-level security personnel, and department heads.</div></div></div>
      <div class="clearance-card reveal" data-lvl="5" style="--lv:5"><div class="clearance-level">5</div><div><div class="clearance-title">Specialized Access</div><div class="clearance-desc">Study of anomalies with dangerous or unknown properties. Leading experts in anomaly research and specialized containment team leaders.</div></div></div>
      <div class="clearance-card reveal" data-lvl="6" style="--lv:6"><div class="clearance-level">6</div><div><div class="clearance-title">Expert Access</div><div class="clearance-desc">Top researchers and operatives with direct anomaly containment responsibilities. Highest-level containment protocols and restricted materials.</div></div></div>
      <div class="clearance-card reveal" data-lvl="7" style="--lv:7"><div class="clearance-level">7</div><div><div class="clearance-title">Omega-Class Access</div><div class="clearance-desc">Full operational control over the most dangerous or unknown entities. Command authority over catastrophic anomaly situations. Top-level operatives with global influence over anomaly management.</div></div></div>

      <div class="clearance-card dcard reveal" data-lvl="8" style="--lv:8">
        <div class="clearance-level">D.I.V.I.D.E.</div>
        <div style="flex:1;min-width:240px;">
          <div class="clearance-title">D.I.V.I.D.E. Clearance — Absolute Authority</div>
          <div class="clearance-desc">The highest level of access. Grants complete authority over all anomalies including execution, containment, and release. Allows override of all containment protocols and authorization of the Foundation's self-destruction — including simultaneous activation of 50 nuclear warheads. Reserved for the highest authorities of the Foundation. Used only in cases of existential crisis or global catastrophe. No sub-levels exist.</div>
        </div>
        <div class="nuke">
          <div class="wh" id="wh" aria-hidden="true"></div>
          <button class="btn hold" id="hold" type="button"><div class="fill" id="holdFill"></div><span>Hold to authorize — simulation</span></button>
          <div class="nmsg" id="nmsg">50 warheads — standing by</div>
        </div>
      </div>
    </div>

    <div class="end-line">End of file</div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

  <script>
    (function () {
      'use strict';
      var reduce = !!(window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches);
      var light = reduce, root = document.documentElement, TAU = Math.PI * 2;
      function $(id) { return document.getElementById(id); }
      function rand(a, b) { return a + Math.random() * (b - a); }
      function clamp(v, a, b) { return v < a ? a : (v > b ? b : v); }
      function pad(n) { return (n < 10 ? '0' : '') + n; }

      var TH = {
        base: { c: [204, 0, 0], m: 'data', l: 'CLASSIFICATION SYSTEM', i: -1 },
        '1': { c: [79, 195, 247], m: 'calm', l: 'CLASS I \u2014 LOW THREAT', i: 0 },
        '2': { c: [76, 175, 80], m: 'flow', l: 'CLASS II \u2014 MODERATE THREAT', i: 1 },
        '3': { c: [255, 214, 0], m: 'spark', l: 'CLASS III \u2014 HIGH THREAT', i: 2 },
        '4': { c: [255, 110, 20], m: 'warp', l: 'CLASS IV \u2014 EXTREME THREAT', i: 3 },
        '5': { c: [244, 67, 54], m: 'rift', l: 'CLASS V \u2014 CATASTROPHIC THREAT', i: 4 },
        '6': { c: [190, 80, 220], m: 'portal', l: 'CLASS VI \u2014 OMEGA-CLASS THREAT', i: 5 },
        '7': { c: [220, 20, 220], m: 'glitch', l: 'CLASS VII \u2014 [DATA EXPUNGED]', i: 6 },
        omega: { c: [255, 255, 255], m: 'void', l: 'CLASS \u03A9 \u2014 THE END', i: 7 },
        redacted: { c: [255, 105, 180], m: 'bars', l: 'REDACTED ANOMALIES', i: 8 },
        how: { c: [130, 160, 200], m: 'data', l: 'HOW ANOMALIES WORK', i: -1 },
        pulse: { c: [79, 195, 247], m: 'ripple', l: 'ANOMALY PULSE SYSTEM', i: -1 },
        clear: { c: [255, 60, 60], m: 'radar', l: 'CLEARANCE LEVELS', i: -1 }
      };
      var MODES = ['calm', 'flow', 'spark', 'warp', 'rift', 'portal', 'glitch', 'void', 'bars', 'data', 'ripple', 'radar'];

      /* ═══ BACKGROUND ═══ */
      var bgCv = $('bg'), g = bgCv.getContext('2d'), wvCv = $('wave'), wv = wvCv.getContext('2d');
      var W = 0, H = 0, dpr = Math.min(window.devicePixelRatio || 1, 1.5);
      var active = 'base', wts = {}, cur = [204, 0, 0], parts = [], waves = [], shakeT = 0, lastCol = '';
      MODES.forEach(function (m) { wts[m] = 0; });
      function mkP() { return { x: rand(0, W), y: rand(0, H), vx: 0, vy: 0, s: rand(1, 2.8), ph: rand(0, TAU) }; }
      var glitchRects = [], glitchT = 0, sparkList = [], sparkT = 0;

      function overlay(m, w, t, col) {
        var i, x, y;
        switch (m) {
          case 'calm': for (i = 0; i < 3; i++) { var gr = g.createRadialGradient(W * (0.2 + i * 0.3), H * 0.6, 0, W * (0.2 + i * 0.3), H * 0.6, 340); gr.addColorStop(0, 'rgba(' + col + ',' + (0.1 * w * (0.7 + 0.3 * Math.sin(t * 0.5 + i))) + ')'); gr.addColorStop(1, 'rgba(' + col + ',0)'); g.fillStyle = gr; g.fillRect(0, 0, W, H); } break;
          case 'flow': g.lineWidth = 1; for (i = 0; i < 14; i++) { g.strokeStyle = 'rgba(' + col + ',' + (0.12 * w) + ')'; g.beginPath(); for (x = 0; x <= W; x += 30) { y = H * (i + 0.5) / 14 + Math.sin(x * 0.006 + t * 0.7 + i) * 26; if (x === 0) g.moveTo(x, y); else g.lineTo(x, y); } g.stroke(); } break;
          case 'spark': if (t - sparkT > 0.12) { sparkT = t; sparkList = []; for (i = 0; i < 5; i++) { var sx = rand(0, W), sy = rand(0, H), pts = [[sx, sy]], k; for (k = 0; k < 6; k++) { sx += rand(-30, 30); sy += rand(8, 40); pts.push([sx, sy]); } sparkList.push(pts); } } g.strokeStyle = 'rgba(' + col + ',' + (0.4 * w) + ')'; g.lineWidth = 1.4; sparkList.forEach(function (p) { g.beginPath(); p.forEach(function (q, j) { if (j === 0) g.moveTo(q[0], q[1]); else g.lineTo(q[0], q[1]); }); g.stroke(); }); break;
          case 'warp': g.lineWidth = 1; g.strokeStyle = 'rgba(' + col + ',' + (0.16 * w) + ')'; for (x = -20; x < W + 40; x += 36) { g.beginPath(); for (y = 0; y <= H; y += 24) { var dx = Math.sin(y * 0.012 + t * 1.2 + x * 0.01) * 16 * w; if (y === 0) g.moveTo(x + dx, y); else g.lineTo(x + dx, y); } g.stroke(); } for (y = 0; y < H; y += 36) { g.beginPath(); for (x = 0; x <= W; x += 24) { var dy = Math.sin(x * 0.012 + t * 1.1 + y * 0.01) * 14 * w; if (x === 0) g.moveTo(x, y + dy); else g.lineTo(x, y + dy); } g.stroke(); } break;
          case 'rift': for (i = 0; i < 6; i++) { var bx = W * (i + 0.5) / 6; g.strokeStyle = 'rgba(' + col + ',' + (0.38 * w * (0.6 + 0.4 * Math.sin(t * 3 + i * 2))) + ')'; g.lineWidth = 2; g.beginPath(); for (y = 0; y <= H; y += 28) { var jx = bx + Math.sin(y * 0.05 + i * 3 + t * 0.4) * 22 + Math.sin(y * 0.21 + i) * 8; if (y === 0) g.moveTo(jx, y); else g.lineTo(jx, y); } g.stroke(); } var rg = g.createLinearGradient(0, H, 0, H * 0.4); rg.addColorStop(0, 'rgba(' + col + ',' + (0.22 * w) + ')'); rg.addColorStop(1, 'rgba(' + col + ',0)'); g.fillStyle = rg; g.fillRect(0, H * 0.4, W, H * 0.6); break;
          case 'portal': g.lineWidth = 1.4; for (i = 0; i < 9; i++) { var r = ((t * 40 + i * 70) % 630) + 10, a = (1 - r / 640) * 0.3 * w; g.strokeStyle = 'rgba(' + col + ',' + a + ')'; g.beginPath(); g.ellipse(W / 2, H * 0.62, r * 1.5, r * 0.5, Math.sin(t * 0.2 + i) * 0.2, 0, TAU); g.stroke(); } for (i = 0; i < 12; i++) { var an = i * TAU / 12 + t * 0.15; g.strokeStyle = 'rgba(' + col + ',' + (0.1 * w) + ')'; g.beginPath(); g.moveTo(W / 2, H * 0.62); g.lineTo(W / 2 + Math.cos(an) * W, H * 0.62 + Math.sin(an) * W * 0.4); g.stroke(); } break;
          case 'glitch': if (t - glitchT > 0.09) { glitchT = t; glitchRects = []; for (i = 0; i < 14; i++) glitchRects.push([rand(0, W), rand(0, H), rand(40, 320), rand(4, 26), Math.random() < 0.3 ? '0,229,255' : (Math.random() < 0.5 ? col : '255,0,64')]); } glitchRects.forEach(function (r) { g.fillStyle = 'rgba(' + r[4] + ',' + (0.1 * w) + ')'; g.fillRect(r[0], r[1], r[2], r[3]); }); break;
          case 'void': var cx = W / 2, cy = H * 0.5, hg = g.createRadialGradient(cx, cy, 0, cx, cy, Math.max(W, H) * 0.6); hg.addColorStop(0, 'rgba(0,0,0,' + (0.9 * w) + ')'); hg.addColorStop(0.1, 'rgba(0,0,0,' + (0.9 * w) + ')'); hg.addColorStop(0.14, 'rgba(255,255,255,' + (0.5 * w) + ')'); hg.addColorStop(0.3, 'rgba(255,255,255,' + (0.1 * w) + ')'); hg.addColorStop(1, 'rgba(255,255,255,0)'); g.fillStyle = hg; g.fillRect(0, 0, W, H); g.strokeStyle = 'rgba(255,255,255,' + (0.5 * w) + ')'; g.lineWidth = 2; g.beginPath(); g.ellipse(cx, cy, 190, 46, t * 0.3, 0, TAU); g.stroke(); break;
          case 'bars': for (i = 0; i < 9; i++) { var by = H * (i + 0.5) / 9 - 16, bw = W * (0.35 + 0.4 * ((i * 37) % 10) / 10), bxo = ((Math.sin(t * 0.4 + i * 1.7) + 1) / 2) * (W - bw); g.fillStyle = 'rgba(0,0,0,' + (0.55 * w) + ')'; g.fillRect(bxo, by, bw, 32); g.strokeStyle = 'rgba(' + col + ',' + (0.35 * w) + ')'; g.lineWidth = 1; g.strokeRect(bxo, by, bw, 32); } break;
          case 'data': g.fillStyle = 'rgba(' + col + ',' + (0.2 * w) + ')'; for (x = 30; x < W; x += 64) for (y = 30; y < H; y += 64) { if (Math.sin(x * 12.9 + y * 7.7 + t * 1.3) > 0.55) { g.fillRect(x - 5, y, 11, 1); g.fillRect(x, y - 5, 1, 11); } } break;
          case 'ripple': for (i = 0; i < 4; i++) { var rr = ((t * 60 + i * 150) % 600), aa = (1 - rr / 600) * 0.28 * w; g.strokeStyle = 'rgba(' + col + ',' + aa + ')'; g.lineWidth = 1.6; g.beginPath(); g.arc(W / 2, H * 0.5, rr, 0, TAU); g.stroke(); } break;
          case 'radar': var rx = W / 2, ry = H * 1.02, an2 = (t * 0.5) % TAU - TAU / 2; g.strokeStyle = 'rgba(' + col + ',' + (0.14 * w) + ')'; g.lineWidth = 1; for (i = 1; i <= 5; i++) { g.beginPath(); g.arc(rx, ry, i * H * 0.24, Math.PI, TAU); g.stroke(); } for (i = 0; i < 20; i++) { g.strokeStyle = 'rgba(' + col + ',' + (0.3 * w * (1 - i / 20)) + ')'; g.lineWidth = 2; g.beginPath(); g.moveTo(rx, ry); g.lineTo(rx + Math.cos(an2 - Math.PI / 2 - i * 0.02) * H * 1.2, ry + Math.sin(an2 - Math.PI / 2 - i * 0.02) * H * 1.2); g.stroke(); } break;
        }
      }

      var last = performance.now(), hudLab = $('hudLab'), needle = $('needle'), dialArc = $('dialArc'), shownTheme = '';
      function frame(now) {
        requestAnimationFrame(frame);
        var dt = Math.min(0.05, (now - last) / 1000); last = now; var t = light ? 0 : now / 1000, i, T = TH[active];
        for (i = 0; i < 3; i++) cur[i] += (T.c[i] - cur[i]) * Math.min(1, dt * 2.5);
        var col = Math.round(cur[0]) + ',' + Math.round(cur[1]) + ',' + Math.round(cur[2]);
        if (col !== lastCol) { lastCol = col; root.style.setProperty('--tc', col); }
        MODES.forEach(function (m) { wts[m] += ((m === T.m ? 1 : 0) - wts[m]) * Math.min(1, dt * 2.5); });
        root.style.setProperty('--vw', clamp(wts.void * 0.9, 0, 1).toFixed(2));
        g.clearRect(0, 0, W, H);
        var base = g.createRadialGradient(W / 2, H * 1.1, 0, W / 2, H * 1.1, H * 1.1); base.addColorStop(0, 'rgba(' + col + ',0.16)'); base.addColorStop(1, 'rgba(' + col + ',0)'); g.fillStyle = base; g.fillRect(0, 0, W, H);
        if (!light) MODES.forEach(function (m) { if (wts[m] > 0.02) overlay(m, wts[m], t, col); });
        /* particles */
        var m0 = T.m, cx = W / 2, cy = H * 0.5; g.fillStyle = 'rgba(' + col + ',0.7)';
        for (i = 0; i < parts.length; i++) {
          var p = parts[i], tx = 0, ty = 0;
          switch (m0) {
            case 'calm': tx = Math.sin(t * 0.3 + p.ph) * 8; ty = -6; break;
            case 'flow': tx = 34; ty = Math.sin(p.x * 0.01 + t) * 14; break;
            case 'spark': tx = 120; ty = -90; break;
            case 'warp': tx = Math.cos(t * 0.6 + p.ph) * 22; ty = Math.sin(t * 0.6 + p.ph) * 22; break;
            case 'rift': tx = Math.sin(t + p.ph) * 12; ty = -70 - p.s * 16; break;
            case 'portal': var ax = p.x - cx, ay = p.y - cy, al = Math.hypot(ax, ay) || 1; tx = -ay / al * 60; ty = ax / al * 60; break;
            case 'glitch': tx = (Math.random() - 0.5) * 160; ty = (Math.random() - 0.5) * 160; break;
            case 'void': var vx = cx - p.x, vy = cy - p.y, vl = Math.hypot(vx, vy) || 1; tx = vx / vl * 110; ty = vy / vl * 110; if (vl < 40) { p.x = rand(0, W); p.y = rand(0, H); } break;
            case 'bars': tx = 40; ty = 0; break;
            case 'ripple': tx = 0; ty = 0; break;
            case 'radar': tx = Math.cos(t * 0.3 + p.ph) * 14; ty = Math.sin(t * 0.3 + p.ph) * 14; break;
            default: tx = 0; ty = 10;
          }
          p.vx += (tx - p.vx) * Math.min(1, dt * 2); p.vy += (ty - p.vy) * Math.min(1, dt * 2);
          if (!light) { p.x += p.vx * dt; p.y += p.vy * dt; }
          if (p.x < -10) p.x = W + 10; else if (p.x > W + 10) p.x = -10; if (p.y < -10) p.y = H + 10; else if (p.y > H + 10) p.y = -10;
          g.globalAlpha = 0.25 + 0.5 * Math.abs(Math.sin(t * 0.8 + p.ph)); g.fillRect(p.x, p.y, p.s, p.s);
        }
        g.globalAlpha = 1;
        drawWaves(dt);
        if (shakeT > 0) { shakeT = Math.max(0, shakeT - dt); var sm = shakeT * 10; document.querySelector('.container').style.transform = 'translate(' + rand(-sm, sm).toFixed(1) + 'px,' + rand(-sm, sm).toFixed(1) + 'px)'; } else document.querySelector('.container').style.transform = '';
        seisFrame(now);
        if (shownTheme !== active) { shownTheme = active; hudLab.textContent = T.l; var idx = T.i < 0 ? 0 : T.i; needle.style.transform = 'rotate(' + (-90 + (T.i < 0 ? 0 : idx / 8 * 180)).toFixed(0) + 'deg)'; dialArc.style.strokeDashoffset = (182 - (T.i < 0 ? 0 : (idx + 1) / 9 * 182)).toFixed(0); dialArc.style.stroke = 'rgb(' + T.c.join(',') + ')'; document.querySelectorAll('#ladder a').forEach(function (a) { a.classList.toggle('on', a.getAttribute('data-k') === active); }); document.querySelectorAll('.class-card').forEach(function (c) { c.classList.toggle('active', c.getAttribute('data-th') === active); }); }
      }

      /* active section tracking */
      var secEls = Array.prototype.slice.call(document.querySelectorAll('[data-th]')), scrollQ = false;
      function pickActive() { scrollQ = false; var best = secEls[0], line = window.innerHeight * 0.5; secEls.forEach(function (e) { if (e.getBoundingClientRect().top < line) best = e; }); active = best.getAttribute('data-th'); }
      window.addEventListener('scroll', function () { if (!scrollQ) { scrollQ = true; requestAnimationFrame(pickActive); } }, { passive: true });

      /* ladder */
      (function () {
        var nav = $('ladder'), h = '';
        secEls.forEach(function (e) { var k = e.getAttribute('data-th'); if (k === 'base') return; var c = TH[k].c.join(','); h += '<a href="#" data-k="' + k + '" style="--dc:' + c + '"><span>' + e.getAttribute('data-lab') + '</span></a>'; });
        nav.innerHTML = h;
        nav.querySelectorAll('a').forEach(function (a) { a.addEventListener('click', function (ev) { ev.preventDefault(); var t = document.querySelector('[data-th="' + a.getAttribute('data-k') + '"]'); t.scrollIntoView({ behavior: reduce ? 'auto' : 'smooth', block: 'center' }); }); });
      })();

      /* ═══ SHOCKWAVES ═══ */
      var PC = { 1: '79,195,247', 2: '76,175,80', 3: '255,214,0', 4: '255,110,20', 5: '244,67,54', 6: '190,80,220', 7: '255,255,255' };
      function firePulse(lv, ox, oy) {
        waves.push({ x: ox == null ? W / 2 : ox, y: oy == null ? H * 0.4 : oy, lv: lv, t: 0 });
        if (lv >= 4 && !reduce) shakeT = Math.max(shakeT, lv >= 6 ? 0.9 : 0.4);
        if (lv === 7) { var om = $('omegaMsg'); om.classList.remove('go'); void om.offsetWidth; om.classList.add('go'); }
      }
      function drawWaves(dt) {
        wv.clearRect(0, 0, W, H);
        for (var i = waves.length - 1; i >= 0; i--) {
          var w = waves[i]; w.t += dt; var dur = 1 + w.lv * 0.4, k = w.t / dur; if (k >= 1) { waves.splice(i, 1); continue; }
          var maxR = w.lv <= 2 ? 260 : w.lv <= 4 ? 520 : Math.hypot(W, H), e = 1 - Math.pow(1 - k, 3), r = maxR * e, a = 1 - k, col = PC[w.lv];
          wv.save(); wv.globalCompositeOperation = 'lighter';
          if (k < 0.25) { var gr = wv.createRadialGradient(w.x, w.y, 0, w.x, w.y, 160 + w.lv * 90); gr.addColorStop(0, 'rgba(' + col + ',' + ((1 - k / 0.25) * 0.08 * w.lv) + ')'); gr.addColorStop(1, 'rgba(' + col + ',0)'); wv.fillStyle = gr; wv.fillRect(0, 0, W, H); }
          for (var j = 0; j < 3; j++) { wv.strokeStyle = 'rgba(' + col + ',' + (a * (0.9 - j * 0.25)) + ')'; wv.lineWidth = (2 + w.lv * 1.4) * (1 - k) * (1 - j * 0.25) + 0.5; wv.beginPath(); wv.arc(w.x, w.y, Math.max(1, r * (1 - j * 0.18)), 0, TAU); wv.stroke(); }
          wv.restore();
        }
      }

      /* ═══ PULSE SEISMOGRAPH ═══ */
      var sCv = $('seis'), sc2 = sCv.getContext('2d'), SW = 0, SH = 0, samples = [], env = 0, envDec = 3, flat = 0, selLv = 3, ph = 0, anomN = 0, curAn = null, vis = true;
      var AMP = { 1: 0.12, 2: 0.22, 3: 0.36, 4: 0.52, 5: 0.72, 6: 0.95, 7: 1.8 };
      var LN = { 1: 'CLASS I', 2: 'CLASS II', 3: 'CLASS III', 4: 'CLASS IV', 5: 'CLASS V', 6: 'CLASS VI', 7: 'CLASS \u03A9' };
      var plog = $('plog'), psim = $('psim');
      function say(t, cls) { var d = document.createElement('div'); if (cls) d.className = cls; d.textContent = '> ' + t; plog.appendChild(d); while (plog.children.length > 5) plog.removeChild(plog.firstChild); }
      function sizeSeis() { SW = sCv.clientWidth; SH = sCv.clientHeight; sCv.width = SW * dpr; sCv.height = SH * dpr; sc2.setTransform(dpr, 0, 0, dpr, 0, 0); samples = []; for (var i = 0; i < Math.floor(SW / 2); i++) samples.push(0); }
      (function () {
        var box = $('lvls');
        [1, 2, 3, 4, 5, 6, 7].forEach(function (lv) { var b = document.createElement('button'); b.type = 'button'; b.className = 'btn' + (lv === selLv ? ' on' : ''); b.style.setProperty('--bc', PC[lv]); b.textContent = lv === 7 ? '\u03A9' : lv; b.setAttribute('data-l', lv); b.title = LN[lv]; b.addEventListener('click', function () { selLv = lv; psim.style.setProperty('--pc', PC[lv]); box.querySelectorAll('.btn').forEach(function (x) { x.classList.toggle('on', x === b); }); }); box.appendChild(b); });
        psim.style.setProperty('--pc', PC[selLv]);
      })();
      $('bManifest').addEventListener('click', function () {
        anomN++; var id = 'SIM-' + (anomN < 10 ? '00' : anomN < 100 ? '0' : '') + anomN; curAn = { id: id, lv: selLv };
        var r = psim.getBoundingClientRect(); firePulse(selLv, r.left + r.width / 2, r.top + r.height / 2);
        env = AMP[selLv]; envDec = selLv === 7 ? 0.8 : 3.4 - selLv * 0.3; if (selLv === 7) flat = 3.4;
        say(id + ' manifests. Exactly one Pulse generated (' + LN[selLv] + ').', 'g'); if (selLv === 7) say('Total annihilation signature. All known laws break down.', 'r');
      });
      $('bRep').addEventListener('click', function () {
        if (!curAn) { say('No anomaly has manifested.', 'r'); return; }
        env = 0.05; say(curAn.id + ': replication rejected. Pulses are rare, one-time events that cannot be replicated.', 'r');
      });
      function seisFrame(now) {
        if (!SW || !vis) return;
        ph += 0.9 + env * 2; var v = (Math.random() - 0.5) * 0.04;
        if (flat > 0) { flat -= 1 / 60; v = 0; env *= 0.9; } else { v += env * Math.sin(ph) * (0.6 + Math.random() * 0.4); env *= Math.exp(-envDec / 60); }
        samples.push(v); samples.shift();
        var c = sc2, mid = SH / 2, col = PC[selLv];
        c.clearRect(0, 0, SW, SH); c.strokeStyle = 'rgba(' + col + ',0.12)'; c.lineWidth = 1; for (var y = 0; y < SH; y += SH / 6) { c.beginPath(); c.moveTo(0, y); c.lineTo(SW, y); c.stroke(); } for (var x = 0; x < SW; x += 40) { c.beginPath(); c.moveTo(x, 0); c.lineTo(x, SH); c.stroke(); }
        c.strokeStyle = 'rgb(' + col + ')'; c.lineWidth = 2; c.shadowColor = 'rgb(' + col + ')'; c.shadowBlur = 8; c.beginPath();
        for (var i = 0; i < samples.length; i++) { var yy = clamp(mid - samples[i] * mid * 0.95, 1, SH - 1); if (i === 0) c.moveTo(0, yy); else c.lineTo(i * 2, yy); } c.stroke(); c.shadowBlur = 0;
        c.fillStyle = 'rgba(' + col + ',0.8)'; c.font = '10px "Share Tech Mono", monospace'; c.textAlign = 'left'; c.fillText(flat > 0 ? 'NO SIGNAL' : 'MAGNITUDE ' + (Math.abs(env) * 100).toFixed(0), 10, 16);
      }
      if ('IntersectionObserver' in window) new IntersectionObserver(function (en) { vis = en[0].isIntersecting; }, { threshold: 0 }).observe(sCv);

      /* mini waves on pulse cards */
      (function () {
        var A = { p1: 5, p2: 9, p3: 14, p4: 19, p5: 26, p6: 34, pomega: 60 };
        document.querySelectorAll('.pulse-card').forEach(function (c) {
          var k = [].filter.call(c.classList, function (x) { return A[x]; })[0], a = A[k], d = 'M0 22 ', x;
          for (x = 5; x <= 120; x += 5) { var spike = (x > 50 && x < 80) ? Math.sin((x - 50) / 30 * Math.PI * 3) * a * (1 - Math.abs(x - 65) / 18) : (Math.random() - 0.5) * 2; d += 'L' + x + ' ' + clamp(22 - spike, -10, 54).toFixed(1) + ' '; }
          c.insertAdjacentHTML('beforeend', '<svg class="mw" viewBox="0 0 120 44" aria-hidden="true"><path d="' + d + '"/></svg>');
        });
      })();

      /* ═══ CLASS CARD DECOR ═══ */
      var GL = {
        1: '<circle cx="30" cy="30" r="20" fill="none" stroke="currentColor" stroke-width="2"/><circle class="gy-br" cx="30" cy="30" r="5" fill="currentColor"/>',
        2: '<circle cx="30" cy="30" r="12" fill="none" stroke="currentColor" stroke-width="2"/><circle class="gy-spin" cx="30" cy="30" r="22" fill="none" stroke="currentColor" stroke-width="2" stroke-dasharray="6 6"/>',
        3: '<polygon class="gy-spin" points="30,4 36,22 54,18 42,32 56,46 36,42 30,58 24,42 4,46 18,32 6,18 24,22" fill="none" stroke="currentColor" stroke-width="2" stroke-linejoin="round"/>',
        4: '<g class="gy-sk" fill="none" stroke="currentColor" stroke-width="2"><rect x="8" y="8" width="44" height="44"/><path d="M8 23 H52 M8 38 H52 M23 8 V52 M38 8 V52"/></g>',
        5: '<circle cx="30" cy="30" r="22" fill="none" stroke="currentColor" stroke-width="2"/><path class="gy-br" d="M30 8 L24 24 L34 32 L26 42 L32 52" fill="none" stroke="currentColor" stroke-width="2.4"/><circle class="gy-br" cx="30" cy="30" r="4" fill="currentColor"/>',
        6: '<ellipse class="gy-spin" cx="30" cy="30" rx="24" ry="9" fill="none" stroke="currentColor" stroke-width="2"/><ellipse class="gy-spin r" cx="30" cy="30" rx="24" ry="9" fill="none" stroke="currentColor" stroke-width="2" transform="rotate(60 30 30)"/><ellipse class="gy-spin" cx="30" cy="30" rx="24" ry="9" fill="none" stroke="currentColor" stroke-width="2" transform="rotate(120 30 30)"/>',
        7: '<g class="gy-gl" fill="currentColor"><rect x="8" y="12" width="30" height="8"/><rect x="20" y="26" width="32" height="8"/><rect x="12" y="40" width="26" height="8"/></g>',
        8: '<circle cx="30" cy="30" r="22" fill="#000" stroke="currentColor" stroke-width="2.4"/><circle class="gy-spin" cx="30" cy="30" r="14" fill="none" stroke="currentColor" stroke-width="1.6" stroke-dasharray="3 5"/><circle cx="30" cy="30" r="6" fill="#000" stroke="currentColor" stroke-width="2"/>',
        9: '<g fill="currentColor"><rect x="6" y="10" width="48" height="9"/><rect x="6" y="26" width="34" height="9"/><rect x="6" y="42" width="44" height="9"/></g><line x1="4" y1="56" x2="56" y2="4" stroke="#000" stroke-width="3"/>'
      };
      document.querySelectorAll('.class-card').forEach(function (cd) {
        var gi = +cd.getAttribute('data-gi'), hd = cd.querySelector('.class-header'), name = cd.querySelector('.class-name');
        hd.insertAdjacentHTML('afterbegin', '<svg class="glyph" viewBox="0 0 60 60" aria-hidden="true">' + GL[gi] + '</svg>');
        var gh = '<div class="gauge" aria-hidden="true">'; for (var i = 1; i <= 7; i++) gh += '<i' + ((gi >= 8 || i <= gi) && gi !== 9 ? ' class="on"' : '') + '></i>'; gh += '</div><span class="chev">\u25BE</span>';
        name.insertAdjacentHTML('afterend', gh);
        hd.addEventListener('click', function () { cd.classList.toggle('collapsed'); });
        cd.addEventListener('pointermove', function (e) { var r = cd.getBoundingClientRect(); cd.style.setProperty('--cx', (e.clientX - r.left) + 'px'); cd.style.setProperty('--cy', (e.clientY - r.top) + 'px'); });
      });
      var allCol = false, tg = $('toggleAll');
      tg.addEventListener('click', function () { allCol = !allCol; document.querySelectorAll('.class-card').forEach(function (c) { c.classList.toggle('collapsed', allCol); }); tg.textContent = allCol ? '\u25B8 Expand all' : '\u25BE Collapse all'; });

      /* ═══ REGISTRY OF MISSING ═══ */
      (function () {
        var reg = $('reg'), h = '', i, rs = [];
        for (i = 0; i < 100; i++) { var m = Math.random() < 0.3, r = (Math.random() * 4) | 0; rs.push(m ? r : -1); h += '<i class="' + (m ? 'm' : '') + '" data-r="' + (m ? r : -1) + '"></i>'; }
        reg.innerHTML = h; var cells = reg.querySelectorAll('i');
        document.querySelectorAll('#whyList li').forEach(function (li) { var r = li.getAttribute('data-r'); li.addEventListener('mouseenter', function () { cells.forEach(function (c) { if (c.getAttribute('data-r') === r) c.className = 'm hot r' + r; }); }); li.addEventListener('mouseleave', function () { cells.forEach(function (c) { if (c.getAttribute('data-r') !== '-1') c.className = 'm'; }); }); });
        var ld = $('ldx'); if ('IntersectionObserver' in window) { new IntersectionObserver(function (en, o) { if (en[0].isIntersecting) { ld.classList.add('in'); o.disconnect(); } }, { threshold: 0.6 }).observe(ld); } else ld.classList.add('in');
      })();

      /* ═══ CLEARANCE TERMINAL ═══ */
      (function () {
        var box = $('cterm'), cards = document.querySelectorAll('.clearance-card'), cl = 8;
        var labs = ['1', '2', '3', '4', '5', '6', '7', 'D.I.V.I.D.E.'];
        labs.forEach(function (l, i) { var b = document.createElement('button'); b.type = 'button'; b.className = 'btn' + (i === 7 ? ' on' : ''); b.textContent = l; b.addEventListener('click', function () { cl = i + 1; box.querySelectorAll('.btn').forEach(function (x) { x.classList.toggle('on', x === b); }); cards.forEach(function (c) { c.classList.toggle('locked', +c.getAttribute('data-lvl') > cl); }); }); box.appendChild(b); });
        /* warheads */
        var wh = $('wh'), h = '', i; for (i = 0; i < 50; i++) h += '<i style="--i:' + i + '"></i>'; wh.innerHTML = h;
        var hold = $('hold'), fill = $('holdFill'), nmsg = $('nmsg'), t0 = 0, raf = null, done = false;
        function stop() { if (raf) cancelAnimationFrame(raf); raf = null; if (!done) { fill.style.width = '0'; nmsg.textContent = '50 warheads \u2014 standing by'; } }
        function step(now) { var p = clamp((now - t0) / 2400, 0, 1); fill.style.width = (p * 100) + '%'; nmsg.textContent = 'Authorizing\u2026 ' + Math.round(p * 100) + '%'; if (p >= 1) { done = true; raf = null; wh.classList.add('armed'); nmsg.textContent = 'Simultaneous activation \u2014 50 warheads. Reserved for existential crisis or global catastrophe.'; var r = hold.getBoundingClientRect(); firePulse(5, r.left + r.width / 2, r.top); setTimeout(function () { wh.classList.remove('armed'); fill.style.width = '0'; nmsg.textContent = 'Simulation ended. 50 warheads \u2014 standing by'; done = false; }, 5200); return; } raf = requestAnimationFrame(step); }
        function start(e) { if (done) return; e.preventDefault(); t0 = performance.now(); raf = requestAnimationFrame(step); }
        hold.addEventListener('pointerdown', start); ['pointerup', 'pointerleave', 'pointercancel'].forEach(function (ev) { hold.addEventListener(ev, stop); });
        hold.addEventListener('keydown', function (e) { if ((e.key === ' ' || e.key === 'Enter') && !raf && !done) start(e); }); hold.addEventListener('keyup', stop);
      })();

      /* ═══ INIT ═══ */
      (function () {
        var t = $('siteTitle'); function fire() { if (reduce) return; t.classList.add('glitch'); setTimeout(function () { t.classList.remove('glitch'); }, 420); } t.addEventListener('mouseenter', fire); (function loop() { setTimeout(function () { fire(); loop(); }, 4500 + Math.random() * 5000); })(); setTimeout(fire, 1200);
      })();
      var fb = $('fxBtn'); function fx() { fb.innerHTML = '&#9680; Effects: ' + (light ? 'light' : 'full'); } fb.addEventListener('click', function () { light = !light; fx(); }); fx();
      function resize() { W = window.innerWidth; H = window.innerHeight; [bgCv, wvCv].forEach(function (c) { c.width = Math.floor(W * dpr); c.height = Math.floor(H * dpr); c.style.width = W + 'px'; c.style.height = H + 'px'; }); g.setTransform(dpr, 0, 0, dpr, 0, 0); wv.setTransform(dpr, 0, 0, dpr, 0, 0); parts = []; for (var i = 0; i < 110; i++) parts.push(mkP()); sizeSeis(); }
      var rt = null; resize(); pickActive(); requestAnimationFrame(frame);
      window.addEventListener('resize', function () { clearTimeout(rt); rt = setTimeout(resize, 250); });
      var els = document.querySelectorAll('.reveal');
      if ('IntersectionObserver' in window) { var io = new IntersectionObserver(function (en) { en.forEach(function (x) { if (x.isIntersecting) { x.target.classList.add('in'); io.unobserve(x.target); } }); }, { threshold: 0.08 }); els.forEach(function (e) { io.observe(e); }); } else els.forEach(function (e) { e.classList.add('in'); });
    })();
  </script>

</body>
</html>
