
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#060610">
  <title>D.I.V.I.D.E. — SYS-01 Servant Card System</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;500;600;700&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --bg: #060610; --ink: #c8c8e6; --dim: #6a6a8a;
      --b1: #4444cc; --b2: #7777ff; --p1: #9c27b0; --p2: #ce7adb;
      --th: 0; --cr: 0;
      --acc: color-mix(in srgb, var(--b2) calc((1 - var(--th)) * 100%), var(--p2));
      --acc-d: color-mix(in srgb, var(--b1) calc((1 - var(--th)) * 100%), var(--p1));
      --panel: rgba(10,10,24,0.86); --line: rgba(80,80,200,0.28);
      --tc: #4fc3f7; --tcrgb: 79,195,247; --hue: 195;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg); color: var(--ink);
      font-family: 'Share Tech Mono', monospace; min-height: 100vh; overflow-x: hidden; position: relative;
    }
    :focus-visible { outline: 2px solid var(--acc); outline-offset: 2px; }

    body::before {
      content: ''; position: fixed; inset: 0; z-index: 0; pointer-events: none;
      background:
        radial-gradient(ellipse at 50% -10%, color-mix(in srgb, rgba(68,68,204,0.28) calc((1 - var(--th)) * 100%), rgba(156,39,176,0.30)), transparent 60%),
        url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='56' height='100' viewBox='0 0 56 100'%3E%3Cpath d='M28 66L0 50L0 16L28 0L56 16L56 50L28 66L28 100' fill='none' stroke='%237777ff' stroke-opacity='0.5' stroke-width='1'/%3E%3Cpath d='M28 0L28 34L0 50L0 84L28 100L56 84L56 50L28 34' fill='none' stroke='%237777ff' stroke-opacity='0.5' stroke-width='1'/%3E%3C/svg%3E");
      background-size: auto, 56px 100px; opacity: 1;
    }
    body::after { content: ''; position: fixed; inset: 0; z-index: 70; pointer-events: none; background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(140,140,255,0.012) 3px, rgba(140,140,255,0.012) 4px); }

    #bg, #wave, #cracks { position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; }
    #bg { z-index: 1; } #wave { z-index: 40; } #cracks { z-index: 42; opacity: var(--cr); mix-blend-mode: screen; }
    .ov-vig { position: fixed; inset: 0; z-index: 3; pointer-events: none; background: radial-gradient(ellipse at 50% 40%, transparent 50%, rgba(2,2,8,0.8) 100%); }

    /* ═══ TOP ═══ */
    .warning-bar {
      background: repeating-linear-gradient(135deg, #8b0000 0 18px, #7a0000 18px 36px); color: #fff; text-align: center; padding: 7px 10px;
      font-size: 11px; letter-spacing: 3px; text-transform: uppercase; border-bottom: 1px solid #ff0000; position: relative; z-index: 100; text-shadow: 0 1px 2px rgba(0,0,0,0.6);
    }
    .container { max-width: 1000px; margin: 0 auto; padding: 40px 20px 30px; position: relative; z-index: 10; }
    .back-link { display: inline-flex; align-items: center; gap: 8px; color: #6a6a8a; text-decoration: none; font-size: 11px; letter-spacing: 2px; margin-bottom: 20px; transition: color 0.2s, gap 0.2s; }
    .back-link:hover { color: #cc0000; gap: 14px; }
    .reveal { opacity: 0; transform: translateY(18px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .reveal.in { opacity: 1; transform: none; }

    /* ═══ HEADER ═══ */
    .file-header {
      border: 1px solid #1a1a4a; padding: 34px 32px 30px; margin-bottom: 26px; position: relative; overflow: hidden;
      background: linear-gradient(180deg, rgba(5,5,15,0.92) 0%, rgba(8,8,8,0.92) 100%);
      box-shadow: inset 0 0 80px rgba(68,68,204,0.10), 0 0 50px rgba(68,68,204,0.10);
    }
    .file-header::before { content: '// SYSTEM FILE //'; position: absolute; top: -10px; left: 20px; background: var(--bg); padding: 0 10px; color: #4444cc; font-size: 11px; letter-spacing: 3px; }
    .file-header::after { content: ''; position: absolute; top: 0; right: 0; width: 44px; height: 44px; border-top: 2px solid #4444cc; border-right: 2px solid #4444cc; }
    .hline { position: absolute; left: 0; bottom: 0; width: 100%; height: 2px; background: linear-gradient(90deg, transparent, #4444cc, #cfcfff, #9c27b0, transparent); background-size: 200% 100%; animation: slide 5s linear infinite; }
    @keyframes slide { from { background-position: 0 0; } to { background-position: 200% 0; } }
    .file-id { font-size: 11px; color: #4444cc; letter-spacing: 4px; margin-bottom: 8px; }
    .file-title {
      font-family: 'Rajdhani', sans-serif; font-size: 62px; font-weight: 700; letter-spacing: 6px; line-height: 1.02; margin-bottom: 8px; position: relative; display: inline-block;
      background: linear-gradient(100deg, #4444cc 0%, #aab0ff 25%, #ffffff 40%, #ce7adb 60%, #7777ff 80%, #4444cc 100%); background-size: 250% 100%;
      -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent; animation: holo 6s linear infinite; filter: drop-shadow(0 0 18px rgba(100,100,255,0.4));
    }
    @keyframes holo { from { background-position: 0 0; } to { background-position: 250% 0; } }
    @media (max-width: 700px) { .file-title { font-size: 34px; letter-spacing: 3px; } .file-header { padding: 26px 18px 22px; } }
    .file-designation { font-size: 12px; color: #6a6a8a; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 22px; }
    .meta-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 6px; }
    @media (max-width: 600px) { .meta-grid { grid-template-columns: 1fr; } }
    .meta-item { display: flex; gap: 10px; padding: 9px 13px; background: rgba(13,13,24,0.88); border: 1px solid #1a1a2a; font-size: 11px; transition: border-color 0.2s, transform 0.2s; }
    .meta-item:hover { border-color: var(--acc-d); transform: translateX(3px); }
    .meta-label { color: #6a6a8a; letter-spacing: 1px; white-space: nowrap; }
    .meta-value { color: #aaa; letter-spacing: 1px; }
    .meta-value.purple { color: #b04bd0; } .meta-value.red { color: #ff3a3a; } .meta-value.orange { color: #ff7a2a; }

    /* ═══ HERO SIMULATOR ═══ */
    .hero { display: grid; grid-template-columns: 330px 1fr; gap: 26px; align-items: center; margin-bottom: 8px; padding: 26px; border: 1px solid #1a1a4a; background: linear-gradient(160deg, rgba(8,8,24,0.9), rgba(6,6,16,0.9)); position: relative; }
    @media (max-width: 800px) { .hero { grid-template-columns: 1fr; } }
    .hero::before { content: '// SERVANT CARD SIMULATOR //'; position: absolute; top: -10px; left: 20px; background: var(--bg); padding: 0 10px; color: var(--acc-d); font-size: 11px; letter-spacing: 3px; }
    .stage { perspective: 900px; display: flex; justify-content: center; }
    .float { animation: floaty 5s ease-in-out infinite; }
    @keyframes floaty { 0%,100% { transform: translateY(0); } 50% { transform: translateY(-8px); } }
    .card3d {
      --rx: 0deg; --ry: 0deg; --fx: 50; position: relative; width: 250px; height: 365px; transform-style: preserve-3d;
      transform: rotateX(var(--rx)) rotateY(var(--ry)); transition: transform 0.25s ease-out; will-change: transform;
    }
    .card3d.t1 { --tc: #4fc3f7; --tcrgb: 79,195,247; --hue: 195; }
    .card3d.t2 { --tc: #ffd600; --tcrgb: 255,214,0; --hue: 50; }
    .card3d.t3 { --tc: #f44336; --tcrgb: 244,67,54; --hue: 5; }
    .face {
      position: absolute; inset: 0; border-radius: 18px; overflow: hidden; background: linear-gradient(160deg, #12122e, #080818);
      border: 2px solid color-mix(in srgb, var(--tc) 75%, #223); box-shadow: 0 0 46px rgba(var(--tcrgb), 0.38), inset 0 0 40px rgba(var(--tcrgb), 0.12); transition: box-shadow 0.4s, border-color 0.4s, filter 0.6s;
    }
    .foil { position: absolute; inset: 0; z-index: 4; pointer-events: none; mix-blend-mode: color-dodge; opacity: 0.55; background: linear-gradient(115deg, transparent calc(var(--fx) * 1% - 22%), rgba(255,255,255,0.35) calc(var(--fx) * 1%), hsla(var(--hue),100%,68%,0.4) calc(var(--fx) * 1% + 12%), transparent calc(var(--fx) * 1% + 32%)); }
    .ctop { position: absolute; top: 10px; left: 12px; right: 12px; z-index: 3; display: flex; justify-content: space-between; font-size: 9px; letter-spacing: 3px; color: var(--tc); text-transform: uppercase; }
    .art { position: absolute; left: 12px; right: 12px; top: 32px; height: 215px; border: 1px solid rgba(var(--tcrgb), 0.4); overflow: hidden; background: #05050f; }
    .art svg { width: 100%; height: 100%; display: block; }
    .art .ent { opacity: 0.0; transform: translateY(14px) scale(0.96); transform-origin: 50% 100%; transition: opacity 0.9s ease, transform 0.9s cubic-bezier(.2,.8,.2,1); }
    .hero.summoned .art .ent { opacity: 1; transform: none; }
    .art .eye { fill: var(--tc); filter: drop-shadow(0 0 6px var(--tc)); animation: eyeb 3s ease-in-out infinite; }
    @keyframes eyeb { 0%,92%,100% { opacity: 1; } 95% { opacity: 0.1; } }
    .art .ring { fill: none; stroke: rgba(var(--tcrgb), 0.55); stroke-width: 1; transform-box: fill-box; transform-origin: center; animation: spin 24s linear infinite; }
    .art .ring.r2 { animation-duration: 16s; animation-direction: reverse; stroke-dasharray: 4 6; }
    @keyframes spin { to { transform: rotate(360deg); } }
    .art .mist { fill: rgba(var(--tcrgb), 0.16); animation: mist 6s ease-in-out infinite; }
    @keyframes mist { 0%,100% { transform: translateX(-6px); } 50% { transform: translateX(8px); } }
    .cbot { position: absolute; left: 12px; right: 12px; bottom: 12px; z-index: 3; display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
    .cstat { border: 1px solid rgba(var(--tcrgb), 0.35); padding: 6px 8px; background: rgba(5,5,15,0.7); }
    .cstat i { display: block; font-style: normal; font-size: 8px; letter-spacing: 3px; color: #8a8aaa; }
    .cstat b { font-family: 'Rajdhani', sans-serif; font-size: 22px; font-weight: 700; color: var(--tc); line-height: 1.1; }
    .cserial { position: absolute; left: 12px; right: 12px; bottom: 76px; z-index: 3; font-size: 9px; letter-spacing: 4px; color: #7a7aa0; text-align: center; }
    .ccrack { position: absolute; inset: 0; z-index: 5; pointer-events: none; width: 100%; height: 100%; }
    .ccrack path { fill: none; stroke: #e8e8ff; stroke-width: 1.6; stroke-linecap: round; stroke-linejoin: round; stroke-dasharray: 1; stroke-dashoffset: 0; filter: drop-shadow(0 0 4px var(--tc)); }
    .ccrack path.new { animation: draw 0.9s ease-out; }
    @keyframes draw { from { stroke-dashoffset: 1; } to { stroke-dashoffset: 0; } }
    .stampc { position: absolute; left: 0; right: 0; top: 38%; z-index: 6; text-align: center; font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 26px; letter-spacing: 6px; color: #ff4a4a; transform: rotate(-14deg) scale(1.5); opacity: 0; transition: all 0.5s cubic-bezier(.2,.9,.3,1.3); text-shadow: 0 0 14px rgba(255,40,40,0.8); border-top: 3px solid #ff4a4a; border-bottom: 3px solid #ff4a4a; padding: 4px 0; background: rgba(20,0,0,0.6); }
    .hero.inactive .stampc, .hero.broken .stampc { opacity: 1; transform: rotate(-14deg) scale(1); }
    .hero.inactive .face { filter: grayscale(1) brightness(0.7); border-color: #444; box-shadow: none; }
    .hero.low .face { animation: lowflick 1.4s steps(2) infinite; }
    @keyframes lowflick { 0%,88% { opacity: 1; } 90% { opacity: 0.55; } 94% { opacity: 1; } 96% { opacity: 0.7; } }
    .hero.broken .face { border-color: #ff4a4a; box-shadow: 0 0 60px rgba(255,40,40,0.6); }
    .hero.sc01 .face { animation: scflash 0.4s steps(2) 3; }
    @keyframes scflash { 50% { box-shadow: 0 0 70px rgba(255,30,30,0.9), inset 0 0 60px rgba(255,30,30,0.5); border-color: #ff3030; } }

    .panel { min-width: 0; }
    .ptitle { font-size: 10px; letter-spacing: 4px; color: var(--dim); text-transform: uppercase; margin-bottom: 6px; }
    .state { font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 44px; letter-spacing: 8px; color: #7777ff; line-height: 1; margin-bottom: 14px; transition: color 0.3s, text-shadow 0.3s; }
    .hero.summoned .state { color: var(--tc); text-shadow: 0 0 22px rgba(var(--tcrgb), 0.9); }
    .hero.inactive .state, .hero.broken .state { color: #ff4a4a; text-shadow: 0 0 22px rgba(255,40,40,0.8); }
    .intbar { height: 8px; background: #101024; border: 1px solid #1a1a3a; margin: 4px 0 14px; position: relative; overflow: hidden; }
    .intbar span { position: absolute; left: 0; top: 0; bottom: 0; width: 100%; background: linear-gradient(90deg, #ff3a3a, #ffd600 45%, #4fc3f7); transition: width 0.6s ease; }
    .tiers { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 14px; }
    .btn { background: rgba(10,10,24,0.9); color: #9a9aff; border: 1px solid rgba(100,100,255,0.4); font-family: 'Share Tech Mono', monospace; font-size: 11px; letter-spacing: 2px; padding: 10px 16px; cursor: pointer; text-transform: uppercase; transition: all 0.22s; }
    .btn:hover:not(:disabled) { background: rgba(100,100,255,0.2); color: #fff; box-shadow: 0 0 20px rgba(100,100,255,0.4); transform: translateY(-1px); }
    .btn:disabled { opacity: 0.35; cursor: default; }
    .btn.on { background: var(--acc-d); color: #fff; border-color: var(--acc); }
    .btn.pri { border-color: #7777ff; color: #fff; background: rgba(68,68,204,0.4); }
    .btn.dng { border-color: rgba(204,0,0,0.6); color: #ff6a6a; }
    .btn.dng:hover:not(:disabled) { background: rgba(204,0,0,0.3); box-shadow: 0 0 20px rgba(255,0,0,0.4); }
    .btn.t1.on { background: #1a5a7a; border-color: #4fc3f7; } .btn.t2.on { background: #6a5a00; border-color: #ffd600; } .btn.t3.on { background: #7a1a14; border-color: #f44336; }
    .btns { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 14px; }
    .log { font-size: 12px; line-height: 1.8; min-height: 130px; color: #8a8aba; border-left: 2px solid #1a1a4a; padding-left: 12px; }
    .log div { animation: logIn 0.4s ease both; }
    .log div.bad { color: #ff6a6a; } .log div.good { color: #8aa0ff; }
    @keyframes logIn { from { opacity: 0; transform: translateX(-6px); } to { opacity: 1; transform: none; } }

    /* ═══ SECTIONS ═══ */
    .section-label { font-size: 10px; letter-spacing: 4px; color: var(--acc-d); text-transform: uppercase; margin-bottom: 12px; margin-top: 42px; padding-bottom: 7px; border-bottom: 1px solid #0a0a2a; position: relative; }
    .section-label::after { content: ''; position: absolute; left: 0; bottom: -1px; width: 90px; height: 2px; background: linear-gradient(90deg, var(--acc), transparent); }
    .section-label.addendum { color: #b04bd0; border-bottom-color: #1a0a2a; }
    .section-label.addendum::after { background: linear-gradient(90deg, #9c27b0, transparent); }

    .content-block { background: var(--panel); border: 1px solid #1a1a2a; border-left: 3px solid #1a1a4a; padding: 18px 20px; margin-bottom: 8px; font-size: 12px; line-height: 1.95; color: #9a9ab8; backdrop-filter: blur(2px); transition: border-left-color 0.25s; }
    .content-block:hover { border-left-color: var(--acc); }
    .content-block p { margin-bottom: 8px; } .content-block p:last-child { margin-bottom: 0; }
    .content-block strong.k { color: #cfcfff; }

    .mechanic-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 10px; margin-bottom: 10px; perspective: 900px; }
    @media (max-width: 700px) { .mechanic-grid { grid-template-columns: 1fr; } }
    .mechanic-card, .pulse-card {
      --rx: 0deg; --ry: 0deg; --px: 50%; --py: 50%; position: relative; padding: 18px; background: var(--panel); border: 1px solid #1a1a2a; border-top: 3px solid #1a1a4a;
      font-size: 11px; color: #8a8aa8; line-height: 1.8; overflow: hidden; transform: rotateX(var(--rx)) rotateY(var(--ry)); transition: transform 0.2s ease-out, border-color 0.3s, box-shadow 0.3s; transform-style: preserve-3d;
    }
    .mechanic-card::after, .pulse-card::after { content: ''; position: absolute; inset: 0; pointer-events: none; opacity: 0; transition: opacity 0.3s; background: radial-gradient(circle at var(--px) var(--py), rgba(190,190,255,0.20), transparent 55%); }
    .mechanic-card:hover, .pulse-card:hover { border-color: var(--acc-d); box-shadow: 0 10px 34px rgba(0,0,0,0.6), 0 0 26px rgba(100,100,255,0.22); }
    .mechanic-card:hover::after, .pulse-card:hover::after { opacity: 1; }
    .mechanic-card .title { font-family: 'Rajdhani', sans-serif; font-size: 15px; font-weight: 700; color: var(--acc); letter-spacing: 3px; text-transform: uppercase; margin-bottom: 8px; }

    .rule-item { display: flex; align-items: flex-start; gap: 12px; padding: 11px 16px; background: var(--panel); border: 1px solid #1a1a2a; border-left: 3px solid #1a1a4a; font-size: 12px; color: #9a9ab8; margin-bottom: 5px; line-height: 1.7; transition: transform 0.2s, border-left-color 0.2s, color 0.2s; }
    .rule-item:hover { transform: translateX(5px); border-left-color: var(--acc); color: #dcdcff; }
    .rule-item .arrow { color: var(--acc); flex-shrink: 0; margin-top: 2px; }
    .rule-item.ad { border-left-color: #3a0a4a; } .rule-item.ad .arrow { color: #b04bd0; } .rule-item.ad:hover { border-left-color: #b04bd0; }
    .rule-item a.inl { color: #b8b8ff; text-decoration: none; border-bottom: 1px dashed #5555cc; } .rule-item a.inl:hover { color: #fff; }

    .denied-item { display: flex; align-items: center; gap: 12px; padding: 11px 16px; background: rgba(13,0,0,0.8); border: 1px solid #1a0000; border-left: 3px solid #8b0000; font-size: 12px; color: #cc4444; margin-bottom: 5px; transition: transform 0.2s; position: relative; overflow: hidden; }
    .denied-item:hover { transform: translateX(5px); }
    .denied-item::after { content: 'INELIGIBLE'; position: absolute; right: 12px; font-size: 9px; letter-spacing: 4px; color: rgba(204,0,0,0.35); }
    .denied-item .x { color: #ff2a2a; font-size: 14px; }

    .warning-block { background: rgba(13,0,0,0.85); border: 1px solid #3a0000; border-left: 3px solid #cc0000; padding: 16px 20px; margin-bottom: 8px; font-size: 12px; color: #cc4444; line-height: 1.9; position: relative; overflow: hidden; }
    .warning-block::before { content: ''; position: absolute; right: -30px; top: -30px; width: 120px; height: 120px; border-radius: 50%; background: radial-gradient(circle, rgba(255,40,40,0.18), transparent 70%); animation: pulse 3s ease-in-out infinite; }
    @keyframes pulse { 0%,100% { transform: scale(1); opacity: 0.6; } 50% { transform: scale(1.4); opacity: 1; } }
    .warning-block strong { color: #ff4444; }

    .pulse-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 10px; margin-bottom: 10px; perspective: 900px; }
    @media (max-width: 700px) { .pulse-grid { grid-template-columns: 1fr; } }
    .pulse-card .tier { font-family: 'Rajdhani', sans-serif; font-size: 15px; font-weight: 700; letter-spacing: 3px; margin-bottom: 8px; text-transform: uppercase; position: relative; }
    .pulse-card.low { border-top-color: #4fc3f7; } .pulse-card.low .tier { color: #4fc3f7; }
    .pulse-card.mid { border-top-color: #ffd600; } .pulse-card.mid .tier { color: #ffd600; }
    .pulse-card.high { border-top-color: #f44336; } .pulse-card.high .tier { color: #f44336; }
    .pring { position: absolute; right: 26px; top: 26px; width: 8px; height: 8px; pointer-events: none; }
    .pring i { position: absolute; inset: 0; border-radius: 50%; border: 2px solid currentColor; opacity: 0; animation: pr 3s ease-out infinite; }
    .pring i:nth-child(2) { animation-delay: 1s; } .pring i:nth-child(3) { animation-delay: 2s; }
    @keyframes pr { 0% { transform: scale(0.4); opacity: var(--op); } 100% { transform: scale(var(--sc)); opacity: 0; } }
    .pulse-card.low .pring { color: #4fc3f7; } .pulse-card.mid .pring { color: #ffd600; } .pulse-card.high .pring { color: #f44336; }

    /* widgets */
    .wbox { padding: 22px 24px; margin: 10px 0; background: var(--panel); border: 1px solid #1a1a4a; border-left: 3px solid var(--acc-d); position: relative; }
    .wbox .wt { font-size: 10px; letter-spacing: 4px; color: var(--dim); text-transform: uppercase; margin-bottom: 12px; }
    .chips { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 12px; }
    .readout { font-size: 12px; letter-spacing: 2px; color: #8a8aba; margin: 6px 0 10px; text-transform: uppercase; } .readout b { color: #fff; font-weight: 400; font-size: 16px; }
    .tmsg { min-height: 26px; font-size: 13px; color: #9a9aff; letter-spacing: 1px; }
    .tmsg.drop { color: #ffd600; text-shadow: 0 0 14px rgba(255,214,0,0.8); }
    .strip { display: flex; flex-wrap: wrap; gap: 2px; margin-top: 10px; }
    .strip i { width: 9px; height: 9px; background: #14142c; display: block; } .strip i.hit { background: #ffd600; box-shadow: 0 0 10px #ffd600; }
    .dropcard { position: absolute; right: 24px; top: -70px; width: 56px; height: 80px; border: 2px solid #ffd600; border-radius: 6px; background: linear-gradient(160deg, #3a3000, #151000); box-shadow: 0 0 30px rgba(255,214,0,0.8); opacity: 0; pointer-events: none; }
    .dropcard.go { animation: dropc 2.4s ease-in forwards; }
    @keyframes dropc { 0% { opacity: 1; transform: translateY(0) rotate(-12deg); } 60% { opacity: 1; transform: translateY(150px) rotate(10deg); } 100% { opacity: 0; transform: translateY(190px) rotate(0); } }
    input[type=range] { -webkit-appearance: none; appearance: none; width: 100%; height: 8px; border-radius: 6px; background: linear-gradient(90deg, #3a3a6a, #7777ff 60%, #ce7adb); outline: none; margin: 8px 0 14px; }
    input[type=range]::-webkit-slider-thumb { -webkit-appearance: none; width: 22px; height: 22px; border-radius: 50%; background: #fff; border: 3px solid #7777ff; box-shadow: 0 0 14px rgba(120,120,255,0.8); cursor: pointer; }
    input[type=range]::-moz-range-thumb { width: 18px; height: 18px; border-radius: 50%; background: #fff; border: 3px solid #7777ff; cursor: pointer; }
    .bars { display: grid; gap: 8px; margin-bottom: 10px; }
    .bar { position: relative; height: 22px; background: #0c0c1e; border: 1px solid #1a1a3a; }
    .bar i { position: absolute; left: 8px; top: 0; bottom: 0; display: flex; align-items: center; font-style: normal; font-size: 10px; letter-spacing: 2px; color: #fff; z-index: 2; text-transform: uppercase; text-shadow: 0 0 6px #000; }
    .bar span { position: absolute; left: 0; top: 0; bottom: 0; transition: width 0.4s ease, background 0.4s; }
    .bar.orig span { width: 60%; background: linear-gradient(90deg, #333366, #5555aa); }
    .bar.serv span { background: linear-gradient(90deg, #4444cc, #aab0ff); }
    .bar .mk { position: absolute; left: 60%; top: -4px; bottom: -4px; width: 2px; background: #ffd600; z-index: 3; }

    .priority-box { display: flex; align-items: center; gap: 18px; padding: 16px 20px; background: rgba(13,0,0,0.85); border: 1px solid #3a0000; border-left: 4px solid #cc0000; margin-bottom: 8px; flex-wrap: wrap; }
    .priority-label { font-size: 10px; color: #6a6a8a; letter-spacing: 2px; text-transform: uppercase; }
    .priority-value { font-family: 'Rajdhani', sans-serif; font-size: 26px; font-weight: 700; color: #ff2a2a; letter-spacing: 4px; text-shadow: 0 0 14px rgba(255,0,0,0.5); }
    .priority-note { font-size: 11px; color: #7a7a9a; line-height: 1.7; flex: 1; min-width: 220px; }

    .internal-quote { background: rgba(8,8,16,0.9); border: 1px solid #1a1a2a; border-left: 4px solid #7777ff; padding: 22px 26px; margin: 16px 0; position: relative; }
    .internal-quote::before { content: '"'; position: absolute; top: -10px; left: 16px; background: var(--bg); padding: 0 6px; color: #7777ff; font-size: 30px; font-family: serif; line-height: 1; }
    .internal-quote.purple { border-left-color: #9c27b0; } .internal-quote.purple::before { color: #9c27b0; }
    .internal-quote p { font-size: 14px; color: #b8b8d8; line-height: 1.9; font-style: italic; }
    .internal-quote .attribution { margin-top: 12px; font-size: 10px; color: #6a6a8a; letter-spacing: 2px; text-transform: uppercase; font-style: normal; }

    /* addendum */
    .addendum-header { border: 1px solid #1a0a2a; padding: 24px 26px; margin-top: 54px; margin-bottom: 18px; position: relative; background: linear-gradient(180deg, rgba(10,5,15,0.92) 0%, rgba(8,8,8,0.92) 100%); box-shadow: inset 0 0 60px rgba(156,39,176,0.10), 0 0 40px rgba(156,39,176,0.12); overflow: hidden; }
    .addendum-header::before { content: '// ADDENDUM //'; position: absolute; top: -10px; left: 20px; background: var(--bg); padding: 0 10px; color: #9c27b0; font-size: 11px; letter-spacing: 3px; }
    .addendum-header::after { content: ''; position: absolute; top: 0; right: 0; width: 34px; height: 34px; border-top: 2px solid #9c27b0; border-right: 2px solid #9c27b0; }
    .addendum-id { font-size: 10px; color: #9c27b0; letter-spacing: 4px; margin-bottom: 6px; }
    .addendum-title { font-family: 'Rajdhani', sans-serif; font-size: 36px; font-weight: 700; color: #ce7adb; letter-spacing: 4px; text-shadow: 0 0 16px rgba(156,39,176,0.5); animation: glitch 7s steps(1) infinite; }
    @keyframes glitch { 0%,94%,100% { transform: none; text-shadow: 0 0 16px rgba(156,39,176,0.5); } 95% { transform: translateX(3px); text-shadow: -3px 0 #00e5ff, 3px 0 #ff0040; } 96% { transform: translateX(-3px); } 97% { transform: none; } }
    .status-badge { display: inline-block; padding: 4px 12px; font-size: 10px; letter-spacing: 2px; border: 1px solid; text-transform: uppercase; margin-top: 6px; }
    .status-badge.unverified { color: #ff7a2a; border-color: #5a2a00; animation: unv 2.4s ease-in-out infinite; }
    @keyframes unv { 50% { background: rgba(255,122,42,0.14); } }

    /* console */
    .console { display: grid; grid-template-columns: 1fr 270px; gap: 10px; margin: 10px 0; }
    @media (max-width: 800px) { .console { grid-template-columns: 1fr; } }
    .radar-wrap { position: relative; border: 1px solid #1a0a2a; background: rgba(5,3,10,0.92); height: 330px; overflow: hidden; box-shadow: inset 0 0 40px rgba(156,39,176,0.12); }
    #radar { width: 100%; height: 100%; display: block; }
    .radar-wrap::before { content: 'GLOBAL PULSE TRACKING'; position: absolute; top: 8px; left: 12px; z-index: 2; font-size: 9px; letter-spacing: 4px; color: #9c27b0; }
    .clog { border: 1px solid #1a0a2a; background: rgba(8,5,14,0.9); padding: 12px; height: 330px; overflow: hidden; }
    .clog-t { font-size: 9px; letter-spacing: 3px; color: #9c27b0; margin-bottom: 10px; }
    .clog .ev { font-size: 10px; line-height: 1.6; letter-spacing: 1px; padding: 5px 0; border-bottom: 1px solid #14102a; animation: logIn 0.4s ease both; color: #9a9ab8; }
    .clog .ev b { font-weight: 400; } .clog .ev.un { color: #ff6a6a; }

    .footer { border-top: 1px solid #1a0000; padding-top: 20px; margin-top: 50px; font-size: 10px; color: #333; letter-spacing: 1px; line-height: 1.8; text-align: center; }
    .end-line { display: flex; align-items: center; gap: 14px; margin: 14px 0 20px; color: #3a2a5a; font-size: 10px; letter-spacing: 4px; text-transform: uppercase; }
    .end-line::before, .end-line::after { content: ''; flex: 1; height: 1px; background: linear-gradient(90deg, transparent, #2a1a4a, transparent); }

    .hud { position: fixed; left: 14px; bottom: 14px; z-index: 700; }
    .hud button { background: rgba(8,8,20,0.9); color: #9a9aff; border: 1px solid rgba(100,100,255,0.35); padding: 7px 12px; font-family: inherit; font-size: 10px; letter-spacing: 2px; cursor: pointer; text-transform: uppercase; }
    .hud button:hover { color: #fff; border-color: #9a9aff; }

    @media (prefers-reduced-motion: reduce) { .float, .file-title, .hline, .addendum-title, .pring i, .warning-block::before, .art .ring, .art .mist { animation: none !important; } .reveal { opacity: 1; transform: none; transition: none; } }
  </style>
</head>
<body>

  <svg width="0" height="0" style="position:absolute" aria-hidden="true">
    <defs>
      <radialGradient id="artg" cx=".5" cy=".5" r=".7"><stop offset="0" stop-color="#1a1a4a"/><stop offset="1" stop-color="#05050f"/></radialGradient>
    </defs>
  </svg>

  <canvas id="bg" aria-hidden="true"></canvas>
  <canvas id="wave" aria-hidden="true"></canvas>
  <canvas id="cracks" aria-hidden="true"></canvas>
  <div class="ov-vig"></div>
  <div class="hud"><button id="fxBtn" type="button">&#9680; Effects: full</button></div>

  <div class="warning-bar">
    ⚠ RESTRICTED ACCESS — AUTHORIZED PERSONNEL ONLY — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="container" id="page">

    <a href="index.html" class="back-link">← RETURN TO DATABASE INDEX</a>

    <div class="file-header reveal">
      <div class="hline"></div>
      <div class="file-id">FILE: SYS-01</div>
      <div class="file-title">SERVANT CARD SYSTEM</div>
      <div class="file-designation">Post-Termination Anomalous Artifact System — Active Research</div>
      <div class="meta-grid">
        <div class="meta-item"><span class="meta-label">THREAT LEVEL</span><span class="meta-value purple">Variable — User Dependent</span></div>
        <div class="meta-item"><span class="meta-label">CLEARANCE</span><span class="meta-value red">DIVIDE Level 2+</span></div>
        <div class="meta-item"><span class="meta-label">STATUS</span><span class="meta-value orange">Uncontained / Monitored</span></div>
        <div class="meta-item"><span class="meta-label">RESEARCH PRIORITY</span><span class="meta-value red">HIGH</span></div>
      </div>
    </div>

    <!-- SIMULATOR -->
    <div class="hero reveal" id="hero">
      <div class="stage" id="stage">
        <div class="float">
          <div class="card3d t1" id="hcard">
            <div class="face">
              <div class="foil"></div>
              <div class="ctop"><span>Servant Card</span><span>SYS-01</span></div>
              <div class="art">
                <svg viewBox="0 0 200 215" preserveAspectRatio="xMidYMid slice" aria-hidden="true">
                  <rect width="200" height="215" fill="url(#artg)"/>
                  <circle class="ring" cx="100" cy="108" r="82"/><circle class="ring r2" cx="100" cy="108" r="64"/>
                  <polygon class="ring" points="100,34 164,134 36,134" /><polygon class="ring r2" points="100,182 36,82 164,82"/>
                  <ellipse class="mist" cx="100" cy="190" rx="90" ry="16"/>
                  <g class="ent">
                    <path d="M100 38 c-22 0-34 18-34 38 c0 14 6 24 6 24 l-20 100 h96 l-20-100 s6-10 6-24 c0-20-12-38-34-38z" fill="#06060f" stroke="rgba(160,160,255,0.45)" stroke-width="1.4"/>
                    <path d="M72 100 L44 150 M128 100 L156 150" stroke="rgba(160,160,255,0.35)" stroke-width="2"/>
                    <circle class="eye" cx="88" cy="76" r="3.4"/><circle class="eye" cx="112" cy="76" r="3.4"/>
                  </g>
                </svg>
              </div>
              <div class="cserial" id="cSerial">— — — —</div>
              <div class="cbot"><div class="cstat"><i>SUMMONS</i><b id="cSum">0</b></div><div class="cstat"><i>INTEGRITY</i><b id="cInt">100%</b></div></div>
              <svg class="ccrack" id="cCrack" viewBox="0 0 250 365" preserveAspectRatio="none" aria-hidden="true"></svg>
              <div class="stampc" id="cStamp">INACTIVE</div>
            </div>
          </div>
        </div>
      </div>
      <div class="panel">
        <div class="ptitle">Servant state</div>
        <div class="state" id="cState">DORMANT</div>
        <div class="ptitle">Card integrity</div>
        <div class="intbar"><span id="intBar"></span></div>
        <div class="ptitle">Servant power tier — sets Fracture Pulse intensity</div>
        <div class="tiers" id="tiers">
          <button class="btn t1 on" data-t="1" type="button">Class I</button>
          <button class="btn t2" data-t="2" type="button">Class II–III</button>
          <button class="btn t3" data-t="3" type="button">Class IV+</button>
        </div>
        <div class="btns">
          <button class="btn pri" id="bSummon" type="button">&#10022; Summon</button>
          <button class="btn" id="bDismiss" type="button">Dismiss</button>
          <button class="btn dng" id="bKill" type="button">Servant killed</button>
          <button class="btn dng" id="bSC" type="button">Simulate SC-01</button>
          <button class="btn" id="bNew" type="button">&#8635; Draw new card</button>
        </div>
        <div class="log" id="cLog"></div>
      </div>
    </div>

    <!-- OVERVIEW -->
    <div class="section-label reveal">// Overview //</div>
    <div class="content-block reveal">
      <p>The Servant Card System refers to a rare phenomenon in which a terminated anomaly has an extremely low probability of generating a physical artifact known as a <strong class="k">Servant Card</strong>.</p>
      <p>These cards allow the holder to summon a bound version of the original anomaly. The mechanism of generation is not fully understood. D.I.V.I.D.E. research into the origin of the phenomenon remains ongoing with HIGH priority classification.</p>
    </div>

    <!-- ACQUISITION -->
    <div class="section-label reveal">// Acquisition Conditions //</div>
    <div class="mechanic-grid reveal">
      <div class="mechanic-card"><div class="title">Trigger</div>Successful termination of an anomaly. Drop rate is near-zero. Cannot be forced or predicted.</div>
      <div class="mechanic-card"><div class="title">Eligible</div>Living and sentient anomalies only. Item anomalies and location anomalies do not generate cards.</div>
      <div class="mechanic-card"><div class="title">Drop Rate</div>Near-zero probability. Exact figures classified. Most termination events yield no artifact.</div>
    </div>

    <div class="wbox reveal" id="termBox">
      <div class="dropcard" id="dropCard"></div>
      <div class="wt">Termination yield simulator</div>
      <div class="chips" id="termChips">
        <button class="btn on" data-k="living" type="button">Living &amp; sentient anomaly</button>
        <button class="btn" data-k="item" type="button">Item anomaly</button>
        <button class="btn" data-k="loc" type="button">Location anomaly</button>
      </div>
      <div class="btns"><button class="btn pri" id="bTerm" type="button">Terminate anomaly</button><button class="btn" id="bTerm1k" type="button">Run 1,000 terminations</button></div>
      <div class="readout">Terminations <b id="tN">0</b> &nbsp;·&nbsp; Servant Cards generated <b id="tC">0</b></div>
      <div class="tmsg" id="tMsg">Most termination events yield no artifact.</div>
      <div class="strip" id="tStrip"></div>
    </div>

    <!-- SUMMONING -->
    <div class="section-label reveal">// Summoning Rules //</div>
    <div class="rule-item reveal"><span class="arrow">▶</span>Servants can be summoned, dismissed, and re-summoned at will by the card holder.</div>
    <div class="rule-item reveal"><span class="arrow">▶</span>If the Servant is killed while summoned, the card becomes permanently inactive and cannot be restored or repaired.</div>

    <div class="denied-item reveal"><span class="x">✕</span>Item anomalies — ineligible for card generation</div>
    <div class="denied-item reveal"><span class="x">✕</span>Location anomalies — ineligible for card generation</div>
    <div class="denied-item reveal"><span class="x">✕</span>Activated cards — cannot be sold or transferred</div>

    <!-- POWER SCALING -->
    <div class="section-label reveal">// Power Scaling //</div>
    <div class="content-block reveal">
      <p>Servants are not exact copies of the original anomaly. Their effective power is influenced by user compatibility, psychological alignment, and unknown external factors.</p>
      <p>Some Servants manifest weaker than the original entity. Others exceed the original's power under specific users. The compatibility mechanism is not fully understood.</p>
    </div>

    <div class="wbox reveal">
      <div class="wt">Compatibility sandbox</div>
      <div class="readout">User compatibility <b id="cmpOut">50%</b></div>
      <input type="range" id="cmp" min="0" max="100" value="50" aria-label="User compatibility">
      <div class="bars">
        <div class="bar orig"><i>Original anomaly</i><span></span></div>
        <div class="bar serv"><i>Servant</i><span id="servBar"></span><div class="mk"></div></div>
      </div>
      <div class="tmsg" id="cmpMsg"></div>
    </div>

    <div class="mechanic-grid reveal">
      <div class="mechanic-card"><div class="title">High Sync</div>Reaction time improves drastically. Combat coordination becomes near-perfect. Power output increases beyond baseline.</div>
      <div class="mechanic-card"><div class="title">Recorded Case</div>A Tier I anomaly paired with a compatible human user achieved perfect synchronization and was temporarily reclassified as a Tier III combat threat.</div>
      <div class="mechanic-card"><div class="title">High Tier Risk</div>High-tier Servants are more likely to reject control, act independently, and refuse participation entirely. Instability scales with power.</div>
    </div>

    <!-- BEHAVIOR -->
    <div class="section-label reveal">// Behavior & Control //</div>
    <div class="content-block reveal">
      <p>Servants generally follow commands. However, they are not fully controlled entities. Known exceptions include refusal of commands, refusal to fight, and refusal to be summoned at all.</p>
    </div>
    <div class="warning-block reveal">
      <strong>CRITICAL INCIDENT — SC-01:</strong><br>
      A Servant rejected its master, terminated the summoner, and immediately de-summoned itself afterward. No further incidents of this type have been formally recorded. Probability of recurrence: unknown.
    </div>

    <!-- TRADE -->
    <div class="section-label reveal">// Trade & Black Market //</div>
    <div class="rule-item reveal"><span class="arrow">▶</span><span>Servant Cards are extremely rare, highly valuable, and traded primarily within <a class="inl" href="black_streets.html">Black Street</a>.</span></div>
    <div class="rule-item reveal"><span class="arrow">▶</span>Unused cards can be sold or stolen. Once activated through summoning, ownership becomes permanently bound to the user.</div>
    <div class="rule-item reveal"><span class="arrow">▶</span>D.I.V.I.D.E. actively monitors card circulation and attempts acquisition when possible.</div>

    <!-- RISK -->
    <div class="section-label reveal">// Risk Classification //</div>
    <div class="mechanic-grid reveal">
      <div class="mechanic-card"><div class="title">Permanent Loss</div>If the Servant dies while active, the card is gone forever. No recovery. No repair. High-tier cards represent catastrophic value loss.</div>
      <div class="mechanic-card"><div class="title">Unstable Obedience</div>Servants are not guaranteed to follow orders. High-tier entities may ignore commands entirely or act against the holder's interests.</div>
      <div class="mechanic-card"><div class="title">User Termination</div>Documented cases of Servants killing their summoners exist. Risk scales with tier and psychological incompatibility.</div>
    </div>

    <div class="priority-box reveal">
      <div><div class="priority-label">D.I.V.I.D.E. Research Priority</div><div class="priority-value">HIGH</div></div>
      <div class="priority-note">Origin mechanism unknown. Circulation monitored. Acquisition attempted when possible. Full understanding has not been achieved.</div>
    </div>

    <div class="internal-quote reveal">
      <p>You don't own them.<br>You convince them not to kill you.</p>
      <div class="attribution">— D.I.V.I.D.E. Anomalous Systems Division</div>
    </div>

    <!-- ADDENDUM -->
    <div class="addendum-header reveal" id="addendum">
      <div class="addendum-id">ADDENDUM: SYS-01-A</div>
      <div class="addendum-title">Card Fracture Pulse Phenomenon</div>
    </div>

    <div class="section-label addendum reveal">// Fracture Behavior //</div>
    <div class="content-block reveal" style="border-left-color: #3a0a4a;">
      <p>Upon initial summoning from a Servant Card, the card undergoes a micro-fracture event accompanied by the release of an anomalous energy surge designated as a <strong class="k">Fracture Pulse</strong>. This phenomenon has been confirmed in all successful summoning events.</p>
      <p>The card develops visible cracks across its surface. These cracks do not destroy the card but remain permanently. Crack patterns appear unique per anomaly. With each subsequent summon, existing fractures expand slightly and structural integrity degrades over time.</p>
    </div>

    <div class="section-label addendum reveal">// Fracture Pulse Characteristics //</div>
    <div class="rule-item ad reveal"><span class="arrow">▶</span>Origin point: Card location. Duration under 1 second.</div>
    <div class="rule-item ad reveal"><span class="arrow">▶</span>Detectable by D.I.V.I.D.E. monitoring systems and high-sensitivity anomaly sensors.</div>
    <div class="rule-item ad reveal"><span class="arrow">▶</span>Pulse intensity scales directly with the Servant's effective power tier.</div>

    <div class="section-label addendum reveal">// Pulse Intensity by Tier //</div>
    <div class="pulse-grid reveal">
      <div class="pulse-card low"><span class="pring" style="--sc:5;--op:.35"><i></i><i></i></span><div class="tier">Class I — Low</div>Barely detectable. Localized disturbance only. Standard monitoring may miss entirely.</div>
      <div class="pulse-card mid"><span class="pring" style="--sc:9;--op:.55"><i></i><i></i><i></i></span><div class="tier">Class II–III — Mid</div>Noticeable energy spike. Trackable within the surrounding region. Raises monitoring flags.</div>
      <div class="pulse-card high"><span class="pring" style="--sc:15;--op:.85"><i></i><i></i><i></i></span><div class="tier">Class IV+ — High</div>Strong anomaly signal. Triggers immediate D.I.V.I.D.E. attention. Possible temporary environmental distortion.</div>
    </div>

    <div class="section-label addendum reveal">// Operational Risks //</div>
    <div class="rule-item ad reveal"><span class="arrow">▶</span>Repeated summoning increases detection risk and card structural instability simultaneously.</div>
    <div class="rule-item ad reveal"><span class="arrow">▶</span>High-frequency use may attract nearby anomalies and interfere with adjacent anomalous systems.</div>

    <div class="content-block reveal" style="border-left-color: #3a0a4a; margin-top: 8px;">
      <p><strong class="k">Failure Risk (Unconfirmed):</strong> Ongoing investigations suggest excessive fracturing may result in uncontrolled Servant manifestation, permanent summoning state, or hostile behavior deviation from baseline parameters.</p>
      <div style="margin-top: 10px;"><span class="status-badge unverified">Status: Unverified</span></div>
    </div>

    <div class="section-label addendum reveal">// D.I.V.I.D.E. Utilization //</div>
    <div class="rule-item ad reveal"><span class="arrow">▶</span>Fracture Pulses are actively used to track Servant Card usage globally.</div>
    <div class="rule-item ad reveal"><span class="arrow">▶</span>Unauthorized summoning events are identified and investigated through pulse signature analysis.</div>
    <div class="rule-item ad reveal"><span class="arrow">▶</span>High-value targets are located through sustained pulse tracking over time.</div>

    <div class="console reveal">
      <div class="radar-wrap"><canvas id="radar"></canvas></div>
      <div class="clog"><div class="clog-t">PULSE LOG — FP SERIES</div><div id="clogList"></div></div>
    </div>

    <div class="internal-quote purple reveal">
      <p>We thought the cards were quiet tools.<br>Turns out every time you use one… you're lighting a flare.</p>
      <div class="attribution">— D.I.V.I.D.E. Monitoring Division — Internal Log FP-07</div>
    </div>

    <div class="end-line">End of file</div>

    <div class="footer">
      <p>&copy; 2026 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2026-04-24</p>
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
      var TC = { 1: '79,195,247', 2: '255,214,0', 3: '244,67,54' };
      var TN = { 1: 'CLASS I', 2: 'CLASS II\u2013III', 3: 'CLASS IV+' };

      var bgCv = $('bg'), bg = bgCv.getContext('2d'), wvCv = $('wave'), wv = wvCv.getContext('2d'), crCv = $('cracks');
      var rdCv = $('radar'), rd = rdCv.getContext('2d');
      var W = 0, H = 0, dpr = Math.min(window.devicePixelRatio || 1, 1.5), th = 0, summonsTotal = 0, shakeT = 0;
      var cards = [], dust = [], waves = [], ptr = { x: 0, y: 0 };
      var container = $('page');

      /* ═══ BACKGROUND CARDS ═══ */
      function mkCard(init) { var w = rand(34, 88); return { x: rand(0, W), y: init ? rand(0, H) : H + 120, w: w, h: w * 1.45, a: rand(-0.5, 0.5), va: rand(-0.07, 0.07), vy: -rand(6, 22), depth: w / 88, al: rand(0.05, 0.15), crack: Math.random() < 0.4 }; }
      function mixc(t) { return Math.round(119 + 87 * t) + ',' + Math.round(119 + 3 * t) + ',' + Math.round(255 - 36 * t); }
      function drawCard(c, col) {
        var x = c.x + ptr.x * c.depth * 26, y = c.y + ptr.y * c.depth * 18, w = c.w, h = c.h, r = 6;
        bg.save(); bg.translate(x, y); bg.rotate(c.a);
        bg.beginPath(); bg.moveTo(-w / 2 + r, -h / 2); bg.lineTo(w / 2 - r, -h / 2); bg.quadraticCurveTo(w / 2, -h / 2, w / 2, -h / 2 + r); bg.lineTo(w / 2, h / 2 - r); bg.quadraticCurveTo(w / 2, h / 2, w / 2 - r, h / 2); bg.lineTo(-w / 2 + r, h / 2); bg.quadraticCurveTo(-w / 2, h / 2, -w / 2, h / 2 - r); bg.lineTo(-w / 2, -h / 2 + r); bg.quadraticCurveTo(-w / 2, -h / 2, -w / 2 + r, -h / 2); bg.closePath();
        bg.fillStyle = 'rgba(' + col + ',' + (c.al * 0.18) + ')'; bg.fill(); bg.lineWidth = 1; bg.strokeStyle = 'rgba(' + col + ',' + (c.al * 1.7) + ')'; bg.stroke();
        bg.beginPath(); bg.arc(0, 0, w * 0.22, 0, TAU); bg.moveTo(-w * 0.22, 0); bg.lineTo(w * 0.22, 0); bg.moveTo(0, -w * 0.22); bg.lineTo(0, w * 0.22); bg.stroke();
        if (c.crack) { bg.beginPath(); bg.moveTo(-w * 0.5, -h * 0.2); bg.lineTo(-w * 0.1, -h * 0.05); bg.lineTo(w * 0.05, h * 0.15); bg.lineTo(w * 0.5, h * 0.3); bg.stroke(); }
        bg.restore();
      }

      /* ═══ SHOCKWAVES ═══ */
      function firePulse(tier, ox, oy, src, auth) {
        if (ox == null) { ox = W / 2; oy = H * 0.4; }
        waves.push({ x: ox, y: oy, tier: tier, t: 0 });
        if (tier >= 2 && !reduce) shakeT = Math.max(shakeT, tier === 3 ? 0.7 : 0.35);
        addEvent(tier, src || 'LOCAL', auth !== false);
      }
      function drawWaves(dt) {
        wv.clearRect(0, 0, W, H);
        for (var i = waves.length - 1; i >= 0; i--) {
          var w = waves[i]; w.t += dt; var dur = 1.2 + w.tier * 0.45, k = w.t / dur;
          if (k >= 1) { waves.splice(i, 1); continue; }
          var maxR = w.tier === 1 ? 300 : w.tier === 2 ? 600 : Math.hypot(W, H) * 0.95, e = 1 - Math.pow(1 - k, 3), r = maxR * e, a = 1 - k, col = TC[w.tier];
          wv.save(); wv.globalCompositeOperation = 'lighter';
          if (k < 0.22) { var fl = (1 - k / 0.22) * 0.28 * w.tier, g = wv.createRadialGradient(w.x, w.y, 0, w.x, w.y, 160 + w.tier * 120); g.addColorStop(0, 'rgba(' + col + ',' + fl + ')'); g.addColorStop(1, 'rgba(' + col + ',0)'); wv.fillStyle = g; wv.fillRect(0, 0, W, H); }
          for (var j = 0; j < 3; j++) { wv.strokeStyle = 'rgba(' + col + ',' + (a * (0.9 - j * 0.25)) + ')'; wv.lineWidth = (3 + w.tier * 2.2) * (1 - k) * (1 - j * 0.25) + 0.5; wv.beginPath(); wv.arc(w.x, w.y, Math.max(1, r * (1 - j * 0.18)), 0, TAU); wv.stroke(); }
          wv.restore();
        }
      }

      /* ═══ SCREEN CRACKS (grow toward the addendum) ═══ */
      function mulberry32(a) { return function () { a |= 0; a = a + 0x6D2B79F5 | 0; var t = Math.imul(a ^ a >>> 15, 1 | a); t = t + Math.imul(t ^ t >>> 7, 61 | t) ^ t; return ((t ^ t >>> 14) >>> 0) / 4294967296; }; }
      function buildCracks() {
        crCv.width = W; crCv.height = H; var g = crCv.getContext('2d'); g.clearRect(0, 0, W, H); g.lineCap = 'round';
        function crack(rnd, x, y, a, len, wd, depth) {
          var px = x, py = y, i;
          for (i = 0; i < len; i += 9) {
            a += (rnd() - 0.5) * 0.7; var nx = px + Math.cos(a) * 9, ny = py + Math.sin(a) * 9;
            g.lineWidth = Math.max(0.5, wd * (1 - i / len)); g.beginPath(); g.moveTo(px, py); g.lineTo(nx, ny); g.stroke(); px = nx; py = ny;
            if (depth > 0 && rnd() < 0.08) crack(rnd, px, py, a + (rnd() < 0.5 ? -1 : 1) * (0.6 + rnd() * 0.8), len * (0.4 + rnd() * 0.3) * (1 - i / len), wd * 0.6, depth - 1);
          }
        }
        var rnd = mulberry32(777), i;
        g.strokeStyle = 'rgba(206,122,219,0.9)';
        for (i = 0; i < 13; i++) {
          var side = (rnd() * 4) | 0, x, y, a;
          if (side === 0) { x = 0; y = rnd() * H; a = (rnd() - 0.5) * 1.3; } else if (side === 1) { x = W; y = rnd() * H; a = Math.PI + (rnd() - 0.5) * 1.3; }
          else if (side === 2) { x = rnd() * W; y = 0; a = Math.PI / 2 + (rnd() - 0.5) * 1.3; } else { x = rnd() * W; y = H; a = -Math.PI / 2 + (rnd() - 0.5) * 1.3; }
          crack(rnd, x, y, a, 160 + rnd() * 340, 1.6 + rnd() * 1.6, 3);
        }
      }

      /* ═══ HERO CARD ═══ */
      var hero = $('hero'), hcard = $('hcard'), cState = $('cState'), cSum = $('cSum'), cInt = $('cInt'), intBar = $('intBar'), cLog = $('cLog'), cCrack = $('cCrack'), cStamp = $('cStamp'), cSerial = $('cSerial');
      var S = { state: 'dormant', sum: 0, integ: 100, tier: 1, cracks: [], busy: false, serial: '' };
      var bS = $('bSummon'), bD = $('bDismiss'), bK = $('bKill'), bSC = $('bSC'), bN = $('bNew');
      function serial() { var s = '', i; for (i = 0; i < 4; i++) s += '0123456789ABCDEF'[(Math.random() * 16) | 0] + '0123456789ABCDEF'[(Math.random() * 16) | 0] + (i < 3 ? '-' : ''); return s; }
      function say(t, cls) { var d = document.createElement('div'); if (cls) d.className = cls; d.textContent = '> ' + t; cLog.appendChild(d); while (cLog.children.length > 6) cLog.removeChild(cLog.firstChild); }
      function newCrackPath() {
        var side = (Math.random() * 4) | 0, x, y, a, Wc = 250, Hc = 365;
        if (side === 0) { x = rand(10, 240); y = 0; a = Math.PI / 2 + rand(-0.6, 0.6); } else if (side === 1) { x = Wc; y = rand(20, 345); a = Math.PI + rand(-0.6, 0.6); }
        else if (side === 2) { x = rand(10, 240); y = Hc; a = -Math.PI / 2 + rand(-0.6, 0.6); } else { x = 0; y = rand(20, 345); a = rand(-0.6, 0.6); }
        var d = 'M' + x.toFixed(1) + ' ' + y.toFixed(1), n = 8 + ((Math.random() * 7) | 0), br = '', i;
        for (i = 0; i < n; i++) { a += (Math.random() - 0.5) * 0.9; x += Math.cos(a) * rand(12, 22); y += Math.sin(a) * rand(12, 22); d += ' L' + x.toFixed(1) + ' ' + y.toFixed(1); if (i === 3 || i === 5) br += ' M' + x.toFixed(1) + ' ' + y.toFixed(1) + ' L' + (x + Math.cos(a + 1) * rand(20, 40)).toFixed(1) + ' ' + (y + Math.sin(a + 1) * rand(20, 40)).toFixed(1); }
        return d + br;
      }
      function renderCracks() { cCrack.innerHTML = S.cracks.map(function (d, i) { return '<path pathLength="1"' + (i === S.cracks.length - 1 && S.fresh ? ' class="new"' : '') + ' d="' + d + '"/>'; }).join(''); S.fresh = false; }
      function ui() {
        hero.classList.toggle('summoned', S.state === 'summoned' || S.state === 'broken');
        hero.classList.toggle('inactive', S.state === 'inactive');
        hero.classList.toggle('broken', S.state === 'broken');
        hero.classList.toggle('low', S.integ < 30 && S.state !== 'inactive');
        cState.textContent = S.state === 'summoned' ? 'SUMMONED' : S.state === 'inactive' ? 'INACTIVE' : S.state === 'broken' ? 'UNSTABLE' : 'DORMANT';
        cStamp.textContent = S.state === 'broken' ? 'UNVERIFIED' : 'INACTIVE';
        cSum.textContent = S.sum; cInt.textContent = Math.round(S.integ) + '%'; intBar.style.width = S.integ + '%'; cSerial.textContent = S.serial;
        var dead = S.state === 'inactive', br = S.state === 'broken';
        bS.disabled = dead || br || S.state === 'summoned' || S.busy; bD.disabled = dead || br || S.state !== 'summoned' || S.busy; bK.disabled = dead || S.state !== 'summoned' && S.state !== 'broken' || S.busy; bSC.disabled = dead || br || S.busy;
      }
      function center() { var r = hcard.getBoundingClientRect(); return [r.left + r.width / 2, r.top + r.height / 2]; }
      function summon(auto) {
        if (S.state === 'inactive' || S.state === 'broken') return;
        S.sum++; summonsTotal++; S.state = 'summoned';
        S.integ = Math.max(0, S.integ - (5 + S.tier * 3 + Math.min(14, S.sum * 1.4)));
        S.cracks.push(newCrackPath()); S.fresh = true; if (S.sum > 3 && Math.random() < 0.6) S.cracks.push(newCrackPath()); renderCracks();
        var c = center(); firePulse(S.tier, c[0], c[1], 'LOCAL', true);
        say('Summon #' + S.sum + ' \u2014 Fracture Pulse released (' + TN[S.tier] + ').', 'good');
        if (S.sum > 1) say('Existing fractures expand. Integrity ' + Math.round(S.integ) + '%.');
        if (S.integ <= 0) { S.state = 'broken'; say('Excessive fracturing \u2014 uncontrolled manifestation. Permanent summoning state. (Unverified)', 'bad'); }
        onScroll(); ui();
      }
      function setTier(t) { S.tier = t; hcard.classList.remove('t1', 't2', 't3'); hcard.classList.add('t' + t); document.querySelectorAll('#tiers .btn').forEach(function (b) { b.classList.toggle('on', +b.getAttribute('data-t') === t); }); }
      function reset() { S.state = 'dormant'; S.sum = 0; S.integ = 100; S.cracks = []; S.busy = false; S.serial = serial(); cLog.innerHTML = ''; renderCracks(); say('New card drawn. The servant sleeps.'); ui(); }
      bS.addEventListener('click', function () { summon(); });
      bD.addEventListener('click', function () { S.state = 'dormant'; say('Servant dismissed. The card remains cracked.'); ui(); });
      bK.addEventListener('click', function () { S.state = 'inactive'; say('Servant killed while summoned. The card is permanently inactive and cannot be restored or repaired.', 'bad'); ui(); });
      bN.addEventListener('click', reset);
      bSC.addEventListener('click', function () {
        if (S.busy) return; S.busy = true; ui();
        if (S.state !== 'summoned') { S.busy = false; summon(); S.busy = true; ui(); }
        setTimeout(function () { hero.classList.add('sc01'); say('Servant rejected its master.', 'bad'); }, 1100);
        setTimeout(function () { say('Summoner terminated.', 'bad'); }, 2300);
        setTimeout(function () { hero.classList.remove('sc01'); S.state = 'dormant'; S.busy = false; say('Servant de-summoned itself.'); ui(); }, 3500);
      });
      document.querySelectorAll('#tiers .btn').forEach(function (b) { b.addEventListener('click', function () { setTier(+b.getAttribute('data-t')); }); });

      /* card tilt */
      (function () {
        var stage = $('stage');
        stage.addEventListener('pointermove', function (e) { var r = hcard.getBoundingClientRect(), x = (e.clientX - r.left) / r.width - 0.5, y = (e.clientY - r.top) / r.height - 0.5; hcard.style.setProperty('--rx', (-y * 16).toFixed(1) + 'deg'); hcard.style.setProperty('--ry', (x * 22).toFixed(1) + 'deg'); hcard.style.setProperty('--fx', (50 + x * 80).toFixed(0)); });
        stage.addEventListener('pointerleave', function () { hcard.style.setProperty('--rx', '0deg'); hcard.style.setProperty('--ry', '0deg'); hcard.style.setProperty('--fx', '50'); });
        document.querySelectorAll('.mechanic-card, .pulse-card').forEach(function (el) {
          el.addEventListener('pointermove', function (e) { var r = el.getBoundingClientRect(), x = (e.clientX - r.left) / r.width, y = (e.clientY - r.top) / r.height; el.style.setProperty('--rx', ((0.5 - y) * 10).toFixed(1) + 'deg'); el.style.setProperty('--ry', ((x - 0.5) * 12).toFixed(1) + 'deg'); el.style.setProperty('--px', (x * 100).toFixed(0) + '%'); el.style.setProperty('--py', (y * 100).toFixed(0) + '%'); });
          el.addEventListener('pointerleave', function () { el.style.setProperty('--rx', '0deg'); el.style.setProperty('--ry', '0deg'); });
        });
      })();

      /* ═══ TERMINATION SIMULATOR ═══ */
      (function () {
        var kind = 'living', n = 0, c = 0, P = 0.0004, strip = $('tStrip'), msg = $('tMsg'), tN = $('tN'), tC = $('tC'), dropEl = $('dropCard');
        document.querySelectorAll('#termChips .btn').forEach(function (b) { b.addEventListener('click', function () { kind = b.getAttribute('data-k'); document.querySelectorAll('#termChips .btn').forEach(function (x) { x.classList.toggle('on', x === b); }); msg.className = 'tmsg'; msg.textContent = kind === 'living' ? 'Most termination events yield no artifact.' : (kind === 'item' ? 'Item anomalies \u2014 ineligible for card generation.' : 'Location anomalies \u2014 ineligible for card generation.'); }); });
        function addBlock(hit) { var i = document.createElement('i'); if (hit) i.className = 'hit'; strip.appendChild(i); while (strip.children.length > 120) strip.removeChild(strip.firstChild); }
        function run(times) {
          if (kind !== 'living') { msg.className = 'tmsg'; msg.textContent = (kind === 'item' ? 'Item anomalies' : 'Location anomalies') + ' \u2014 ineligible for card generation.'; return; }
          var hits = 0, i;
          for (i = 0; i < times; i++) { n++; var hit = Math.random() < P; if (hit) { c++; hits++; } if (times === 1 || i % Math.ceil(times / 60) === 0 || hit) addBlock(hit); }
          tN.textContent = n.toLocaleString('en-US'); tC.textContent = c;
          if (hits) { msg.className = 'tmsg drop'; msg.textContent = 'A Servant Card has been generated.'; dropEl.classList.remove('go'); void dropEl.offsetWidth; dropEl.classList.add('go'); firePulse(1, window.innerWidth / 2, window.innerHeight / 2, 'LOCAL', true); }
          else { msg.className = 'tmsg'; msg.textContent = times > 1 ? times.toLocaleString('en-US') + ' terminations \u2014 no artifact.' : 'Termination successful. No artifact.'; }
        }
        $('bTerm').addEventListener('click', function () { run(1); }); $('bTerm1k').addEventListener('click', function () { run(1000); });
      })();

      /* ═══ COMPATIBILITY SANDBOX ═══ */
      (function () {
        var r = $('cmp'), out = $('cmpOut'), bar = $('servBar'), msg = $('cmpMsg');
        function upd() {
          var c = r.value / 100, f = 0.3 + 1.0 * Math.pow(c, 1.2), pct = 60 * f; out.textContent = r.value + '%'; bar.style.width = Math.min(100, pct) + '%';
          msg.textContent = f < 0.9 ? 'This Servant manifests weaker than the original entity.' : (f <= 1.1 ? 'Power roughly matches the original entity.' : (r.value >= 97 ? 'Perfect synchronization. Power output increases beyond baseline.' : 'This Servant exceeds the original\u2019s power under this user.'));
        }
        r.addEventListener('input', upd); upd();
      })();

      /* ═══ RADAR CONSOLE ═══ */
      var sources = [], blips = [], hist = {}, logEl = $('clogList'), evN = 7;
      var SRC = ['SRC-03', 'SRC-07', 'SRC-11', 'SRC-14', 'SRC-19', 'SRC-22'];
      SRC.forEach(function (s) { sources.push({ id: s, x: rand(0.12, 0.88), y: rand(0.2, 0.86) }); });
      function sizeRadar() { rdCv.width = Math.max(10, rdCv.clientWidth) * dpr; rdCv.height = Math.max(10, rdCv.clientHeight) * dpr; rd.setTransform(dpr, 0, 0, dpr, 0, 0); }
      function addEvent(tier, src, auth) {
        var s = null, i; for (i = 0; i < sources.length; i++) if (sources[i].id === src) s = sources[i];
        var x, y; if (s) { x = s.x; y = s.y; } else { x = 0.5; y = 0.5; src = 'LOCAL'; }
        var b = { x: x, y: y, tier: tier, born: performance.now(), src: src, auth: auth };
        blips.push(b); (hist[src] = hist[src] || []).push(b); if (hist[src].length > 5) hist[src].shift(); if (blips.length > 40) blips.shift();
        var d = new Date(), el = document.createElement('div'); el.className = 'ev' + (auth ? '' : ' un');
        el.innerHTML = '<b>FP-' + pad(evN++ % 100) + '</b> ' + pad(d.getUTCHours()) + ':' + pad(d.getUTCMinutes()) + ':' + pad(d.getUTCSeconds()) + ' \u00B7 ' + TN[tier] + '<br>' + src + (src === 'LOCAL' ? ' \u00B7 SIMULATION' : (auth ? ' \u00B7 MONITORED' : ' \u00B7 UNAUTHORIZED \u2014 INVESTIGATING'));
        logEl.insertBefore(el, logEl.firstChild); while (logEl.children.length > 9) logEl.removeChild(logEl.lastChild);
      }
      var nextAmb = 1500;
      function ambient(now) { if (now < nextAmb) return; nextAmb = now + rand(2600, 6000); var s = sources[(Math.random() * sources.length) | 0], r = Math.random(), tier = r < 0.55 ? 1 : (r < 0.88 ? 2 : 3); addEvent(tier, s.id, Math.random() > 0.3); }
      function drawRadar(now) {
        var w = rdCv.clientWidth, h = rdCv.clientHeight, cx = w / 2, cy = h / 2, R = Math.min(w, h) * 0.46, i;
        rd.clearRect(0, 0, w, h);
        rd.strokeStyle = 'rgba(156,39,176,0.28)'; rd.lineWidth = 1;
        for (i = 1; i <= 4; i++) { rd.beginPath(); rd.arc(cx, cy, R * i / 4, 0, TAU); rd.stroke(); }
        for (i = 0; i < 8; i++) { rd.beginPath(); rd.moveTo(cx, cy); rd.lineTo(cx + Math.cos(i * TAU / 8) * R, cy + Math.sin(i * TAU / 8) * R); rd.stroke(); }
        rd.strokeStyle = 'rgba(156,39,176,0.1)'; for (i = 0; i < 12; i++) { rd.beginPath(); rd.moveTo(i * w / 12, 0); rd.lineTo(i * w / 12, h); rd.stroke(); }
        var ang = light ? 0 : (now / 2400) % TAU;
        for (i = 0; i < 24; i++) { rd.strokeStyle = 'rgba(206,122,219,' + (0.35 * (1 - i / 24)) + ')'; rd.lineWidth = 2; rd.beginPath(); rd.moveTo(cx, cy); rd.lineTo(cx + Math.cos(ang - i * 0.03) * R, cy + Math.sin(ang - i * 0.03) * R); rd.stroke(); }
        Object.keys(hist).forEach(function (k) { var hs = hist[k]; if (hs.length >= 3) { rd.save(); rd.setLineDash([4, 5]); rd.strokeStyle = 'rgba(255,214,0,0.55)'; rd.lineWidth = 1.2; rd.beginPath(); hs.forEach(function (b, j) { var x = b.x * w, y = b.y * h; if (j === 0) rd.moveTo(x, y); else rd.lineTo(x, y); }); rd.stroke(); rd.restore(); var l = hs[hs.length - 1]; rd.fillStyle = 'rgba(255,214,0,0.8)'; rd.font = '9px "Share Tech Mono", monospace'; rd.fillText('TRACKING ' + k, l.x * w + 10, l.y * h - 10); } });
        blips.forEach(function (b) {
          var age = (now - b.born) / 1000, a = clamp(1 - age / 14, 0, 1); if (a <= 0) return;
          var col = !b.auth ? '255,70,70' : (b.src === 'LOCAL' ? '210,220,255' : TC[b.tier]), x = b.x * w, y = b.y * h;
          rd.fillStyle = 'rgba(' + col + ',' + (a * 0.95) + ')'; rd.beginPath(); rd.arc(x, y, 3 + b.tier, 0, TAU); rd.fill();
          var rr = (age % 2.4) / 2.4; rd.strokeStyle = 'rgba(' + col + ',' + (a * (1 - rr)) + ')'; rd.lineWidth = 1.5; rd.beginPath(); rd.arc(x, y, 6 + rr * (16 + b.tier * 12), 0, TAU); rd.stroke();
        });
        sources.forEach(function (s) { rd.fillStyle = 'rgba(160,160,255,0.35)'; rd.fillRect(s.x * w - 2, s.y * h - 2, 4, 4); });
      }

      /* ═══ LOOP / SCROLL / HUD ═══ */
      function onScroll() {
        var r = $('addendum').getBoundingClientRect();
        th = clamp((window.innerHeight * 0.75 - r.top) / (window.innerHeight * 0.75), 0, 1);
        root.style.setProperty('--th', th.toFixed(3));
        root.style.setProperty('--cr', clamp(th * 0.8 + Math.min(0.55, summonsTotal * 0.06), 0, 1).toFixed(3));
      }
      var last = performance.now();
      function frame(now) {
        requestAnimationFrame(frame);
        var dt = Math.min(0.05, (now - last) / 1000); last = now;
        bg.clearRect(0, 0, W, H);
        if (!light) {
          var col = mixc(th), i;
          for (i = 0; i < cards.length; i++) { var c = cards[i]; c.y += c.vy * dt; c.a += c.va * dt; if (c.y < -140) { cards[i] = mkCard(false); continue; } drawCard(c, col); }
          bg.fillStyle = 'rgba(' + col + ',0.5)';
          for (i = 0; i < dust.length; i++) { var d = dust[i]; d.y += d.vy * dt; if (d.y < -4) { d.y = H + 4; d.x = rand(0, W); } bg.globalAlpha = d.a; bg.fillRect(d.x + ptr.x * d.s * 6, d.y, d.s, d.s); }
          bg.globalAlpha = 1;
        }
        drawWaves(dt);
        if (shakeT > 0) { shakeT = Math.max(0, shakeT - dt); var m = shakeT * 9; container.style.transform = 'translate(' + (rand(-m, m)).toFixed(1) + 'px,' + (rand(-m, m)).toFixed(1) + 'px)'; } else if (container.style.transform) container.style.transform = '';
        ambient(now); drawRadar(now);
      }
      window.addEventListener('pointermove', function (e) { ptr.x = e.clientX / W * 2 - 1; ptr.y = e.clientY / H * 2 - 1; }, { passive: true });
      window.addEventListener('scroll', onScroll, { passive: true });
      var fb = $('fxBtn'); function fx() { fb.innerHTML = '&#9680; Effects: ' + (light ? 'light' : 'full'); }
      fb.addEventListener('click', function () { light = !light; fx(); }); fx();

      function resizeAll() {
        W = window.innerWidth; H = window.innerHeight;
        [bgCv, wvCv].forEach(function (c) { c.width = Math.floor(W * dpr); c.height = Math.floor(H * dpr); c.style.width = W + 'px'; c.style.height = H + 'px'; });
        bg.setTransform(dpr, 0, 0, dpr, 0, 0); wv.setTransform(dpr, 0, 0, dpr, 0, 0);
        cards = []; var i; for (i = 0; i < 28; i++) cards.push(mkCard(true));
        dust = []; for (i = 0; i < 70; i++) dust.push({ x: rand(0, W), y: rand(0, H), vy: -rand(5, 18), s: rand(1, 2.6), a: rand(0.2, 0.7) });
        buildCracks(); sizeRadar(); onScroll();
      }
      var rt = null;
      resizeAll(); S.serial = serial(); setTier(1); renderCracks(); say('Card drawn. The servant sleeps.'); ui();
      requestAnimationFrame(frame);
      window.addEventListener('resize', function () { clearTimeout(rt); rt = setTimeout(resizeAll, 250); });

      var els = document.querySelectorAll('.reveal');
      if ('IntersectionObserver' in window) { var io = new IntersectionObserver(function (en) { en.forEach(function (x) { if (x.isIntersecting) { x.target.classList.add('in'); io.unobserve(x.target); } }); }, { threshold: 0.08 }); els.forEach(function (e) { io.observe(e); }); } else els.forEach(function (e) { e.classList.add('in'); });
    })();
  </script>

</body>
</html>
