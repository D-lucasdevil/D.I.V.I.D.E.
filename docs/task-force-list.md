
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Task Force Profiles</title>
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
      border: 1px solid #3a0000;
      padding: 30px;
      margin-bottom: 30px;
      position: relative;
      background: linear-gradient(180deg, #0f0000 0%, #080808 100%);
    }

    .file-header::before {
      content: '// CLASSIFIED //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #8b0000;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #8b0000;
      border-right: 2px solid #8b0000;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #cc0000;
      letter-spacing: 6px;
      text-shadow: 0 0 20px rgba(200,0,0,0.4);
      margin-bottom: 6px;
    }

    .file-designation {
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

    .status-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 16px;
      background: #0d0d0d;
      border: 1px solid #1a0000;
      margin-bottom: 30px;
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
      margin-bottom: 14px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a0000;
    }

    /* Task force cards */
    .taskforce-card {
      display: flex;
      align-items: stretch;
      gap: 0;
      margin-bottom: 8px;
      border: 1px solid #1a1a1a;
      text-decoration: none;
      transition: all 0.2s ease;
      position: relative;
      overflow: hidden;
    }

    .taskforce-card::after {
      content: '▶';
      position: absolute;
      right: 16px;
      top: 50%;
      transform: translateY(-50%);
      color: #2a2a2a;
      font-size: 12px;
      transition: color 0.2s;
    }

    .taskforce-card:hover::after { color: #cc0000; }

    .taskforce-card:hover {
      border-color: #3a0000;
      background: #0d0000;
    }

    /* Color accent bar */
    .card-accent {
      width: 4px;
      flex-shrink: 0;
    }

    .card-body {
      flex: 1;
      padding: 18px 48px 18px 20px;
    }

    .card-id {
      font-size: 10px;
      letter-spacing: 3px;
      margin-bottom: 6px;
      text-transform: uppercase;
    }

    .card-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 20px;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 6px;
      line-height: 1.2;
    }

    .card-role {
      font-size: 11px;
      color: #555;
      letter-spacing: 1px;
      margin-bottom: 10px;
    }

    .card-tags {
      display: flex;
      gap: 6px;
      flex-wrap: wrap;
    }

    .card-tag {
      font-size: 9px;
      letter-spacing: 2px;
      padding: 2px 8px;
      border: 1px solid;
      text-transform: uppercase;
    }

    /* APA — Blue */
    .tf-apa .card-accent { background: #4fc3f7; }
    .tf-apa .card-id { color: #4fc3f7; }
    .tf-apa .card-name { color: #7dd5f7; }
    .tf-apa .card-tag { color: #4fc3f7; border-color: #1a4a6a; }
    .tf-apa:hover { border-color: #1a4a6a; }

    /* ECHO-9 — Green */
    .tf-echo .card-accent { background: #4caf50; }
    .tf-echo .card-id { color: #4caf50; }
    .tf-echo .card-name { color: #7dc87f; }
    .tf-echo .card-tag { color: #4caf50; border-color: #1a4a1a; }
    .tf-echo:hover { border-color: #1a4a1a; }

    /* BERSERK — Red */
    .tf-berserk .card-accent { background: #f44336; }
    .tf-berserk .card-id { color: #f44336; }
    .tf-berserk .card-name { color: #f77; }
    .tf-berserk .card-tag { color: #f44336; border-color: #4a0000; }
    .tf-berserk:hover { border-color: #3a0000; }

    /* PHANTOM — Purple */
    .tf-phantom .card-accent { background: #9c27b0; }
    .tf-phantom .card-id { color: #9c27b0; }
    .tf-phantom .card-name { color: #ce7adb; }
    .tf-phantom .card-tag { color: #9c27b0; border-color: #3a0a4a; }
    .tf-phantom:hover { border-color: #3a0a4a; }

    /* SORAD — Teal */
    .tf-sorad .card-accent { background: #00bcd4; }
    .tf-sorad .card-id { color: #00bcd4; }
    .tf-sorad .card-name { color: #4dd6e8; }
    .tf-sorad .card-tag { color: #00bcd4; border-color: #004a5a; }
    .tf-sorad:hover { border-color: #004a5a; }

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

    <a href="index.html" class="back-link">← RETURN TO DATABASE INDEX</a>

    <div class="file-header">
      <div class="file-title">TASK FORCE PROFILES</div>
      <div class="file-designation">D.I.V.I.D.E. Special Operations — Personnel & Unit Registry</div>
      <div class="clearance-badge">Clearance Level 1+ Required</div>
    </div>

    <div class="status-bar">
      <span><span class="status-dot"></span>DATABASE ONLINE</span>
      <span>ACTIVE TASK FORCES: 5</span>
      <span>CLASSIFIED UNITS: [REDACTED]</span>
    </div>

    <div class="section-label">// Registered Task Force Units //</div>

    <!-- APA -->
    <a href="apa.html" class="taskforce-card tf-apa">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">UNIT DESIGNATION: A.P.A.</div>
        <div class="card-name">Anomaly Pursuit Agent</div>
        <div class="card-role">Adaptive Protocol Apex — Elite Anomaly Containment & Neutralization</div>
        <div class="card-tags">
          <span class="card-tag">Elite</span>
          <span class="card-tag">Adaptive</span>
          <span class="card-tag">Level 6+</span>
          <span class="card-tag">Last Resort</span>
        </div>
      </div>
    </a>

    <!-- ECHO-9 -->
    <a href="echo9.html" class="taskforce-card tf-echo">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">UNIT DESIGNATION: ECHO-9</div>
        <div class="card-name">Echo Unit-9</div>
        <div class="card-role">Security Subdivision — Anomaly Threat Response & Facility Protection</div>
        <div class="card-tags">
          <span class="card-tag">Security</span>
          <span class="card-tag">Response</span>
          <span class="card-tag">Level 3+</span>
          <span class="card-tag">Facility</span>
        </div>
      </div>
    </a>

    <!-- BERSERK -->
    <a href="viking.html" class="taskforce-card tf-berserk">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">UNIT DESIGNATION: B.E.R.S.E.R.K.</div>
        <div class="card-name">Bio-Enhanced Rapid Strike & Extraction Recon Killteam</div>
        <div class="card-role">High-Fatality Anomaly Annihilation — Tactical Assault Unit</div>
        <div class="card-tags">
          <span class="card-tag">Warhammers</span>
          <span class="card-tag">Last Door</span>
          <span class="card-tag">Level 5+</span>
          <span class="card-tag">Expendable Zone</span>
        </div>
      </div>
    </a>

    <!-- PHANTOM -->
    <a href="phantom.html" class="taskforce-card tf-phantom">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">UNIT DESIGNATION: PHANTOM</div>
        <div class="card-name">Phantom Squad</div>
        <div class="card-role">Stealth Operations — Covert Anomaly Tracking & Elimination</div>
        <div class="card-tags">
          <span class="card-tag">Stealth</span>
          <span class="card-tag">Covert</span>
          <span class="card-tag">Level 4+</span>
          <span class="card-tag">Ghost Ops</span>
        </div>
      </div>
    </a>

    <!-- SORAD -->
    <a href="SORAD.html" class="taskforce-card tf-sorad">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">UNIT DESIGNATION: S.O.R.A.D.</div>
        <div class="card-name">Special Oceanic Retrieval and Analysis Division</div>
        <div class="card-role">Deep Sea Operations — Aquatic Anomaly Recovery & Containment</div>
        <div class="card-tags">
          <span class="card-tag">Oceanic</span>
          <span class="card-tag">Retrieval</span>
          <span class="card-tag">Level 3+</span>
          <span class="card-tag">Deep Operations</span>
        </div>
      </div>
    </a>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
