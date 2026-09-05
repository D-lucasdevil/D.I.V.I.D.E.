
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Security Personnel</title>
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

    .file-header {
      border: 1px solid #1a4a1a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #05100a 0%, #080808 100%);
    }

    .file-header::before {
      content: '// PERSONNEL FILE //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #4caf50;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #4caf50;
      border-right: 2px solid #4caf50;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #4caf50;
      letter-spacing: 5px;
      text-shadow: 0 0 20px rgba(76,175,80,0.2);
      margin-bottom: 6px;
    }

    .file-designation {
      font-size: 11px;
      color: #555;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 20px;
    }

    .meta-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
    }

    @media (max-width: 600px) { .meta-grid { grid-template-columns: 1fr; } }

    .meta-item {
      display: flex;
      gap: 10px;
      padding: 8px 12px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      font-size: 11px;
    }

    .meta-label { color: #555; letter-spacing: 1px; white-space: nowrap; }
    .meta-value { color: #aaa; letter-spacing: 1px; }
    .meta-value.green { color: #4caf50; }
    .meta-value.red { color: #cc0000; }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #4caf50;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #0a2a0a;
    }

    .content-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #1a4a1a;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      line-height: 1.9;
      color: #888;
    }

    .content-block p { margin-bottom: 8px; }
    .content-block p:last-child { margin-bottom: 0; }

    /* Duty list */
    .duty-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #1a4a1a;
      font-size: 12px;
      color: #888;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .duty-item .arrow { color: #4caf50; flex-shrink: 0; margin-top: 2px; }

    /* Equipment cards */
    .equipment-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .equipment-grid { grid-template-columns: 1fr; } }

    .equipment-card {
      padding: 14px 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-top: 3px solid #1a4a1a;
      font-size: 11px;
      color: #777;
      line-height: 1.7;
    }

    .equipment-card .eq-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #4caf50;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    /* Phrase blocks */
    .phrase-block {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #4caf50;
      padding: 16px 20px;
      margin-bottom: 6px;
      position: relative;
    }

    .phrase-block::before {
      content: '"';
      position: absolute;
      top: -8px; left: 14px;
      background: #080808;
      padding: 0 5px;
      color: #4caf50;
      font-size: 24px;
      font-family: serif;
      line-height: 1;
    }

    .phrase-block p {
      font-size: 12px;
      color: #888;
      font-style: italic;
      line-height: 1.7;
    }

    /* Casualty rate warning */
    .warning-block {
      background: #0d0000;
      border: 1px solid #3a0000;
      border-left: 3px solid #cc0000;
      padding: 14px 18px;
      margin-top: 20px;
      font-size: 11px;
      color: #884444;
      line-height: 1.7;
      letter-spacing: 1px;
    }

    .warning-block strong { color: #cc0000; }

    .footer {
      border-top: 1px solid #1a0000;
      padding-top: 20px;
      margin-top: 30px;
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

    <a href="personnel.html" class="back-link">← RETURN TO PERSONNEL INDEX</a>

    <div class="file-header">
      <div class="file-title">SECURITY PERSONNEL</div>
      <div class="file-designation">Standard Security Operatives — Active Deployment</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">DESIGNATION</span>
          <span class="meta-value green">Standard Security Operative (SSO)</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value green">Level 1 — Level 2</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">NICKNAMES</span>
          <span class="meta-value">"Casuals" / "Blue Coats"</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CASUALTY RATE</span>
          <span class="meta-value red">[REDACTED] — ELEVATED</span>
        </div>
      </div>
    </div>

    <!-- DESCRIPTION -->
    <div class="section-label">// Description //</div>
    <div class="content-block">
      <p>Standard Security Operatives form the backbone of D.I.V.I.D.E.'s containment and facility defense. They're the first line of response against breaches and internal threats — and the last thing an AT-Class subject sees if they run.</p>
      <p>Trained in anomaly-adjacent environments, SSOs are well aware that their job is dangerous. But not <em style="color:#aaa">important</em>. They exist to hold the line until someone more valuable arrives.</p>
    </div>

    <!-- DUTIES -->
    <div class="section-label">// Duties //</div>
    <div class="duty-item"><span class="arrow">▶</span>Guard containment zones, labs, and restricted wings against internal and external threats.</div>
    <div class="duty-item"><span class="arrow">▶</span>Escort personnel, scientists, and AT-Class subjects between designated areas.</div>
    <div class="duty-item"><span class="arrow">▶</span>Neutralize threats until APA or higher-tier units arrive on site.</div>
    <div class="duty-item"><span class="arrow">▶</span>Clean up after failed experiments — or containment accidents.</div>

    <!-- EQUIPMENT -->
    <div class="section-label">// Standard Equipment //</div>
    <div class="equipment-grid">
      <div class="equipment-card">
        <div class="eq-name">Ballistic Armor</div>
        Lightweight anomaly-rated armor. Resistant to standard kinetic threats. Not rated for Class III+ anomalous contact.
      </div>
      <div class="equipment-card">
        <div class="eq-name">Anomaly Suppressor</div>
        Standard-issue anomaly-suppression firearm. Effective against Class I and low Class II entities under controlled conditions.
      </div>
      <div class="equipment-card">
        <div class="eq-name">Panic Injector</div>
        Wrist-locked dual-dose injector. Primary: nerve stabilizer for anomalous psychic exposure. Secondary: self-termination dose.
      </div>
    </div>

    <!-- PHRASES -->
    <div class="section-label">// Common Internal Phrases //</div>

    <div class="phrase-block">
      <p>We're not paid to ask questions — just to shoot if it screams.</p>
    </div>

    <div class="phrase-block">
      <p>If you see something glowing, shoot it. If it laughs, run.</p>
    </div>

    <div class="phrase-block">
      <p>Casualty rate? Comes with the coat.</p>
    </div>

    <div class="warning-block">
      <strong>INTERNAL NOTE:</strong> SSO life expectancy during a Class III+ containment breach is significantly below D.I.V.I.D.E. standard minimums. Recruitment pipelines are maintained accordingly. Replacements are pre-processed.
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
