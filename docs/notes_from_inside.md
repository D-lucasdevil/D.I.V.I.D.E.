
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Classification System</title>
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
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #8b0000;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #8b0000;
      border-right: 2px solid #8b0000;
    }

    .site-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 36px;
      font-weight: 700;
      color: #cc0000;
      letter-spacing: 6px;
      text-shadow: 0 0 20px rgba(200,0,0,0.4);
      margin-bottom: 6px;
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

    /* Section divider */
    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #8b0000;
      text-transform: uppercase;
      margin-bottom: 16px;
      margin-top: 40px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a0000;
    }

    /* Class card */
    .class-card {
      border: 1px solid #1a1a1a;
      border-left: 4px solid;
      margin-bottom: 10px;
      overflow: hidden;
      transition: border-color 0.2s;
    }

    .class-header {
      display: flex;
      align-items: center;
      gap: 16px;
      padding: 14px 18px;
      cursor: pointer;
      transition: background 0.2s;
    }

    .class-header:hover { background: rgba(255,255,255,0.02); }

    .class-badge {
      font-family: 'Rajdhani', sans-serif;
      font-size: 18px;
      font-weight: 700;
      letter-spacing: 2px;
      min-width: 80px;
    }

    .class-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      font-weight: 600;
      letter-spacing: 3px;
      text-transform: uppercase;
      flex: 1;
    }

    .class-body {
      padding: 0 18px 16px 18px;
      font-size: 12px;
      line-height: 1.8;
      color: #888;
      border-top: 1px solid #111;
    }

    .class-body p { margin-top: 10px; }

    .class-body .example {
      margin-top: 10px;
      padding: 10px 14px;
      background: #0a0a0a;
      border-left: 2px solid #222;
      font-size: 11px;
      color: #666;
      font-style: italic;
    }

    /* Pulse card */
    .pulse-card {
      display: flex;
      gap: 16px;
      align-items: flex-start;
      padding: 12px 16px;
      border: 1px solid #1a1a1a;
      border-left: 4px solid;
      margin-bottom: 8px;
      font-size: 12px;
    }

    .pulse-level {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      font-weight: 700;
      min-width: 30px;
      letter-spacing: 1px;
    }

    .pulse-name {
      font-size: 11px;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 4px;
    }

    .pulse-desc {
      color: #666;
      font-size: 11px;
      line-height: 1.6;
    }

    /* Clearance card */
    .clearance-card {
      display: flex;
      gap: 16px;
      padding: 12px 16px;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0000;
      margin-bottom: 6px;
      align-items: flex-start;
      transition: border-color 0.2s, background 0.2s;
    }

    .clearance-card:hover {
      border-left-color: #8b0000;
      background: #0d0000;
    }

    .clearance-level {
      font-family: 'Rajdhani', sans-serif;
      font-size: 20px;
      font-weight: 700;
      color: #cc0000;
      min-width: 30px;
    }

    .clearance-title {
      font-size: 12px;
      letter-spacing: 2px;
      color: #cc0000;
      text-transform: uppercase;
      margin-bottom: 4px;
    }

    .clearance-desc {
      font-size: 11px;
      color: #666;
      line-height: 1.6;
    }

    /* Info box */
    .info-box {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #8b0000;
      padding: 16px 18px;
      margin-bottom: 10px;
      font-size: 12px;
      line-height: 1.8;
      color: #888;
    }

    .info-box h3 {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      letter-spacing: 2px;
      color: #aaa;
      margin-bottom: 8px;
      text-transform: uppercase;
    }

    .info-box ul {
      padding-left: 16px;
      color: #666;
    }

    .info-box ul li { margin-bottom: 4px; }

    /* Tier colors */
    .c0    { border-left-color: #666; }
    .c0 .class-badge, .c0 .class-name { color: #888; }

    .c1    { border-left-color: #4fc3f7; }
    .c1 .class-badge, .c1 .class-name { color: #4fc3f7; }

    .c2    { border-left-color: #4caf50; }
    .c2 .class-badge, .c2 .class-name { color: #4caf50; }

    .c3    { border-left-color: #ffd600; }
    .c3 .class-badge, .c3 .class-name { color: #ffd600; }

    .c4    { border-left-color: #e65100; }
    .c4 .class-badge, .c4 .class-name { color: #e65100; }

    .c5    { border-left-color: #f44336; }
    .c5 .class-badge, .c5 .class-name { color: #f44336; }

    .c6    { border-left-color: #9c27b0; }
    .c6 .class-badge, .c6 .class-name { color: #9c27b0; }

    .c7    { border-left-color: #cc00cc; }
    .c7 .class-badge, .c7 .class-name { color: #cc00cc; text-shadow: 0 0 8px rgba(204,0,204,0.4); }

    .comega { border-left-color: #fff; }
    .comega .class-badge, .comega .class-name { color: #fff; text-shadow: 0 0 12px rgba(255,255,255,0.3); }

    .credacted { border-left-color: #ff69b4; }
    .credacted .class-badge, .credacted .class-name { color: #ff69b4; text-shadow: 0 0 8px rgba(255,105,180,0.3); }

    /* Pulse tier colors */
    .p1 { border-left-color: #4fc3f7; }
    .p1 .pulse-level, .p1 .pulse-name { color: #4fc3f7; }

    .p2 { border-left-color: #4caf50; }
    .p2 .pulse-level, .p2 .pulse-name { color: #4caf50; }

    .p3 { border-left-color: #ffd600; }
    .p3 .pulse-level, .p3 .pulse-name { color: #ffd600; }

    .p4 { border-left-color: #e65100; }
    .p4 .pulse-level, .p4 .pulse-name { color: #e65100; }

    .p5 { border-left-color: #f44336; }
    .p5 .pulse-level, .p5 .pulse-name { color: #f44336; }

    .p6 { border-left-color: #9c27b0; }
    .p6 .pulse-level, .p6 .pulse-name { color: #9c27b0; }

    .pomega { border-left-color: #fff; }
    .pomega .pulse-level, .pomega .pulse-name { color: #fff; text-shadow: 0 0 8px rgba(255,255,255,0.3); }

    .footer {
      border-top: 1px solid #1a0000;
      padding-top: 20px;
      margin-top: 40px;
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

    <div class="header">
      <div class="site-title">CLASSIFICATION SYSTEM</div>
      <div class="site-subtitle">Anomaly Threat Levels, Pulse Ratings & Clearance Protocols</div>
      <div class="clearance-badge">Clearance Level 1+ Required</div>
    </div>

    <!-- ANOMALY CLASSES -->
    <div class="section-label">// Anomaly Threat Classification //</div>

    <div class="class-card c1">
      <div class="class-header">
        <div class="class-badge">I</div>
        <div class="class-name">Low Threat</div>
      </div>
      <div class="class-body">
        <p>Minimal risk. Typically stable and harmless anomalies that do not alter their environment or pose significant danger unless provoked.</p>
        <div class="example">Example: A sentient entity that remains passive under standard conditions and exhibits no environmental manipulation.</div>
      </div>
    </div>

    <div class="class-card c2">
      <div class="class-header">
        <div class="class-badge">II</div>
        <div class="class-name">Moderate Threat</div>
      </div>
      <div class="class-body">
        <p>Some risk, though manageable with standard containment procedures. These anomalies exhibit defensive or reactive behavior under specific circumstances.</p>
        <div class="example">Example: An entity that becomes hostile when approached, but can be stabilized with standard containment protocols.</div>
      </div>
    </div>

    <div class="class-card c3">
      <div class="class-header">
        <div class="class-badge">III</div>
        <div class="class-name">High Threat</div>
      </div>
      <div class="class-body">
        <p>Potential for significant danger if mishandled. Requires strict monitoring and specialized safety protocols. These anomalies are capable of direct harm or environmental manipulation.</p>
        <div class="example">Example: An entity capable of causing casualties through direct action or reality-adjacent manipulation of its immediate environment.</div>
      </div>
    </div>

    <div class="class-card c4">
      <div class="class-header">
        <div class="class-badge">IV</div>
        <div class="class-name">Extreme Threat</div>
      </div>
      <div class="class-body">
        <p>Significant risk to personnel and surrounding environment. Requires specialized containment and constant monitoring. These anomalies can alter environmental factors or reality within a confined space.</p>
        <div class="example">Example: An anomaly capable of altering local reality, warping physical laws, or neutralizing standard containment measures.</div>
      </div>
    </div>

    <div class="class-card c5">
      <div class="class-header">
        <div class="class-badge">V</div>
        <div class="class-name">Catastrophic Threat</div>
      </div>
      <div class="class-body">
        <p>Large-scale destructive potential. Full understanding of the entity may not be possible. These anomalies can erase or alter memories, timelines, or existence on a grand scale.</p>
        <div class="example">Example: A reality-warping entity capable of erasing localized existence or restructuring physical and metaphysical elements across wide areas.</div>
      </div>
    </div>

    <div class="class-card c6">
      <div class="class-header">
        <div class="class-badge">VI</div>
        <div class="class-name">Omega-Class Threat</div>
      </div>
      <div class="class-body">
        <p>The most extreme threats known to D.I.V.I.D.E. These entities are capable of overwhelming large-scale destruction, manipulating fundamental aspects of reality, and causing chaos across dimensions. Their power is limitless and exceeds the scope of all standard classification systems.</p>
        <div class="example">Example: An entity whose presence destabilizes entire dimensional strata, rendering standard containment protocols irrelevant.</div>
      </div>
    </div>

    <div class="class-card c7">
      <div class="class-header">
        <div class="class-badge">VII</div>
        <div class="class-name">[DATA EXPUNGED]</div>
      </div>
      <div class="class-body">
        <p>[REDACTED — DIVIDE LEVEL CLEARANCE REQUIRED]</p>
        <div class="example">[ACCESS DENIED]</div>
      </div>
    </div>

    <div class="class-card comega">
      <div class="class-header">
        <div class="class-badge">Ω</div>
        <div class="class-name">The End</div>
      </div>
      <div class="class-body">
        <p>There is nothing you can do. We are all dead.</p>
        <p>Ω-Class anomalies are uncontainable, capable of reshaping time, space, and reality itself. Their influence extends far beyond the physical realm. They are often considered apocalyptic in nature. These anomalies exist beyond all known physical or metaphysical constraints — capable of manipulating and controlling life, death, and reality itself.</p>
        <p><strong style="color:#aaa">Containment:</strong> Impossible. These anomalies defy the fundamental laws of the universe. No measures exist or are theorized to be achievable.</p>
        <div class="example">Anomaly Ω-01: A being whose presence can collapse entire galaxies, alter timelines, or erase life from existence.<br><br>Anomaly Ω-02: A cosmic entity that governs life and death across multiple dimensions, able to create and destroy universes with a single action.</div>
      </div>
    </div>

    <div class="class-card credacted">
      <div class="class-header">
        <div class="class-badge">—</div>
        <div class="class-name">Redacted Anomalies</div>
      </div>
      <div class="class-body">
        <p>Entities that are either too dangerous, unknown, or classified as too great a threat to disclose. These anomalies are beyond containment and may fall under Ω-Class, but their exact nature remains sealed by the highest authorities of D.I.V.I.D.E.</p>
        <p><strong style="color:#aaa">Access:</strong> D.I.V.I.D.E. Level clearance required. No exceptions.</p>
        <div class="example">[ALL FURTHER DATA SUPPRESSED]</div>
      </div>
    </div>

    <!-- HOW ANOMALIES WORK -->
    <div class="section-label">// How Anomalies Work //</div>

    <div class="info-box">
      <h3>What Does "LD" Stand For?</h3>
      <p>The classification code "LD" stands for <strong style="color:#aaa">Liminal Division</strong> — the division responsible for locating, documenting, and (if possible) containing or neutralizing supernatural, reality-bending, or otherwise anomalous entities and objects. Each anomaly is assigned a unique LD ID number for cataloging and identification.</p>
    </div>

    <div class="info-box">
      <h3>Why Are Some Anomalies Missing?</h3>
      <ul>
        <li><strong style="color:#aaa">Terminated Cases:</strong> Some anomalies were permanently destroyed or neutralized and removed from active records.</li>
        <li><strong style="color:#aaa">Undiscovered Anomalies:</strong> The world is vast — many anomalies remain hidden or misunderstood. Reports come in daily from across the globe.</li>
        <li><strong style="color:#aaa">Withheld or Stolen:</strong> Certain individuals have discovered powerful anomalies and taken them for personal use — rogue agents, civilians, and corporate interests.</li>
        <li><strong style="color:#aaa">Task Force Suppression:</strong> The APA Task Force actively hunts, retrieves, or destroys anomalies before they spread. Some slip through.</li>
      </ul>
    </div>

    <div class="info-box">
      <h3>What Qualifies as an Anomaly?</h3>
      <p>Any object, creature, location, or substance that breaks known scientific laws or causes extreme psychological, physical, or dimensional effects. Most anomalies:</p>
      <ul>
        <li>Defy conventional physics or biology</li>
        <li>Exhibit sentience, manipulation, or hostile traits</li>
        <li>Cannot be safely explained or reproduced</li>
        <li>Must be handled under strict containment protocols</li>
      </ul>
    </div>

    <!-- PULSES -->
    <div class="section-label">// Anomaly Pulse System //</div>

    <div class="info-box" style="margin-bottom: 16px;">
      <h3>What Are Pulses?</h3>
      <p>Pulses are intense bursts of reality distortion that occur exclusively when an anomaly first manifests or breaches into our reality — a signature "rip" in the fabric of space-time. Each anomaly generates exactly one Pulse at the moment of arrival. The magnitude directly reflects the threat level. Pulses are rare, one-time events that cannot be replicated.</p>
    </div>

    <div class="pulse-card p1">
      <div>
        <div class="pulse-level">1</div>
      </div>
      <div>
        <div class="pulse-name">Minor Distortion — Class I</div>
        <div class="pulse-desc">Slight, barely noticeable ripples in reality. Often detected only by sensitive instruments. No immediate danger.</div>
      </div>
    </div>

    <div class="pulse-card p2">
      <div>
        <div class="pulse-level">2</div>
      </div>
      <div>
        <div class="pulse-name">Noticeable Ripple — Class II</div>
        <div class="pulse-desc">Detectable dimensional pulses causing mild spatial disturbances. Usually stable but signals an active anomaly.</div>
      </div>
    </div>

    <div class="pulse-card p3">
      <div>
        <div class="pulse-level">3</div>
      </div>
      <div>
        <div class="pulse-name">Severe Fluctuation — Class III</div>
        <div class="pulse-desc">Strong reality disruptions manifesting as visible distortions or auditory anomalies. Can cause environmental interference and requires caution.</div>
      </div>
    </div>

    <div class="pulse-card p4">
      <div>
        <div class="pulse-level">4</div>
      </div>
      <div>
        <div class="pulse-name">Critical Tear — Class IV</div>
        <div class="pulse-desc">Intense, violent rips in space-time. These pulses cause hazardous phenomena around the anomaly's vicinity. Immediate containment necessary.</div>
      </div>
    </div>

    <div class="pulse-card p5">
      <div>
        <div class="pulse-level">5</div>
      </div>
      <div>
        <div class="pulse-name">Catastrophic Rend — Class V</div>
        <div class="pulse-desc">Massive reality ruptures capable of large-scale destruction and erasure of physical or metaphysical elements. Signals an anomaly of global or universal threat.</div>
      </div>
    </div>

    <div class="pulse-card p6">
      <div>
        <div class="pulse-level">6</div>
      </div>
      <div>
        <div class="pulse-name">Omega Surge — Class VI</div>
        <div class="pulse-desc">Uncontainable and omnipresent pulses disrupting multiple dimensions. These surges often precede apocalyptic events or interdimensional collapse.</div>
      </div>
    </div>

    <div class="pulse-card pomega">
      <div>
        <div class="pulse-level">Ω</div>
      </div>
      <div>
        <div class="pulse-name">The End Wave — Class Ω</div>
        <div class="pulse-desc">The final, unstoppable pulse signaling total annihilation. All known laws break down. No containment or resistance possible.</div>
      </div>
    </div>

    <!-- CLEARANCE LEVELS -->
    <div class="section-label">// Clearance Levels //</div>

    <div class="clearance-card">
      <div class="clearance-level">1</div>
      <div>
        <div class="clearance-title">Entry-Level Access</div>
        <div class="clearance-desc">Basic security access. Non-sensitive anomalies and public records only. General staff, researchers, and new personnel.</div>
      </div>
    </div>

    <div class="clearance-card">
      <div class="clearance-level">2</div>
      <div>
        <div class="clearance-title">Restricted Access</div>
        <div class="clearance-desc">Specific anomalies and sensitive areas. Limited access to dangerous or volatile entities. Security personnel and authorized technicians.</div>
      </div>
    </div>

    <div class="clearance-card">
      <div class="clearance-level">3</div>
      <div>
        <div class="clearance-title">Intermediate Access</div>
        <div class="clearance-desc">Common research and standard containment protocols. Full access to classified anomalies at moderate clearance. Containment staff and researchers on routine high-risk cases.</div>
      </div>
    </div>

    <div class="clearance-card">
      <div class="clearance-level">4</div>
      <div>
        <div class="clearance-title">Advanced Access</div>
        <div class="clearance-desc">High-risk anomalies, restricted data, and classified operations. Senior researchers, top-level security personnel, and department heads.</div>
      </div>
    </div>

    <div class="clearance-card">
      <div class="clearance-level">5</div>
      <div>
        <div class="clearance-title">Specialized Access</div>
        <div class="clearance-desc">Study of anomalies with dangerous or unknown properties. Leading experts in anomaly research and specialized containment team leaders.</div>
      </div>
    </div>

    <div class="clearance-card">
      <div class="clearance-level">6</div>
      <div>
        <div class="clearance-title">Expert Access</div>
        <div class="clearance-desc">Top researchers and operatives with direct anomaly containment responsibilities. Highest-level containment protocols and restricted materials.</div>
      </div>
    </div>

    <div class="clearance-card">
      <div class="clearance-level">7</div>
      <div>
        <div class="clearance-title">Omega-Class Access</div>
        <div class="clearance-desc">Full operational control over the most dangerous or unknown entities. Command authority over catastrophic anomaly situations. Top-level operatives with global influence over anomaly management.</div>
      </div>
    </div>

    <div class="clearance-card" style="border-left-color: #cc0000; background: #0d0000;">
      <div class="clearance-level" style="color:#ff4444; font-size: 14px; letter-spacing: 1px; padding-top: 4px;">D.I.V.I.D.E.</div>
      <div>
        <div class="clearance-title" style="color: #ff4444;">D.I.V.I.D.E. Clearance — Absolute Authority</div>
        <div class="clearance-desc">The highest level of access. Grants complete authority over all anomalies including execution, containment, and release. Allows override of all containment protocols and authorization of the Foundation's self-destruction — including simultaneous activation of 50 nuclear warheads. Reserved for the highest authorities of the Foundation. Used only in cases of existential crisis or global catastrophe. No sub-levels exist.</div>
      </div>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
