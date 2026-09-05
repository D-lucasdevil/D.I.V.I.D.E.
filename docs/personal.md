
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Personnel</title>
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

    /* Personnel category cards */
    .personnel-card {
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

    .personnel-card::after {
      content: '▶';
      position: absolute;
      right: 16px;
      top: 50%;
      transform: translateY(-50%);
      color: #2a2a2a;
      font-size: 12px;
      transition: color 0.2s;
    }

    .personnel-card:hover::after { color: #cc0000; }
    .personnel-card:hover { border-color: #3a0000; background: #0d0000; }

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
      line-height: 1.2;
    }

    .card-desc {
      font-size: 11px;
      color: #555;
      letter-spacing: 1px;
      margin-bottom: 10px;
      line-height: 1.5;
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

    /* Researchers — Blue */
    .cat-researchers .card-accent { background: #4fc3f7; }
    .cat-researchers .card-id { color: #4fc3f7; }
    .cat-researchers .card-name { color: #7dd5f7; }
    .cat-researchers .card-tag { color: #4fc3f7; border-color: #1a4a6a; }
    .cat-researchers:hover { border-color: #1a4a6a; }

    /* Guards — Green */
    .cat-guards .card-accent { background: #4caf50; }
    .cat-guards .card-id { color: #4caf50; }
    .cat-guards .card-name { color: #7dc87f; }
    .cat-guards .card-tag { color: #4caf50; border-color: #1a4a1a; }
    .cat-guards:hover { border-color: #1a4a1a; }

    /* Task Force — Red */
    .cat-taskforce .card-accent { background: #f44336; }
    .cat-taskforce .card-id { color: #f44336; }
    .cat-taskforce .card-name { color: #f77; }
    .cat-taskforce .card-tag { color: #f44336; border-color: #4a0000; }
    .cat-taskforce:hover { border-color: #3a0000; }

    /* Special Individuals — Purple */
    .cat-special .card-accent { background: #9c27b0; }
    .cat-special .card-id { color: #9c27b0; }
    .cat-special .card-name { color: #ce7adb; }
    .cat-special .card-tag { color: #9c27b0; border-color: #3a0a4a; }
    .cat-special:hover { border-color: #3a0a4a; }

    /* AT-Class — Gray/Dark */
    .cat-at .card-accent { background: #333; }
    .cat-at .card-id { color: #555; }
    .cat-at .card-name { color: #666; }
    .cat-at .card-tag { color: #555; border-color: #2a2a2a; }
    .cat-at:hover { border-color: #2a2a2a; background: #0a0a0a; }
    .cat-at:hover::after { color: #555; }

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
      <div class="file-title">PERSONNEL</div>
      <div class="file-designation">D.I.V.I.D.E. Staff Registry — All Divisions</div>
      <div class="clearance-badge">Clearance Level 1+ Required</div>
    </div>

    <div class="status-bar">
      <span><span class="status-dot"></span>REGISTRY ONLINE</span>
      <span>ACTIVE DIVISIONS: 5</span>
      <span>TOTAL PERSONNEL: [CLASSIFIED]</span>
    </div>

    <div class="section-label">// Personnel Categories //</div>

    <!-- Researchers -->
    <a href="researchers.html" class="personnel-card cat-researchers">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">DIVISION — 01</div>
        <div class="card-name">Researchers</div>
        <div class="card-desc">Anomaly analysis, documentation, and containment research personnel. The scientific backbone of D.I.V.I.D.E. operations.</div>
        <div class="card-tags">
          <span class="card-tag">Science</span>
          <span class="card-tag">Analysis</span>
          <span class="card-tag">Containment</span>
          <span class="card-tag">Level 2+</span>
        </div>
      </div>
    </a>

    <!-- Guards -->
    <a href="guards.html" class="personnel-card cat-guards">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">DIVISION — 02</div>
        <div class="card-name">Guards</div>
        <div class="card-desc">Security and enforcement personnel responsible for facility protection and standard containment enforcement.</div>
        <div class="card-tags">
          <span class="card-tag">Security</span>
          <span class="card-tag">Enforcement</span>
          <span class="card-tag">Facility</span>
          <span class="card-tag">Level 1+</span>
        </div>
      </div>
    </a>

    <!-- Task Force -->
    <a href="task-force-list.html" class="personnel-card cat-taskforce">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">DIVISION — 03</div>
        <div class="card-name">Task Forces</div>
        <div class="card-desc">Specialized operational units deployed for high-risk anomaly engagement, containment, and neutralization across all threat levels.</div>
        <div class="card-tags">
          <span class="card-tag">A.P.A.</span>
          <span class="card-tag">B.E.R.S.E.R.K.</span>
          <span class="card-tag">Phantom</span>
          <span class="card-tag">Level 3+</span>
        </div>
      </div>
    </a>

    <!-- Special Individuals -->
    <a href="special-individuals.html" class="personnel-card cat-special">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">DIVISION — 04</div>
        <div class="card-name">Special Individuals</div>
        <div class="card-desc">Personnel of extraordinary classification — anomalous, enhanced, or otherwise outside standard operational categories.</div>
        <div class="card-tags">
          <span class="card-tag">Anomalous</span>
          <span class="card-tag">Enhanced</span>
          <span class="card-tag">Classified</span>
          <span class="card-tag">Level 5+</span>
        </div>
      </div>
    </a>

    <!-- AT-Class -->
    <a href="at-class.html" class="personnel-card cat-at">
      <div class="card-accent"></div>
      <div class="card-body">
        <div class="card-id">DESIGNATION — AT</div>
        <div class="card-name">AT-Class — Absolute Trash</div>
        <div class="card-desc">Forcibly drafted test subjects used for anomaly experimentation. No clearance. No rights. Expendable by classification.</div>
        <div class="card-tags">
          <span class="card-tag">Test Rats</span>
          <span class="card-tag">Expendable</span>
          <span class="card-tag">No Clearance</span>
          <span class="card-tag">Terminated on Use</span>
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
