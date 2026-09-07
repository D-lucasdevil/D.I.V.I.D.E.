
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — B.E.R.S.E.R.K.</title>
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
      background-color: #3a0000;
      color: #ff4444;
      text-align: center;
      padding: 6px;
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      border-bottom: 1px solid #cc0000;
      animation: flicker 3s infinite;
    }

    @keyframes flicker {
      0%, 95%, 100% { opacity: 1; }
      96% { opacity: 0.8; }
      97% { opacity: 1; }
      98% { opacity: 0.7; }
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
    .back-link:hover { color: #f44336; }

    .file-header {
      border: 1px solid #4a0000;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #120000 0%, #080808 100%);
    }

    .file-header::before {
      content: '// HIGH-FATALITY UNIT — LEVEL 5+ //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #f44336;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #f44336;
      border-right: 2px solid #f44336;
    }

    .file-codename {
      font-size: 10px;
      color: #f44336;
      letter-spacing: 5px;
      margin-bottom: 6px;
      text-transform: uppercase;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 42px;
      font-weight: 700;
      color: #ff4444;
      letter-spacing: 4px;
      text-shadow: 0 0 30px rgba(244,67,54,0.5);
      margin-bottom: 4px;
    }

    .file-subtitle {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      color: #cc0000;
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
    .meta-value.red { color: #f44336; }
    .meta-value.orange { color: #e65100; }
    .meta-value.dark { color: #cc0000; }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #cc0000;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #2a0000;
    }

    .content-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0000;
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
      font-size: 16px;
      font-weight: 700;
      color: #f44336;
      letter-spacing: 4px;
      text-transform: uppercase;
      padding: 14px;
      border: 1px solid #2a0000;
      background: #0d0000;
      margin-bottom: 8px;
      text-shadow: 0 0 10px rgba(244,67,54,0.3);
    }

    /* Duty list */
    .duty-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0000;
      font-size: 12px;
      color: #888;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .duty-item .arrow { color: #f44336; flex-shrink: 0; margin-top: 2px; }

    /* Equipment cards */
    .equipment-card {
      padding: 16px 18px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #3a0000;
      margin-bottom: 8px;
      transition: border-left-color 0.2s, background 0.2s;
    }

    .equipment-card:hover {
      border-left-color: #f44336;
      background: #110000;
    }

    .equipment-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 15px;
      font-weight: 700;
      color: #f44336;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 8px;
    }

    .equipment-body {
      font-size: 12px;
      color: #777;
      line-height: 1.8;
    }

    .sub-list {
      margin-top: 8px;
      padding-left: 0;
      list-style: none;
    }

    .sub-list li {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 11px;
      color: #666;
      margin-bottom: 4px;
    }

    .sub-list li::before {
      content: '';
      width: 4px; height: 4px;
      background: #cc0000;
      border-radius: 50%;
      flex-shrink: 0;
    }

    /* Deaths dream special card */
    .deaths-dream {
      background: #0a0010;
      border: 1px solid #2a0a4a;
      border-left: 4px solid #9c27b0;
      padding: 16px 18px;
      margin-top: 8px;
      font-size: 12px;
      color: #7a4a8a;
      line-height: 1.8;
      font-style: italic;
    }

    .deaths-dream .dd-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      font-weight: 700;
      color: #ce7adb;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 8px;
      font-style: normal;
    }

    /* Deployment criteria */
    .criteria-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0000;
      border: 1px solid #1a0000;
      border-left: 3px solid #cc0000;
      font-size: 12px;
      color: #884444;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .criteria-item .warn { color: #cc0000; flex-shrink: 0; }

    /* Comparison bar */
    .comparison-box {
      display: grid;
      grid-template-columns: 1fr auto 1fr;
      gap: 0;
      margin-bottom: 8px;
      align-items: center;
    }

    .comp-unit {
      padding: 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      text-align: center;
    }

    .comp-unit .cu-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 18px;
      font-weight: 700;
      letter-spacing: 3px;
      margin-bottom: 6px;
    }

    .comp-unit .cu-desc {
      font-size: 10px;
      color: #555;
      letter-spacing: 1px;
    }

    .comp-unit.apa .cu-name { color: #4fc3f7; }
    .comp-unit.berserk .cu-name { color: #f44336; }

    .comp-vs {
      padding: 16px 20px;
      background: #111;
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      color: #333;
      letter-spacing: 2px;
    }

    /* Operation Hellmouth */
    .hellmouth-box {
      background: #0d0000;
      border: 1px solid #3a0000;
      border-left: 4px solid #f44336;
      padding: 20px;
      margin-bottom: 8px;
    }

    .hellmouth-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      font-weight: 700;
      color: #f44336;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 14px;
    }

    .hellmouth-body {
      font-size: 12px;
      color: #884444;
      line-height: 1.9;
    }

    .hellmouth-body p { margin-bottom: 8px; }

    .log-line {
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      font-weight: 700;
      color: #cc0000;
      letter-spacing: 2px;
      padding: 10px 14px;
      background: #0a0000;
      border-left: 3px solid #cc0000;
      margin: 10px 0;
      font-style: italic;
    }

    .outcome-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 6px;
      margin-top: 12px;
    }

    @media (max-width: 600px) { .outcome-grid { grid-template-columns: 1fr; } }

    .outcome-card {
      padding: 12px 14px;
      background: #0a0000;
      border: 1px solid #1a0000;
      font-size: 11px;
      color: #666;
      line-height: 1.6;
    }

    .outcome-card .oc-label {
      font-size: 9px;
      letter-spacing: 2px;
      color: #f44336;
      text-transform: uppercase;
      margin-bottom: 4px;
    }

    /* Clearance warning */
    .clearance-warning {
      background: #0d0000;
      border: 2px solid #cc0000;
      padding: 18px 20px;
      margin-bottom: 8px;
      font-size: 12px;
      color: #884444;
      line-height: 1.8;
    }

    .clearance-warning strong { color: #f44336; }

    .clearance-stat {
      display: inline-block;
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      font-weight: 700;
      color: #f44336;
      letter-spacing: 2px;
      margin: 4px 0;
    }

    /* Quote blocks */
    .quote-block {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #f44336;
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
      color: #f44336;
      font-size: 24px;
      font-family: serif;
      line-height: 1;
    }

    .quote-block p {
      font-size: 13px;
      color: #cc4444;
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
    ⚠ CODE BLACK AUTHORIZED — B.E.R.S.E.R.K. ACTIVE FILE — LEVEL 5+ ONLY — COLLATERAL ACCEPTED ⚠
  </div>

  <div class="container">

    <a href="task-force-list.html" class="back-link">← RETURN TO TASK FORCE INDEX</a>

    <div class="file-header">
      <div class="file-codename">Unit Designation: B.E.R.S.E.R.K.</div>
      <div class="file-title">B.E.R.S.E.R.K.</div>
      <div class="file-subtitle">Bio-Enhanced Rapid Strike & Extraction Recon Killteam<br>"Warhammers" / "The Last Door" / "Walking Cataclysm"</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">DESIGNATION</span>
          <span class="meta-value red">High-Fatality Anomaly Annihilation Unit</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">Level 5+</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">COLLATERAL RADIUS</span>
          <span class="meta-value orange">55 KM Minimum</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">ZONE STATUS</span>
          <span class="meta-value dark">DEATH ZONE Post-Deployment</span>
        </div>
      </div>
    </div>

    <!-- DESCRIPTION -->
    <div class="section-label">// Unit Description //</div>
    <div class="content-block">
      <p>B.E.R.S.E.R.K. is a classified rapid-response killteam developed by the D.I.V.I.D.E. Special Warfare Division. Composed of genetically and cybernetically enhanced operatives, this unit is engineered for zero-prep, maximum-impact anomaly eradication.</p>
      <p>Where APA is a scalpel, B.E.R.S.E.R.K. is a wrecking ball — deployed only when overwhelming, unapologetic force is the last remaining option. When containment fails and diplomacy dies, this unit drops from orbit into the heart of destruction.</p>
    </div>

    <div class="tagline">HIT FAST. HIT HARD. LEAVE NOTHING STANDING.</div>

    <!-- DUTIES -->
    <div class="section-label">// Operational Duties //</div>
    <div class="duty-item"><span class="arrow">▶</span>Eliminate Tier-3+ anomalies in high-fatality, escalation-prone zones.</div>
    <div class="duty-item"><span class="arrow">▶</span>Respond to catastrophic breaches where standard containment has completely collapsed.</div>
    <div class="duty-item"><span class="arrow">▶</span>Deploy to sectors marked as expendable or non-recoverable.</div>
    <div class="duty-item"><span class="arrow">▶</span>Execute total obliteration when APA is unavailable, occupied, or deemed excessive for the threat.</div>

    <!-- EQUIPMENT -->
    <div class="section-label">// Features & Equipment //</div>

    <div class="equipment-card">
      <div class="equipment-name">Genetic Rage Protocols</div>
      <div class="equipment-body">Operatives are implanted with Rage Core bioware — inducing a controlled berserker state under threat. This state enhances strength, aggression, speed, and pain suppression while maintaining coordinated movement with the team.</div>
    </div>

    <div class="equipment-card">
      <div class="equipment-name">Neural Combat Synchronization</div>
      <div class="equipment-body">Linked via tactical neural-net implants, B.E.R.S.E.R.K. moves as one. Reactions are hive-fast, sensory data is shared instantly, and no threat goes unseen by any member of the unit.</div>
    </div>

    <div class="equipment-card">
      <div class="equipment-name">Shockframe Armor</div>
      <div class="equipment-body">Custom-built exo-frames resistant to kinetic, concussive, and anomalous forces. Designed to punch through walls and anomalies simultaneously. Integrated systems include:
        <ul class="sub-list">
          <li>Kinetic Boosters</li>
          <li>Cognitohazard Filters</li>
          <li>Spatial Stabilizers</li>
          <li>Adrenal Override Modules</li>
        </ul>
      </div>
    </div>

    <div class="equipment-card">
      <div class="equipment-name">Overkill Arsenal — Tier-0 Loadout</div>
      <div class="equipment-body">Every operative is armed to terminate existence — not preserve it. Ammunition is measured in kilotons. Precision is optional.
        <ul class="sub-list">
          <li>Micro-fusion cannons</li>
          <li>Dimensional warhammers</li>
          <li>Anomaly disruptors</li>
          <li>Megaton plasma slugs</li>
        </ul>
      </div>
    </div>

    <div class="equipment-card">
      <div class="equipment-name">Psychological Conditioning</div>
      <div class="equipment-body">B.E.R.S.E.R.K. units are emotionally dulled, but not mindless. Hesitation is purged through intense neural-loop indoctrination. Loyalty is to the mission alone — not survival, not ethics, not restraint.</div>
    </div>

    <div class="deaths-dream">
      <div class="dd-title">☽ Death's Dream</div>
      When a B.E.R.S.E.R.K. operative falls in combat, they are shown the most beautiful dream they would wish to see as they die. There is a comfort in knowing that if they fall, they too will be greeted by Death's Dream. It gives them the strength to charge into battle with resolve — for death is no longer something to fear, but a beautiful, final reward.
    </div>

    <!-- COMPARISON -->
    <div class="section-label">// Force Classification //</div>
    <div class="comparison-box">
      <div class="comp-unit apa">
        <div class="cu-name">A.P.A.</div>
        <div class="cu-desc">The Scalpel<br>Clears Continents</div>
      </div>
      <div class="comp-vs">VS</div>
      <div class="comp-unit berserk">
        <div class="cu-name">B.E.R.S.E.R.K.</div>
        <div class="cu-desc">The Warhammer<br>Clears Cities</div>
      </div>
    </div>

    <!-- DEPLOYMENT -->
    <div class="section-label">// Deployment Criteria //</div>
    <div class="criteria-item"><span class="warn">⚠</span>Tier-3+ anomaly has neutralized multiple strike teams prior to deployment.</div>
    <div class="criteria-item"><span class="warn">⚠</span>Standard containment has failed or actively escalated the breach.</div>
    <div class="criteria-item"><span class="warn">⚠</span>APA units are unavailable, occupied, or deemed excessive for the threat class.</div>
    <div class="criteria-item"><span class="warn">⚠</span>Sector is formally designated as non-recoverable — classified "Expendable."</div>

    <!-- OPERATION HELLMOUTH -->
    <div class="section-label">// Code Black Record — Operation Hellmouth //</div>
    <div class="hellmouth-box">
      <div class="hellmouth-title">⬛ Operation Hellmouth — Code Black</div>
      <div class="hellmouth-body">
        <p>A Class-5 interdimensional rupture occurred at Containment Site ██. Entity [REDACTED] emerged across 3 sectors simultaneously. APA-01 was engaged off-site and unavailable for deployment.</p>
        <p>B.E.R.S.E.R.K. was dropped into the epicenter via orbital shockpods.</p>
        <p>Visual data terminated within 3 minutes of insertion. Sound logs captured only static, screams, and one sentence:</p>
      </div>
      <div class="log-line">"B.E.R.S.E.R.K. has entered the pit."</div>
      <div class="hellmouth-body">
        <p>12 minutes later, the anomaly ceased. 24 hours later, recon teams entered the zone.</p>
      </div>
      <div class="outcome-grid">
        <div class="outcome-card">
          <div class="oc-label">Entity</div>
          Obliterated. No recoverable material.
        </div>
        <div class="outcome-card">
          <div class="oc-label">Facility</div>
          Half-vaporized. Restoration not attempted.
        </div>
        <div class="outcome-card">
          <div class="oc-label">Operatives</div>
          6 KIA. 4 recovered alive — smiling and laughing.
        </div>
      </div>
    </div>

    <!-- CLEARANCE WARNING -->
    <div class="section-label">// Clearance Warning //</div>
    <div class="clearance-warning">
      <strong>LEVEL 6+ ONLY:</strong> Do NOT deploy B.E.R.S.E.R.K. in any area expected to be salvageable.<br><br>
      <div class="clearance-stat">55 KM</div> — Minimum estimated collateral radius<br>
      <div class="clearance-stat">DEATH ZONE</div> — Zone classification post-deployment<br><br>
      Survivability is improbable. Restoration is not a goal. Civilian presence is an acceptable variable.
    </div>

    <!-- QUOTES -->
    <div class="section-label">// Internal Unit Phrases //</div>

    <div class="quote-block">
      <p>We don't knock. We detonate. And obliterate.</p>
    </div>

    <div class="quote-block">
      <p>Containment failed? We'll erase the coordinates.</p>
    </div>

    <div class="quote-block">
      <p>APA is the scalpel. We are the warhammer.</p>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
