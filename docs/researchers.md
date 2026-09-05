
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Research Division</title>
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
      content: '// PERSONNEL FILE //';
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

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #4fc3f7;
      letter-spacing: 5px;
      text-shadow: 0 0 20px rgba(79,195,247,0.25);
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
    .meta-value.blue { color: #4fc3f7; }
    .meta-value.red { color: #cc0000; }

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

    /* Nickname tags */
    .nickname-row {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      margin-bottom: 8px;
    }

    .nickname-tag {
      font-size: 10px;
      letter-spacing: 2px;
      padding: 4px 12px;
      border: 1px solid #1a4a6a;
      color: #4fc3f7;
      text-transform: uppercase;
    }

    /* Responsibility list */
    .resp-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #1a4a6a;
      font-size: 12px;
      color: #888;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .resp-item .arrow { color: #4fc3f7; flex-shrink: 0; margin-top: 2px; }

    /* Tier cards */
    .tier-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .tier-grid { grid-template-columns: 1fr; } }

    .tier-card {
      padding: 14px 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      font-size: 11px;
      color: #777;
      line-height: 1.7;
    }

    .tier-card .tier-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 4px;
    }

    .tier-card .tier-level {
      font-size: 9px;
      letter-spacing: 2px;
      margin-bottom: 8px;
      padding: 2px 8px;
      border: 1px solid;
      display: inline-block;
      text-transform: uppercase;
    }

    .tier-l1 { border-top: 3px solid #4fc3f7; }
    .tier-l1 .tier-name { color: #4fc3f7; }
    .tier-l1 .tier-level { color: #4fc3f7; border-color: #1a4a6a; }

    .tier-l3 { border-top: 3px solid #4caf50; }
    .tier-l3 .tier-name { color: #4caf50; }
    .tier-l3 .tier-level { color: #4caf50; border-color: #1a4a1a; }

    .tier-l4 { border-top: 3px solid #ffd600; }
    .tier-l4 .tier-name { color: #ffd600; }
    .tier-l4 .tier-level { color: #ffd600; border-color: #4a4000; }

    .tier-l5 { border-top: 3px solid #e65100; }
    .tier-l5 .tier-name { color: #e65100; }
    .tier-l5 .tier-level { color: #e65100; border-color: #4a1a00; }

    .tier-l7 {
      border-top: 3px solid #9c27b0;
      grid-column: 1 / -1;
    }
    .tier-l7 .tier-name { color: #9c27b0; }
    .tier-l7 .tier-level { color: #9c27b0; border-color: #3a0a4a; }

    /* Culture warning block */
    .culture-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #555;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      line-height: 1.9;
      color: #777;
      font-style: italic;
    }

    .culture-block p { margin-bottom: 8px; }
    .culture-block p:last-child { margin-bottom: 0; }

    /* Quote */
    .internal-quote {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #4fc3f7;
      padding: 20px 24px;
      margin: 20px 0;
      position: relative;
    }

    .internal-quote::before {
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

    .internal-quote p { font-size: 13px; color: #aaa; line-height: 1.8; font-style: italic; }
    .internal-quote .attribution { margin-top: 10px; font-size: 10px; color: #555; letter-spacing: 2px; text-transform: uppercase; font-style: normal; }

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

    <a href="personnel.html" class="back-link">← RETURN TO PERSONNEL INDEX</a>

    <div class="file-header">
      <div class="file-title">RESEARCH DIVISION</div>
      <div class="file-designation">D.I.V.I.D.E. Research Division — Personnel File — Active</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">DESIGNATION</span>
          <span class="meta-value blue">Researcher</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value blue">Level 1 — Level 7+</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">NICKNAMES</span>
          <span class="meta-value">"White Coats" / "The Brains" / "Corpse Counters"</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">STATUS</span>
          <span class="meta-value blue">Active — All Sites</span>
        </div>
      </div>
    </div>

    <!-- OVERVIEW -->
    <div class="section-label">// Overview //</div>
    <div class="content-block">
      <p>D.I.V.I.D.E. Researchers are the scientific backbone of the organization — responsible for analyzing, understanding, and occasionally reverse-engineering anomalous phenomena. Operating in tightly controlled environments, these individuals serve as the bridge between theoretical knowledge and frontline application.</p>
      <p>Though rarely seen outside containment zones or deep labs, their decisions directly impact field protocols, weaponization strategies, and survival rates for entire task forces. One wrong calculation, and it's not just the test subject that dies — it's the entire city. Or in extremely rare, catastrophic cases, an entire country.</p>
    </div>

    <!-- RESPONSIBILITIES -->
    <div class="section-label">// Responsibilities //</div>
    <div class="resp-item"><span class="arrow">▶</span>Conducting in-depth analysis of anomalies, infection vectors, psychic influence zones, and spatial-temporal instability.</div>
    <div class="resp-item"><span class="arrow">▶</span>Designing containment protocols for new and evolving threats.</div>
    <div class="resp-item"><span class="arrow">▶</span>Overseeing AT-Class test operations and reviewing post-field reports.</div>
    <div class="resp-item"><span class="arrow">▶</span>Developing prototype countermeasures and anomaly-interfacing technology for Task Forces and A.P.A. units.</div>
    <div class="resp-item"><span class="arrow">▶</span>Reporting directly to higher-ranking Researchers. D.I.V.I.D.E. Overseers, if present, are to be prioritized and briefed before any other clearance level.</div>

    <!-- INTERNAL CULTURE -->
    <div class="section-label">// Internal Culture //</div>
    <div class="culture-block">
      <p>D.I.V.I.D.E. researchers are often cold, clinical, and disturbingly desensitized. Years of exposure to grotesque outcomes and existential threats have stripped away much of their emotional response. A screaming AT-Class subject isn't a tragedy — it's "data in motion."</p>
      <p>Departments quietly compete for results and recognition. Discoveries that influence protocol or containment methods earn greater funding and access. Ethics exist, but mostly as a formality.</p>
    </div>

    <!-- CLASSIFICATION TIERS -->
    <div class="section-label">// Classification Tiers //</div>
    <div class="tier-grid">
      <div class="tier-card tier-l1">
        <div class="tier-level">L1 — L2</div>
        <div class="tier-name">Junior Researchers</div>
        Monitor experiments, review logs, manage minor anomaly interactions. Entry-level scientific access only.
      </div>
      <div class="tier-card tier-l3">
        <div class="tier-level">L3</div>
        <div class="tier-name">Field Analysts</div>
        Occasionally accompany armed squads to document anomaly behavior during controlled missions.
      </div>
      <div class="tier-card tier-l4">
        <div class="tier-level">L4</div>
        <div class="tier-name">Senior Researchers</div>
        Oversee full labs, supervise AT-Class experimentation, and author containment proposals.
      </div>
      <div class="tier-card tier-l5">
        <div class="tier-level">L5 — L6</div>
        <div class="tier-name">Project Leads</div>
        Architect entire containment facilities, advise APA deployments, and authorize emergency lockdowns.
      </div>
      <div class="tier-card tier-l7">
        <div class="tier-level">L7+</div>
        <div class="tier-name">[REDACTED]</div>
        Unknown. Limited references exist in any accessible database. Their clearance supersedes all personnel on-site. Further information requires D.I.V.I.D.E. level access.
      </div>
    </div>

    <!-- QUOTE -->
    <div class="internal-quote">
      <p>Curiosity didn't kill the cat. Exposure did. Curiosity just wrote the request form.</p>
      <div class="attribution">— Common Researcher Saying — Origin Unknown</div>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
