<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Classified Database</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;600;700&display=swap');

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background-color: #080808;
      color: #c0c0c0;
      font-family: 'Share Tech Mono', monospace;
      min-height: 100vh;
      padding: 0;
    }

    /* Top warning bar */
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

    /* Header */
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
      top: 0;
      right: 0;
      width: 40px;
      height: 40px;
      border-top: 2px solid #8b0000;
      border-right: 2px solid #8b0000;
    }

    .site-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 48px;
      font-weight: 700;
      color: #cc0000;
      letter-spacing: 8px;
      text-shadow: 0 0 20px rgba(200, 0, 0, 0.4);
      margin-bottom: 8px;
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

    /* Hero image */
    .hero-image {
      width: 100%;
      max-height: 400px;
      object-fit: cover;
      border: 1px solid #1a0000;
      margin-bottom: 30px;
      filter: contrast(1.1) saturate(0.8);
      display: block;
    }

    /* Section label */
    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #8b0000;
      text-transform: uppercase;
      margin-bottom: 12px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a0000;
    }

    /* Navigation grid */
    .nav-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 8px;
      margin-bottom: 30px;
    }

    @media (max-width: 100%) {
      .nav-grid {
        grid-template-columns: 1fr;
      }
    }

    .nav-link {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 14px 18px;
      background-color: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0000;
      color: #aaa;
      text-decoration: none;
      font-size: 13px;
      letter-spacing: 1px;
      transition: all 0.2s ease;
      position: relative;
      overflow: hidden;
    }

    .nav-link::before {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      height: 100%;
      width: 0;
      background: rgba(139, 0, 0, 0.08);
      transition: width 0.2s ease;
    }

    .nav-link:hover {
      border-left-color: #cc0000;
      color: #fff;
      border-color: #3a0000;
    }

    .nav-link:hover::before {
      width: 100%;
    }

    .nav-link .link-id {
      color: #3a0000;
      font-size: 10px;
      min-width: 40px;
    }

    .nav-link:hover .link-id {
      color: #8b0000;
    }

    /* Status bar */
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
      width: 6px;
      height: 6px;
      background: #cc0000;
      border-radius: 50%;
      margin-right: 6px;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.3; }
    }

    /* Footer */
    .footer {
      border-top: 1px solid #1a0000;
      padding-top: 20px;
      font-size: 10px;
      color: #333;
      letter-spacing: 1px;
      line-height: 1.8;
      text-align: center;
    }

    .footer a {
      color: #555;
      text-decoration: none;
    }
  </style>
</head>
<body>

  <div class="warning-bar">
    ⚠ RESTRICTED ACCESS — AUTHORIZED PERSONNEL ONLY — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="container">

    <div class="header">
      <div class="site-title">D.I.V.I.D.E.</div>
      <div class="site-subtitle">Department for Internal Vigilance, Intervention, Destruction, and Erasure</div>
      <div class="clearance-badge">Clearance Level 1+ Required</div>
    </div>

    <img class="hero-image" src="https://github.com/user-attachments/assets/f0f5e73b-c5f5-4b3d-b1ef-b560a87e3bc5" alt="D.I.V.I.D.E. Header" />

    <div class="status-bar">
      <span><span class="status-dot"></span>DATABASE ONLINE</span>
      <span>ACTIVE ANOMALIES: 96</span>
      <span>THREAT STATUS: ELEVATED</span>
    </div>

    <div class="section-label">// Database Index — Select File //</div>

    <div class="nav-grid">
      <a href="timeline.html" class="nav-link">
        <span class="link-id">01 //</span>
        Timeline of Events
      </a>
      <a href="anomaly_reports.html" class="nav-link">
        <span class="link-id">02 //</span>
        Anomaly Reports
      </a>
      <a href="anomaly_threatlevel.html" class="nav-link">
        <span class="link-id">03 //</span>
        Anomaly Threat Levels
      </a>
      <a href="personal.html" class="nav-link">
        <span class="link-id">04 //</span>
        Personnel Files
      </a>
      <a href="servant_cards.html" class="nav-link">
        <span class="link-id">05 //</span>
        Servant Cards
      </a>
      <a href="black_streets.html" class="nav-link">
        <span class="link-id">06 //</span>
        Black Streets
      </a>
      <a href="doro_sightings.html" class="nav-link">
        <span class="link-id">07 //</span>
        Doro Sightings
      </a>
      <a href="notes_from_inside.html" class="nav-link">
        <span class="link-id">08 //</span>
        Notes from Inside
      </a>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
