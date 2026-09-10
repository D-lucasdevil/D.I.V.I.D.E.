
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Dr. Connor</title>
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
      content: '// RESEARCHER PROFILE — D.I.V.I.D.E. CLEARANCE //';
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

    .file-id {
      font-size: 10px;
      color: #4fc3f7;
      letter-spacing: 4px;
      margin-bottom: 6px;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #7dd5f7;
      letter-spacing: 4px;
      text-shadow: 0 0 20px rgba(79,195,247,0.2);
      margin-bottom: 4px;
    }

    .file-subtitle {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
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
    .meta-value.redacted { color: #cc0000; letter-spacing: 2px; }

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

    /* Timeline */
    .timeline {
      position: relative;
      padding-left: 0;
      margin-bottom: 8px;
    }

    .timeline::before {
      content: '';
      position: absolute;
      left: 80px;
      top: 0; bottom: 0;
      width: 1px;
      background: linear-gradient(180deg, #1a4a6a, #0a1a2a 80%, transparent);
    }

    .tl-entry {
      display: flex;
      gap: 0;
      margin-bottom: 0;
    }

    .tl-year {
      width: 80px;
      flex-shrink: 0;
      padding-top: 18px;
      padding-right: 16px;
      text-align: right;
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      font-weight: 700;
      color: #4fc3f7;
      letter-spacing: 1px;
    }

    .tl-node {
      flex-shrink: 0;
      width: 0;
      position: relative;
      margin-top: 20px;
    }

    .tl-node::before {
      content: '';
      position: absolute;
      left: -4px; top: 4px;
      width: 8px; height: 8px;
      border-radius: 50%;
      border: 2px solid #4fc3f7;
      background: #080808;
    }

    .tl-content {
      flex: 1;
      padding: 12px 0 20px 24px;
    }

    .tl-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #7dd5f7;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    .tl-body {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #1a4a6a;
      padding: 12px 14px;
      font-size: 12px;
      color: #777;
      line-height: 1.8;
    }

    /* Notable files */
    .file-card {
      display: flex;
      align-items: flex-start;
      gap: 16px;
      padding: 16px 18px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #1a4a6a;
      margin-bottom: 6px;
      transition: border-left-color 0.2s, background 0.2s;
    }

    .file-card:hover {
      border-left-color: #4fc3f7;
      background: #0a1520;
    }

    .file-code {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #4fc3f7;
      letter-spacing: 2px;
      min-width: 160px;
      flex-shrink: 0;
    }

    .file-desc {
      font-size: 12px;
      color: #777;
      line-height: 1.7;
    }

    /* Controversy block */
    .controversy-block {
      background: #0d0000;
      border: 1px solid #2a0000;
      border-left: 3px solid #cc0000;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      color: #884444;
      line-height: 1.9;
    }

    .controversy-block p { margin-bottom: 8px; }
    .controversy-block p:last-child { margin-bottom: 0; }

    /* Failed termination */
    .failed-box {
      background: #080000;
      border: 2px solid #cc0000;
      padding: 16px 20px;
      margin: 12px 0;
      text-align: center;
    }

    .failed-label {
      font-size: 9px;
      letter-spacing: 4px;
      color: #cc0000;
      text-transform: uppercase;
      margin-bottom: 8px;
    }

    .failed-text {
      font-family: 'Rajdhani', sans-serif;
      font-size: 20px;
      font-weight: 700;
      color: #f44336;
      letter-spacing: 4px;
      text-shadow: 0 0 10px rgba(244,67,54,0.3);
    }

    /* Quote */
    .main-quote {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #4fc3f7;
      padding: 22px 26px;
      margin: 20px 0;
      position: relative;
    }

    .main-quote::before {
      content: '"';
      position: absolute;
      top: -10px; left: 16px;
      background: #080808;
      padding: 0 6px;
      color: #4fc3f7;
      font-size: 30px;
      font-family: serif;
      line-height: 1;
    }

    .main-quote p {
      font-size: 14px;
      color: #aaa;
      line-height: 1.8;
      font-style: italic;
    }

    .main-quote .attribution {
      margin-top: 10px;
      font-size: 10px;
      color: #555;
      letter-spacing: 2px;
      text-transform: uppercase;
      font-style: normal;
    }

    /* Internal assessment */
    .assessment-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .assessment-grid { grid-template-columns: 1fr; } }

    .assessment-card {
      padding: 12px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-top: 3px solid #1a4a6a;
      font-size: 11px;
      color: #666;
      line-height: 1.6;
    }

    .assessment-card .ac-label {
      font-size: 9px;
      letter-spacing: 2px;
      color: #4fc3f7;
      text-transform: uppercase;
      margin-bottom: 6px;
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
    ⚠ D.I.V.I.D.E. CLEARANCE REQUIRED — SPECIAL INDIVIDUAL — RESEARCHER DIVISION ⚠
  </div>

  <div class="container">

    <a href="special-individuals.html" class="back-link">← RETURN TO SPECIAL INDIVIDUALS</a>

    <div class="file-header">
      <div class="file-id">FILE: RESEARCHER — SPECIAL CLEARANCE</div>
      <div class="file-title">DR. CONNOR</div>
      <div class="file-subtitle">LD-Anomaly Containment Division — VALEN Protocol Author</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">D.I.V.I.D.E. Level — Full Access</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">DIVISION</span>
          <span class="meta-value blue">LD-Anomaly Containment</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">STATUS</span>
          <span class="meta-value redacted">[REDACTED]</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">RISK LEVEL</span>
          <span class="meta-value red">Extreme — Monitor Continuously</span>
        </div>
      </div>
    </div>

    <!-- BACKGROUND TIMELINE -->
    <div class="section-label">// Background — Chronological //</div>

    <div class="timeline">
      <div class="tl-entry">
        <div class="tl-year">2010</div>
        <div class="tl-node"></div>
        <div class="tl-content">
          <div class="tl-title">Independent Detection</div>
          <div class="tl-body">While working as a theoretical physicist specializing in multidimensional decay and entropy tethering, Connor independently detected anomalous "noise" — later confirmed as residual output from LD-001. No other civilian or institutional instrument registered the signal. His methodology remains partially classified.</div>
        </div>
      </div>

      <div class="tl-entry">
        <div class="tl-year">2010—12</div>
        <div class="tl-node"></div>
        <div class="tl-content">
          <div class="tl-title">Institutional Rejection</div>
          <div class="tl-body">Connor approached multiple academic institutions and government bodies with his findings. Each dismissed his reports as symptomatic of acute psychotic disorder. He was formally stripped of his research position and placed under psychiatric review. Records of this period have since been sealed by D.I.V.I.D.E. on his behalf.</div>
        </div>
      </div>

      <div class="tl-entry">
        <div class="tl-year">2012</div>
        <div class="tl-node"></div>
        <div class="tl-content">
          <div class="tl-title">LD-001 Public Manifestation — D.I.V.I.D.E. Contact</div>
          <div class="tl-body">Following the first public manifestation of LD-001, D.I.V.I.D.E. cross-referenced historical detection reports. Connor's 2010 data matched the pre-manifest signal profile exactly. Contact was made within 72 hours of the incident. He accepted recruitment the same day.</div>
        </div>
      </div>

      <div class="tl-entry">
        <div class="tl-year">Post-12</div>
        <div class="tl-node"></div>
        <div class="tl-content">
          <div class="tl-title">VALEN Protocol — Full Clearance Granted</div>
          <div class="tl-body">Connor developed the VALEN Protocol — a dimensional triangulation method capable of locating temporal fractures used by anomalies during manifestation. The system remains the most reliable early-warning tool in D.I.V.I.D.E.'s detection arsenal. Full clearance was granted immediately upon successful field validation.</div>
        </div>
      </div>
    </div>

    <!-- ROLE -->
    <div class="section-label">// Role Within D.I.V.I.D.E. //</div>
    <div class="content-block">
      <p>Connor remains one of the few operatives trusted to interact directly with high-tier LD entities. His detection instinct — described by peers as "pre-cognitive" — has proven accurate in situations where standard instrumentation failed entirely.</p>
      <p>His primary focus is dimensional fracture mapping, high-tier entity behavior analysis, and pre-manifestation signal interpretation. He is considered indispensable to the containment division despite ongoing concerns about his psychological stability.</p>
    </div>

    <!-- INTERNAL ASSESSMENT -->
    <div class="section-label">// Internal Assessment //</div>
    <div class="assessment-grid">
      <div class="assessment-card">
        <div class="ac-label">Analytical Capability</div>
        Exceptional. Pre-organization detection of LD-001 without institutional support remains unmatched in D.I.V.I.D.E. history.
      </div>
      <div class="assessment-card">
        <div class="ac-label">Psychological Profile</div>
        Unstable under prolonged LD exposure. Intense fixation on specific entities flagged repeatedly. Loyalty verified — conditionally.
      </div>
      <div class="assessment-card">
        <div class="ac-label">Threat Assessment</div>
        Low direct. High indirect. His knowledge of VALEN Protocol and high-tier entity locations makes him dangerous if compromised.
      </div>
    </div>

    <!-- NOTABLE FILES -->
    <div class="section-label">// Notable Research Files //</div>

    <div class="file-card">
      <div class="file-code">R-Ω-VALEN-T01</div>
      <div class="file-desc">Research notes theorizing LD-000 "D" as a corrupted, yandere-coded entity — emotionally tethered to LD-001 in ways that defy standard anomaly behavioral models. Connor hypothesizes this tether is not incidental but foundational to D's classification as Ω-class. Further reading requires D.I.V.I.D.E. clearance.</div>
    </div>

    <!-- PERSONALITY & CONTROVERSY -->
    <div class="section-label">// Personality & Controversy //</div>

    <div class="controversy-block">
      <p>Feared and respected across the organization in equal measure. Connor's intense fixation on LD entities — particularly [REDACTED] — sparked internal concerns about compromised loyalty and potential sympathizer classification. Several department heads formally requested his reassignment.</p>
      <p>Those concerns were silenced during an unsanctioned internal test. Without hesitation, without visible reluctance, Connor issued the command to terminate the entity he had spent years studying.</p>
    </div>

    <div class="failed-box">
      <div class="failed-label">Termination Attempt Result</div>
      <div class="failed-text">THE ATTEMPT FAILED.</div>
    </div>

    <div class="controversy-block">
      <p>The entity was not destroyed. Connor's authority over the situation ended there. But the gesture was observed, logged, and noted at the highest clearance levels. Whatever his fixation, his loyalty to D.I.V.I.D.E. was not in question.</p>
      <p>What the failure told the organization about the entity is a separate matter — and one classified well above this file.</p>
    </div>

    <div class="main-quote">
      <p>I don't want to understand it. I want to bury it so deep reality forgets it existed.</p>
      <div class="attribution">— Dr. Connor — Post-Incident Statement</div>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>


© 2025 Lucas Devil. All Rights Reserved.
D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.
First created: 2025-05-07
