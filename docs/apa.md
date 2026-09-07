
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — A.P.A.</title>
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
      border: 1px solid #1a4a6a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #05101a 0%, #080808 100%);
    }

    .file-header::before {
      content: '// TASK FORCE OVERVIEW — LEVEL 6+ //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #4fc3f7;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #4fc3f7;
      border-right: 2px solid #4fc3f7;
    }

    .file-codename {
      font-size: 11px;
      color: #4fc3f7;
      letter-spacing: 5px;
      margin-bottom: 6px;
      text-transform: uppercase;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 42px;
      font-weight: 700;
      color: #7dd5f7;
      letter-spacing: 6px;
      text-shadow: 0 0 20px rgba(79,195,247,0.25);
      margin-bottom: 4px;
    }

    .file-subtitle {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      color: #4fc3f7;
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
    .meta-value.blue { color: #4fc3f7; }
    .meta-value.red { color: #cc0000; }
    .meta-value.orange { color: #e65100; }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #4fc3f7;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #0a2a3a;
    }

    .content-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #1a4a6a;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      line-height: 1.9;
      color: #888;
    }

    .content-block p { margin-bottom: 8px; }
    .content-block p:last-child { margin-bottom: 0; }

    /* Dual meaning block */
    .meaning-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 8px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .meaning-grid { grid-template-columns: 1fr; } }

    .meaning-card {
      padding: 18px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-top: 3px solid #1a4a6a;
      font-size: 12px;
      color: #777;
      line-height: 1.8;
    }

    .meaning-label {
      font-size: 9px;
      letter-spacing: 3px;
      color: #4fc3f7;
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    .meaning-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      font-weight: 700;
      color: #7dd5f7;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 10px;
    }

    .meaning-card.classified {
      border-top-color: #cc0000;
      position: relative;
    }

    .meaning-card.classified .meaning-label { color: #cc0000; }
    .meaning-card.classified .meaning-title { color: #f77; }

    .classified-stamp {
      position: absolute;
      top: 10px;
      right: 14px;
      font-size: 9px;
      letter-spacing: 2px;
      color: #cc0000;
      border: 1px solid #3a0000;
      padding: 2px 6px;
      text-transform: uppercase;
      opacity: 0.7;
    }

    /* Attribute cards */
    .attr-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .attr-grid { grid-template-columns: 1fr; } }

    .attr-card {
      padding: 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #1a4a6a;
      font-size: 12px;
      color: #777;
      line-height: 1.7;
      transition: border-color 0.2s, background 0.2s;
    }

    .attr-card:hover {
      border-left-color: #4fc3f7;
      background: #0a1520;
    }

    .attr-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #4fc3f7;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 8px;
    }

    /* Quote */
    .main-quote {
      background: #080808;
      border: 1px solid #1a2a3a;
      border-left: 4px solid #4fc3f7;
      padding: 24px 28px;
      margin: 24px 0;
      position: relative;
      text-align: center;
    }

    .main-quote::before {
      content: '"';
      position: absolute;
      top: -12px; left: 16px;
      background: #080808;
      padding: 0 6px;
      color: #4fc3f7;
      font-size: 30px;
      font-family: serif;
      line-height: 1;
    }

    .main-quote p {
      font-family: 'Rajdhani', sans-serif;
      font-size: 18px;
      color: #7dd5f7;
      line-height: 1.6;
      letter-spacing: 2px;
      font-weight: 600;
    }

    /* Profile link */
    .profile-link {
      display: flex;
      align-items: center;
      gap: 16px;
      padding: 18px 20px;
      background: #0d0d0d;
      border: 1px solid #1a4a6a;
      text-decoration: none;
      transition: all 0.2s;
      margin-top: 8px;
      position: relative;
    }

    .profile-link::after {
      content: '▶';
      position: absolute;
      right: 16px;
      color: #1a4a6a;
      transition: color 0.2s;
    }

    .profile-link:hover {
      background: #0a1520;
      border-color: #4fc3f7;
    }

    .profile-link:hover::after { color: #4fc3f7; }

    .profile-link .pl-id {
      font-size: 10px;
      color: #4fc3f7;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 4px;
    }

    .profile-link .pl-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      font-weight: 700;
      color: #7dd5f7;
      letter-spacing: 2px;
      text-transform: uppercase;
    }

    .profile-link .pl-desc {
      font-size: 11px;
      color: #555;
      letter-spacing: 1px;
      margin-top: 3px;
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
    ⚠ LEVEL 6 CLEARANCE REQUIRED — TASK FORCE OVERVIEW — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="container">

    <a href="task-force-list.html" class="back-link">← RETURN TO TASK FORCE INDEX</a>

    <div class="file-header">
      <div class="file-codename">Codename: A.P.A.</div>
      <div class="file-title">A.P.A.</div>
      <div class="file-subtitle">Anomaly Pursuit Agent — Adaptive Protocol Apex</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">FULL NAME</span>
          <span class="meta-value blue">Anomaly Pursuit Agent</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">Level 6 — Elevated if Required</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">ALT. MEANING</span>
          <span class="meta-value red">[CLASSIFIED]</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">STATUS</span>
          <span class="meta-value orange">Active — All Sites</span>
        </div>
      </div>
    </div>

    <!-- WHAT IT REPRESENTS -->
    <div class="section-label">// What It Represents //</div>
    <div class="meaning-grid">
      <div class="meaning-card">
        <div class="meaning-label">Primary Designation</div>
        <div class="meaning-title">Anomaly Pursuit Agent</div>
        A high-ranking field operative within D.I.V.I.D.E., specifically deployed for the containment, neutralization, and eradication of anomalous entities or phenomena that threaten local realities. The A.P.A. designation is reserved for the most elite agents — entrusted with missions that others would consider suicidal.
      </div>
      <div class="meaning-card classified">
        <div class="classified-stamp">Classified</div>
        <div class="meaning-label">Alternate Meaning</div>
        <div class="meaning-title">Adaptive Protocol Apex</div>
        A reference to the agent's unparalleled capacity to improvise, adapt, and execute extreme, unconventional protocols under extreme pressure. These agents are the last line of defense against anomalies — often the difference between survival and annihilation for D.I.V.I.D.E. and the world at large.
      </div>
    </div>

    <!-- DESCRIPTION -->
    <div class="section-label">// Program Description //</div>
    <div class="content-block">
      <p>APA-01 was the first human to survive direct exposure to a Tier-4 anomaly — an event that should have been fatal. Instead of succumbing to the anomaly's devastating effects, APA-01 not only survived but adapted. Their body and mind were irrevocably altered, becoming something far beyond human. This extreme resilience, paired with unmatched combat intuition, formed the foundation for the APA program.</p>
      <p>APA agents are capable of enduring unimaginable trauma and executing precision strikes in high-risk scenarios where conventional tactics would fail. They possess the innate ability to think and react with split-second accuracy, making them indispensable when confronting the most dangerous anomalies known to D.I.V.I.D.E.</p>
    </div>

    <!-- ATTRIBUTES -->
    <div class="section-label">// Special Attributes //</div>
    <div class="attr-grid">
      <div class="attr-card">
        <div class="attr-name">Tier-4 Adaptation</div>
        Enhanced durability, heightened senses, and rapid threat analysis. Built to survive in hostile, anomalous environments that would destroy standard operatives.
      </div>
      <div class="attr-card">
        <div class="attr-name">Combat Intuition</div>
        Preternatural reflexes and strategic instincts allow APA agents to operate effectively under conditions of extreme pressure and near-zero survival probability.
      </div>
      <div class="attr-card">
        <div class="attr-name">Unquestionable Loyalty</div>
        APA agents are conditioned for absolute obedience. They will follow any command — including self-termination — without hesitation or resistance.
      </div>
      <div class="attr-card">
        <div class="attr-name">Clearance Authority</div>
        Automatically granted Level 6 Clearance upon designation. Potential for elevation based on mission scope and active threat level at D.I.V.I.D.E. command discretion.
      </div>
    </div>

    <!-- KNOWN AGENTS -->
    <div class="section-label">// Known Active Agents //</div>

    <a href="apa-01.html" class="profile-link">
      <div>
        <div class="pl-id">AGENT — APA-01</div>
        <div class="pl-name">The First Adaptive Protocol Apex</div>
        <div class="pl-desc">Program prototype — Squad Leader — Non-Human Classification</div>
      </div>
    </a>

    <!-- QUOTE -->
    <div class="main-quote">
      <p>"We don't send APA to clean up the mess.<br>We send them to end it."</p>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
