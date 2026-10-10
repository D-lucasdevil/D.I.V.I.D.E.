
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#060606">
  <title>D.I.V.I.D.E. — Black Streets</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;500;600;700&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --bg: #060606; --y: #ffd600; --o: #e65100; --r: #cc0000; --ink: #c8c8c8; --dim: #6a6a6a;
      --panel: rgba(12,12,12,0.88); --depth: 0;
    }

    html { scroll-behavior: smooth; }

    body { background: var(--bg); color: var(--ink); font-family: 'Share Tech Mono', monospace; min-height: 100vh; overflow-x: hidden; position: relative; }
    :focus-visible { outline: 2px solid var(--y); outline-offset: 2px; }

    #bg { position: fixed; inset: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none; }
    .ov-vig { position: fixed; inset: 0; z-index: 2; pointer-events: none; background: radial-gradient(ellipse at 50% 46%, rgba(0,0,0,0.25) 25%, rgba(0,0,0,0.88) 100%); }
    .ov-tint { position: fixed; inset: 0; z-index: 3; pointer-events: none; mix-blend-mode: color; background: rgb(255,60,20); opacity: calc(var(--depth) * 0.22); }
    body::after { content: ''; position: fixed; inset: 0; z-index: 90; pointer-events: none; background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(255,214,0,0.012) 3px, rgba(255,214,0,0.012) 4px); }

    .warning-bar { background: repeating-linear-gradient(135deg, #8b0000 0 18px, #7a0000 18px 36px); color: #fff; text-align: center; padding: 7px 10px; font-size: 11px; letter-spacing: 3px; text-transform: uppercase; border-bottom: 1px solid #ff0000; position: relative; z-index: 100; text-shadow: 0 1px 2px rgba(0,0,0,0.6); }
    .ticker { position: relative; z-index: 100; overflow: hidden; background: #0c0a00; border-bottom: 1px solid #3a3000; height: 28px; display: flex; align-items: center; }
    .ticker-label { flex-shrink: 0; height: 100%; display: flex; align-items: center; gap: 6px; padding: 0 14px; background: #4a3c00; color: var(--y); font-size: 10px; letter-spacing: 3px; text-transform: uppercase; z-index: 2; }
    .ticker-label::before { content: ''; width: 6px; height: 6px; border-radius: 50%; background: var(--y); animation: blink 1.2s steps(2) infinite; }
    @keyframes blink { 50% { opacity: 0.15; } }
    .ticker-vp { overflow: hidden; flex: 1; }
    .ticker-track { display: inline-flex; white-space: nowrap; animation: tick 60s linear infinite; }
    .ticker-item { font-size: 10px; letter-spacing: 2px; color: #9a8a40; padding: 0 22px; text-transform: uppercase; }
    .ticker-item::after { content: '◆'; margin-left: 44px; color: #3a3000; }
    @keyframes tick { from { transform: translateX(0); } to { transform: translateX(-50%); } }

    .container { max-width: 980px; margin: 0 auto; padding: 36px 20px 30px; position: relative; z-index: 10; }
    .back-link { display: inline-flex; align-items: center; gap: 8px; color: #6a6a6a; text-decoration: none; font-size: 11px; letter-spacing: 2px; margin-bottom: 20px; transition: color 0.2s, gap 0.2s; }
    .back-link:hover { color: #cc0000; gap: 14px; }
    .reveal { opacity: 0; transform: translateY(18px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .reveal.in { opacity: 1; transform: none; }

    /* ═══ HEADER ═══ */
    .file-header { border: 1px solid #3a2a00; padding: 0; margin-bottom: 26px; position: relative; overflow: hidden; background: linear-gradient(180deg, rgba(15,10,0,0.92) 0%, rgba(8,8,8,0.94) 100%); box-shadow: inset 0 0 90px rgba(255,214,0,0.06), 0 0 50px rgba(255,214,0,0.08); }
    .file-header::before { content: '// CLASSIFIED FILE //'; position: absolute; top: -10px; left: 20px; background: var(--bg); padding: 0 10px; color: #8b0000; font-size: 11px; letter-spacing: 3px; z-index: 2; }
    .tape { height: 10px; background: repeating-linear-gradient(45deg, var(--y) 0 14px, #111 14px 28px); opacity: 0.85; }
    .hdr-in { display: grid; grid-template-columns: 1fr 270px; gap: 26px; padding: 30px 30px 28px; align-items: center; }
    @media (max-width: 820px) { .hdr-in { grid-template-columns: 1fr; padding: 24px 18px; } .mapbox { max-width: 300px; } }
    .file-title { font-family: 'Rajdhani', sans-serif; font-size: 74px; font-weight: 700; color: var(--y); letter-spacing: 8px; line-height: 1; margin-bottom: 8px; cursor: default; }
    .file-title span { display: inline-block; text-shadow: 0 0 6px rgba(255,214,0,0.9), 0 0 22px rgba(255,214,0,0.55), 0 0 60px rgba(255,150,0,0.35); }
    .file-title span.off { animation: neonoff 5.5s steps(1) infinite; }
    @keyframes neonoff { 0%,90%,100% { opacity: 1; } 91% { opacity: 0.15; } 93% { opacity: 1; } 95% { opacity: 0.3; } 96% { opacity: 1; } }
    @media (max-width: 700px) { .file-title { font-size: 40px; letter-spacing: 4px; } }
    .file-designation { font-size: 12px; color: #7a7a7a; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 22px; }
    .meta-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 6px; }
    @media (max-width: 600px) { .meta-grid { grid-template-columns: 1fr; } }
    .meta-item { display: flex; gap: 10px; padding: 9px 13px; background: rgba(13,13,13,0.9); border: 1px solid #1a1a1a; font-size: 11px; transition: border-color 0.2s, transform 0.2s; }
    .meta-item:hover { border-color: #5a4a00; transform: translateX(3px); }
    .meta-label { color: #6a6a6a; letter-spacing: 1px; white-space: nowrap; }
    .meta-value { color: #aaa; letter-spacing: 1px; }
    .meta-value.yellow { color: var(--y); } .meta-value.red { color: #ff3a3a; } .meta-value.green { color: #4caf50; }

    .mapbox { position: relative; border: 1px solid #2a2200; background: rgba(5,5,2,0.9); padding: 10px; }
    .mapbox svg { width: 100%; height: auto; display: block; overflow: visible; }
    .mapbox .cz { fill: rgba(255,214,0,0.06); stroke: rgba(255,214,0,0.7); stroke-width: 1.4; stroke-linejoin: round; filter: drop-shadow(0 0 6px rgba(255,214,0,0.5)); }
    .mapbox .grid { stroke: rgba(255,214,0,0.1); stroke-width: 1; }
    .mapcap { display: flex; justify-content: space-between; font-size: 9px; letter-spacing: 3px; color: #7a6a20; margin-top: 8px; text-transform: uppercase; }
    .mapcap b { color: #ff4a4a; font-weight: 400; background: #000; padding: 0 5px; }
    #blip { transition: cx 0.5s ease, cy 0.5s ease; }
    .bring { fill: none; stroke: #ff3a3a; stroke-width: 1.4; transform-box: fill-box; transform-origin: center; animation: bring 2.4s ease-out infinite; }
    .bring.b2 { animation-delay: 1.2s; }
    @keyframes bring { 0% { transform: scale(0.4); opacity: 1; } 100% { transform: scale(3); opacity: 0; } }

    /* ═══ SECTIONS ═══ */
    .section-label { font-size: 10px; letter-spacing: 4px; color: #8b0000; text-transform: uppercase; margin-bottom: 12px; margin-top: 44px; padding-bottom: 7px; border-bottom: 1px solid #1a0000; position: relative; }
    .section-label::after { content: ''; position: absolute; left: 0; bottom: -1px; width: 90px; height: 2px; background: linear-gradient(90deg, var(--y), transparent); }

    .content-block { background: var(--panel); border: 1px solid #1a1a1a; border-left: 3px solid #3a0000; padding: 18px 20px; margin-bottom: 8px; font-size: 12px; line-height: 1.95; color: #8a8a8a; backdrop-filter: blur(2px); transition: border-left-color 0.25s, box-shadow 0.25s; }
    .content-block:hover { border-left-color: var(--y); box-shadow: 0 0 26px rgba(255,214,0,0.08); }
    .content-block p { margin-bottom: 8px; } .content-block p:last-child { margin-bottom: 0; }
    .content-block strong.k { color: #cfcfcf; }

    .rank { display: grid; gap: 8px; margin: 8px 0; }
    .rk { display: flex; align-items: center; gap: 16px; padding: 14px 18px; background: var(--panel); border: 1px solid #1a1a1a; position: relative; overflow: hidden; }
    .rk .n { font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 38px; line-height: 1; width: 52px; color: #555; }
    .rk .t { font-size: 12px; letter-spacing: 2px; text-transform: uppercase; color: #9a9a9a; flex: 1; }
    .rk .shield { width: 34px; height: 40px; flex-shrink: 0; }
    .rk.one { border-left: 4px solid #4fc3f7; } .rk.one .n { color: #4fc3f7; }
    .rk.two { border-left: 4px solid var(--y); box-shadow: 0 0 30px rgba(255,214,0,0.12); } .rk.two .n { color: var(--y); text-shadow: 0 0 16px rgba(255,214,0,0.6); } .rk.two .t { color: #ffe680; }
    .rk .bar { position: absolute; left: 0; bottom: 0; height: 3px; width: 0; background: linear-gradient(90deg, currentColor, transparent); transition: width 1.4s ease 0.4s; }
    .rk.one { color: #4fc3f7; } .rk.two { color: var(--y); }
    .rank.in .rk .bar { width: 100%; }
    .rank.in .rk.one .bar { width: 100%; } .rank.in .rk.two .bar { width: 92%; }

    /* trade signs */
    .trade-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 8px; }
    @media (max-width: 600px) { .trade-grid { grid-template-columns: 1fr; } }
    .trade-item { --nc: 255,214,0; position: relative; display: flex; align-items: center; gap: 14px; padding: 16px 18px; background: rgba(8,8,8,0.9); border: 2px solid rgba(var(--nc),0.65); font-size: 13px; letter-spacing: 1.5px; color: rgb(var(--nc)); text-transform: uppercase; box-shadow: 0 0 14px rgba(var(--nc),0.25), inset 0 0 18px rgba(var(--nc),0.1); transition: box-shadow 0.25s, transform 0.25s; text-shadow: 0 0 8px rgba(var(--nc),0.8); }
    .trade-item:hover { transform: translateY(-3px); box-shadow: 0 0 30px rgba(var(--nc),0.55), inset 0 0 28px rgba(var(--nc),0.22); animation: flick 0.4s steps(2) 1; }
    @keyframes flick { 0% { opacity: 1; } 25% { opacity: 0.4; } 50% { opacity: 1; } 75% { opacity: 0.6; } 100% { opacity: 1; } }
    .trade-item .dot { width: 10px; height: 10px; background: rgb(var(--nc)); border-radius: 50%; flex-shrink: 0; box-shadow: 0 0 12px rgb(var(--nc)); animation: pulse 2.4s ease-in-out infinite; }
    @keyframes pulse { 50% { opacity: 0.4; transform: scale(0.8); } }
    .trade-item:nth-child(2) { --nc: 255,90,30; } .trade-item:nth-child(3) { --nc: 255,60,160; } .trade-item:nth-child(4) { --nc: 255,60,60; }
    .trade-item:nth-child(5) { --nc: 0,229,255; } .trade-item:nth-child(6) { --nc: 170,255,60; }
    .trade-item::before { content: ''; position: absolute; left: 18%; right: 18%; top: -14px; height: 12px; border-left: 1px solid #555; border-right: 1px solid #555; }

    /* table */
    .market-table { width: 100%; border-collapse: collapse; margin-bottom: 8px; position: relative; z-index: 2; }
    .market-table th { background: #111; color: #7a7a7a; font-size: 10px; letter-spacing: 2px; text-transform: uppercase; padding: 9px 14px; text-align: left; border: 1px solid #1a1a1a; }
    .market-table td { padding: 11px 14px; border: 1px solid #1a1a1a; font-size: 12px; color: #8a8a8a; background: rgba(13,13,13,0.9); transition: background 0.2s, color 0.2s; }
    .market-table tr:hover td, .market-table tr.hl td { background: #17150a; color: #ddd; }
    .tier-i { color: #4fc3f7; } .tier-ii { color: #4caf50; } .tier-iii { color: var(--y); }
    .tbl-wrap { overflow-x: auto; }

    .chart { padding: 18px 16px 10px; margin: 8px 0; background: var(--panel); border: 1px solid #2a2200; }
    .chart svg { width: 100%; height: auto; display: block; overflow: visible; }
    .chart .ax { stroke: #333; stroke-width: 1; } .chart .tk { stroke: #222; stroke-dasharray: 3 4; }
    .chart text { font-family: 'Share Tech Mono', monospace; fill: #6a6a6a; font-size: 10px; letter-spacing: 1px; }
    .chart .rb { transform-box: fill-box; transform-origin: left center; transform: scaleX(0); transition: transform 1.3s cubic-bezier(.2,.8,.2,1); cursor: pointer; }
    .chart.in .rb { transform: scaleX(1); } .chart.in .rb:nth-of-type(2) { transition-delay: .2s; } .chart.in .rb.c3 { transition-delay: .4s; }
    .chart .rb:hover { filter: brightness(1.4) drop-shadow(0 0 10px currentColor); }
    .chart .mkr { opacity: 0; transition: opacity 0.6s ease 1.4s; } .chart.in .mkr { opacity: 1; }
    .chart .lbl { fill: #fff; font-size: 11px; font-weight: 700; }

    .vs { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin: 8px 0; }
    @media (max-width: 600px) { .vs { grid-template-columns: 1fr; } }
    .vs div { padding: 12px 16px; border: 1px solid #1a1a1a; background: var(--panel); font-size: 11px; letter-spacing: 2px; text-transform: uppercase; display: flex; align-items: center; gap: 12px; }
    .vs .up { border-left: 3px solid #4caf50; color: #7ad07e; } .vs .dn { border-left: 3px solid #e65100; color: #ff8a4a; }
    .vs b { font-family: 'Rajdhani', sans-serif; font-size: 24px; }

    /* funnel */
    .funnel { display: grid; grid-template-columns: 300px 1fr; gap: 20px; align-items: center; padding: 18px; background: var(--panel); border: 1px solid #1a1a1a; margin: 8px 0; }
    @media (max-width: 700px) { .funnel { grid-template-columns: 1fr; } }
    .funnel svg { width: 100%; height: auto; display: block; overflow: visible; }
    .fp { fill: var(--y); animation: fall 3.6s linear infinite; filter: drop-shadow(0 0 4px var(--y)); }
    @keyframes fall { 0% { transform: translate(var(--x0), 0); opacity: 0; } 12% { opacity: 1; } 75% { opacity: 1; } 100% { transform: translate(0, 150px); opacity: 0; } }
    .fsteps { display: grid; gap: 8px; }
    .fstep { display: flex; gap: 14px; align-items: center; padding: 12px 14px; border: 1px solid #1a1a1a; border-left: 3px solid var(--y); background: rgba(8,8,8,0.8); font-size: 12px; letter-spacing: 1px; color: #aaa; }
    .fstep i { font-style: normal; font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 24px; color: var(--y); width: 26px; }

    .protocol-item { display: flex; align-items: flex-start; gap: 12px; padding: 12px 16px; background: var(--panel); border: 1px solid #1a1a1a; border-left: 3px solid #3a0000; font-size: 12px; color: #8a8a8a; margin-bottom: 5px; line-height: 1.7; transition: transform 0.2s, border-left-color 0.2s, color 0.2s; }
    .protocol-item:hover { transform: translateX(5px); border-left-color: var(--r); color: #ddd; }
    .protocol-item .arrow { color: #8b0000; flex-shrink: 0; margin-top: 2px; }

    /* law */
    .law { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 8px; }
    @media (max-width: 600px) { .law { grid-template-columns: 1fr; } }
    .forbidden-item { display: flex; align-items: center; gap: 14px; padding: 14px 18px; background: rgba(13,0,0,0.85); border: 1px solid #2a0000; border-left: 4px solid #8b0000; font-size: 14px; letter-spacing: 3px; text-transform: uppercase; color: #ff6a6a; transition: transform 0.2s, box-shadow 0.2s; text-shadow: 0 0 10px rgba(255,40,40,0.5); }
    .forbidden-item:hover { transform: translateX(5px); box-shadow: 0 0 24px rgba(255,0,0,0.25); }
    .forbidden-item .x { color: #ff2a2a; font-size: 22px; }
    .punishment-block { position: relative; background: rgba(13,0,0,0.9); border: 1px solid #3a0000; border-left: 3px solid #cc0000; padding: 26px 22px 18px; margin-bottom: 8px; font-size: 12px; color: #cc4444; line-height: 1.9; overflow: hidden; }
    .punishment-block::before, .punishment-block::after { content: ''; position: absolute; left: 0; right: 0; height: 8px; background: repeating-linear-gradient(45deg, #cc0000 0 14px, #111 14px 28px); opacity: 0.7; }
    .punishment-block::before { top: 0; } .punishment-block::after { bottom: 0; }
    .punishment-block { padding-bottom: 26px; }
    .punishment-block strong { color: #ff4444; }

    /* floor monitor */
    .cctv { position: relative; border: 1px solid #2a2200; background: #04040a; margin: 10px 0 8px; overflow: hidden; box-shadow: 0 0 30px rgba(255,214,0,0.08); }
    #floor { width: 100%; height: 380px; display: block; }
    @media (max-width: 600px) { #floor { height: 300px; } }
    .cbar { display: flex; flex-wrap: wrap; gap: 8px; padding: 12px; background: #0a0a06; border-top: 1px solid #2a2200; }
    .btn { background: rgba(10,10,6,0.9); color: var(--y); border: 1px solid #5a4a00; font-family: 'Share Tech Mono', monospace; font-size: 11px; letter-spacing: 2px; padding: 10px 16px; cursor: pointer; text-transform: uppercase; transition: all 0.22s; }
    .btn:hover { background: var(--y); color: #060606; box-shadow: 0 0 22px rgba(255,214,0,0.5); transform: translateY(-1px); }
    .btn.dng { color: #ff6a6a; border-color: #6a0000; } .btn.dng:hover { background: #cc0000; color: #fff; box-shadow: 0 0 22px rgba(255,0,0,0.5); }
    .btn.vio { color: #d58aff; border-color: #5a1a7a; } .btn.vio:hover { background: #9c27b0; color: #fff; box-shadow: 0 0 22px rgba(156,39,176,0.6); }
    .flog { padding: 12px 16px; font-size: 12px; line-height: 1.9; min-height: 118px; background: #07070a; border-top: 1px solid #1a1a1a; color: #8a8a8a; }
    .flog div { animation: logIn 0.4s ease both; } .flog .r { color: #ff6a6a; } .flog .y { color: var(--y); } .flog .v { color: #d58aff; }
    @keyframes logIn { from { opacity: 0; transform: translateX(-6px); } to { opacity: 1; transform: none; } }

    .protector-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 8px; }
    @media (max-width: 600px) { .protector-grid { grid-template-columns: 1fr; } }
    .protector-card { position: relative; padding: 20px; background: var(--panel); border: 1px solid #1a1a1a; font-size: 12px; overflow: hidden; display: grid; grid-template-columns: 86px 1fr; gap: 16px; align-items: center; transition: transform 0.25s, box-shadow 0.25s; }
    .protector-card:hover { transform: translateY(-4px); }
    .protector-card.standard { border-top: 3px solid var(--y); } .protector-card.standard:hover { box-shadow: 0 10px 30px rgba(0,0,0,0.6), 0 0 28px rgba(255,214,0,0.2); }
    .protector-card.elite { border-top: 3px solid var(--o); } .protector-card.elite:hover { box-shadow: 0 10px 30px rgba(0,0,0,0.6), 0 0 28px rgba(230,81,0,0.3); }
    .protector-card svg { width: 86px; height: 120px; overflow: visible; }
    .pe { animation: peye 3s ease-in-out infinite; } @keyframes peye { 0%,90%,100% { opacity: 1; } 94% { opacity: 0.2; } }
    .protector-title { font-family: 'Rajdhani', sans-serif; font-size: 18px; font-weight: 700; letter-spacing: 3px; margin-bottom: 6px; text-transform: uppercase; }
    .protector-card.standard .protector-title { color: var(--y); } .protector-card.elite .protector-title { color: #ff7a2a; }
    .protector-card p { color: #7a7a7a; line-height: 1.7; }
    .eq { display: inline-block; margin-top: 8px; padding: 2px 10px; font-size: 10px; letter-spacing: 3px; border: 1px solid; text-transform: uppercase; }
    .standard .eq { color: var(--y); border-color: #4a3c00; } .elite .eq { color: #ff7a2a; border-color: #5a2400; }

    /* residency */
    .res { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin: 8px 0; }
    @media (max-width: 700px) { .res { grid-template-columns: 1fr; } }
    .door { position: relative; padding: 18px 16px 16px; background: var(--panel); border: 1px solid #1a1a1a; text-align: center; overflow: hidden; transition: transform 0.25s, border-color 0.25s; }
    .door:hover { transform: translateY(-3px); border-color: #5a4a00; }
    .door .plate { display: inline-block; border: 2px solid var(--y); color: var(--y); padding: 2px 12px; font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 18px; letter-spacing: 4px; margin-bottom: 10px; }
    .door .name { font-size: 11px; letter-spacing: 2px; text-transform: uppercase; color: #aaa; }
    .door .cam { position: absolute; right: 10px; top: 10px; width: 8px; height: 8px; border-radius: 50%; background: #ff2a2a; animation: blink 1.4s steps(2) infinite; box-shadow: 0 0 8px #ff2a2a; }
    .door .wins { display: flex; justify-content: center; gap: 5px; margin-bottom: 12px; }
    .door .wins i { width: 14px; height: 18px; background: #1a1400; border: 1px solid #3a3000; } .door .wins i.l { background: #ffd600; box-shadow: 0 0 10px rgba(255,214,0,0.7); animation: win 6s steps(1) infinite; }
    @keyframes win { 0%,70% { opacity: 1; } 75% { opacity: 0.3; } 80% { opacity: 1; } }

    /* receipt */
    .receipt { position: relative; max-width: 560px; margin: 14px auto 8px; padding: 26px 28px 22px; color: #1a1500; background: #f0e8c0; font-family: 'Share Tech Mono', monospace; box-shadow: 0 14px 40px rgba(0,0,0,0.7), 0 0 40px rgba(255,214,0,0.1); transform: rotate(-0.8deg); -webkit-mask: radial-gradient(circle 8px at 0 50%, transparent 98%, #000) left / 51% 20px repeat-y, radial-gradient(circle 8px at 100% 50%, transparent 98%, #000) right / 51% 20px repeat-y; mask: radial-gradient(circle 8px at 0 50%, transparent 98%, #000) left / 51% 20px repeat-y, radial-gradient(circle 8px at 100% 50%, transparent 98%, #000) right / 51% 20px repeat-y; }
    .receipt .rh { font-size: 10px; letter-spacing: 4px; text-align: center; border-bottom: 2px dashed #8a7a30; padding-bottom: 8px; margin-bottom: 14px; }
    .receipt .amount { font-family: 'Rajdhani', sans-serif; font-size: 40px; font-weight: 700; color: #1a1500; letter-spacing: 2px; margin-bottom: 4px; }
    .receipt .item { font-size: 14px; color: #3a3000; letter-spacing: 1px; margin-bottom: 10px; } .receipt .item a { color: #7a1a00; text-decoration: none; border-bottom: 1px dashed #7a1a00; }
    .receipt .detail { font-size: 11px; color: #5a4a10; letter-spacing: 1px; line-height: 1.7; }
    .receipt .bc { height: 36px; margin-top: 16px; background: repeating-linear-gradient(90deg, #1a1500 0 2px, transparent 2px 5px, #1a1500 5px 6px, transparent 6px 10px, #1a1500 10px 13px, transparent 13px 15px); }
    .receipt .paid { position: absolute; right: 24px; top: 62px; border: 4px solid #b01010; color: #b01010; font-family: 'Rajdhani', sans-serif; font-weight: 700; font-size: 34px; letter-spacing: 6px; padding: 0 12px; transform: rotate(14deg) scale(2); opacity: 0; transition: all 0.5s cubic-bezier(.2,.9,.3,1.3) 0.8s; }
    .receipt.in .paid { opacity: 0.85; transform: rotate(14deg) scale(1); }

    .internal-quote { background: rgba(8,8,8,0.92); border: 1px solid #1a1a1a; border-left: 4px solid var(--y); padding: 24px 28px; margin: 22px 0; position: relative; }
    .internal-quote::before { content: '"'; position: absolute; top: -10px; left: 16px; background: var(--bg); padding: 0 6px; color: var(--y); font-size: 30px; font-family: serif; line-height: 1; }
    .internal-quote p { font-size: 15px; color: #bbb; line-height: 1.9; font-style: italic; }
    .internal-quote .attribution { margin-top: 12px; font-size: 10px; color: #6a6a6a; letter-spacing: 2px; text-transform: uppercase; font-style: normal; }

    .risk { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin: 8px 0; }
    @media (max-width: 700px) { .risk { grid-template-columns: 1fr; } }
    .risk div { padding: 14px 16px; border: 1px solid #1a1a1a; border-top: 3px solid #5a4a00; background: var(--panel); font-size: 11px; letter-spacing: 2px; text-transform: uppercase; color: #bba85a; text-align: center; }

    .notice-box { background: rgba(13,8,0,0.9); border: 1px solid #2a1a00; border-left: 3px solid #e65100; padding: 16px 20px; font-size: 11px; color: #998877; line-height: 1.8; margin-top: 20px; position: relative; }
    .notice-box::after { content: ''; position: absolute; left: 0; right: 0; bottom: 0; height: 4px; background: repeating-linear-gradient(45deg, #e65100 0 12px, #111 12px 24px); opacity: 0.5; }
    .notice-box strong { color: #e65100; }

    .end-line { display: flex; align-items: center; gap: 14px; margin: 16px 0 20px; color: #3a3000; font-size: 10px; letter-spacing: 4px; text-transform: uppercase; }
    .end-line::before, .end-line::after { content: ''; flex: 1; height: 1px; background: linear-gradient(90deg, transparent, #3a3000, transparent); }
    .footer { border-top: 1px solid #1a0000; padding-top: 20px; margin-top: 30px; font-size: 10px; color: #333; letter-spacing: 1px; line-height: 1.8; text-align: center; }

    .hud-l { position: fixed; left: 14px; bottom: 14px; z-index: 700; }
    .hud-l button { background: rgba(10,10,6,0.9); color: var(--y); border: 1px solid #5a4a00; padding: 7px 12px; font-family: inherit; font-size: 10px; letter-spacing: 2px; cursor: pointer; text-transform: uppercase; }
    .hud-l button:hover { color: #fff; border-color: var(--y); }
    .hud-r { position: fixed; right: 14px; bottom: 14px; z-index: 700; font-size: 10px; letter-spacing: 3px; color: #9a8a40; text-transform: uppercase; background: rgba(10,10,6,0.88); border: 1px solid #3a3000; padding: 7px 12px; }
    .hud-r b { color: var(--y); font-weight: 400; } .hud-r i { display: inline-block; width: 7px; height: 7px; border-radius: 50%; background: #ff2a2a; margin-right: 8px; animation: blink 1.2s steps(2) infinite; }
    @media (max-width: 700px) { .hud-r { display: none; } }

    @media (prefers-reduced-motion: reduce) { .ticker-track, .file-title span.off, .trade-item .dot, .bring, .fp, .pe, .door .cam, .door .wins i.l { animation: none !important; } .reveal { opacity: 1; transform: none; transition: none; } }
  </style>
</head>
<body>

  <canvas id="bg" aria-hidden="true"></canvas>
  <div class="ov-vig"></div>
  <div class="ov-tint"></div>
  <div class="hud-l"><button id="fxBtn" type="button">&#9680; Effects: full</button></div>
  <div class="hud-r"><i></i>DEPTH <b id="depthVal">0%</b></div>

  <div class="warning-bar">
    ⚠ RESTRICTED ACCESS — AUTHORIZED PERSONNEL ONLY — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>
  <div class="ticker" aria-hidden="true">
    <div class="ticker-label">Market feed</div>
    <div class="ticker-vp"><div class="ticker-track" id="tickerTrack"></div></div>
  </div>

  <div class="container">

    <a href="index.html" class="back-link">← RETURN TO DATABASE INDEX</a>

    <div class="file-header reveal">
      <div class="tape"></div>
      <div class="hdr-in">
        <div>
          <div class="file-title" id="fileTitle">BLACK STREETS</div>
          <div class="file-designation">Illicit Trade Zone / Anomalous Market Hub — Active File</div>
          <div class="meta-grid">
            <div class="meta-item"><span class="meta-label">THREAT LEVEL</span><span class="meta-value yellow">Class III — Localized</span></div>
            <div class="meta-item"><span class="meta-label">CLEARANCE</span><span class="meta-value red">DIVIDE Level 1+</span></div>
            <div class="meta-item"><span class="meta-label">STATUS</span><span class="meta-value green">Monitored / Indirectly Controlled</span></div>
            <div class="meta-item"><span class="meta-label">LOCATION</span><span class="meta-value red">[REDACTED] — Czech Republic</span></div>
          </div>
        </div>
        <div class="mapbox" aria-hidden="true">
          <svg viewBox="0 0 304 180">
            <g class="grid"><line x1="0" y1="45" x2="304" y2="45"/><line x1="0" y1="90" x2="304" y2="90"/><line x1="0" y1="135" x2="304" y2="135"/><line x1="76" y1="0" x2="76" y2="180"/><line x1="152" y1="0" x2="152" y2="180"/><line x1="228" y1="0" x2="228" y2="180"/></g>
            <polygon class="cz" points="4,58 22,48 44,41 72,22 100,4 126,14 143,17 183,41 217,54 243,54 278,71 298,105 261,119 226,152 215,173 165,156 130,145 78,170 65,146 39,109"/>
            <circle class="bring" id="br1" cx="150" cy="95" r="7"/><circle class="bring b2" id="br2" cx="150" cy="95" r="7"/>
            <circle id="blip" cx="150" cy="95" r="4" fill="#ff3a3a"/>
          </svg>
          <div class="mapcap"><span>CZECH REPUBLIC</span><b>[REDACTED]</b></div>
        </div>
      </div>
    </div>

    <div class="section-label reveal">// Overview //</div>
    <div class="content-block reveal">
      <p>Black Street is a highly secured, underground trade zone located within the Czech Republic at [REDACTED]. It functions as a global marketplace for illegal, restricted, and anomalous goods, operating beyond conventional law enforcement and partially tolerated by D.I.V.I.D.E.</p>
      <p>The location is considered the <strong class="k">second most protected area in the world</strong>, surpassed only by D.I.V.I.D.E. central command infrastructure.</p>
      <p>Black Street is widely known among criminal networks, private collectors, rogue researchers, and certain government contacts. Despite its illegal nature, it operates under strict internal order and enforcement.</p>
    </div>
    <div class="rank reveal" id="rank">
      <div class="rk one"><svg class="shield" viewBox="0 0 34 40"><path d="M17 2 L32 8 V20 C32 30 25 36 17 38 C9 36 2 30 2 20 V8 Z" fill="rgba(79,195,247,0.12)" stroke="#4fc3f7" stroke-width="2"/></svg><span class="n">1</span><span class="t">D.I.V.I.D.E. central command infrastructure</span><span class="bar"></span></div>
      <div class="rk two"><svg class="shield" viewBox="0 0 34 40"><path d="M17 2 L32 8 V20 C32 30 25 36 17 38 C9 36 2 30 2 20 V8 Z" fill="rgba(255,214,0,0.14)" stroke="#ffd600" stroke-width="2"/><path d="M11 20 L16 25 L24 14" fill="none" stroke="#ffd600" stroke-width="2.4"/></svg><span class="n">2</span><span class="t">Black Street</span><span class="bar"></span></div>
    </div>

    <div class="section-label reveal">// Trade & Economy //</div>
    <div class="trade-grid reveal">
      <div class="trade-item"><div class="dot"></div>Anomalies — Primary Commodity</div>
      <div class="trade-item"><div class="dot"></div>Military-Grade Weapons</div>
      <div class="trade-item"><div class="dot"></div>Controlled Substances</div>
      <div class="trade-item"><div class="dot"></div>Human Organs — On-Site Surgical Staff</div>
      <div class="trade-item"><div class="dot"></div>Classified Documents</div>
      <div class="trade-item"><div class="dot"></div>Restricted Technology</div>
    </div>

    <div class="section-label reveal">// Anomaly Market Values (Estimated) //</div>
    <div class="chart reveal" id="chart">
      <svg viewBox="0 0 760 240" aria-hidden="true" id="chartSvg"></svg>
    </div>
    <div class="tbl-wrap reveal">
    <table class="market-table" id="mtable">
      <thead>
        <tr>
          <th>Class</th>
          <th>Threat Level</th>
          <th>Estimated Value</th>
          <th>Notes</th>
        </tr>
      </thead>
      <tbody>
        <tr data-r="0">
          <td class="tier-i">Class I</td>
          <td>Low</td>
          <td class="tier-i">$20M – $50M</td>
          <td>Stable, low-risk items</td>
        </tr>
        <tr data-r="1">
          <td class="tier-ii">Class II</td>
          <td>Moderate</td>
          <td class="tier-ii">$100M – $500M</td>
          <td>Manageable with containment</td>
        </tr>
        <tr data-r="2">
          <td class="tier-iii">Class III</td>
          <td>High</td>
          <td class="tier-iii">Rare — up to $2B+</td>
          <td>Extreme demand, low availability</td>
        </tr>
      </tbody>
    </table>
    </div>

    <div class="content-block reveal">
      <p><strong class="k">Item-type anomalies</strong> are significantly more valuable than living entities due to their stability, ease of transport, and controllability.</p>
      <p><strong class="k">Living anomalies</strong> are rarely sold unless deceased, heavily contained, or deemed genuinely low-risk to the buyer.</p>
    </div>
    <div class="vs reveal"><div class="up"><b>▲</b>Item-type — higher value</div><div class="dn"><b>▼</b>Living — rarely sold</div></div>

    <div class="section-label reveal">// D.I.V.I.D.E. Involvement //</div>
    <div class="content-block reveal">
      <p>Despite its nature, D.I.V.I.D.E. does not shut down Black Street. The organization views it as a centralized anomaly funnel, a live tracking system for high-risk artifacts, and an active acquisition opportunity.</p>
    </div>
    <div class="funnel reveal">
      <svg viewBox="0 0 300 220" aria-hidden="true">
        <path d="M20 10 L280 10 L170 150 L170 200 L130 200 L130 150 Z" fill="rgba(255,214,0,0.05)" stroke="rgba(255,214,0,0.6)" stroke-width="1.6" stroke-linejoin="round"/>
        <g id="fparts"></g>
        <circle cx="150" cy="212" r="9" fill="none" stroke="#ff2a2a" stroke-width="2"/><circle cx="150" cy="212" r="3.5" fill="#ff2a2a"/>
      </svg>
      <div class="fsteps">
        <div class="fstep"><i>1</i>Centralized anomaly funnel</div>
        <div class="fstep"><i>2</i>Live tracking system for high-risk artifacts</div>
        <div class="fstep"><i>3</i>Active acquisition opportunity</div>
      </div>
    </div>
    <div class="protocol-item reveal"><span class="arrow">▶</span>Any discovered anomaly may be purchased, temporarily confiscated, or permanently seized — with fair market compensation offered.</div>
    <div class="protocol-item reveal"><span class="arrow">▶</span>If an individual resists and weaponizes an anomaly: immediate termination is authorized. The artifact is recovered without negotiation.</div>
    <div class="protocol-item reveal"><span class="arrow">▶</span>Nuclear weapon transactions are strictly monitored. Unauthorized buyers are executed without warning.</div>

    <div class="section-label reveal">// Internal Law — Strictly Forbidden //</div>
    <div class="law reveal">
      <div class="forbidden-item"><span class="x">✕</span>Murder</div>
      <div class="forbidden-item"><span class="x">✕</span>Assault</div>
      <div class="forbidden-item"><span class="x">✕</span>Sexual Violence</div>
      <div class="forbidden-item"><span class="x">✕</span>Theft</div>
    </div>
    <div class="punishment-block reveal">
      <strong>PUNISHMENT:</strong> Immediate execution followed by public skinning of the offender.<br>
      Punishments are carried out publicly to maintain order and deter disruption. No exceptions. No appeals.
    </div>

    <div class="section-label reveal">// Security & Protection //</div>
    <div class="protector-grid reveal">
      <div class="protector-card standard">
        <svg viewBox="0 0 86 120" aria-hidden="true"><path d="M43 8 C54 8 58 18 58 26 C58 32 56 36 54 38 L66 46 L70 110 L16 110 L20 46 L32 38 C30 36 28 32 28 26 C28 18 32 8 43 8Z" fill="#050403" stroke="rgba(255,214,0,0.5)" stroke-width="1.5"/><rect class="pe" x="34" y="22" width="18" height="4" fill="#ffd600"/></svg>
        <div><div class="protector-title">Standard Protectors</div><p>Enforcement entities comparable to Class III anomalies. Deployed throughout the trading floor. Zero conflict tolerance. Rapid neutralization of any threat to market stability.</p><span class="eq">≈ Class III</span></div>
      </div>
      <div class="protector-card elite">
        <svg viewBox="0 0 86 120" aria-hidden="true"><path d="M43 4 C56 4 60 16 60 24 C60 30 58 34 56 36 L72 44 L78 112 L8 112 L14 44 L30 36 C28 34 26 30 26 24 C26 16 30 4 43 4Z" fill="#050403" stroke="rgba(255,122,42,0.6)" stroke-width="1.5"/><path d="M14 44 L2 30 L18 38 M72 44 L84 30 L68 38" fill="none" stroke="rgba(255,122,42,0.6)" stroke-width="2"/><rect class="pe" x="32" y="20" width="9" height="4" fill="#ff7a2a"/><rect class="pe" x="45" y="20" width="9" height="4" fill="#ff7a2a"/></svg>
        <div><div class="protector-title">Elite Protectors</div><p>Comparable to low Class IV anomalies. Reserved for high-value zones and direct enforcement. Total control of all activity. Their presence alone deters most threats.</p><span class="eq">≈ Low Class IV</span></div>
      </div>
    </div>

    <div class="cctv reveal">
      <canvas id="floor"></canvas>
      <div class="cbar">
        <button class="btn dng" id="eFight" type="button">&#9889; Start a fight</button>
        <button class="btn vio" id="eWeapon" type="button">&#9763; Weaponize an anomaly</button>
        <button class="btn dng" id="eNuke" type="button">&#9762; Unauthorized nuclear buyer</button>
        <button class="btn" id="eReset" type="button">Clear</button>
      </div>
      <div class="flog" id="flog"></div>
    </div>

    <div class="section-label reveal">// Residency //</div>
    <div class="content-block reveal">
      <p>Permanent residence within Black Street is possible but extremely expensive, restricted to high-value individuals, and subject to constant monitoring.</p>
      <p>Known resident categories include: black market traders, rogue scientists, and wealthy anomaly collectors.</p>
    </div>
    <div class="res reveal">
      <div class="door"><span class="cam"></span><div class="wins"><i class="l"></i><i></i><i class="l"></i><i class="l"></i></div><div class="plate">A-01</div><div class="name">Black market traders</div></div>
      <div class="door"><span class="cam"></span><div class="wins"><i></i><i class="l"></i><i class="l"></i><i></i></div><div class="plate">B-07</div><div class="name">Rogue scientists</div></div>
      <div class="door"><span class="cam"></span><div class="wins"><i class="l"></i><i class="l"></i><i></i><i class="l"></i></div><div class="plate">C-13</div><div class="name">Wealthy anomaly collectors</div></div>
    </div>

    <div class="section-label reveal">// Notable Transaction //</div>
    <div class="receipt reveal" id="receipt">
      <div class="rh">BLACK STREET — TRANSACTION RECORD</div>
      <div class="amount">$220,000,000 USD</div>
      <div class="item"><a href="LD-016.html">LD-016 — "Andy's Revolver"</a></div>
      <div class="detail">Transaction included an additional agreement: D.I.V.I.D.E. protection contract for the buyer. Terms classified.</div>
      <div class="bc"></div>
      <div class="paid">PAID</div>
    </div>

    <div class="internal-quote reveal">
      <p>You don't shut down Black Street.<br>You watch it… and make sure the wrong people don't walk out with the wrong things.</p>
      <div class="attribution">— D.I.V.I.D.E. Oversight Command</div>
    </div>

    <div class="section-label reveal">// Risk Assessment //</div>
    <div class="content-block reveal">
      <p>While dangerous, Black Street is considered more stable than decentralized black markets, significantly easier to monitor than global anomaly smuggling networks, and a necessary evil within the current containment system.</p>
    </div>
    <div class="risk reveal"><div>More stable than decentralized black markets</div><div>Easier to monitor than smuggling networks</div><div>A necessary evil</div></div>

    <div class="notice-box reveal">
      <strong>Classification Notice:</strong> This file is accessible to Level 1 personnel due to the widespread awareness of Black Street within both civilian and underground networks. Operational details remain classified at higher clearance levels.
    </div>

    <div class="end-line">End of file</div>
    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2026-03-24</p>
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

      /* title letters (neon flicker) */
      (function () {
        var t = $('fileTitle'), s = t.textContent, h = '', i;
        for (i = 0; i < s.length; i++) { var ch = s[i] === ' ' ? '&nbsp;' : s[i]; h += '<span' + (Math.random() < 0.28 ? ' class="off" style="animation-delay:' + (Math.random() * 5).toFixed(1) + 's;animation-duration:' + (4 + Math.random() * 5).toFixed(1) + 's"' : '') + '>' + ch + '</span>'; }
        t.setAttribute('aria-label', s); t.innerHTML = h;
        var tk = ['Anomalies \u2014 primary commodity', 'Zero conflict tolerance', 'Nuclear transactions strictly monitored', 'No exceptions. No appeals.', 'D.I.V.I.D.E. is watching', 'Second most protected area in the world', 'Fair market compensation offered', 'Unauthorized buyers executed without warning'], o = '', r;
        for (r = 0; r < 2; r++) tk.forEach(function (x) { o += '<span class="ticker-item">' + x + '</span>'; });
        $('tickerTrack').innerHTML = o;
      })();

      /* redacted blip jitters around the map */
      (function () {
        var b = $('blip'), r1 = $('br1'), r2 = $('br2');
        function jump() { var x = rand(90, 215), y = rand(45, 140); [b, r1, r2].forEach(function (e) { e.setAttribute('cx', x.toFixed(0)); e.setAttribute('cy', y.toFixed(0)); }); }
        if (!reduce) setInterval(jump, 1800);
      })();

      /* ═══ BACKGROUND: walk down the street ═══ */
      var bgCv = $('bg'), g = bgCv.getContext('2d');
      var W = 0, H = 0, VX = 0, VY = 0, dpr = Math.min(window.devicePixelRatio || 1, 1.5);
      var F = 420, WALL = 560, FLR = 250, CEI = 260, ZREP = 3600;
      var objs = [], dust = [], vis = [], z0 = 0, zs = 0, drift = 0, prog = 0, ptr = { x: 0, y: 0 };
      var NEON = ['255,214,0', '255,60,160', '0,229,255', '255,90,30', '170,255,60'];
      var SIGNS = ['ANOMALIES', 'WEAPONS', 'SUBSTANCES', 'ORGANS', 'DOCUMENTS', 'TECHNOLOGY', 'ZERO CONFLICT', 'NO EXCEPTIONS', 'BLACK STREET', 'MONITORED', 'NO APPEALS', 'CLASSIFIED'];
      function sprite(c) { var cv = document.createElement('canvas'); cv.width = cv.height = 64; var x = cv.getContext('2d'), gr = x.createRadialGradient(32, 32, 0, 32, 32, 32); gr.addColorStop(0, 'rgba(' + c + ',1)'); gr.addColorStop(0.4, 'rgba(' + c + ',0.3)'); gr.addColorStop(1, 'rgba(' + c + ',0)'); x.fillStyle = gr; x.fillRect(0, 0, 64, 64); return cv; }
      var GS = NEON.map(sprite), SG = sprite('150,140,110'), SR = sprite('255,40,40');
      function pcol(p) { var a = [255, 214, 0], b = [255, 120, 20], c = [255, 50, 40], f = p < 0.5 ? p / 0.5 : (p - 0.5) / 0.5, s = p < 0.5 ? a : b, e = p < 0.5 ? b : c; return Math.round(s[0] + (e[0] - s[0]) * f) + ',' + Math.round(s[1] + (e[1] - s[1]) * f) + ',' + Math.round(s[2] + (e[2] - s[2]) * f); }

      function build() {
        objs = []; var i;
        for (i = 0; i < 18; i++) objs.push({ t: 'sign', z: (i / 18) * ZREP + rand(0, 100), x: (i % 2 ? 1 : -1) * rand(230, 440), y: -rand(60, 190), w: rand(130, 210), h: rand(34, 50), txt: SIGNS[i % SIGNS.length], c: i % NEON.length, ph: rand(0, TAU), fl: Math.random() < 0.4 });
        for (i = 0; i < 14; i++) objs.push({ t: 'stall', z: (i / 14) * ZREP + rand(0, 150), x: (i % 2 ? 1 : -1) * rand(400, 470), w: rand(150, 210), h: rand(130, 170), c: (Math.random() * NEON.length) | 0 });
        for (i = 0; i < 16; i++) objs.push({ t: 'lamp', z: (i / 16) * ZREP, x: (i % 2 ? 1 : -1) * rand(120, 300), ph: rand(0, TAU) });
        for (i = 0; i < 5; i++) objs.push({ t: 'cam', z: (i / 5) * ZREP + 300, x: (i % 2 ? 1 : -1) * rand(160, 320), ph: rand(0, TAU) });
        for (i = 0; i < 16; i++) objs.push({ t: 'ppl', z: rand(0, ZREP), x: rand(-190, 190), v: rand(-40, 70), h: rand(140, 165), ph: rand(0, TAU), tall: false });
        for (i = 0; i < 7; i++) objs.push({ t: 'ppl', z: (i / 7) * ZREP + rand(0, 200), x: (i % 2 ? 1 : -1) * rand(210, 330), v: 0, h: rand(205, 235), ph: rand(0, TAU), tall: true, elite: Math.random() < 0.4 });
        for (i = 0; i < 12; i++) objs.push({ t: 'steam', z: rand(0, ZREP), x: rand(-420, 420), ph: rand(0, TAU) });
        dust = []; for (i = 0; i < 60; i++) dust.push({ x: rand(0, W), y: rand(0, H), s: rand(1, 2.4), vy: -rand(4, 16), a: rand(0.2, 0.7) });
      }

      function drawTunnel(col) {
        var gap = 220, off = (((-z0) % gap) + gap) % gap, i, d, s, a;
        g.lineWidth = 1;
        for (i = 0; i < 17; i++) {
          d = off + i * gap + 30; if (d > ZREP) break; s = F / (d + F); a = 1 - d / ZREP; a = a * a * 0.3;
          g.strokeStyle = 'rgba(' + col + ',' + a + ')'; g.strokeRect(VX - WALL * s, VY - CEI * s, WALL * 2 * s, (CEI + FLR) * s);
          g.beginPath(); g.moveTo(VX - WALL * s, VY + FLR * s); g.lineTo(VX + WALL * s, VY + FLR * s); g.stroke();
        }
        [-WALL, -300, -100, 100, 300, WALL].forEach(function (x) { var s1 = F / (40 + F), s2 = F / (ZREP + F); g.strokeStyle = 'rgba(' + col + ',0.12)'; g.beginPath(); g.moveTo(VX + x * s1, VY + FLR * s1); g.lineTo(VX + x * s2, VY + FLR * s2); g.stroke(); });
        [-300, 0, 300].forEach(function (x) { var s1 = F / (40 + F), s2 = F / (ZREP + F); g.strokeStyle = 'rgba(' + col + ',0.07)'; g.beginPath(); g.moveTo(VX + x * s1, VY - CEI * s1); g.lineTo(VX + x * s2, VY - CEI * s2); g.stroke(); });
        [-90, 70].forEach(function (y) { var s1 = F / (40 + F), s2 = F / (ZREP + F); g.strokeStyle = 'rgba(' + col + ',0.08)'; [-WALL, WALL].forEach(function (x) { g.beginPath(); g.moveTo(VX + x * s1, VY + y * s1); g.lineTo(VX + x * s2, VY + y * s2); g.stroke(); }); });
      }

      function drawObj(o, d, t, col) {
        var s = F / (d + F), a = Math.pow(1 - d / ZREP, 1.1), sx = VX + (o.x || 0) * s, i;
        switch (o.t) {
          case 'sign': {
            var sy = VY + o.y * s, w = o.w * s, h = o.h * s; if (w < 10) return;
            var fl = o.fl && !light ? (Math.sin(t * 23 + o.ph) > 0.86 ? 0.25 : 1) : 1; a *= fl * (light ? 1 : 0.75 + 0.25 * Math.sin(t * 2 + o.ph));
            var c = NEON[o.c];
            g.strokeStyle = 'rgba(120,120,120,' + (a * 0.4) + ')'; g.lineWidth = 1; g.beginPath(); g.moveTo(sx - w * 0.35, sy - h / 2); g.lineTo(sx - w * 0.35, VY - CEI * s); g.moveTo(sx + w * 0.35, sy - h / 2); g.lineTo(sx + w * 0.35, VY - CEI * s); g.stroke();
            g.globalCompositeOperation = 'lighter'; g.globalAlpha = a * 0.5; g.drawImage(GS[o.c], sx - w, sy - h * 2.2, w * 2, h * 4.4); g.globalAlpha = 1; g.globalCompositeOperation = 'source-over';
            g.fillStyle = 'rgba(6,6,6,' + (0.8 * a + 0.1) + ')'; g.fillRect(sx - w / 2, sy - h / 2, w, h);
            g.strokeStyle = 'rgba(' + c + ',' + a + ')'; g.lineWidth = Math.max(1, 2.4 * s); g.strokeRect(sx - w / 2, sy - h / 2, w, h);
            var fs = Math.max(8, Math.min(h * 0.58, (w * 0.88) / (o.txt.length * 0.55)));
            g.fillStyle = 'rgba(' + c + ',' + a + ')'; g.font = '700 ' + fs + 'px Rajdhani, sans-serif'; g.textAlign = 'center'; g.textBaseline = 'middle'; g.fillText(o.txt, sx, sy + h * 0.04);
            break;
          }
          case 'stall': {
            var base = VY + FLR * s, w2 = o.w * s, h2 = o.h * s; if (w2 < 12) return; var c2 = NEON[o.c];
            g.fillStyle = 'rgba(10,8,5,0.92)'; g.fillRect(sx - w2 / 2, base - h2, w2, h2);
            var n = 6, k; for (k = 0; k < n; k++) { g.fillStyle = k % 2 ? 'rgba(' + c2 + ',' + (a * 0.55) + ')' : 'rgba(20,16,10,' + a + ')'; g.fillRect(sx - w2 / 2 + k * w2 / n, base - h2, w2 / n, h2 * 0.22); }
            g.globalCompositeOperation = 'lighter'; g.globalAlpha = a * 0.4; g.drawImage(GS[0], sx - w2, base - h2 * 1.05, w2 * 2, h2 * 1.5); g.globalAlpha = 1; g.globalCompositeOperation = 'source-over';
            g.fillStyle = 'rgba(255,214,0,' + (a * 0.18) + ')'; g.fillRect(sx - w2 * 0.4, base - h2 * 0.6, w2 * 0.8, h2 * 0.08);
            for (k = 0; k < 5; k++) { g.fillStyle = 'rgba(3,3,2,' + (0.9 * a) + ')'; g.fillRect(sx - w2 * 0.38 + k * w2 * 0.16, base - h2 * 0.5, w2 * 0.1, h2 * (0.14 + ((k * 7) % 3) * 0.05)); }
            break;
          }
          case 'lamp': {
            var ly = VY - CEI * s * 0.55, lr = 26 * s; g.strokeStyle = 'rgba(100,100,90,' + (a * 0.5) + ')'; g.beginPath(); g.moveTo(sx, VY - CEI * s); g.lineTo(sx, ly); g.stroke();
            g.globalCompositeOperation = 'lighter'; g.globalAlpha = a * (0.55 + (light ? 0 : 0.1 * Math.sin(t * 3 + o.ph))); g.drawImage(GS[0], sx - lr * 4, ly - lr * 4, lr * 8, lr * 8); g.globalAlpha = 1; g.globalCompositeOperation = 'source-over';
            g.fillStyle = 'rgba(255,230,140,' + a + ')'; g.beginPath(); g.arc(sx, ly, Math.max(1.5, 5 * s), 0, TAU); g.fill();
            break;
          }
          case 'cam': {
            var cy = VY - (CEI - 12) * s, sw = light ? 0 : Math.sin(t * 0.9 + o.ph) * 0.9, tx = sx + (sw * 260) * s, ty = VY + FLR * s;
            g.fillStyle = 'rgba(40,40,40,' + a + ')'; g.fillRect(sx - 9 * s, cy - 5 * s, 18 * s, 10 * s);
            var gr = g.createLinearGradient(sx, cy, tx, ty); gr.addColorStop(0, 'rgba(255,40,40,' + (0.18 * a) + ')'); gr.addColorStop(1, 'rgba(255,40,40,0)');
            g.fillStyle = gr; g.beginPath(); g.moveTo(sx, cy); g.lineTo(tx - 60 * s, ty); g.lineTo(tx + 60 * s, ty); g.closePath(); g.fill();
            g.globalCompositeOperation = 'lighter'; g.globalAlpha = a * ((light || Math.sin(t * 5 + o.ph) > 0) ? 0.9 : 0.2); var rr = 14 * s; g.drawImage(SR, sx - rr, cy - rr, rr * 2, rr * 2); g.globalAlpha = 1; g.globalCompositeOperation = 'source-over';
            break;
          }
          case 'ppl': {
            var fy = VY + FLR * s, h3 = o.h * s; if (h3 < 8) return; var swy = light ? 0 : Math.sin(t * 3 + o.ph) * h3 * 0.02, px = sx + swy;
            g.fillStyle = 'rgba(4,3,2,' + Math.min(1, 0.95 * a + 0.1) + ')';
            g.beginPath(); g.arc(px, fy - h3 * 0.9, h3 * 0.075, 0, TAU); g.fill();
            g.beginPath(); g.moveTo(px - h3 * 0.17, fy - h3 * 0.82); g.quadraticCurveTo(px - h3 * 0.2, fy - h3 * 0.45, sx - h3 * 0.12, fy); g.lineTo(sx + h3 * 0.12, fy); g.quadraticCurveTo(px + h3 * 0.2, fy - h3 * 0.45, px + h3 * 0.17, fy - h3 * 0.82); g.closePath(); g.fill();
            g.strokeStyle = 'rgba(' + col + ',' + (a * 0.28) + ')'; g.lineWidth = 1; g.stroke();
            if (o.tall) { var ec = o.elite ? '255,120,20' : '255,214,0', ew = Math.max(2, h3 * 0.05); g.fillStyle = 'rgba(' + ec + ',' + (a * 0.95) + ')'; g.fillRect(px - h3 * 0.06, fy - h3 * 0.9, ew, Math.max(1.5, ew * 0.4)); g.fillRect(px + h3 * 0.015, fy - h3 * 0.9, ew, Math.max(1.5, ew * 0.4)); g.globalCompositeOperation = 'lighter'; g.globalAlpha = a * 0.5; g.drawImage(GS[o.elite ? 3 : 0], px - h3 * 0.18, fy - h3 * 1.0, h3 * 0.36, h3 * 0.2); g.globalAlpha = 1; g.globalCompositeOperation = 'source-over'; }
            break;
          }
          case 'steam': {
            var r = (120 + 60 * Math.sin(t * 0.4 + o.ph)) * s, y = VY + (FLR - 40) * s; g.globalAlpha = a * 0.09; g.drawImage(SG, sx - r, y - r, r * 2, r * 2); g.globalAlpha = 1;
            break;
          }
        }
      }

      var last = performance.now(), depthEl = $('depthVal'), shownP = -1;
      function frame(now) {
        requestAnimationFrame(frame);
        var dt = Math.min(0.05, (now - last) / 1000); last = now; var t = now / 1000, i;
        var max = document.documentElement.scrollHeight - window.innerHeight, p = max > 0 ? clamp(window.scrollY / max, 0, 1) : 0;
        prog += (p - prog) * Math.min(1, dt * 3);
        if (Math.abs(prog - shownP) > 0.003) { shownP = prog; root.style.setProperty('--depth', prog.toFixed(3)); depthEl.textContent = Math.round(prog * 100) + '%'; }
        zs += (window.scrollY * 1.1 - zs) * Math.min(1, dt * 3); drift += light ? 0 : dt * 30; z0 = zs + drift;
        VX = W / 2 + ptr.x * 40; VY = H * 0.46 + ptr.y * 24;
        var col = pcol(prog);
        g.clearRect(0, 0, W, H);
        drawTunnel(col);
        vis.length = 0;
        for (i = 0; i < objs.length; i++) { var o = objs[i]; if (o.t === 'ppl' && !light) o.z += o.v * dt; if (o.t === 'steam' && light) continue; var d = (((o.z - z0) % ZREP) + ZREP) % ZREP; if (d < 60) continue; vis.push({ d: d, o: o }); }
        vis.sort(function (a, b) { return b.d - a.d; });
        for (i = 0; i < vis.length; i++) drawObj(vis[i].o, vis[i].d, light ? 0 : t, col);
        if (!light) { g.fillStyle = 'rgba(' + col + ',0.6)'; for (i = 0; i < dust.length; i++) { var q = dust[i]; q.y += q.vy * dt; if (q.y < -4) { q.y = H + 4; q.x = rand(0, W); } g.globalAlpha = q.a; g.fillRect(q.x + ptr.x * q.s * 8, q.y, q.s, q.s); } g.globalAlpha = 1; }
      }
      window.addEventListener('pointermove', function (e) { ptr.x = e.clientX / W * 2 - 1; ptr.y = e.clientY / H * 2 - 1; }, { passive: true });

      /* ═══ PRICE CHART (log scale) ═══ */
      (function () {
        var svg = $('chartSvg'), x0 = 50, x1 = 735, lo = 7, hi = 9.7;
        function X(v) { return x0 + (Math.log(v) / Math.LN10 - lo) / (hi - lo) * (x1 - x0); }
        var h = '<line class="ax" x1="' + x0 + '" y1="200" x2="' + x1 + '" y2="200"/>';
        [[1e7, '$10M'], [1e8, '$100M'], [1e9, '$1B'], [5e9, '$5B']].forEach(function (t) { h += '<line class="tk" x1="' + X(t[0]) + '" y1="20" x2="' + X(t[0]) + '" y2="200"/><text x="' + X(t[0]) + '" y="218" text-anchor="middle">' + t[1] + '</text>'; });
        var rows = [{ y: 34, a: 2e7, b: 5e7, c: '#4fc3f7', t: '$20M \u2013 $50M', n: 'CLASS I' }, { y: 92, a: 1e8, b: 5e8, c: '#4caf50', t: '$100M \u2013 $500M', n: 'CLASS II' }, { y: 150, a: 5e8, b: 2e9, c: '#ffd600', t: 'UP TO $2B+', n: 'CLASS III', open: true }];
        rows.forEach(function (r, i) {
          var xa = X(r.a), xb = X(r.b);
          h += '<g class="rb' + (i === 2 ? ' c3' : '') + '" data-r="' + i + '" style="color:' + r.c + '"><rect x="' + xa + '" y="' + r.y + '" width="' + (xb - xa) + '" height="34" rx="2" fill="' + r.c + '" fill-opacity="' + (r.open ? 0.28 : 0.55) + '" stroke="' + r.c + '" stroke-width="1.5"' + (r.open ? ' stroke-dasharray="5 4"' : '') + '/>' + (r.open ? '<path d="M' + xb + ' ' + (r.y + 6) + ' l16 11 l-16 11z" fill="' + r.c + '"/>' : '') + '<text class="lbl" x="' + (xa + 10) + '" y="' + (r.y + 21) + '">' + r.t + '</text></g>';
          h += '<text x="' + (x0 - 4) + '" y="' + (r.y + 21) + '" text-anchor="end" style="fill:' + r.c + '">' + r.n + '</text>';
        });
        var mx = X(2.2e8); h += '<g class="mkr"><line x1="' + mx + '" y1="70" x2="' + mx + '" y2="92" stroke="#fff" stroke-width="1"/><polygon points="' + mx + ',92 ' + (mx - 6) + ',99 ' + mx + ',106 ' + (mx + 6) + ',99" fill="#fff"/><text x="' + mx + '" y="66" text-anchor="middle" style="fill:#fff">LD-016 \u2014 $220M</text></g>';
        svg.innerHTML = h;
        var trs = document.querySelectorAll('#mtable tbody tr'), bars = svg.querySelectorAll('.rb');
        function hl(i, on) { trs[i].classList.toggle('hl', on); }
        bars.forEach(function (b) { var i = +b.getAttribute('data-r'); b.addEventListener('mouseenter', function () { hl(i, true); }); b.addEventListener('mouseleave', function () { hl(i, false); }); });
        trs.forEach(function (tr, i) { tr.addEventListener('mouseenter', function () { bars[i].style.filter = 'brightness(1.5) drop-shadow(0 0 10px currentColor)'; }); tr.addEventListener('mouseleave', function () { bars[i].style.filter = ''; }); });
      })();

      /* funnel particles */
      (function () {
        var gp = $('fparts'), h = '', i;
        for (i = 0; i < 22; i++) { var x0 = rand(-110, 110); h += '<circle class="fp" r="' + rand(2, 3.6).toFixed(1) + '" cx="150" cy="' + rand(14, 40).toFixed(0) + '" style="--x0:' + x0.toFixed(0) + 'px;animation-delay:' + (-rand(0, 3.6)).toFixed(2) + 's"/>'; }
        gp.innerHTML = h;
      })();

      /* ═══ CCTV FLOOR MONITOR ═══ */
      (function () {
        var cv = $('floor'), c = cv.getContext('2d'), FW = 0, FH = 0, NX = 7, NY = 4, nodes = [], stalls = [], agents = [], prots = [], flashes = [], units = [], watchers = [], logEl = $('flog');
        function say(t, cls) { var d = document.createElement('div'); if (cls) d.className = cls; d.textContent = '> ' + t; logEl.appendChild(d); while (logEl.children.length > 5) logEl.removeChild(logEl.firstChild); }
        function layout() {
          FW = cv.clientWidth; FH = cv.clientHeight; cv.width = FW * dpr; cv.height = FH * dpr; c.setTransform(dpr, 0, 0, dpr, 0, 0);
          nodes = []; var i, j; for (j = 0; j < NY; j++) for (i = 0; i < NX; i++) nodes.push({ x: (i + 0.5) * FW / NX, y: (j + 0.5) * FH / NY, i: i, j: j });
          stalls = []; for (j = 0; j < NY - 1; j++) for (i = 0; i < NX - 1; i++) { var n = nodes[j * NX + i]; stalls.push({ x: n.x + 14, y: n.y + 14, w: FW / NX - 28, h: FH / NY - 28, i: i, j: j }); }
          watchers = [nodes[0], nodes[NX - 1], nodes[NX * (NY - 1)], nodes[NX * NY - 1], nodes[3], nodes[NX * 2 + 3]];
          if (!agents.length) init();
        }
        function nb(n) { var r = []; if (n.i > 0) r.push(n.j * NX + n.i - 1); if (n.i < NX - 1) r.push(n.j * NX + n.i + 1); if (n.j > 0) r.push((n.j - 1) * NX + n.i); if (n.j < NY - 1) r.push((n.j + 1) * NX + n.i); return r; }
        function mkAgent() { var n0 = (Math.random() * nodes.length) | 0, k = nb(nodes[n0]), kinds = ['trader', 'buyer', 'collector']; return { n0: n0, n1: k[(Math.random() * k.length) | 0], t: Math.random(), sp: rand(0.18, 0.45), kind: kinds[(Math.random() * 3) | 0], off: null, x: 0, y: 0, dead: false }; }
        function init() {
          agents = []; var i; for (i = 0; i < 26; i++) agents.push(mkAgent());
          prots = []; var homes = [[1, 1], [3, 0], [5, 1], [2, 3], [4, 2], [0, 2]];
          homes.forEach(function (h) { var n = nodes[h[1] * NX + h[0]]; prots.push({ k: 'std', hx: n.x + 20, hy: n.y + 20, x: n.x + 20, y: n.y + 20, st: 'post', tg: null, ph: rand(0, TAU) }); });
          [[NX - 2, 0], [NX - 1, 1]].forEach(function (h) { var n = nodes[h[1] * NX + h[0]]; prots.push({ k: 'elite', hx: n.x + 14, hy: n.y + 14, x: n.x + 14, y: n.y + 14, st: 'post', tg: null, ph: rand(0, TAU) }); });
        }
        function pos(a) { var A = nodes[a.n0], B = nodes[a.n1]; a.x = A.x + (B.x - A.x) * a.t; a.y = A.y + (B.y - A.y) * a.t; }
        function pickAgent() { var live = agents.filter(function (a) { return !a.off && !a.dead; }); return live[(Math.random() * live.length) | 0]; }
        function nearest(a, k, n) { return prots.filter(function (p) { return k.indexOf(p.k) > -1 && p.st === 'post'; }).sort(function (p, q) { return Math.hypot(p.x - a.x, p.y - a.y) - Math.hypot(q.x - a.x, q.y - a.y); }).slice(0, n); }
        function flash(x, y, col) { flashes.push({ x: x, y: y, t: 0, col: col }); }
        function fight() { var a = pickAgent(); if (!a) return; a.off = { k: 'fight', t0: performance.now() }; say('Disturbance detected on the trading floor.', 'r'); nearest(a, ['std'], 2).forEach(function (p) { p.st = 'chase'; p.tg = a; }); }
        function weapon() { var a = pickAgent(); if (!a) return; a.off = { k: 'weapon', t0: performance.now() }; say('Anomaly weaponized. Response inbound.', 'v'); nearest(a, ['std', 'elite'], 3).forEach(function (p) { p.st = 'chase'; p.tg = a; }); var e = Math.random() < 0.5; units.push({ x: e ? -10 : FW + 10, y: rand(20, FH - 20), tg: a }); }
        function nuke() { var desk = stalls[stalls.length - 3 > 0 ? stalls.length - 3 : 0]; var a = { n0: 0, n1: 0, t: 0, sp: 0, kind: 'buyer', off: { k: 'nuke', t0: performance.now() }, x: -10, y: desk.y + desk.h / 2, dead: false, desk: desk }; agents.push(a); say('Nuclear weapon transaction in progress. Strictly monitored.', 'y'); }
        function resolveFight(a) { a.dead = true; flash(a.x, a.y, '255,40,40'); var el = ((performance.now() - a.off.t0) / 1000).toFixed(1); say('Offender neutralized in ' + el + 's. Zero conflict tolerance. No exceptions. No appeals.', 'r'); setTimeout(function () { agents.push(mkAgent()); }, 2500); }
        function resolveWeapon(a) { a.dead = true; flash(a.x, a.y, '180,60,255'); say('Immediate termination authorized. The artifact is recovered without negotiation.', 'v'); setTimeout(function () { agents.push(mkAgent()); }, 2500); }
        $('eFight').addEventListener('click', fight); $('eWeapon').addEventListener('click', weapon); $('eNuke').addEventListener('click', nuke);
        $('eReset').addEventListener('click', function () { agents = []; prots = []; flashes = []; units = []; logEl.innerHTML = ''; init(); say('Floor cleared. Monitoring resumed.'); });

        var lastT = performance.now();
        function loop(now) {
          requestAnimationFrame(loop); var dt = Math.min(0.05, (now - lastT) / 1000); lastT = now; if (!FW) return; var i, t = now / 1000;
          c.fillStyle = '#05050a'; c.fillRect(0, 0, FW, FH);
          c.fillStyle = '#0c0c12'; for (i = 0; i < NY; i++) c.fillRect(0, nodes[i * NX].y - 9, FW, 18); for (i = 0; i < NX; i++) c.fillRect(nodes[i].x - 9, 0, 18, FH);
          stalls.forEach(function (s, idx) { var vault = (s.i === NX - 2 && s.j === 0), nk = idx === stalls.length - 3; c.fillStyle = vault ? 'rgba(230,81,0,0.14)' : 'rgba(20,18,8,0.9)'; c.fillRect(s.x, s.y, s.w, s.h); c.strokeStyle = vault ? 'rgba(255,122,42,0.8)' : (nk ? 'rgba(255,60,60,0.6)' : 'rgba(255,214,0,0.2)'); c.lineWidth = vault || nk ? 1.6 : 1; c.strokeRect(s.x, s.y, s.w, s.h); if (vault || nk) { c.fillStyle = vault ? '#ff7a2a' : '#ff6a6a'; c.font = '9px "Share Tech Mono", monospace'; c.textAlign = 'center'; c.fillText(vault ? 'HIGH-VALUE ZONE' : 'NUCLEAR DESK', s.x + s.w / 2, s.y + s.h / 2 + 3); } });
          watchers.forEach(function (w, k) { var on = Math.sin(t * 4 + k) > 0; c.fillStyle = on ? 'rgba(255,40,40,0.9)' : 'rgba(255,40,40,0.25)'; c.fillRect(w.x - 2, w.y - 2, 4, 4); var an = t * 0.8 + k; c.fillStyle = 'rgba(255,40,40,0.05)'; c.beginPath(); c.moveTo(w.x, w.y); c.arc(w.x, w.y, 80, an, an + 0.6); c.closePath(); c.fill(); });
          for (i = agents.length - 1; i >= 0; i--) {
            var a = agents[i]; if (a.dead) { agents.splice(i, 1); continue; }
            if (a.off && a.off.k === 'nuke') { var dx = a.desk.x + a.desk.w / 2 - a.x, dy = a.desk.y + a.desk.h + 6 - a.y, dl = Math.hypot(dx, dy); a.x += dx / dl * 80 * dt; a.y += dy / dl * 80 * dt; if (dl < 24 || (performance.now() - a.off.t0) > 3600) { a.dead = true; flash(a.x, a.y, '255,40,40'); say('Nuclear weapon transactions are strictly monitored. Unauthorized buyers are executed without warning.', 'r'); } }
            else if (!a.off) { a.t += a.sp * dt * 0.6; if (a.t >= 1) { a.n0 = a.n1; var k = nb(nodes[a.n0]); a.n1 = k[(Math.random() * k.length) | 0]; a.t = 0; } pos(a); }
            var col = a.off ? (a.off.k === 'weapon' ? '190,70,255' : '255,50,50') : (a.kind === 'collector' ? '255,214,0' : a.kind === 'buyer' ? '150,170,190' : '220,220,220');
            if (a.off) { var pr = (t * 2 % 1); c.strokeStyle = 'rgba(' + col + ',' + (1 - pr) + ')'; c.lineWidth = 1.5; c.beginPath(); c.arc(a.x, a.y, 5 + pr * 14, 0, TAU); c.stroke(); }
            c.fillStyle = 'rgb(' + col + ')'; c.beginPath(); c.arc(a.x, a.y, a.off ? 4.2 : 3, 0, TAU); c.fill();
          }
          prots.forEach(function (p) {
            if (p.st === 'post') { p.x = p.hx + Math.cos(t * 0.6 + p.ph) * 6; p.y = p.hy + Math.sin(t * 0.8 + p.ph) * 4; }
            else if (p.st === 'chase') { var tg = p.tg; if (!tg || tg.dead) { p.st = 'ret'; } else { var dx = tg.x - p.x, dy = tg.y - p.y, dl = Math.hypot(dx, dy); if (dl < 9) { if (!tg.dead && tg.off) { if (tg.off.k === 'fight') resolveFight(tg); else resolveWeapon(tg); } p.st = 'ret'; } else { p.x += dx / dl * 280 * dt; p.y += dy / dl * 280 * dt; } } }
            else { var rx = p.hx - p.x, ry = p.hy - p.y, rl = Math.hypot(rx, ry); if (rl < 8) p.st = 'post'; else { p.x += rx / rl * 90 * dt; p.y += ry / rl * 90 * dt; } }
            var el = p.k === 'elite', rc = el ? '255,122,42' : '255,214,0';
            c.strokeStyle = 'rgba(' + rc + ',0.9)'; c.lineWidth = el ? 2 : 1.6; c.beginPath(); c.arc(p.x, p.y, el ? 9 : 7, 0, TAU); c.stroke(); if (el) { c.beginPath(); c.arc(p.x, p.y, 5, 0, TAU); c.stroke(); } c.fillStyle = 'rgb(' + rc + ')'; c.fillRect(p.x - 1.5, p.y - 1.5, 3, 3);
          });
          for (i = units.length - 1; i >= 0; i--) { var u = units[i], tg2 = u.tg; if (!tg2 || tg2.dead) { units.splice(i, 1); continue; } var ux = tg2.x - u.x, uy = tg2.y - u.y, ul = Math.hypot(ux, uy); u.x += ux / ul * 220 * dt; u.y += uy / ul * 220 * dt; c.fillStyle = '#4fc3f7'; c.beginPath(); c.moveTo(u.x, u.y - 7); c.lineTo(u.x + 6, u.y + 5); c.lineTo(u.x - 6, u.y + 5); c.closePath(); c.fill(); c.strokeStyle = 'rgba(79,195,247,0.5)'; c.beginPath(); c.arc(u.x, u.y, 11, 0, TAU); c.stroke(); }
          for (i = flashes.length - 1; i >= 0; i--) { var f = flashes[i]; f.t += dt; if (f.t > 0.9) { flashes.splice(i, 1); continue; } var k2 = f.t / 0.9; c.strokeStyle = 'rgba(' + f.col + ',' + (1 - k2) + ')'; c.lineWidth = 3 * (1 - k2) + 0.5; c.beginPath(); c.arc(f.x, f.y, 6 + k2 * 40, 0, TAU); c.stroke(); c.fillStyle = 'rgba(' + f.col + ',' + (0.4 * (1 - k2)) + ')'; c.beginPath(); c.arc(f.x, f.y, 6 + k2 * 40, 0, TAU); c.fill(); }
          c.fillStyle = 'rgba(255,214,0,0.04)'; for (i = 0; i < FH; i += 4) c.fillRect(0, i, FW, 1);
          var d = new Date(); c.fillStyle = '#ffd600'; c.font = '10px "Share Tech Mono", monospace'; c.textAlign = 'left'; c.fillText('CAM 07 // BLACK STREET \u2014 TRADING FLOOR', 12, 18); c.textAlign = 'right'; c.fillText(pad(d.getUTCHours()) + ':' + pad(d.getUTCMinutes()) + ':' + pad(d.getUTCSeconds()) + ' UTC', FW - 12, 18);
          if (Math.sin(t * 3) > 0) { c.fillStyle = '#ff2a2a'; c.beginPath(); c.arc(FW - 108, 14, 3.5, 0, TAU); c.fill(); }
          c.textAlign = 'left'; c.fillStyle = 'rgba(255,214,0,0.55)'; c.fillText('\u25CB STANDARD  \u25CE ELITE  \u25B2 D.I.V.I.D.E.  \u25A0 WATCH', 12, FH - 10);
        }
        layout(); say('Floor monitor online. Zero conflict tolerance.', 'y'); requestAnimationFrame(loop);
        var rt = null; window.addEventListener('resize', function () { clearTimeout(rt); rt = setTimeout(function () { var a = agents; layout(); agents = a; }, 250); });
      })();

      /* ═══ INIT ═══ */
      var fb = $('fxBtn'); function fx() { fb.innerHTML = '&#9680; Effects: ' + (light ? 'light' : 'full'); }
      fb.addEventListener('click', function () { light = !light; fx(); }); fx();
      function resize() { W = window.innerWidth; H = window.innerHeight; bgCv.width = Math.floor(W * dpr); bgCv.height = Math.floor(H * dpr); bgCv.style.width = W + 'px'; bgCv.style.height = H + 'px'; g.setTransform(dpr, 0, 0, dpr, 0, 0); build(); }
      var rt2 = null; resize(); requestAnimationFrame(frame);
      window.addEventListener('resize', function () { clearTimeout(rt2); rt2 = setTimeout(resize, 250); });

      var els = document.querySelectorAll('.reveal, .rank, .chart');
      if ('IntersectionObserver' in window) { var io = new IntersectionObserver(function (en) { en.forEach(function (x) { if (x.isIntersecting) { x.target.classList.add('in'); io.unobserve(x.target); } }); }, { threshold: 0.12 }); els.forEach(function (e) { io.observe(e); }); } else els.forEach(function (e) { e.classList.add('in'); });
    })();
  </script>

</body>
</html>
