
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Anomaly Threat Levels</title>
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
      top: -10px;
      left: 20px;
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

    /* Tier section */
    .tier-section {
      margin-bottom: 28px;
    }

    .tier-header {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 10px 16px;
      margin-bottom: 8px;
      border-left: 4px solid;
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
    }

    .tier-badge {
      font-size: 10px;
      padding: 2px 8px;
      border: 1px solid;
      letter-spacing: 2px;
      font-family: 'Share Tech Mono', monospace;
    }

    .tier-count {
      margin-left: auto;
      font-size: 10px;
      color: #444;
      letter-spacing: 2px;
    }

    .tier-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 5px;
      padding-left: 4px;
    }

    @media (max-width: 600px) {
      .tier-grid { grid-template-columns: 1fr; }
    }

    .anomaly-link {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 8px 14px;
      background-color: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid transparent;
      color: #888;
      text-decoration: none;
      font-size: 12px;
      letter-spacing: 0.5px;
      transition: all 0.15s ease;
    }

    .anomaly-link:hover {
      color: #fff;
      background: #111;
    }

    .empty-tier {
      padding: 10px 14px;
      color: #2a2a2a;
      font-size: 11px;
      letter-spacing: 2px;
      border: 1px solid #111;
      border-left: 3px solid #1a1a1a;
    }

    /* TIER 0 — Gray */
    .tier-0 .tier-header { border-color: #666; background: rgba(102,102,102,0.05); color: #888; }
    .tier-0 .tier-badge { color: #666; border-color: #444; }
    .tier-0 .anomaly-link { border-left-color: #444; }
    .tier-0 .anomaly-link:hover { border-left-color: #888; color: #aaa; }

    /* TIER I — Light Blue */
    .tier-1 .tier-header { border-color: #4fc3f7; background: rgba(79,195,247,0.05); color: #4fc3f7; }
    .tier-1 .tier-badge { color: #4fc3f7; border-color: #1a6a8a; }
    .tier-1 .anomaly-link { border-left-color: #1a4a6a; }
    .tier-1 .anomaly-link:hover { border-left-color: #4fc3f7; color: #7dd5f7; }

    /* TIER II — Green */
    .tier-2 .tier-header { border-color: #4caf50; background: rgba(76,175,80,0.05); color: #4caf50; }
    .tier-2 .tier-badge { color: #4caf50; border-color: #1a5a1a; }
    .tier-2 .anomaly-link { border-left-color: #1a4a1a; }
    .tier-2 .anomaly-link:hover { border-left-color: #4caf50; color: #7dc87f; }

    /* TIER III — Yellow */
    .tier-3 .tier-header { border-color: #ffd600; background: rgba(255,214,0,0.05); color: #ffd600; }
    .tier-3 .tier-badge { color: #ffd600; border-color: #6a5a00; }
    .tier-3 .anomaly-link { border-left-color: #4a4000; }
    .tier-3 .anomaly-link:hover { border-left-color: #ffd600; color: #ffe44d; }

    /* TIER IV — Dark Orange */
    .tier-4 .tier-header { border-color: #e65100; background: rgba(230,81,0,0.05); color: #e65100; }
    .tier-4 .tier-badge { color: #e65100; border-color: #6a2500; }
    .tier-4 .anomaly-link { border-left-color: #4a1a00; }
    .tier-4 .anomaly-link:hover { border-left-color: #e65100; color: #ff7c3a; }

    /* TIER V — Red */
    .tier-5 .tier-header { border-color: #f44336; background: rgba(244,67,54,0.05); color: #f44336; }
    .tier-5 .tier-badge { color: #f44336; border-color: #6a1a1a; }
    .tier-5 .anomaly-link { border-left-color: #3a0000; }
    .tier-5 .anomaly-link:hover { border-left-color: #f44336; color: #f77; }

    /* TIER VI — Purple */
    .tier-6 .tier-header { border-color: #9c27b0; background: rgba(156,39,176,0.05); color: #9c27b0; }
    .tier-6 .tier-badge { color: #9c27b0; border-color: #4a0a5a; }
    .tier-6 .anomaly-link { border-left-color: #3a0a4a; }
    .tier-6 .anomaly-link:hover { border-left-color: #9c27b0; color: #ce7adb; }

    /* TIER VII — Red and Purple */
    .tier-7 .tier-header {
      border-color: #cc00cc;
      background: linear-gradient(90deg, rgba(244,67,54,0.05), rgba(156,39,176,0.05));
      color: #cc00cc;
      text-shadow: 0 0 8px rgba(204,0,204,0.4);
    }
    .tier-7 .tier-badge { color: #cc00cc; border-color: #6a006a; }
    .tier-7 .anomaly-link { border-left-color: #4a004a; }
    .tier-7 .anomaly-link:hover { border-left-color: #cc00cc; color: #ee66ee; }

    /* TIER Ω — Black and White */
    .tier-omega .tier-header {
      border-color: #fff;
      background: linear-gradient(90deg, rgba(255,255,255,0.03), rgba(0,0,0,0));
      color: #fff;
      text-shadow: 0 0 12px rgba(255,255,255,0.3);
    }
    .tier-omega .tier-badge { color: #fff; border-color: #555; }
    .tier-omega .anomaly-link { border-left-color: #333; }
    .tier-omega .anomaly-link:hover { border-left-color: #fff; color: #fff; }

    /* TIER REDACTED — Galaxy Pink */
    .tier-redacted .tier-header {
      border-color: #ff69b4;
      background: linear-gradient(90deg, rgba(255,105,180,0.05), rgba(147,112,219,0.05), rgba(255,20,147,0.03));
      color: #ff69b4;
      text-shadow: 0 0 10px rgba(255,105,180,0.4);
    }
    .tier-redacted .tier-badge { color: #ff69b4; border-color: #7a1a5a; }
    .tier-redacted .anomaly-link { border-left-color: #5a0a4a; }
    .tier-redacted .anomaly-link:hover { border-left-color: #ff69b4; color: #ffadd6; }

    .footer {
      border-top: 1px solid #1a0000;
      padding-top: 20px;
      font-size: 10px;
      color: #333;
      letter-spacing: 1px;
      line-height: 1.8;
      text-align: center;
      margin-top: 20px;
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
      <div class="site-title">THREAT LEVEL INDEX</div>
      <div class="site-subtitle">Anomaly Classification by Danger Rating</div>
      <div class="clearance-badge">Clearance Level 1+ Required</div>
    </div>

    <!-- TIER 0 -->
    <div class="tier-section tier-0">
      <div class="tier-header">
        <span class="tier-badge">CLASS 0</span>
        Threat Level: Zero
        <span class="tier-count">2 ANOMALIES</span>
      </div>
      <div class="tier-grid">
        <a href="LD-030.html" class="anomaly-link">▶ LD-030 — Infinite Pizza Slice</a>
        <a href="LD-067.html" class="anomaly-link">▶ LD-067 — The Attempted Entertainer</a>
      </div>
    </div>

    <!-- TIER I -->
    <div class="tier-section tier-1">
      <div class="tier-header">
        <span class="tier-badge">CLASS I</span>
        Threat Level: Low
        <span class="tier-count">8 ANOMALIES</span>
      </div>
      <div class="tier-grid">
        <a href="LD-004.html" class="anomaly-link">▶ LD-004 — The Swine Hybrid</a>
        <a href="LD-006.html" class="anomaly-link">▶ LD-006 — The Oracle Terminal</a>
        <a href="LD-020.html" class="anomaly-link">▶ LD-020 — The Finder's Shard</a>
        <a href="LD-021.html" class="anomaly-link">▶ LD-021 — Velocity Pills</a>
        <a href="LD-022.html" class="anomaly-link">▶ LD-022 — RedSap</a>
        <a href="LD-023.html" class="anomaly-link">▶ LD-023 — The Kindler's Box</a>
        <a href="LD-029.html" class="anomaly-link">▶ LD-029 — Flashbang Lens</a>
        <a href="LD-046.html" class="anomaly-link">▶ LD-046 — Gloom Smoking Tube</a>
      </div>
    </div>

    <!-- TIER II -->
    <div class="tier-section tier-2">
      <div class="tier-header">
        <span class="tier-badge">CLASS II</span>
        Threat Level: Moderate
        <span class="tier-count">33 ANOMALIES</span>
      </div>
      <div class="tier-grid">
        <a href="LD-007.html" class="anomaly-link">▶ LD-007 — The Visitor's Folklore</a>
        <a href="LD-008.html" class="anomaly-link">▶ LD-008 — Laughtrack</a>
        <a href="LD-009.html" class="anomaly-link">▶ LD-009 — The Endless Lift</a>
        <a href="LD-016.html" class="anomaly-link">▶ LD-016 — Andy's Revolver</a>
        <a href="LD-018.html" class="anomaly-link">▶ LD-018 — REDACTED Neutralized</a>
        <a href="LD-019.html" class="anomaly-link">▶ LD-019 — The House Always Wins</a>
        <a href="LD-024.html" class="anomaly-link">▶ LD-024 — The Hunting Slide</a>
        <a href="LD-025.html" class="anomaly-link">▶ LD-025 — The Red Stalker</a>
        <a href="LD-027.html" class="anomaly-link">▶ LD-027 — Angel Terminal</a>
        <a href="LD-028.html" class="anomaly-link">▶ LD-028 — It's a Fking UFO</a>
        <a href="LD-031.html" class="anomaly-link">▶ LD-031 — First Bottle's Free</a>
        <a href="LD-032.html" class="anomaly-link">▶ LD-032 — Free Parking</a>
        <a href="LD-036.html" class="anomaly-link">▶ LD-036 — The Hunters</a>
        <a href="LD-037.html" class="anomaly-link">▶ LD-037 — The Lost Episode</a>
        <a href="LD-038.html" class="anomaly-link">▶ LD-038 — The All-Brewer</a>
        <a href="LD-039.html" class="anomaly-link">▶ LD-039 — The Suicide Line</a>
        <a href="LD-041.html" class="anomaly-link">▶ LD-041 — The Crow Guard</a>
        <a href="LD-052.html" class="anomaly-link">▶ LD-052 — Judgement Coin</a>
        <a href="LD-057.html" class="anomaly-link">▶ LD-057 — Egg of Concepts</a>
        <a href="LD-059.html" class="anomaly-link">▶ LD-059 — The Murder Bucket</a>
        <a href="LD-062.html" class="anomaly-link">▶ LD-062 — The Hollow Farm</a>
        <a href="LD-065.html" class="anomaly-link">▶ LD-065 — The Rabbit Mother</a>
        <a href="LD-072.html" class="anomaly-link">▶ LD-072 — The Finger Maiden</a>
        <a href="LD-073.html" class="anomaly-link">▶ LD-073 — The Watchers</a>
        <a href="LD-075.html" class="anomaly-link">▶ LD-075 — Phantom Edge</a>
        <a href="LD-077.html" class="anomaly-link">▶ LD-077 — The White Maiden</a>
        <a href="LD-080.html" class="anomaly-link">▶ LD-080 — The Marionette</a>
        <a href="LD-084.html" class="anomaly-link">▶ LD-084 — The Mourning Coffin</a>
        <a href="LD-085.html" class="anomaly-link">▶ LD-085 — Eclipse</a>
        <a href="LD-086.html" class="anomaly-link">▶ LD-086 — The Hook Embrace</a>
        <a href="LD-087.html" class="anomaly-link">▶ LD-087 — The Second Skin</a>
        <a href="LD-093.html" class="anomaly-link">▶ LD-093 — Don't Fear The Reaper</a>
        <a href="LD-096.html" class="anomaly-link">▶ LD-096 — The Candle Maiden</a>
      </div>
    </div>

    <!-- TIER III -->
    <div class="tier-section tier-3">
      <div class="tier-header">
        <span class="tier-badge">CLASS III</span>
        Threat Level: High
        <span class="tier-count">29 ANOMALIES</span>
      </div>
      <div class="tier-grid">
        <a href="LD-003.html" class="anomaly-link">▶ LD-003 — The Drowned Girl</a>
        <a href="LD-005.html" class="anomaly-link">▶ LD-005 — The Hollow Plaything</a>
        <a href="LD-010.html" class="anomaly-link">▶ LD-010 — The Pactbound</a>
        <a href="LD-011.html" class="anomaly-link">▶ LD-011 — The Echo-Faced</a>
        <a href="LD-012.html" class="anomaly-link">▶ LD-012 — The Molded</a>
        <a href="LD-014.html" class="anomaly-link">▶ LD-014 — The Knife That Loves Too Deeply</a>
        <a href="LD-017.html" class="anomaly-link">▶ LD-017 — The Pactbound Trinket</a>
        <a href="LD-026.html" class="anomaly-link">▶ LD-026 — The Perfect Wife</a>
        <a href="LD-033.html" class="anomaly-link">▶ LD-033 — Black Backseat</a>
        <a href="LD-034.html" class="anomaly-link">▶ LD-034 — The Pale Man</a>
        <a href="LD-035.html" class="anomaly-link">▶ LD-035 — The Wishing Matron</a>
        <a href="LD-040.html" class="anomaly-link">▶ LD-040 — Calcium Devourers</a>
        <a href="LD-047.html" class="anomaly-link">▶ LD-047 — Fragment of One's Imagination</a>
        <a href="LD-048.html" class="anomaly-link">▶ LD-048 — Price of Immortality</a>
        <a href="LD-051.html" class="anomaly-link">▶ LD-051 — Remnants of Ash</a>
        <a href="LD-054.html" class="anomaly-link">▶ LD-054 — The Sailor's Lullaby</a>
        <a href="LD-055.html" class="anomaly-link">▶ LD-055 — The Drowned Shepherd</a>
        <a href="LD-056.html" class="anomaly-link">▶ LD-056 — The Hollow Seraph</a>
        <a href="LD-058.html" class="anomaly-link">▶ LD-058 — The Hunter Tribes</a>
        <a href="LD-061.html" class="anomaly-link">▶ LD-061 — The Gravebound Colossus</a>
        <a href="LD-063.html" class="anomaly-link">▶ LD-063 — The Hollow Stag</a>
        <a href="LD-070.html" class="anomaly-link">▶ LD-070 — There's A Devil In My Heart</a>
        <a href="LD-071.html" class="anomaly-link">▶ LD-071 — Killstreak</a>
        <a href="LD-074.html" class="anomaly-link">▶ LD-074 — Dominance</a>
        <a href="LD-081.html" class="anomaly-link">▶ LD-081 — The Corrosive Drake</a>
        <a href="LD-083.html" class="anomaly-link">▶ LD-083 — The HellBreaker</a>
        <a href="LD-089.html" class="anomaly-link">▶ LD-089 — The Missing</a>
        <a href="LD-091.html" class="anomaly-link">▶ LD-091 — I Love A Man In Uniform</a>
        <a href="LD-095.html" class="anomaly-link">▶ LD-095 — Scythe of Sync</a>
      </div>
    </div>

    <!-- TIER IV -->
    <div class="tier-section tier-4">
      <div class="tier-header">
        <span class="tier-badge">CLASS IV</span>
        Threat Level: Extreme
        <span class="tier-count">14 ANOMALIES</span>
      </div>
      <div class="tier-grid">
        <a href="LD-013.html" class="anomaly-link">▶ LD-013 — The Insect Matron</a>
        <a href="LD-042.html" class="anomaly-link">▶ LD-042 — The Earth Devourers</a>
        <a href="LD-049.html" class="anomaly-link">▶ LD-049 — RAGE</a>
        <a href="LD-050.html" class="anomaly-link">▶ LD-050 — The Calamity Empress</a>
        <a href="LD-053.html" class="anomaly-link">▶ LD-053 — The Crimson Impaler</a>
        <a href="LD-060.html" class="anomaly-link">▶ LD-060 — The Timekeeper's Pocket Watch</a>
        <a href="LD-064.html" class="anomaly-link">▶ LD-064 — The Veiled Queen & The Devourer</a>
        <a href="LD-068.html" class="anomaly-link">▶ LD-068 — The Absolute Zero Blade</a>
        <a href="LD-069.html" class="anomaly-link">▶ LD-069 — The Latex Lament</a>
        <a href="LD-076.html" class="anomaly-link">▶ LD-076 — The Silent Queen</a>
        <a href="LD-078.html" class="anomaly-link">▶ LD-078 — The Golden-Eyed Lord</a>
        <a href="LD-082.html" class="anomaly-link">▶ LD-082 — The Mist Hound</a>
        <a href="LD-090.html" class="anomaly-link">▶ LD-090 — Forever Diamonds</a>
        <a href="LD-094.html" class="anomaly-link">▶ LD-094 — The Last Oath</a>
      </div>
    </div>

    <!-- TIER V -->
    <div class="tier-section tier-5">
      <div class="tier-header">
        <span class="tier-badge">CLASS V</span>
        Threat Level: Catastrophic
        <span class="tier-count">[CLASSIFIED]</span>
      </div>
      <div class="empty-tier">// NO PUBLIC RECORDS — LEVEL 5+ CLEARANCE REQUIRED //</div>
    </div>

    <!-- TIER VI -->
    <div class="tier-section tier-6">
      <div class="tier-header">
        <span class="tier-badge">CLASS VI</span>
        Threat Level: Omega-Class
        <span class="tier-count">[CLASSIFIED]</span>
      </div>
      <div class="empty-tier">// RECORDS SEALED — DIVIDE CLEARANCE REQUIRED //</div>
    </div>

    <!-- TIER VII -->
    <div class="tier-section tier-7">
      <div class="tier-header">
        <span class="tier-badge">CLASS VII</span>
        Threat Level: [DATA EXPUNGED]
        <span class="tier-count">[CLASSIFIED]</span>
      </div>
      <div class="empty-tier">// ACCESS DENIED — EXISTENCE UNCONFIRMED //</div>
    </div>

    <!-- TIER Ω -->
    <div class="tier-section tier-omega">
      <div class="tier-header">
        <span class="tier-badge">CLASS Ω</span>
        Threat Level: The End
        <span class="tier-count">1 ANOMALY</span>
      </div>
      <div class="tier-grid">
        <a href="LD-000.html" class="anomaly-link">▶ LD-000 — [REDACTED]</a>
      </div>
    </div>

    <!-- TIER REDACTED -->
    <div class="tier-section tier-redacted">
      <div class="tier-header">
        <span class="tier-badge">REDACTED</span>
        Threat Level: [DATA EXPUNGED]
        <span class="tier-count">10 ANOMALIES</span>
      </div>
      <div class="tier-grid">
        <a href="LD-001.html" class="anomaly-link">▶ LD-001 — Lucas Devil</a>
        <a href="LD-002.html" class="anomaly-link">▶ LD-002 — Doro</a>
        <a href="LD-015.html" class="anomaly-link">▶ LD-015 — REDACTED</a>
        <a href="LD-043.html" class="anomaly-link">▶ LD-043 — The Crimson Judgement</a>
        <a href="LD-044.html" class="anomaly-link">▶ LD-044 — The Veiled Judgment</a>
        <a href="LD-045.html" class="anomaly-link">▶ LD-045 — DIVA</a>
        <a href="LD-066.html" class="anomaly-link">▶ LD-066 — The Silent Executioner</a>
        <a href="LD-079.html" class="anomaly-link">▶ LD-079 — The Crimson Witness</a>
        <a href="LD-088.html" class="anomaly-link">▶ LD-088 — The Mercy of Life</a>
        <a href="LD-092.html" class="anomaly-link">▶ LD-092 — The Last Wonderer</a>
      </div>
    </div>

    <div class="footer">
      <p>&copy; 2026 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2026-05-30</p>
    </div>

  </div>

</body>
</html>




