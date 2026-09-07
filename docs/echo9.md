
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — ECHO-9</title>
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
      background-color: #0a1a0a;
      color: #4caf50;
      text-align: center;
      padding: 6px;
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      border-bottom: 1px solid #1a4a1a;
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
    .back-link:hover { color: #4caf50; }

    .file-header {
      border: 1px solid #1a4a1a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #050f05 0%, #080808 100%);
    }

    .file-header::before {
      content: '// TASK FORCE — LEVEL 4+ //';
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

    .file-codename {
      font-size: 10px;
      color: #4caf50;
      letter-spacing: 5px;
      margin-bottom: 6px;
      text-transform: uppercase;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 42px;
      font-weight: 700;
      color: #7dc87f;
      letter-spacing: 6px;
      text-shadow: 0 0 20px rgba(76,175,80,0.2);
      margin-bottom: 4px;
    }

    .file-subtitle {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      color: #4caf50;
      letter-spacing: 3px;
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
    .meta-value.orange { color: #e65100; }

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
      grid-template-columns: 1fr 1fr;
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
      transition: border-top-color 0.2s, background 0.2s;
    }

    .equipment-card:hover {
      border-top-color: #4caf50;
      background: #0a150a;
    }

    .equipment-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #4caf50;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    /* Quote blocks */
    .quote-block {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #4caf50;
      padding: 16px 20px;
      margin-bottom: 6px;
      position: relative;
    }

    .quote-block::before {
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

    .quote-block p {
      font-size: 13px;
      color: #7dc87f;
      font-style: italic;
      line-height: 1.7;
      letter-spacing: 1px;
    }

    /* Classified notice */
    .classified-notice {
      background: #050f05;
      border: 1px solid #0a2a0a;
      border-left: 3px solid #4caf50;
      padding: 14px 18px;
      margin-top: 20px;
      font-size: 11px;
      color: #3a6a3a;
      line-height: 1.7;
      letter-spacing: 1px;
    }

    .classified-notice strong { color: #4caf50; }

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
    ⚠ CLASSIFIED — ECHO-9 OPERATIONS — ZERO DISCLOSURE PROTOCOL — LEVEL 4+ ONLY ⚠
  </div>

  <div class="container">

    <a href="task-force-list.html" class="back-link">← RETURN TO TASK FORCE INDEX</a>

    <div class="file-header">
      <div class="file-codename">Unit Designation: ECHO-9</div>
      <div class="file-title">ECHO-9</div>
      <div class="file-subtitle">"Phantom Sweepers" — Rapid Suppression & Recon Unit</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">NICKNAMES</span>
          <span class="meta-value green">"Phantom Sweepers" / "Ghosts in the Halls"</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">Level 4+</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">SPECIALIZATION</span>
          <span class="meta-value green">Infiltration / Suppression / Info-Denial</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">VISIBILITY</span>
          <span class="meta-value orange">Zero — By Design</span>
        </div>
      </div>
    </div>

    <!-- DESCRIPTION -->
    <div class="section-label">// Unit Description //</div>
    <div class="content-block">
      <p>Echo-9 is a highly classified rapid response team deployed when silence, speed, and zero survivors are required. Experts in infiltration, precision anomaly suppression, and information-denial operations. When Echo-9 is dispatched, not even the security cameras survive.</p>
      <p>They are the shadows between screams — the team sent in <em style="color:#aaa">before</em> the breach is public. By the time other personnel hear the alarms, Echo-9 is already gone. Their existence is not acknowledged in standard D.I.V.I.D.E. operational records.</p>
    </div>

    <!-- DUTIES -->
    <div class="section-label">// Operational Duties //</div>
    <div class="duty-item"><span class="arrow">▶</span>Pre-emptive neutralization of anomalies with potential to leak beyond containment zones.</div>
    <div class="duty-item"><span class="arrow">▶</span>Covert clean-up of internal insubordination, espionage, or unauthorized information disclosure.</div>
    <div class="duty-item"><span class="arrow">▶</span>Anomaly recovery in populated or politically sensitive areas requiring zero civilian awareness.</div>
    <div class="duty-item"><span class="arrow">▶</span>Blacksite purges and off-the-books termination orders at D.I.V.I.D.E. command discretion.</div>

    <!-- EQUIPMENT -->
    <div class="section-label">// Standard Equipment //</div>
    <div class="equipment-grid">
      <div class="equipment-card">
        <div class="equipment-name">Cloaking Harness</div>
        Prototype-class active optical camouflage. Renders operatives effectively invisible under standard and anomaly-adjacent lighting conditions. Battery life classified.
      </div>
      <div class="equipment-card">
        <div class="equipment-name">EM-Refracting Armor</div>
        Electromagnetic-refracting plating that defeats standard sensor arrays, thermal imaging, and certain anomalous detection methods simultaneously.
      </div>
      <div class="equipment-card">
        <div class="equipment-name">Silenced Arsenal</div>
        Custom silenced weaponry built specifically for anomaly penetration. Ammunition types classified. Effective against entities up to Class III under standard deployment conditions.
      </div>
      <div class="equipment-card">
        <div class="equipment-name">Neural-Filter Helmets</div>
        Prevents visual and auditory cognitohazard corruption. Allows operatives to engage with Class II-III entities that would otherwise induce immediate psychological collapse.
      </div>
    </div>

    <!-- QUOTES -->
    <div class="section-label">// Internal Unit Phrases //</div>

    <div class="quote-block">
      <p>If you hear us, we failed.</p>
    </div>

    <div class="quote-block">
      <p>Echo-9 doesn't talk. We erase.</p>
    </div>

    <div class="quote-block">
      <p>We aren't the backup. We're the cutoff.</p>
    </div>

    <div class="classified-notice">
      <strong>OPERATIONAL NOTICE:</strong> Echo-9 deployment records are not stored in standard D.I.V.I.D.E. databases. Mission logs are purged upon completion. Personnel rosters are classified above Level 4. If you are reading this file, you have been granted access on a need-to-know basis only.
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
