
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — S.O.R.A.D.</title>
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
      background-color: #020d18;
      color: #00bcd4;
      text-align: center;
      padding: 6px;
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      border-bottom: 1px solid #004a5a;
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
    .back-link:hover { color: #00bcd4; }

    .file-header {
      border: 1px solid #004a5a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #020d18 0%, #080808 100%);
    }

    .file-header::before {
      content: '// DEEP-SEA OPERATIONS — LEVEL 4+ //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #00bcd4;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #00bcd4;
      border-right: 2px solid #00bcd4;
    }

    .file-codename {
      font-size: 10px;
      color: #00bcd4;
      letter-spacing: 5px;
      margin-bottom: 6px;
      text-transform: uppercase;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 42px;
      font-weight: 700;
      color: #4dd6e8;
      letter-spacing: 6px;
      text-shadow: 0 0 20px rgba(0,188,212,0.3);
      margin-bottom: 4px;
    }

    .file-subtitle {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      color: #00bcd4;
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
    .meta-value.teal { color: #00bcd4; }
    .meta-value.red { color: #cc0000; }
    .meta-value.orange { color: #e65100; }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #00bcd4;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #003a4a;
    }

    .content-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #004a5a;
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
      border-left: 3px solid #004a5a;
      font-size: 12px;
      color: #888;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .duty-item .arrow { color: #00bcd4; flex-shrink: 0; margin-top: 2px; }

    /* Equipment cards */
    .equipment-card {
      padding: 18px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-top: 3px solid #004a5a;
      margin-bottom: 8px;
      transition: border-top-color 0.2s, background 0.2s;
    }

    .equipment-card:hover {
      border-top-color: #00bcd4;
      background: #080d12;
    }

    .equipment-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 15px;
      font-weight: 700;
      color: #00bcd4;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 4px;
    }

    .equipment-code {
      font-size: 9px;
      color: #004a5a;
      letter-spacing: 3px;
      margin-bottom: 10px;
      text-transform: uppercase;
    }

    .equipment-body {
      font-size: 12px;
      color: #777;
      line-height: 1.8;
    }

    /* Deployment records */
    .deployment-card {
      display: flex;
      align-items: flex-start;
      gap: 16px;
      padding: 14px 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #004a5a;
      margin-bottom: 6px;
      transition: border-left-color 0.2s;
    }

    .deployment-card:hover { border-left-color: #00bcd4; }

    .dep-id {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #00bcd4;
      letter-spacing: 2px;
      min-width: 100px;
      flex-shrink: 0;
    }

    .dep-body {
      font-size: 12px;
      color: #777;
      line-height: 1.7;
    }

    .dep-status {
      display: inline-block;
      font-size: 9px;
      letter-spacing: 2px;
      padding: 2px 8px;
      border: 1px solid;
      text-transform: uppercase;
      margin-top: 6px;
    }

    .dep-status.destroyed { color: #cc0000; border-color: #3a0000; }
    .dep-status.recovered { color: #4caf50; border-color: #1a4a1a; }
    .dep-status.redacted { color: #555; border-color: #333; }

    /* Depth pressure bar */
    .depth-display {
      background: #020d18;
      border: 1px solid #004a5a;
      padding: 16px 20px;
      margin-bottom: 8px;
      display: flex;
      align-items: center;
      gap: 20px;
    }

    .depth-label {
      font-size: 10px;
      color: #004a5a;
      letter-spacing: 3px;
      text-transform: uppercase;
      white-space: nowrap;
    }

    .depth-bar {
      flex: 1;
      height: 4px;
      background: #0a2a3a;
      position: relative;
      border-radius: 2px;
    }

    .depth-bar::after {
      content: '';
      position: absolute;
      left: 0; top: 0;
      height: 100%;
      width: 85%;
      background: linear-gradient(90deg, #00bcd4, #006080);
      border-radius: 2px;
    }

    .depth-value {
      font-family: 'Rajdhani', sans-serif;
      font-size: 18px;
      font-weight: 700;
      color: #00bcd4;
      letter-spacing: 2px;
      white-space: nowrap;
    }

    /* Clearance warning */
    .clearance-warning {
      background: #020d18;
      border: 1px solid #004a5a;
      border-left: 3px solid #00bcd4;
      padding: 14px 18px;
      margin-top: 20px;
      font-size: 11px;
      color: #3a7a8a;
      line-height: 1.7;
      letter-spacing: 0.5px;
    }

    .clearance-warning strong { color: #00bcd4; }

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
    ⚠ SORAD — DEEP-SEA OPERATIONS — LEVEL 4+ CLEARANCE REQUIRED — OUTPOST-Δ9 ⚠
  </div>

  <div class="container">

    <a href="task-force-list.html" class="back-link">← RETURN TO TASK FORCE INDEX</a>

    <div class="file-header">
      <div class="file-codename">Unit Designation: S.O.R.A.D.</div>
      <div class="file-title">S.O.R.A.D.</div>
      <div class="file-subtitle">Special Oceanic Retrieval and Analysis Division<br>Specialized Deep-Sea Anomaly Containment & Surveillance Unit</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">BASE</span>
          <span class="meta-value teal">Blackridge Naval Sub-Sector / Outpost-Δ9</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">DIVIDE Level 4+</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">SPECIALIZATION</span>
          <span class="meta-value teal">Oceanic Anomaly Detection & Retrieval</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">DEPLOYMENT TIER</span>
          <span class="meta-value orange">Critical-Level — Aquatic Phenomena</span>
        </div>
      </div>
    </div>

    <!-- OVERVIEW -->
    <div class="section-label">// Overview //</div>
    <div class="content-block">
      <p>SORAD is a marine-specialized task force formed in response to deep-ocean Pulse signatures and aquatic anomaly activity. Operating out of Blackridge Naval Sub-Sector and deep-sea facility Outpost-Δ9, SORAD is responsible for detection, retrieval, surveillance, and containment of any anomaly or artifact that emerges, manifests, or pulses within oceanic zones.</p>
      <p>Due to the increasing number of Pulse anomalies near abyssal zones, trench systems, and continental shelves, SORAD's deployment is considered critical-level response whenever underwater phenomena are detected.</p>
    </div>

    <div class="depth-display">
      <div class="depth-label">Max Op Depth</div>
      <div class="depth-bar"></div>
      <div class="depth-value">10,000M+</div>
    </div>

    <!-- PRIMARY FUNCTIONS -->
    <div class="section-label">// Primary Functions //</div>
    <div class="duty-item"><span class="arrow">▶</span>Track and investigate underwater Pulse activity across abyssal zones, trench systems, and continental shelves.</div>
    <div class="duty-item"><span class="arrow">▶</span>Secure and contain anomalies that breach into marine ecosystems or coastal areas.</div>
    <div class="duty-item"><span class="arrow">▶</span>Maintain surveillance on known ocean-based anomalies and designated dead zones.</div>
    <div class="duty-item"><span class="arrow">▶</span>Retrieve artifact-class or biological anomalies from extreme ocean depths.</div>
    <div class="duty-item"><span class="arrow">▶</span>Operate autonomous submersibles and combat-modified deep-sea suits in hostile pressure environments.</div>

    <!-- EQUIPMENT -->
    <div class="section-label">// Notable Equipment //</div>

    <div class="equipment-card">
      <div class="equipment-name">A.D.R.E.N.A Suits</div>
      <div class="equipment-code">Abyssal-Density Reinforced Environmental Navigation Armor</div>
      <div class="equipment-body">Allows operatives to survive depths exceeding 10,000 meters for short durations. Fully pressurized with reinforced armor plating and limited pulse shielding. The only known suit rated for direct contact with abyssal-class anomalies under extreme pressure conditions.</div>
    </div>

    <div class="equipment-card">
      <div class="equipment-name">Nautilus-Class Retrieval Subs</div>
      <div class="equipment-code">Deep-Pressure Extraction Vehicles — Silent Insertion Rated</div>
      <div class="equipment-body">Designed for silent insertion and anomaly extraction in deep-pressure zones. Equipped with long-range sensor arrays, Pulse detectors, and full containment pods. Capable of operating in total communications blackout at maximum depth.</div>
    </div>

    <div class="equipment-card">
      <div class="equipment-name">Tidebreaker Pulse Anchors</div>
      <div class="equipment-code">Aquatic Pulse Stabilization Arrays</div>
      <div class="equipment-body">Deployed around potential breach zones. Stabilizes Pulse energy fields and prevents aquatic anomalies from surfacing or migrating toward populated coastal areas. Anchors are self-maintaining once deployed and can operate indefinitely at depth.</div>
    </div>

    <!-- DEPLOYMENTS -->
    <div class="section-label">// Known Deployments //</div>

    <div class="deployment-card">
      <div class="dep-id">LD-037.5</div>
      <div class="dep-body">
        "The Drowned Pulse" — Active engagement with aquatic Pulse anomaly in abyssal zone. Full operational details classified above standard access.
        <div><span class="dep-status destroyed">Presumed Destroyed</span></div>
      </div>
    </div>

    <div class="deployment-card">
      <div class="dep-id">TRENCH-██</div>
      <div class="dep-body">
        Deep Trench Signal Echo ██ — Artifact recovery operation at extreme depth. One metallic anomaly successfully retrieved and transferred to containment.
        <div><span class="dep-status recovered">1 Artifact Recovered</span></div>
      </div>
    </div>

    <div class="deployment-card">
      <div class="dep-id">COASTAL-██</div>
      <div class="dep-body">
        Coastal Interference Pulse ██ — [REDACTED] neutralized near populated coastal zone. Civilian awareness: zero. Operation classified under info-denial protocol.
        <div><span class="dep-status redacted">[REDACTED] Neutralized</span></div>
      </div>
    </div>

    <!-- CLEARANCE NOTE -->
    <div class="clearance-warning">
      <strong>CLEARANCE NOTICE:</strong> Only DIVIDE Level 4+ personnel or those with marine specialization clearance are permitted to receive unredacted SORAD reports. Any breach of confidentiality will result in full mind-scrub protocol and deep-black disciplinary action. No exceptions. No appeals.
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-06-24</p>
    </div>

  </div>

</body>
</html>
