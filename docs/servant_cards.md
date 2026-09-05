
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — SYS-01 Servant Card System</title>
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

    /* File header */
    .file-header {
      border: 1px solid #1a1a4a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #05050f 0%, #080808 100%);
    }

    .file-header::before {
      content: '// SYSTEM FILE //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #4444cc;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #4444cc;
      border-right: 2px solid #4444cc;
    }

    .file-id {
      font-size: 11px;
      color: #4444cc;
      letter-spacing: 4px;
      margin-bottom: 6px;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #7777ff;
      letter-spacing: 4px;
      text-shadow: 0 0 20px rgba(100,100,255,0.3);
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
    .meta-value.purple { color: #9c27b0; }
    .meta-value.blue { color: #7777ff; }
    .meta-value.red { color: #cc0000; }
    .meta-value.orange { color: #e65100; }

    /* Section label */
    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #4444cc;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #0a0a2a;
    }

    /* Addendum section label */
    .section-label.addendum {
      color: #9c27b0;
      border-bottom-color: #1a0a2a;
    }

    /* Content block */
    .content-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #1a1a4a;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      line-height: 1.9;
      color: #888;
    }

    .content-block p { margin-bottom: 8px; }
    .content-block p:last-child { margin-bottom: 0; }

    /* Mechanic grid */
    .mechanic-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .mechanic-grid { grid-template-columns: 1fr; } }

    .mechanic-card {
      padding: 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-top: 3px solid #1a1a4a;
      font-size: 11px;
      color: #777;
      line-height: 1.7;
    }

    .mechanic-card .title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 600;
      color: #7777ff;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 8px;
    }

    /* Rule items */
    .rule-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #1a1a4a;
      font-size: 12px;
      color: #888;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .rule-item .arrow { color: #4444cc; flex-shrink: 0; margin-top: 2px; }

    /* Denied items */
    .denied-item {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a0000;
      border-left: 3px solid #8b0000;
      font-size: 12px;
      color: #cc4444;
      margin-bottom: 5px;
    }

    .denied-item .x { color: #cc0000; font-size: 14px; }

    /* Warning block */
    .warning-block {
      background: #0d0000;
      border: 1px solid #3a0000;
      border-left: 3px solid #cc0000;
      padding: 14px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      color: #cc4444;
      line-height: 1.8;
    }

    /* Pulse tier cards */
    .pulse-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .pulse-grid { grid-template-columns: 1fr; } }

    .pulse-card {
      padding: 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      font-size: 11px;
      color: #777;
      line-height: 1.7;
    }

    .pulse-card .tier {
      font-family: 'Rajdhani', sans-serif;
      font-size: 13px;
      font-weight: 700;
      letter-spacing: 2px;
      margin-bottom: 6px;
      text-transform: uppercase;
    }

    .pulse-card.low  { border-top: 3px solid #4fc3f7; }
    .pulse-card.low .tier { color: #4fc3f7; }

    .pulse-card.mid  { border-top: 3px solid #ffd600; }
    .pulse-card.mid .tier { color: #ffd600; }

    .pulse-card.high { border-top: 3px solid #f44336; }
    .pulse-card.high .tier { color: #f44336; }

    /* Status badge */
    .status-badge {
      display: inline-block;
      padding: 3px 10px;
      font-size: 10px;
      letter-spacing: 2px;
      border: 1px solid;
      text-transform: uppercase;
      margin-top: 6px;
    }

    .status-badge.unverified { color: #e65100; border-color: #4a1a00; }
    .status-badge.high { color: #cc0000; border-color: #3a0000; }

    /* Quote blocks */
    .internal-quote {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #7777ff;
      padding: 20px 24px;
      margin: 16px 0;
      position: relative;
    }

    .internal-quote::before {
      content: '"';
      position: absolute;
      top: -10px; left: 16px;
      background: #080808;
      padding: 0 6px;
      color: #7777ff;
      font-size: 30px;
      font-family: serif;
      line-height: 1;
    }

    .internal-quote.purple { border-left-color: #9c27b0; }
    .internal-quote.purple::before { color: #9c27b0; }

    .internal-quote p { font-size: 13px; color: #aaa; line-height: 1.8; font-style: italic; }
    .internal-quote .attribution { margin-top: 10px; font-size: 10px; color: #555; letter-spacing: 2px; text-transform: uppercase; font-style: normal; }

    /* Addendum header */
    .addendum-header {
      border: 1px solid #1a0a2a;
      padding: 20px 24px;
      margin-top: 40px;
      margin-bottom: 16px;
      position: relative;
      background: linear-gradient(180deg, #0a050f 0%, #080808 100%);
    }

    .addendum-header::before {
      content: '// ADDENDUM //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #9c27b0;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .addendum-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 30px; height: 30px;
      border-top: 2px solid #9c27b0;
      border-right: 2px solid #9c27b0;
    }

    .addendum-id {
      font-size: 10px;
      color: #9c27b0;
      letter-spacing: 4px;
      margin-bottom: 4px;
    }

    .addendum-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 22px;
      font-weight: 700;
      color: #ce7adb;
      letter-spacing: 3px;
      text-shadow: 0 0 12px rgba(156,39,176,0.3);
    }

    /* Research priority */
    .priority-box {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 14px 18px;
      background: #0d0000;
      border: 1px solid #3a0000;
      border-left: 4px solid #cc0000;
      margin-bottom: 8px;
    }

    .priority-label {
      font-size: 10px;
      color: #555;
      letter-spacing: 2px;
      text-transform: uppercase;
    }

    .priority-value {
      font-family: 'Rajdhani', sans-serif;
      font-size: 18px;
      font-weight: 700;
      color: #cc0000;
      letter-spacing: 3px;
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
      <div class="file-id">FILE: SYS-01</div>
      <div class="file-title">SERVANT CARD SYSTEM</div>
      <div class="file-designation">Post-Termination Anomalous Artifact System — Active Research</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">THREAT LEVEL</span>
          <span class="meta-value purple">Variable — User Dependent</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">DIVIDE Level 2+</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">STATUS</span>
          <span class="meta-value orange">Uncontained / Monitored</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">RESEARCH PRIORITY</span>
          <span class="meta-value red">HIGH</span>
        </div>
      </div>
    </div>

    <!-- OVERVIEW -->
    <div class="section-label">// Overview //</div>
    <div class="content-block">
      <p>The Servant Card System refers to a rare phenomenon in which a terminated anomaly has an extremely low probability of generating a physical artifact known as a <strong style="color:#aaa">Servant Card</strong>.</p>
      <p>These cards allow the holder to summon a bound version of the original anomaly. The mechanism of generation is not fully understood. D.I.V.I.D.E. research into the origin of the phenomenon remains ongoing with HIGH priority classification.</p>
    </div>

    <!-- ACQUISITION -->
    <div class="section-label">// Acquisition Conditions //</div>
    <div class="mechanic-grid">
      <div class="mechanic-card">
        <div class="title">Trigger</div>
        Successful termination of an anomaly. Drop rate is near-zero. Cannot be forced or predicted.
      </div>
      <div class="mechanic-card">
        <div class="title">Eligible</div>
        Living and sentient anomalies only. Item anomalies and location anomalies do not generate cards.
      </div>
      <div class="mechanic-card">
        <div class="title">Drop Rate</div>
        Near-zero probability. Exact figures classified. Most termination events yield no artifact.
      </div>
    </div>

    <!-- SUMMONING -->
    <div class="section-label">// Summoning Rules //</div>
    <div class="rule-item"><span class="arrow">▶</span>Servants can be summoned, dismissed, and re-summoned at will by the card holder.</div>
    <div class="rule-item"><span class="arrow">▶</span>If the Servant is killed while summoned, the card becomes permanently inactive and cannot be restored or repaired.</div>

    <div class="denied-item"><span class="x">✕</span>Item anomalies — ineligible for card generation</div>
    <div class="denied-item"><span class="x">✕</span>Location anomalies — ineligible for card generation</div>
    <div class="denied-item"><span class="x">✕</span>Activated cards — cannot be sold or transferred</div>

    <!-- POWER SCALING -->
    <div class="section-label">// Power Scaling //</div>
    <div class="content-block">
      <p>Servants are not exact copies of the original anomaly. Their effective power is influenced by user compatibility, psychological alignment, and unknown external factors.</p>
      <p>Some Servants manifest weaker than the original entity. Others exceed the original's power under specific users. The compatibility mechanism is not fully understood.</p>
    </div>

    <div class="mechanic-grid">
      <div class="mechanic-card">
        <div class="title">High Sync</div>
        Reaction time improves drastically. Combat coordination becomes near-perfect. Power output increases beyond baseline.
      </div>
      <div class="mechanic-card">
        <div class="title">Recorded Case</div>
        A Tier I anomaly paired with a compatible human user achieved perfect synchronization and was temporarily reclassified as a Tier III combat threat.
      </div>
      <div class="mechanic-card">
        <div class="title">High Tier Risk</div>
        High-tier Servants are more likely to reject control, act independently, and refuse participation entirely. Instability scales with power.
      </div>
    </div>

    <!-- BEHAVIOR -->
    <div class="section-label">// Behavior & Control //</div>
    <div class="content-block">
      <p>Servants generally follow commands. However, they are not fully controlled entities. Known exceptions include refusal of commands, refusal to fight, and refusal to be summoned at all.</p>
    </div>

    <div class="warning-block">
      <strong style="color:#ff4444">CRITICAL INCIDENT — SC-01:</strong><br>
      A Servant rejected its master, terminated the summoner, and immediately de-summoned itself afterward. No further incidents of this type have been formally recorded. Probability of recurrence: unknown.
    </div>

    <!-- TRADE -->
    <div class="section-label">// Trade & Black Market //</div>
    <div class="rule-item"><span class="arrow">▶</span>Servant Cards are extremely rare, highly valuable, and traded primarily within Black Street.</div>
    <div class="rule-item"><span class="arrow">▶</span>Unused cards can be sold or stolen. Once activated through summoning, ownership becomes permanently bound to the user.</div>
    <div class="rule-item"><span class="arrow">▶</span>D.I.V.I.D.E. actively monitors card circulation and attempts acquisition when possible.</div>

    <!-- RISK -->
    <div class="section-label">// Risk Classification //</div>
    <div class="mechanic-grid">
      <div class="mechanic-card">
        <div class="title">Permanent Loss</div>
        If the Servant dies while active, the card is gone forever. No recovery. No repair. High-tier cards represent catastrophic value loss.
      </div>
      <div class="mechanic-card">
        <div class="title">Unstable Obedience</div>
        Servants are not guaranteed to follow orders. High-tier entities may ignore commands entirely or act against the holder's interests.
      </div>
      <div class="mechanic-card">
        <div class="title">User Termination</div>
        Documented cases of Servants killing their summoners exist. Risk scales with tier and psychological incompatibility.
      </div>
    </div>

    <div class="priority-box">
      <div>
        <div class="priority-label">D.I.V.I.D.E. Research Priority</div>
        <div class="priority-value">HIGH</div>
      </div>
      <div style="font-size: 11px; color: #666; line-height: 1.6;">Origin mechanism unknown. Circulation monitored. Acquisition attempted when possible. Full understanding has not been achieved.</div>
    </div>

    <div class="internal-quote">
      <p>You don't own them.<br>You convince them not to kill you.</p>
      <div class="attribution">— D.I.V.I.D.E. Anomalous Systems Division</div>
    </div>

    <!-- ADDENDUM -->
    <div class="addendum-header">
      <div class="addendum-id">ADDENDUM: SYS-01-A</div>
      <div class="addendum-title">Card Fracture Pulse Phenomenon</div>
    </div>

    <div class="section-label addendum">// Fracture Behavior //</div>
    <div class="content-block" style="border-left-color: #3a0a4a;">
      <p>Upon initial summoning from a Servant Card, the card undergoes a micro-fracture event accompanied by the release of an anomalous energy surge designated as a <strong style="color:#aaa">Fracture Pulse</strong>. This phenomenon has been confirmed in all successful summoning events.</p>
      <p>The card develops visible cracks across its surface. These cracks do not destroy the card but remain permanently. Crack patterns appear unique per anomaly. With each subsequent summon, existing fractures expand slightly and structural integrity degrades over time.</p>
    </div>

    <div class="section-label addendum">// Fracture Pulse Characteristics //</div>
    <div class="rule-item" style="border-left-color: #3a0a4a;"><span class="arrow" style="color:#9c27b0;">▶</span>Origin point: Card location. Duration under 1 second.</div>
    <div class="rule-item" style="border-left-color: #3a0a4a;"><span class="arrow" style="color:#9c27b0;">▶</span>Detectable by D.I.V.I.D.E. monitoring systems and high-sensitivity anomaly sensors.</div>
    <div class="rule-item" style="border-left-color: #3a0a4a;"><span class="arrow" style="color:#9c27b0;">▶</span>Pulse intensity scales directly with the Servant's effective power tier.</div>

    <div class="section-label addendum">// Pulse Intensity by Tier //</div>
    <div class="pulse-grid">
      <div class="pulse-card low">
        <div class="tier">Class I — Low</div>
        Barely detectable. Localized disturbance only. Standard monitoring may miss entirely.
      </div>
      <div class="pulse-card mid">
        <div class="tier">Class II–III — Mid</div>
        Noticeable energy spike. Trackable within the surrounding region. Raises monitoring flags.
      </div>
      <div class="pulse-card high">
        <div class="tier">Class IV+ — High</div>
        Strong anomaly signal. Triggers immediate D.I.V.I.D.E. attention. Possible temporary environmental distortion.
      </div>
    </div>

    <div class="section-label addendum">// Operational Risks //</div>
    <div class="rule-item" style="border-left-color: #3a0a4a;"><span class="arrow" style="color:#9c27b0;">▶</span>Repeated summoning increases detection risk and card structural instability simultaneously.</div>
    <div class="rule-item" style="border-left-color: #3a0a4a;"><span class="arrow" style="color:#9c27b0;">▶</span>High-frequency use may attract nearby anomalies and interfere with adjacent anomalous systems.</div>

    <div class="content-block" style="border-left-color: #3a0a4a; margin-top: 8px;">
      <p><strong style="color:#aaa">Failure Risk (Unconfirmed):</strong> Ongoing investigations suggest excessive fracturing may result in uncontrolled Servant manifestation, permanent summoning state, or hostile behavior deviation from baseline parameters.</p>
      <div style="margin-top: 10px;"><span class="status-badge unverified">Status: Unverified</span></div>
    </div>

    <div class="section-label addendum">// D.I.V.I.D.E. Utilization //</div>
    <div class="rule-item" style="border-left-color: #3a0a4a;"><span class="arrow" style="color:#9c27b0;">▶</span>Fracture Pulses are actively used to track Servant Card usage globally.</div>
    <div class="rule-item" style="border-left-color: #3a0a4a;"><span class="arrow" style="color:#9c27b0;">▶</span>Unauthorized summoning events are identified and investigated through pulse signature analysis.</div>
    <div class="rule-item" style="border-left-color: #3a0a4a;"><span class="arrow" style="color:#9c27b0;">▶</span>High-value targets are located through sustained pulse tracking over time.</div>

    <div class="internal-quote purple">
      <p>We thought the cards were quiet tools.<br>Turns out every time you use one… you're lighting a flare.</p>
      <div class="attribution">— D.I.V.I.D.E. Monitoring Division — Internal Log FP-07</div>
    </div>

    <div class="footer">
      <p>&copy; 2026 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2026-04-24</p>
    </div>

  </div>

</body>
</html>
