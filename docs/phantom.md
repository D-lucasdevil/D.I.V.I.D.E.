
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — PHANTOM DIVISION</title>
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
      background-color: #080820;
      color: #7777cc;
      text-align: center;
      padding: 6px;
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      border-bottom: 1px solid #2a2a6a;
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
    .back-link:hover { color: #9c9cff; }

    .file-header {
      border: 1px solid #2a2a6a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #080815 0%, #080808 100%);
    }

    .file-header::before {
      content: '// CONTAINMENT UNIT — LEVEL 4+ //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #7777cc;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #9c9cff;
      border-right: 2px solid #9c9cff;
    }

    .file-codename {
      font-size: 10px;
      color: #7777cc;
      letter-spacing: 5px;
      margin-bottom: 6px;
      text-transform: uppercase;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 42px;
      font-weight: 700;
      color: #9c9cff;
      letter-spacing: 5px;
      text-shadow: 0 0 20px rgba(150,150,255,0.2);
      margin-bottom: 4px;
    }

    .file-subtitle {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      color: #7777cc;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 20px;
      line-height: 1.5;
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
    .meta-value.blue { color: #9c9cff; }
    .meta-value.green { color: #4caf50; }
    .meta-value.orange { color: #e65100; }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #7777cc;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a1a3a;
    }

    .content-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #2a2a6a;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      line-height: 1.9;
      color: #888;
    }

    .content-block p { margin-bottom: 8px; }
    .content-block p:last-child { margin-bottom: 0; }

    /* Tagline */
    .tagline {
      text-align: center;
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      font-weight: 600;
      color: #7777cc;
      letter-spacing: 3px;
      text-transform: uppercase;
      padding: 12px;
      border: 1px solid #1a1a3a;
      background: #080815;
      margin-bottom: 8px;
      font-style: italic;
    }

    /* Duty list */
    .duty-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #2a2a6a;
      font-size: 12px;
      color: #888;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .duty-item .arrow { color: #9c9cff; flex-shrink: 0; margin-top: 2px; }

    /* Equipment cards */
    .equipment-card {
      display: flex;
      align-items: flex-start;
      gap: 14px;
      padding: 14px 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #2a2a6a;
      margin-bottom: 6px;
      font-size: 12px;
      color: #777;
      line-height: 1.7;
      transition: border-left-color 0.2s, background 0.2s;
    }

    .equipment-card:hover {
      border-left-color: #9c9cff;
      background: #0a0a18;
    }

    .equipment-card .eq-icon {
      font-size: 16px;
      flex-shrink: 0;
      margin-top: 2px;
    }

    .equipment-card .eq-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #9c9cff;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 4px;
    }

    /* Strengths vs Limitations */
    .comparison-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 8px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .comparison-grid { grid-template-columns: 1fr; } }

    .strength-card {
      padding: 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-top: 3px solid #4caf50;
      font-size: 12px;
      color: #777;
      line-height: 1.7;
    }

    .strength-card .sc-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #4caf50;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 10px;
    }

    .limitation-card {
      padding: 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-top: 3px solid #cc4444;
      font-size: 12px;
      color: #777;
      line-height: 1.7;
    }

    .limitation-card .lc-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #cc4444;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 10px;
    }

    .check-item {
      display: flex;
      align-items: flex-start;
      gap: 8px;
      margin-bottom: 6px;
      font-size: 11px;
    }

    .check-item .check { color: #4caf50; flex-shrink: 0; }
    .check-item .cross { color: #cc4444; flex-shrink: 0; }

    /* Force comparison */
    .force-compare {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .force-compare { grid-template-columns: 1fr; } }

    .force-card {
      padding: 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      text-align: center;
      font-size: 11px;
      color: #666;
    }

    .force-card .fc-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      font-weight: 700;
      letter-spacing: 2px;
      margin-bottom: 4px;
    }

    .force-card .fc-role {
      font-size: 10px;
      letter-spacing: 1px;
      color: #444;
      text-transform: uppercase;
    }

    .force-card.apa .fc-name { color: #4fc3f7; }
    .force-card.berserk .fc-name { color: #f44336; }
    .force-card.phantom .fc-name { color: #9c9cff; border: 1px solid #2a2a6a; padding: 14px; background: #080815; }

    /* Quote blocks */
    .quote-block {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #7777cc;
      padding: 14px 20px;
      margin-bottom: 6px;
      position: relative;
    }

    .quote-block::before {
      content: '"';
      position: absolute;
      top: -8px; left: 14px;
      background: #080808;
      padding: 0 5px;
      color: #7777cc;
      font-size: 24px;
      font-family: serif;
      line-height: 1;
    }

    .quote-block p {
      font-size: 13px;
      color: #7777aa;
      font-style: italic;
      line-height: 1.7;
      letter-spacing: 1px;
    }

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
    ⚠ PHANTOM DIVISION — CONTAINMENT FIRST PROTOCOL — LEVEL 4+ CLEARANCE REQUIRED ⚠
  </div>

  <div class="container">

    <a href="task-force-list.html" class="back-link">← RETURN TO TASK FORCE INDEX</a>

    <div class="file-header">
      <div class="file-codename">Unit Designation: PHANTOM DIVISION</div>
      <div class="file-title">PHANTOM</div>
      <div class="file-subtitle">"The Net" / "Glass Box Crew" / "The Calm Hand"<br>Strategic Anomaly Suppression & Containment Unit</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">DESIGNATION</span>
          <span class="meta-value blue">Strategic Containment Unit</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value blue">Level 4+</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">PRIMARY ROLE</span>
          <span class="meta-value green">Containment — Preservation — Stabilization</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">COMBAT CLASS</span>
          <span class="meta-value orange">Lowest of All Active Units</span>
        </div>
      </div>
    </div>

    <!-- DESCRIPTION -->
    <div class="section-label">// Unit Description //</div>
    <div class="content-block">
      <p>Phantom Division is a specialized taskforce focused solely on the containment and stabilization of anomalies — deployed when brute force is unnecessary, and the situation still allows for recovery, study, or suppression.</p>
      <p>While lacking the raw firepower of APA or B.E.R.S.E.R.K., Phantom Division excels in tactical precision, anomaly analysis, and adaptive field engineering. Their success is measured not in body count, but in how little gets destroyed.</p>
    </div>

    <div class="tagline">"If APA is the scalpel and B.E.R.S.E.R.K. is the warhammer — Phantom is the net. They catch what others would rather crush."</div>

    <!-- FORCE POSITION -->
    <div class="section-label">// Force Comparison //</div>
    <div class="force-compare">
      <div class="force-card apa">
        <div class="fc-name">A.P.A.</div>
        <div class="fc-role">The Scalpel<br>Clears Continents</div>
      </div>
      <div class="force-card berserk">
        <div class="fc-name">B.E.R.S.E.R.K.</div>
        <div class="fc-role">The Warhammer<br>Clears Cities</div>
      </div>
      <div class="force-card phantom">
        <div class="fc-name">PHANTOM</div>
        <div class="fc-role">The Net<br>Catches What Others Crush</div>
      </div>
    </div>

    <!-- DUTIES -->
    <div class="section-label">// Operational Duties //</div>
    <div class="duty-item"><span class="arrow">▶</span>Primary anomaly containment operations in survivable, non-expendable zones.</div>
    <div class="duty-item"><span class="arrow">▶</span>Establishing mobile and long-term suppression fields around active anomaly sites.</div>
    <div class="duty-item"><span class="arrow">▶</span>Stabilizing breaches in populated or research-critical areas where collateral damage is unacceptable.</div>
    <div class="duty-item"><span class="arrow">▶</span>Supporting recovery teams and executing pre-extraction lockdowns.</div>
    <div class="duty-item"><span class="arrow">▶</span>Hand-off to higher-tier units if escalation occurs beyond containment capacity.</div>

    <!-- EQUIPMENT -->
    <div class="section-label">// Equipment //</div>

    <div class="equipment-card">
      <div class="eq-icon">⬡</div>
      <div>
        <div class="eq-name">Containment Packs</div>
        Deployable stasis generators, field cages, and spatial anchors. Configurable for rapid deployment in unpredictable environments.
      </div>
    </div>

    <div class="equipment-card">
      <div class="eq-icon">◈</div>
      <div>
        <div class="eq-name">Anomaly Classifiers</div>
        Real-time scanners for threat level assessment and interaction mapping. Provides continuous data during active containment operations.
      </div>
    </div>

    <div class="equipment-card">
      <div class="eq-icon">⬢</div>
      <div>
        <div class="eq-name">Modular Restraint Gear</div>
        Configurable restraint systems compatible with biological, energy-based, and metaphysical entity types. Adaptive to unknown anomaly classifications.
      </div>
    </div>

    <div class="equipment-card">
      <div class="eq-icon">◉</div>
      <div>
        <div class="eq-name">Cognition-Shielded Suits</div>
        Defends against subtle memetic and infohazard leaks during close-range containment operations. Essential when handling cognitohazardous entities.
      </div>
    </div>

    <div class="equipment-card">
      <div class="eq-icon">◌</div>
      <div>
        <div class="eq-name">Comms Disruptors</div>
        Prevents anomalies from transmitting or interacting with external systems during active containment windows.
      </div>
    </div>

    <!-- STRENGTHS & LIMITATIONS -->
    <div class="section-label">// Strengths & Limitations //</div>
    <div class="comparison-grid">
      <div class="strength-card">
        <div class="sc-title">✓ Strengths</div>
        <div class="check-item"><span class="check">✓</span>Rapid non-lethal neutralization methods</div>
        <div class="check-item"><span class="check">✓</span>High adaptability to emerging threat types</div>
        <div class="check-item"><span class="check">✓</span>Protocol-first decision making focused on preservation</div>
        <div class="check-item"><span class="check">✓</span>Ideal for first-response and low-casualty environments</div>
      </div>
      <div class="limitation-card">
        <div class="lc-title">✕ Limitations</div>
        <div class="check-item"><span class="cross">✕</span>Lowest combat strength of all active D.I.V.I.D.E. squads</div>
        <div class="check-item"><span class="cross">✕</span>Vulnerable to hostile anomalies without support units</div>
        <div class="check-item"><span class="cross">✕</span>Must be reinforced or replaced if containment fails</div>
        <div class="check-item"><span class="cross">✕</span>Not suitable for annihilation-level threats</div>
      </div>
    </div>

    <!-- QUOTES -->
    <div class="section-label">// Internal Unit Phrases //</div>

    <div class="quote-block">
      <p>You destroy what you don't understand. We don't have that luxury.</p>
    </div>

    <div class="quote-block">
      <p>We don't run toward the anomaly. We wrap it.</p>
    </div>

    <div class="quote-block">
      <p>When the world can't afford another crater… they call us.</p>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
