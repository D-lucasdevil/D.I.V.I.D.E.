
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — APA-01</title>
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

    /* Header — red for APA */
    .file-header {
      border: 1px solid #4a0000;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #100505 0%, #080808 100%);
    }

    .file-header::before {
      content: '// SPECIAL INDIVIDUAL — LEVEL 6+ //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #cc0000;
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

    .file-id {
      font-size: 11px;
      color: #f44336;
      letter-spacing: 4px;
      margin-bottom: 6px;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #f77;
      letter-spacing: 4px;
      text-shadow: 0 0 20px rgba(244,67,54,0.3);
      margin-bottom: 4px;
    }

    .file-subtitle {
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      color: #cc0000;
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
    .meta-value.red { color: #f44336; }
    .meta-value.orange { color: #e65100; }

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

    /* Ability cards */
    .ability-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .ability-grid { grid-template-columns: 1fr; } }

    .ability-card {
      padding: 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0000;
      font-size: 12px;
      color: #777;
      line-height: 1.7;
      transition: border-color 0.2s, background 0.2s;
    }

    .ability-card:hover {
      border-left-color: #f44336;
      background: #110000;
    }

    .ability-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      font-weight: 700;
      color: #f44336;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 8px;
    }

    /* Equipment cards */
    .equipment-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .equipment-grid { grid-template-columns: 1fr; } }

    .equipment-card {
      padding: 14px 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-top: 3px solid #4a0000;
      font-size: 11px;
      color: #777;
      line-height: 1.7;
    }

    .equipment-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      color: #cc0000;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    /* Personality block */
    .personality-block {
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

    .personality-block p { margin-bottom: 8px; }
    .personality-block p:last-child { margin-bottom: 0; }

    /* Incident box */
    .incident-box {
      background: #0d0000;
      border: 1px solid #3a0000;
      border-left: 4px solid #f44336;
      padding: 20px;
      margin-bottom: 8px;
    }

    .incident-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      font-weight: 700;
      color: #f44336;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 12px;
    }

    .incident-body {
      font-size: 12px;
      color: #888;
      line-height: 1.9;
    }

    .incident-body p { margin-bottom: 8px; }
    .incident-body p:last-child { margin-bottom: 0; }

    /* Quote */
    .main-quote {
      background: #080808;
      border: 1px solid #2a0000;
      border-left: 4px solid #f44336;
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
      color: #f44336;
      font-size: 30px;
      font-family: serif;
      line-height: 1;
    }

    .main-quote p {
      font-family: 'Rajdhani', sans-serif;
      font-size: 18px;
      color: #cc0000;
      line-height: 1.6;
      letter-spacing: 2px;
      font-style: normal;
      font-weight: 600;
    }

    /* Assessment tags */
    .assessment-row {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      margin-top: 16px;
    }

    .assessment-tag {
      font-size: 10px;
      letter-spacing: 2px;
      padding: 4px 12px;
      border: 1px solid #3a0000;
      color: #cc0000;
      text-transform: uppercase;
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
    ⚠ LEVEL 6+ CLEARANCE REQUIRED — SPECIAL INDIVIDUAL FILE — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="container">

    <a href="special-individuals.html" class="back-link">← RETURN TO SPECIAL INDIVIDUALS</a>

    <div class="file-header">
      <div class="file-id">FILE: APA-01 — SPECIAL INDIVIDUAL</div>
      <div class="file-title">APA-01</div>
      <div class="file-subtitle">The First Adaptive Protocol Apex</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">DESIGNATION</span>
          <span class="meta-value red">Adaptive Protocol Apex</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">Level 6+ Required</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">STATUS</span>
          <span class="meta-value orange">Active — A.P.A. Squad Leader</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLASSIFICATION</span>
          <span class="meta-value red">Non-Human — Evolved</span>
        </div>
      </div>
    </div>

    <!-- BACKGROUND -->
    <div class="section-label">// Background //</div>
    <div class="content-block">
      <p>APA-01 was the first human to survive direct exposure to a Tier-4 anomaly during the catastrophic Containment Breach Event in Sector X-3 — an incident that saw multiple high-risk entities escape containment in rapid succession. As the facility descended into chaos, every agent was either neutralized or overwhelmed. All but one.</p>
      <p>APA-01 didn't just survive the encounter — they <em style="color:#aaa">adapted</em>. Their body and mind evolved in real time, acquiring traits far beyond human limits. This unprecedented transformation gave birth to a new designation: APA — Adaptive Protocol Apex.</p>
      <p>APA-01 became the prototype for a new breed of D.I.V.I.D.E. operatives — elite assets deployed when standard containment is no longer an option. Trained to outlast and eliminate the uncontainable, APA agents are the organization's final line of defense.</p>
    </div>

    <!-- ABILITIES -->
    <div class="section-label">// Abilities & Attributes //</div>
    <div class="ability-grid">
      <div class="ability-card">
        <div class="ability-name">Adaptive Biology</div>
        APA-01's physiology responds dynamically to external threats. Recovery from lethal trauma in minutes. Evolves resistance to previously unknown hazards — physical, chemical, or anomalous.
      </div>
      <div class="ability-card">
        <div class="ability-name">Enhanced Reflexes</div>
        Reaction time far beyond human norms. Battlefield awareness sharpened by anomaly exposure. Predicts hostile behavior and responds with surgical precision.
      </div>
      <div class="ability-card">
        <div class="ability-name">Dimensional Sensitivity</div>
        Detects spatial anomalies before they fully manifest. Senses dimensional fractures, cognitive distortions, and reality shifts. Invaluable for intercepting threats before containment fails.
      </div>
      <div class="ability-card">
        <div class="ability-name">Protocol Mastery</div>
        Trained in dynamic mission logic — improvising complex containment strategies in collapsing environments with zero hesitation. Adaptability in high-stakes situations is unmatched.
      </div>
      <div class="ability-card" style="grid-column: 1 / -1;">
        <div class="ability-name">Anomaly Resistance</div>
        Tier-4 anomaly exposure has rendered APA-01 immune to most cognitohazards. Functions in conditions that destroy ordinary minds. The psychic degradation that kills agents is irrelevant to APA-01.
      </div>
    </div>

    <!-- PERSONALITY -->
    <div class="section-label">// Personality Assessment //</div>
    <div class="personality-block">
      <p>APA-01 operates with cold efficiency. Quiet, controlled, and relentlessly focused — more like a living protocol than a person. Emotion rarely surfaces. Only purpose.</p>
      <p>Despite this, APA-01 holds an unspoken commitment to protect. Those who've served alongside them describe a presence that anchors chaos — someone who doesn't break under pressure, no matter how dire.</p>
      <p>They do not consider themselves a hero. They consider themselves <em style="color:#aaa">necessary</em>.</p>
    </div>

    <!-- EQUIPMENT -->
    <div class="section-label">// Special Equipment //</div>
    <div class="equipment-grid">
      <div class="equipment-card">
        <div class="equipment-name">Quantum Blade</div>
        Harmonic-frequency blade forged from exotic alloys. Cuts through physical and anomalous matter. Attuned to APA-01's unique energy signature. Capable of disrupting transdimensional entities.
      </div>
      <div class="equipment-card">
        <div class="equipment-name">Survival Armor</div>
        Adaptive suit that shifts to meet environmental and anomalous threats. Self-repairs in the field. Counters reality-warping effects. Protects against kinetic and psychic attacks simultaneously.
      </div>
      <div class="equipment-card">
        <div class="equipment-name">Distress Beacon</div>
        Last-resort device transmitting across multiple planes of existence. When activated: D.I.V.I.D.E. command is alerted that containment has failed and the situation is beyond salvaging.
      </div>
    </div>

    <!-- INCIDENT -->
    <div class="section-label">// Incident Record — Sector X-3 //</div>
    <div class="incident-box">
      <div class="incident-title">⚠ Sector X-3 Containment Breach — D.I.V.I.D.E.'s Darkest Hour</div>
      <div class="incident-body">
        <p>The primary threat — codenamed the X-3 Entity — was a Tier-4 apex predator. Every agent dispatched before APA-01 perished — or lost their minds.</p>
        <p>APA-01 was sent in as a last resort. For over three hours, they battled the X-3 Entity inside collapsed containment zones. As the fight progressed, they began adapting — mimicking the anomaly's breach logic, resisting its psychic rot, and evolving mid-combat.</p>
        <p>They didn't just neutralize the entity. They <em style="color:#cc4444">turned its own power against it</em>.</p>
        <p>APA-01 emerged permanently changed — no longer fully human, but something evolved. Something engineered for the inhuman. They became the first operative to eliminate a Tier-4 anomaly — a feat spoken of in hushed reverence across D.I.V.I.D.E. command.</p>
      </div>
    </div>

    <div class="assessment-row">
      <div class="assessment-tag">To Some — A Weapon</div>
      <div class="assessment-tag">To Others — A Warning</div>
      <div class="assessment-tag">A.P.A. Squad Leader</div>
      <div class="assessment-tag">No Longer Fully Human</div>
    </div>

    <!-- MAIN QUOTE -->
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
