
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Doro Sightings</title>
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

    /* Header — pink/galaxy for Doro */
    .file-header {
      border: 1px solid #5a0a4a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #0f050e 0%, #080808 100%);
    }

    .file-header::before {
      content: '// ACTIVE SURVEILLANCE FILE //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #ff69b4;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #ff69b4;
      border-right: 2px solid #ff69b4;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #ff69b4;
      letter-spacing: 5px;
      text-shadow: 0 0 20px rgba(255,105,180,0.3);
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
    .meta-value.pink { color: #ff69b4; }
    .meta-value.red { color: #cc0000; }
    .meta-value.orange { color: #e65100; }

    .status-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 16px;
      background: #0d0d0d;
      border: 1px solid #2a0a2a;
      margin-bottom: 24px;
      font-size: 10px;
      color: #444;
      letter-spacing: 1px;
    }

    .status-dot {
      display: inline-block;
      width: 6px; height: 6px;
      background: #ff69b4;
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
      color: #ff69b4;
      text-transform: uppercase;
      margin-bottom: 12px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #2a0a2a;
    }

    .content-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #5a0a4a;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      line-height: 1.9;
      color: #888;
    }

    .content-block p { margin-bottom: 8px; }
    .content-block p:last-child { margin-bottom: 0; }

    /* Sighting report cards */
    .sighting-card {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #5a0a4a;
      margin-bottom: 10px;
      overflow: hidden;
      transition: border-color 0.2s, background 0.2s;
    }

    .sighting-card:hover {
      border-left-color: #ff69b4;
      background: #0f080e;
    }

    .sighting-header {
      display: flex;
      align-items: center;
      gap: 16px;
      padding: 14px 18px;
      border-bottom: 1px solid #1a1a1a;
    }

    .sighting-id {
      font-family: 'Rajdhani', sans-serif;
      font-size: 20px;
      font-weight: 700;
      color: #ff69b4;
      letter-spacing: 2px;
      min-width: 120px;
    }

    .sighting-title {
      font-size: 12px;
      color: #aaa;
      letter-spacing: 1px;
      flex: 1;
    }

    .sighting-year {
      font-size: 10px;
      color: #555;
      letter-spacing: 2px;
      border: 1px solid #2a0a2a;
      padding: 2px 8px;
      color: #ff69b4;
    }

    .sighting-body {
      padding: 14px 18px;
      font-size: 12px;
      color: #777;
      line-height: 1.8;
    }

    .sighting-body p { margin-bottom: 8px; }
    .sighting-body p:last-child { margin-bottom: 0; }

    .sighting-tags {
      display: flex;
      gap: 6px;
      flex-wrap: wrap;
      padding: 0 18px 14px 18px;
    }

    .sighting-tag {
      font-size: 9px;
      letter-spacing: 2px;
      padding: 2px 8px;
      border: 1px solid #2a0a2a;
      color: #884466;
      text-transform: uppercase;
    }

    /* Warning note */
    .warning-note {
      background: #0d000d;
      border: 1px solid #3a0a3a;
      border-left: 3px solid #ff69b4;
      padding: 14px 18px;
      margin-bottom: 8px;
      font-size: 11px;
      color: #884466;
      line-height: 1.7;
      letter-spacing: 0.5px;
    }

    .warning-note strong { color: #ff69b4; }

    /* Ongoing notice */
    .ongoing-box {
      background: #080808;
      border: 1px dashed #2a0a2a;
      padding: 16px 20px;
      text-align: center;
      font-size: 11px;
      color: #3a0a3a;
      letter-spacing: 2px;
      margin-top: 10px;
    }

    .ongoing-dot {
      display: inline-block;
      width: 6px; height: 6px;
      background: #ff69b4;
      border-radius: 50%;
      margin-right: 8px;
      animation: pulse 1.5s infinite;
      vertical-align: middle;
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
    ⚠ RESTRICTED ACCESS — AUTHORIZED PERSONNEL ONLY — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="container">

    <a href="index.html" class="back-link">← RETURN TO DATABASE INDEX</a>

    <div class="file-header">
      <div class="file-title">DORO SIGHTINGS</div>
      <div class="file-designation">LD-002 — Active Manifestation Log — Ongoing</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">ENTITY</span>
          <span class="meta-value pink">LD-002 — "Doro"</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">DIVIDE Level 1+</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">FIRST SIGHTING</span>
          <span class="meta-value pink">2022</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">STATUS</span>
          <span class="meta-value orange">Active — Uncontained</span>
        </div>
      </div>
    </div>

    <div class="status-bar">
      <span><span class="status-dot"></span>SURVEILLANCE ACTIVE</span>
      <span>CONFIRMED SIGHTINGS: 2+</span>
      <span>CONTAINMENT: IMPOSSIBLE</span>
    </div>

    <!-- OVERVIEW -->
    <div class="section-label">// Entity Overview //</div>
    <div class="content-block">
      <p>LD-002, designated "Doro," is an origin-class anomaly whose manifestation pattern defies standard containment prediction. Unlike most anomalies which arrive through a single Pulse event, Doro has demonstrated repeated and increasingly frequent manifestations across multiple locations and time periods.</p>
      <p>Her appearances are characterized by dimensional distortion, reality glitching, and unexplained environmental corruption in the immediate vicinity. No two sightings have produced identical conditions. Personnel are advised not to approach under any circumstances.</p>
    </div>

    <div class="warning-note">
      <strong>WARNING:</strong> LD-002 has demonstrated awareness of D.I.V.I.D.E. surveillance operations. Observation teams are to maintain maximum distance. Direct engagement is not authorized at any clearance level. See LD-002 full file for containment status.
    </div>

    <!-- SIGHTINGS -->
    <div class="section-label">// Confirmed Sighting Reports //</div>

    <!-- Sighting 001 -->
    <div class="sighting-card">
      <div class="sighting-header">
        <div class="sighting-id">SIGHTING 001</div>
        <div class="sighting-title">First Confirmed Manifestation</div>
        <div class="sighting-year">2022</div>
      </div>
      <div class="sighting-body">
        <p>The first confirmed sighting of LD-002 was recorded in 2022 by D.I.V.I.D.E. surveillance teams operating in an undisclosed monitoring zone. The manifestation lasted approximately [REDACTED] minutes before the entity self-terminated the observation window.</p>
        <p>During the event, all recording equipment within a [REDACTED] meter radius experienced simultaneous failure. Recovered footage shows what appears to be a small, cartoon-like form briefly transitioning into a realistic humanoid shape before returning to its primary form. One [REDACTED] personnel were present. [REDACTED] of them required psychological debriefing afterward.</p>
        <p>The event marked the beginning of active LD-002 tracking protocols within D.I.V.I.D.E. This sighting is classified as the origin point of the Doro monitoring program.</p>
      </div>
      <div class="sighting-tags">
        <span class="sighting-tag">First Contact</span>
        <span class="sighting-tag">Equipment Failure</span>
        <span class="sighting-tag">Form Shift Observed</span>
        <span class="sighting-tag">Psychological Impact</span>
      </div>
    </div>

    <!-- Sighting 002 -->
    <div class="sighting-card">
      <div class="sighting-header">
        <div class="sighting-id">SIGHTING 002</div>
        <div class="sighting-title">Escalating Manifestation Frequency</div>
        <div class="sighting-year">2023</div>
      </div>
      <div class="sighting-body">
        <p>By 2023 the frequency of confirmed LD-002 manifestations had increased significantly. Multiple sighting reports were filed across a [REDACTED] month period, suggesting either active movement across dimensional boundaries or a deliberate increase in the entity's engagement with our reality.</p>
        <p>Several manifestations occurred simultaneously in geographically distant locations, raising questions about whether LD-002 is a singular entity or capable of splitting across multiple points in space-time. This question remains unresolved.</p>
        <p>During this period LD-002 was observed interacting with [REDACTED] on at least [REDACTED] occasions. The nature of these interactions is classified above standard clearance. Proximity to LD-001 during this period appears to correlate with increased manifestation frequency — though whether this is causal or coincidental is debated internally.</p>
      </div>
      <div class="sighting-tags">
        <span class="sighting-tag">Frequency Escalation</span>
        <span class="sighting-tag">Multi-Location</span>
        <span class="sighting-tag">LD-001 Correlation</span>
        <span class="sighting-tag">Reality Distortion</span>
        <span class="sighting-tag">Unresolved</span>
      </div>
    </div>

    <div class="ongoing-box">
      <span class="ongoing-dot"></span>
      // Sighting log ongoing — new reports filed as confirmed //<br>
      // Additional entries require higher clearance to access //
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
