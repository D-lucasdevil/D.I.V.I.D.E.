
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Anomaly Reports</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;600;700&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background-color: #080808;
      color: #c0c0c0;
      font-family: 'Share Tech Mono', monospace;
      min-height: 100vh;
    }

    .warning-bar {
      background-color: #8b0000;
      color: #fff;
      text-align: center;
      padding: 6px;
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      border-bottom: 1px solid #ff0000;
    }

    .container {
      max-width: 900px;
      margin: 0 auto;
      padding: 40px 20px;
    }

    .header {
      border: 1px solid #3a0000;
      padding: 30px;
      margin-bottom: 30px;
      position: relative;
      background: linear-gradient(180deg, #0f0000 0%, #080808 100%);
    }

    .header::before {
      content: '// CLASSIFIED //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #8b0000;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #8b0000;
      border-right: 2px solid #8b0000;
    }

    .site-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 36px;
      font-weight: 700;
      color: #cc0000;
      letter-spacing: 6px;
      text-shadow: 0 0 20px rgba(200,0,0,0.4);
      margin-bottom: 6px;
    }

    .site-subtitle {
      font-size: 11px;
      color: #555;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 16px;
    }

    .clearance-badge {
      display: inline-block;
      border: 1px solid #8b0000;
      color: #8b0000;
      font-size: 10px;
      letter-spacing: 3px;
      padding: 4px 12px;
      text-transform: uppercase;
    }

    .back-link {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: #555;
      text-decoration: none;
      font-size: 11px;
      letter-spacing: 2px;
      margin-bottom: 20px;
      transition: color 0.2s;
    }
    .back-link:hover { color: #cc0000; }

    .status-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 16px;
      background: #0d0d0d;
      border: 1px solid #1a0000;
      margin-bottom: 20px;
      font-size: 10px;
      color: #444;
      letter-spacing: 1px;
    }

    .status-dot {
      display: inline-block;
      width: 6px; height: 6px;
      background: #cc0000;
      border-radius: 50%;
      margin-right: 6px;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.3; }
    }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #8b0000;
      text-transform: uppercase;
      margin-bottom: 12px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a0000;
    }

    .search-bar {
      width: 100%;
      background: #0d0d0d;
      border: 1px solid #1a0000;
      border-left: 3px solid #8b0000;
      color: #c0c0c0;
      font-family: 'Share Tech Mono', monospace;
      font-size: 13px;
      padding: 10px 14px;
      margin-bottom: 20px;
      outline: none;
      letter-spacing: 1px;
    }
    .search-bar::placeholder { color: #333; }
    .search-bar:focus { border-color: #cc0000; }

    /* Legend */
    .legend {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-bottom: 20px;
      padding: 12px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
    }

    .legend-item {
      display: flex;
      align-items: center;
      gap: 6px;
      font-size: 10px;
      letter-spacing: 1px;
      cursor: pointer;
      padding: 3px 8px;
      border: 1px solid transparent;
      transition: border-color 0.2s;
    }

    .legend-dot {
      width: 8px; height: 8px;
      border-radius: 50%;
      flex-shrink: 0;
    }

    .anomaly-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 5px;
      margin-bottom: 30px;
    }

    @media (max-width: 600px) {
      .anomaly-grid { grid-template-columns: 1fr 1fr; }
    }

    /* Base link style */
    .anomaly-link {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 8px 12px;
      background-color: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid transparent;
      color: #777;
      text-decoration: none;
      font-size: 11px;
      letter-spacing: 0.5px;
      transition: all 0.15s ease;
    }

    /* Tier color classes */
    .t0  { border-left-color: #444; }
    .t0:hover  { border-left-color: #888; color: #aaa; background: #0f0f0f; }

    .t1  { border-left-color: #1a4a6a; }
    .t1:hover  { border-left-color: #4fc3f7; color: #7dd5f7; background: #0a1520; }

    .t2  { border-left-color: #1a4a1a; }
    .t2:hover  { border-left-color: #4caf50; color: #7dc87f; background: #0a150a; }

    .t3  { border-left-color: #4a4000; }
    .t3:hover  { border-left-color: #ffd600; color: #ffe44d; background: #151000; }

    .t4  { border-left-color: #4a1a00; }
    .t4:hover  { border-left-color: #e65100; color: #ff7c3a; background: #150800; }

    .t5  { border-left-color: #3a0000; }
    .t5:hover  { border-left-color: #f44336; color: #f77; background: #110000; }

    .t6  { border-left-color: #3a0a4a; }
    .t6:hover  { border-left-color: #9c27b0; color: #ce7adb; background: #0f0015; }

    .t7  { border-left-color: #4a004a; }
    .t7:hover  { border-left-color: #cc00cc; color: #ee66ee; background: #110011; }

    .tomega { border-left-color: #333; }
    .tomega:hover { border-left-color: #fff; color: #fff; background: #111; }

    .tredacted { border-left-color: #5a0a4a; }
    .tredacted:hover { border-left-color: #ff69b4; color: #ffadd6; background: #120010; }

    /* Colored dot indicator */
    .tier-dot {
      width: 6px; height: 6px;
      border-radius: 50%;
      flex-shrink: 0;
    }

    .dot-0       { background: #666; }
    .dot-1       { background: #4fc3f7; }
    .dot-2       { background: #4caf50; }
    .dot-3       { background: #ffd600; }
    .dot-4       { background: #e65100; }
    .dot-5       { background: #f44336; }
    .dot-6       { background: #9c27b0; }
    .dot-7       { background: #cc00cc; }
    .dot-omega   { background: #fff; }
    .dot-redacted { background: #ff69b4; }

    .footer {
      border-top: 1px solid #1a0000;
      padding-top: 20px;
      font-size: 10px;
      color: #333;
      letter-spacing: 1px;
      line-height: 1.8;
      text-align: center;
    }
  </style>
</head>
<body>

  <div class="warning-bar">
    ⚠ RESTRICTED ACCESS — AUTHORIZED PERSONNEL ONLY — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="container">

    <a href="index.html" class="back-link">← RETURN TO DATABASE INDEX</a>

    <div class="header">
      <div class="site-title">ANOMALY REPORTS</div>
      <div class="site-subtitle">Liminal Division — Active Case Files</div>
      <div class="clearance-badge">Clearance Level 1+ Required</div>
    </div>

    <div class="status-bar">
      <span><span class="status-dot"></span>DATABASE ONLINE</span>
      <span>TOTAL DOCUMENTED: 96 ANOMALIES</span>
      <span>THREAT STATUS: ELEVATED</span>
    </div>

    <!-- Legend -->
    <div class="legend">
      <div class="legend-item"><div class="legend-dot dot-0"></div> CLASS 0</div>
      <div class="legend-item"><div class="legend-dot dot-1"></div> CLASS I</div>
      <div class="legend-item"><div class="legend-dot dot-2"></div> CLASS II</div>
      <div class="legend-item"><div class="legend-dot dot-3"></div> CLASS III</div>
      <div class="legend-item"><div class="legend-dot dot-4"></div> CLASS IV</div>
      <div class="legend-item"><div class="legend-dot dot-5"></div> CLASS V</div>
      <div class="legend-item"><div class="legend-dot dot-6"></div> CLASS VI</div>
      <div class="legend-item"><div class="legend-dot dot-7"></div> CLASS VII</div>
      <div class="legend-item"><div class="legend-dot dot-omega"></div> CLASS Ω</div>
      <div class="legend-item"><div class="legend-dot dot-redacted"></div> REDACTED</div>
    </div>

    <input class="search-bar" type="text" placeholder="// SEARCH ANOMALY FILES..." id="searchInput" onkeyup="filterAnomalies()" />

    <div class="section-label">// Active Case Files — LD Series //</div>

    <div class="anomaly-grid" id="anomalyGrid">
      <!-- Ω -->
      <a href="LD-000.html" class="anomaly-link tomega"><div class="tier-dot dot-omega"></div>LD-000 — [REDACTED]</a>
      <!-- REDACTED -->
      <a href="LD-001.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-001 — Lucas Devil</a>
      <!-- REDACTED -->
      <a href="LD-002.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-002 — Doro</a>
      <!-- III -->
      <a href="LD-003.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-003 — The Drowned Girl</a>
      <!-- I -->
      <a href="LD-004.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-004 — The Swine Hybrid</a>
      <!-- III -->
      <a href="LD-005.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-005 — The Hollow Plaything</a>
      <!-- I -->
      <a href="LD-006.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-006 — The Oracle Terminal</a>
      <!-- II -->
      <a href="LD-007.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-007 — The Visitor's Folklore</a>
      <!-- II -->
      <a href="LD-008.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-008 — Laughtrack</a>
      <!-- II -->
      <a href="LD-009.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-009 — The Endless Lift</a>
      <!-- II -->
      <a href="LD-009.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-009.5</a>
      <!-- III -->
      <a href="LD-010.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-010 — The Pactbound</a>
      <!-- III -->
      <a href="LD-011.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-011 — The Echo-Faced</a>
      <!-- III -->
      <a href="LD-012.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-012 — The Molded</a>
      <!-- IV -->
      <a href="LD-013.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-013 — The Insect Matron</a>
      <!-- III -->
      <a href="LD-014.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-014 — The Knife That Loves Too Deeply</a>
      <!-- REDACTED -->
      <a href="LD-015.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-015 — REDACTED</a>
      <!-- II -->
      <a href="LD-016.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-016 — Andy's Revolver</a>
      <!-- III -->
      <a href="LD-017.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-017 — The Pactbound Trinket</a>
      <!-- II -->
      <a href="LD-018.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-018 — REDACTED Neutralized</a>
      <!-- II -->
      <a href="LD-019.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-019 — The House Always Wins</a>
      <!-- I -->
      <a href="LD-020.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-020 — The Finder's Shard</a>
      <!-- I -->
      <a href="LD-021.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-021 — Velocity Pills</a>
      <!-- II -->
      <a href="LD-021.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-021.5</a>
      <!-- I -->
      <a href="LD-022.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-022 — RedSap</a>
      <!-- I -->
      <a href="LD-023.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-023 — The Kindler's Box</a>
      <!-- II -->
      <a href="LD-023.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-023.5</a>
      <!-- II -->
      <a href="LD-024.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-024 — The Hunting Slide</a>
      <!-- II -->
      <a href="LD-025.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-025 — The Red Stalker</a>
      <!-- III -->
      <a href="LD-026.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-026 — The Perfect Wife</a>
      <!-- II -->
      <a href="LD-027.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-027 — Angel Terminal</a>
      <!-- II -->
      <a href="LD-028.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-028 — It's a Fking UFO</a>
      <!-- I -->
      <a href="LD-029.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-029 — Flashbang Lens</a>
      <!-- 0 -->
      <a href="LD-030.html" class="anomaly-link t0"><div class="tier-dot dot-0"></div>LD-030 — Infinite Pizza Slice</a>
      <!-- II -->
      <a href="LD-031.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-031 — First Bottle's Free</a>
      <!-- II -->
      <a href="LD-032.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-032 — Free Parking</a>
      <!-- III -->
      <a href="LD-033.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-033 — Black Backseat</a>
      <!-- III -->
      <a href="LD-034.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-034 — The Pale Man</a>
      <!-- III -->
      <a href="LD-035.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-035 — The Wishing Matron</a>
      <!-- III -->
      <a href="LD-035.5.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-035.5</a>
      <!-- II -->
      <a href="LD-036.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-036 — The Hunters</a>
      <!-- II -->
      <a href="LD-036.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-036.5</a>
      <!-- II -->
      <a href="LD-037.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-037 — The Lost Episode</a>
      <!-- II -->
      <a href="LD-037.5.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-037.5</a>
      <!-- II -->
      <a href="LD-038.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-038 — The All-Brewer</a>
      <!-- II -->
      <a href="LD-039.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-039 — The Suicide Line</a>
      <!-- III -->
      <a href="LD-040.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-040 — Calcium Devourers</a>
      <!-- II -->
      <a href="LD-041.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-041 — The Crow Guard</a>
      <!-- IV -->
      <a href="LD-042.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-042 — The Earth Devourers</a>
      <!-- REDACTED -->
      <a href="LD-043.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-043 — The Crimson Judgement</a>
      <!-- REDACTED -->
      <a href="LD-044.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-044 — The Veiled Judgment</a>
      <!-- REDACTED -->
      <a href="LD-045.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-045 — DIVA</a>
      <!-- I -->
      <a href="LD-046.html" class="anomaly-link t1"><div class="tier-dot dot-1"></div>LD-046 — Gloom Smoking Tube</a>
      <!-- III -->
      <a href="LD-047.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-047 — Fragment of One's Imagination</a>
      <!-- III -->
      <a href="LD-048.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-048 — Price of Immortality</a>
      <!-- IV -->
      <a href="LD-049.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-049 — RAGE</a>
      <!-- IV -->
      <a href="LD-050.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-050 — The Calamity Empress</a>
      <!-- III -->
      <a href="LD-051.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-051 — Remnants of Ash</a>
      <!-- II -->
      <a href="LD-052.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-052 — Judgement Coin</a>
      <!-- IV -->
      <a href="LD-053.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-053 — The Crimson Impaler</a>
      <!-- III -->
      <a href="LD-054.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-054 — The Sailor's Lullaby</a>
      <!-- III -->
      <a href="LD-055.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-055 — The Drowned Shepherd</a>
      <!-- III -->
      <a href="LD-056.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-056 — The Hollow Seraph</a>
      <!-- II -->
      <a href="LD-057.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-057 — Egg of Concepts</a>
      <!-- III -->
      <a href="LD-058.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-058 — The Hunter Tribes</a>
      <!-- II -->
      <a href="LD-059.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-059 — The Murder Bucket</a>
      <!-- IV -->
      <a href="LD-060.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-060 — The Timekeeper's Pocket Watch</a>
      <!-- III -->
      <a href="LD-061.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-061 — The Gravebound Colossus</a>
      <!-- II -->
      <a href="LD-062.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-062 — The Hollow Farm</a>
      <!-- III -->
      <a href="LD-063.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-063 — The Hollow Stag</a>
      <!-- IV -->
      <a href="LD-064.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-064 — The Veiled Queen & The Devourer</a>
      <!-- II -->
      <a href="LD-065.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-065 — The Rabbit Mother</a>
      <!-- REDACTED -->
      <a href="LD-066.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-066 — The Silent Executioner</a>
      <!-- 0 -->
      <a href="LD-067.html" class="anomaly-link t0"><div class="tier-dot dot-0"></div>LD-067 — The Attempted Entertainer</a>
      <!-- IV -->
      <a href="LD-068.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-068 — The Absolute Zero Blade</a>
      <!-- IV -->
      <a href="LD-069.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-069 — The Latex Lament</a>
      <!-- III -->
      <a href="LD-070.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-070 — There's A Devil In My Heart</a>
      <!-- III -->
      <a href="LD-071.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-071 — Killstreak</a>
      <!-- II -->
      <a href="LD-072.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-072 — The Finger Maiden</a>
      <!-- II -->
      <a href="LD-073.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-073 — The Watchers</a>
      <!-- III -->
      <a href="LD-074.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-074 — Dominance</a>
      <!-- II -->
      <a href="LD-075.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-075 — Phantom Edge</a>
      <!-- IV -->
      <a href="LD-076.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-076 — The Silent Queen</a>
      <!-- II -->
      <a href="LD-077.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-077 — The White Maiden</a>
      <!-- IV -->
      <a href="LD-078.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-078 — The Golden-Eyed Lord</a>
      <!-- REDACTED -->
      <a href="LD-079.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-079 — The Crimson Witness</a>
      <!-- II -->
      <a href="LD-080.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-080 — The Marionette</a>
      <!-- III -->
      <a href="LD-081.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-081 — The Corrosive Drake</a>
      <!-- IV -->
      <a href="LD-082.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-082 — The Mist Hound</a>
      <!-- III -->
      <a href="LD-083.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-083 — The HellBreaker</a>
      <!-- II -->
      <a href="LD-084.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-084 — The Mourning Coffin</a>
      <!-- II -->
      <a href="LD-085.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-085 — Eclipse</a>
      <!-- II -->
      <a href="LD-086.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-086 — The Hook Embrace</a>
      <!-- II -->
      <a href="LD-087.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-087 — The Second Skin</a>
      <!-- REDACTED -->
      <a href="LD-088.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-088 — The Mercy of Life</a>
      <!-- III -->
      <a href="LD-089.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-089 — The Missing</a>
      <!-- IV -->
      <a href="LD-090.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-090 — Forever Diamonds</a>
      <!-- III -->
      <a href="LD-091.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-091 — I Love A Man In Uniform</a>
      <!-- REDACTED -->
      <a href="LD-092.html" class="anomaly-link tredacted"><div class="tier-dot dot-redacted"></div>LD-092 — The Last Wonderer</a>
      <!-- II -->
      <a href="LD-093.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-093 — Don't Fear The Reaper</a>
      <!-- IV -->
      <a href="LD-094.html" class="anomaly-link t4"><div class="tier-dot dot-4"></div>LD-094 — The Last Oath</a>
      <!-- III -->
      <a href="LD-095.html" class="anomaly-link t3"><div class="tier-dot dot-3"></div>LD-095 — Scythe of Sync</a>
      <!-- II -->
      <a href="LD-096.html" class="anomaly-link t2"><div class="tier-dot dot-2"></div>LD-096 — The Candle Maiden</a>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

  <script>
    function filterAnomalies() {
      const input = document.getElementById('searchInput').value.toLowerCase();
      const links = document.querySelectorAll('.anomaly-link');
      links.forEach(link => {
        link.style.display = link.textContent.toLowerCase().includes(input) ? 'flex' : 'none';
      });
    }
  </script>

</body>
</html>
