
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Special Individuals</title>
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

    /* Header — purple for special individuals */
    .file-header {
      border: 1px solid #3a0a4a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #0a050f 0%, #080808 100%);
    }

    .file-header::before {
      content: '// RESTRICTED FILE //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #9c27b0;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #9c27b0;
      border-right: 2px solid #9c27b0;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #9c27b0;
      letter-spacing: 5px;
      text-shadow: 0 0 20px rgba(156,39,176,0.3);
      margin-bottom: 6px;
    }

    .file-designation {
      font-size: 11px;
      color: #555;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 20px;
    }

    /* Level 7 restriction banner */
    .restriction-banner {
      background: #0d000d;
      border: 1px solid #9c27b0;
      padding: 20px 24px;
      margin-bottom: 30px;
      position: relative;
      text-align: center;
    }

    .restriction-banner::before {
      content: '⚠';
      position: absolute;
      top: -12px; left: 50%;
      transform: translateX(-50%);
      background: #080808;
      padding: 0 10px;
      color: #9c27b0;
      font-size: 16px;
    }

    .restriction-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 18px;
      font-weight: 700;
      color: #9c27b0;
      letter-spacing: 4px;
      text-transform: uppercase;
      margin-bottom: 8px;
      text-shadow: 0 0 10px rgba(156,39,176,0.3);
    }

    .restriction-text {
      font-size: 11px;
      color: #7a3a8a;
      letter-spacing: 2px;
      line-height: 1.7;
    }

    .restriction-badge {
      display: inline-block;
      margin-top: 12px;
      border: 1px solid #9c27b0;
      color: #9c27b0;
      font-size: 10px;
      letter-spacing: 4px;
      padding: 4px 16px;
      text-transform: uppercase;
    }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #9c27b0;
      text-transform: uppercase;
      margin-bottom: 14px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a0a2a;
    }

    /* Individual profile cards */
    .profile-card {
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

    .profile-card::after {
      content: '▶';
      position: absolute;
      right: 16px;
      top: 50%;
      transform: translateY(-50%);
      color: #2a2a2a;
      font-size: 12px;
      transition: color 0.2s;
    }

    .profile-card:hover::after { color: #9c27b0; }
    .profile-card:hover {
      border-color: #3a0a4a;
      background: #0d000d;
    }

    .card-accent {
      width: 4px;
      flex-shrink: 0;
      background: #9c27b0;
    }

    .card-body {
      flex: 1;
      padding: 18px 48px 18px 20px;
    }

    .card-id {
      font-size: 10px;
      letter-spacing: 3px;
      color: #9c27b0;
      margin-bottom: 5px;
      text-transform: uppercase;
    }

    .card-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 20px;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 5px;
      color: #ce7adb;
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
      border: 1px solid #3a0a4a;
      color: #9c27b0;
      text-transform: uppercase;
    }

    /* More files redacted notice */
    .redacted-notice {
      background: #080808;
      border: 1px dashed #2a0a3a;
      padding: 16px 20px;
      margin-top: 8px;
      font-size: 11px;
      color: #3a1a4a;
      letter-spacing: 2px;
      text-align: center;
      line-height: 1.7;
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
    ⚠ RESTRICTED ACCESS — LEVEL 7 CLEARANCE REQUIRED — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="container">

    <a href="personnel.html" class="back-link">← RETURN TO PERSONNEL INDEX</a>

    <div class="file-header">
      <div class="file-title">SPECIAL INDIVIDUALS</div>
      <div class="file-designation">D.I.V.I.D.E. — Personnel of Extraordinary Classification</div>
    </div>

    <!-- RESTRICTION BANNER -->
    <div class="restriction-banner">
      <div class="restriction-title">Access Restricted</div>
      <div class="restriction-text">
        This section contains files on individuals whose classification falls outside standard personnel categories.<br>
        Anomalous origin, extreme threat potential, or classified operational history may apply.
      </div>
      <div class="restriction-badge">Level 7 Clearance Required</div>
    </div>

    <div class="section-label">// Accessible Profiles — Partial Disclosure //</div>

    <!-- Dr. Connor -->
    <a href="connor.html" class="profile-card">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">PROFILE — RESEARCHER DIVISION</div>
        <div class="card-name">Dr. Connor</div>
        <div class="card-role">Theoretical Physicist — Dimensional Decay Specialist — VALEN Protocol Author</div>
        <div class="card-tags">
          <span class="card-tag">Level 7+</span>
          <span class="card-tag">VALEN Protocol</span>
          <span class="card-tag">LD-001 Adjacent</span>
          <span class="card-tag">High Risk</span>
        </div>
      </div>
    </a>

    <!-- Dr. Manarine -->
    <a href="Dr.Manarine.html" class="profile-card">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">PROFILE — Senior Anomalous Correlation Researcher</div>
        <div class="card-name">Dr. Manarine</div>
        <div class="card-role">Dr. Manarine Hypertheos The Mad Doctor</div>
        <div class="card-tags">
          <span class="card-tag">Level 7+</span>
          <span class="card-tag">Under Permanent Surveillance</span>
          <span class="card-tag">LD-088 and New Omega Tier Anomaly Adjacent</span>
          <span class="card-tag">High Risk</span>
        </div>
      </div>
    </a>
    
    <!-- APA-01 -->
    <a href="apa-01.html" class="profile-card">
      <div class="card-accent" style="background: #f44336;"></div>
      <div class="card-body">
        <div class="card-id" style="color: #f44336;">PROFILE — A.P.A. DIVISION</div>
        <div class="card-name" style="color: #f77;">APA-01 — The First Adaptive Protocol Apex</div>
        <div class="card-role">First Human to Survive Tier-4 Anomaly Exposure — A.P.A. Program Prototype</div>
        <div class="card-tags">
          <span class="card-tag" style="color: #f44336; border-color: #4a0000;">Level 6+</span>
          <span class="card-tag" style="color: #f44336; border-color: #4a0000;">Tier-4 Adapted</span>
          <span class="card-tag" style="color: #f44336; border-color: #4a0000;">Non-Human</span>
          <span class="card-tag" style="color: #f44336; border-color: #4a0000;">Unmatched Combat</span>
        </div>
      </div>
    </a>

    <div class="redacted-notice">
      // Additional profiles exist within this category //<br>
      // Access requires D.I.V.I.D.E. Level clearance //<br>
      // [REDACTED] entries: [DATA EXPUNGED] //
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
