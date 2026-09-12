
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Dr. Manarine Hypertheos</title>
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

    /* Header — purple for special individual */
    .file-header {
      border: 1px solid #3a0a4a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #0a050f 0%, #080808 100%);
    }

    .file-header::before {
      content: '// SPECIAL INDIVIDUAL — S.I.-001 — LEVEL 7+ //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #9c27b0;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #9c27b0;
      border-right: 2px solid #9c27b0;
    }

    .file-id {
      font-size: 11px;
      color: #9c27b0;
      letter-spacing: 4px;
      margin-bottom: 6px;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 36px;
      font-weight: 700;
      color: #ce7adb;
      letter-spacing: 3px;
      text-shadow: 0 0 20px rgba(156,39,176,0.3);
      margin-bottom: 4px;
    }

    .file-nickname {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      color: #9c27b0;
      letter-spacing: 2px;
      font-style: italic;
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
    .meta-value.red { color: #cc0000; }
    .meta-value.orange { color: #e65100; }
    .meta-value.yellow { color: #ffd600; }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #9c27b0;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a0a2a;
    }

    .content-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0a4a;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      line-height: 1.9;
      color: #888;
    }

    .content-block p { margin-bottom: 8px; }
    .content-block p:last-child { margin-bottom: 0; }

    /* Discovery list */
    .discovery-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0a4a;
      font-size: 12px;
      color: #888;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .discovery-item .arrow { color: #9c27b0; flex-shrink: 0; margin-top: 2px; }

    /* Hypothesis box */
    .hypothesis-box {
      background: #0a050f;
      border: 1px solid #2a0a3a;
      border-left: 4px solid #9c27b0;
      padding: 20px;
      margin-bottom: 8px;
    }

    .hypothesis-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      font-weight: 700;
      color: #ce7adb;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 14px;
      text-shadow: 0 0 10px rgba(156,39,176,0.3);
    }

    .hypothesis-body {
      font-size: 12px;
      color: #888;
      line-height: 1.9;
    }

    .hypothesis-body p { margin-bottom: 8px; }
    .hypothesis-body p:last-child { margin-bottom: 0; }

    /* Incident OH-088 */
    .incident-box {
      background: #0d0000;
      border: 1px solid #3a0000;
      border-left: 4px solid #f44336;
      padding: 20px;
      margin-bottom: 8px;
    }

    .incident-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 15px;
      font-weight: 700;
      color: #f44336;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 14px;
    }

    .incident-body {
      font-size: 12px;
      color: #884444;
      line-height: 1.9;
    }

    .incident-body p { margin-bottom: 8px; }
    .incident-body p:last-child { margin-bottom: 0; }

    /* Dialogue lines */
    .dialogue {
      padding: 10px 16px;
      margin: 8px 0;
      font-size: 12px;
      font-style: italic;
      line-height: 1.7;
      border-left: 3px solid;
    }

    .dialogue.entity {
      border-left-color: #9c27b0;
      color: #ce7adb;
      background: #0a050f;
    }

    .dialogue.subject {
      border-left-color: #555;
      color: #777;
      background: #0d0d0d;
    }

    .dialogue.hypertheos {
      border-left-color: #4fc3f7;
      color: #7dd5f7;
      background: #050d12;
    }

    .dialogue .speaker {
      font-size: 9px;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 4px;
      font-style: normal;
      opacity: 0.6;
    }

    /* Silence moment */
    .silence-box {
      background: #080808;
      border: 1px solid #111;
      padding: 16px 20px;
      margin: 12px 0;
      text-align: center;
    }

    .silence-count {
      font-family: 'Rajdhani', sans-serif;
      font-size: 28px;
      font-weight: 700;
      color: #333;
      letter-spacing: 4px;
    }

    .silence-label {
      font-size: 10px;
      color: #2a2a2a;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-top: 4px;
    }

    /* LD correlation list */
    .ld-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 5px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .ld-grid { grid-template-columns: repeat(2, 1fr); } }

    .ld-tag {
      padding: 8px 10px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0a4a;
      font-size: 11px;
      color: #9c27b0;
      letter-spacing: 1px;
      text-align: center;
      font-family: 'Rajdhani', sans-serif;
      font-weight: 700;
    }

    /* Objective possibilities */
    .objective-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a0a1a;
      border-left: 3px solid #3a0a3a;
      font-size: 12px;
      color: #777;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .objective-item .q { color: #9c27b0; flex-shrink: 0; }

    /* Surveillance list */
    .surveillance-item {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 8px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #2a0000;
      font-size: 12px;
      color: #884444;
      margin-bottom: 5px;
    }

    .surveillance-item .dot {
      width: 5px; height: 5px;
      background: #cc0000;
      border-radius: 50%;
      flex-shrink: 0;
    }

    /* Quote blocks */
    .internal-quote {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #9c27b0;
      padding: 18px 22px;
      margin: 16px 0;
      position: relative;
    }

    .internal-quote::before {
      content: '"';
      position: absolute;
      top: -10px; left: 16px;
      background: #080808;
      padding: 0 6px;
      color: #9c27b0;
      font-size: 28px;
      font-family: serif;
      line-height: 1;
    }

    .internal-quote p { font-size: 13px; color: #aaa; line-height: 1.8; font-style: italic; }
    .internal-quote .attribution { margin-top: 10px; font-size: 10px; color: #555; letter-spacing: 2px; text-transform: uppercase; font-style: normal; }

    /* Final directive */
    .directive-box {
      background: #0d0000;
      border: 2px solid #cc0000;
      padding: 20px 24px;
      margin-top: 24px;
    }

    .directive-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      font-weight: 700;
      color: #f44336;
      letter-spacing: 4px;
      text-transform: uppercase;
      margin-bottom: 16px;
    }

    .directive-line {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 8px 0;
      border-bottom: 1px solid #1a0000;
      font-size: 12px;
      color: #884444;
      line-height: 1.6;
    }

    .directive-line:last-child { border-bottom: none; }
    .directive-line .warn { color: #cc0000; flex-shrink: 0; }

    .directive-final {
      margin-top: 14px;
      padding: 12px 16px;
      background: #080000;
      border-left: 3px solid #f44336;
      font-size: 12px;
      color: #cc4444;
      line-height: 1.8;
      font-style: italic;
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
    ⚠ SPECIAL INDIVIDUAL — S.I.-001 — LEVEL 7+ CLEARANCE — DO NOT TERMINATE ⚠
  </div>

  <div class="container">

    <a href="special-individuals.html" class="back-link">← RETURN TO SPECIAL INDIVIDUALS</a>

    <div class="file-header">
      <div class="file-id">FILE: S.I.-001 — SPECIAL INDIVIDUAL — ACTIVE SURVEILLANCE</div>
      <div class="file-title">DR. MANARINE HYPERTHEOS</div>
      <div class="file-nickname">"The Doctor Trying To Be God"</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">OCCUPATION</span>
          <span class="meta-value purple">Senior Anomalous Correlation Researcher</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">DIVIDE Level 7+</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">STATUS</span>
          <span class="meta-value orange">Protected / Permanent Surveillance</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">THREAT CLASS</span>
          <span class="meta-value yellow">UNDETERMINED</span>
        </div>
      </div>
    </div>

    <!-- OVERVIEW -->
    <div class="section-label">// Overview //</div>
    <div class="content-block">
      <p>Dr. Manarine Hypertheos entered D.I.V.I.D.E. as a junior researcher specializing in anomalous behavioral patterns and cross-file comparison. Within several years he became responsible for identifying one of the largest anomalous correlations ever discovered — connecting apparently unrelated LDs to a single theoretical source.</p>
      <p>His first major discovery proposed that LD-069 and LD-088 were not independent anomalies but derivative creations of an Omega-tier entity. The theory was dismissed by nearly every senior researcher. At the time, D.I.V.I.D.E. had only confirmed one Omega-tier anomaly: D.</p>
      <p>Hypertheos argued D.I.V.I.D.E. was making the wrong assumption. He believed D was not necessarily unique. He believed there was another.</p>
    </div>

    <!-- RISE -->
    <div class="section-label">// Rise Through D.I.V.I.D.E. //</div>
    <div class="content-block">
      <p>Following submission of his initial research, Hypertheos advanced rapidly through the research hierarchy. His subsequent discoveries revealed previously ignored similarities across the anomaly catalogue.</p>
    </div>

    <div class="discovery-item"><span class="arrow">▶</span>Repeated appearances of the ΕΤΔ designation across unrelated files.</div>
    <div class="discovery-item"><span class="arrow">▶</span>Anomalies displaying abilities that appeared conceptually related rather than biologically related.</div>
    <div class="discovery-item"><span class="arrow">▶</span>Contradictory records concerning the origins of multiple LDs.</div>
    <div class="discovery-item"><span class="arrow">▶</span>Instances where an anomaly possessed knowledge of entities it should never have encountered.</div>
    <div class="discovery-item"><span class="arrow">▶</span>Repeated references to concepts of Life, Death, creation, destruction, and reincarnation.</div>

    <div class="internal-quote">
      <p>We are not cataloguing isolated anomalies. We are cataloguing fragments.</p>
      <div class="attribution">— Dr. Hypertheos — Foundation of the Omega Correlation Hypothesis</div>
    </div>

    <!-- OMEGA CORRELATION -->
    <div class="section-label">// The Omega Correlation Hypothesis //</div>
    <div class="hypothesis-box">
      <div class="hypothesis-title">Ω Omega Correlation Hypothesis</div>
      <div class="hypothesis-body">
        <p>Dr. Hypertheos theorized that Omega-tier anomalies are fundamentally different from conventional LDs. Rather than functioning as individual creatures or objects, Omega-tier anomalies may possess the ability to create, divide, influence, or manifest additional anomalies.</p>
        <p>Under this theory: D represents one Omega-tier entity. A second Omega-tier entity may exist. And LD-069, LD-088, and several other apparently unrelated anomalies may be fragments, creations, servants, or indirect consequences of that entity's existence.</p>
        <p>Hypertheos initially estimated the number of Omega-tier entities to be two. His reasoning was considered absurd.</p>
        <p>Until Incident OH-088.</p>
      </div>
    </div>

    <!-- INCIDENT OH-088 -->
    <div class="section-label">// Incident OH-088 — "The Question" //</div>
    <div class="incident-box">
      <div class="incident-title">⚠ Incident OH-088 — Classified</div>
      <div class="incident-body">
        <p>An AT-Class subject was authorized to interact with LD-088 under controlled conditions. The purpose: determine whether LD-088 possessed knowledge concerning Omega-tier anomalies.</p>
      </div>

      <div class="dialogue subject">
        <div class="speaker">AT-Class Subject</div>
        "How many Omega-tier anomalies exist?"
      </div>

      <div class="dialogue entity">
        <div class="speaker">LD-088</div>
        "Two."
      </div>

      <div class="dialogue subject">
        <div class="speaker">AT-Class Subject</div>
        "What constitutes an Omega-tier anomaly?"
      </div>

      <div class="silence-box">
        <div class="silence-count">11 SECONDS</div>
        <div class="silence-label">Complete silence — no movement — no response</div>
      </div>

      <div class="dialogue entity">
        <div class="speaker">LD-088</div>
        "What do you offer?"
      </div>

      <div class="incident-body">
        <p>The AT-Class subject refused to provide a sacrifice. Dr. Hypertheos, observing from behind one-way glass, reportedly ordered the questioning to continue under the threat of the subject's family members. The subject again refused.</p>
      </div>

      <div class="dialogue entity">
        <div class="speaker">LD-088</div>
        "Unfortunately, not enough."
      </div>

      <div class="incident-body">
        <p>The anomaly drained the entirety of the subject's life force. The subject died immediately. LD-088 then turned toward the observation window — and moved toward it. Its head passed through the one-way glass without breaking the material.</p>
        <p>At this point every audio recording within the chamber simultaneously failed. No alarms. No ventilation. No movement. Nothing. Dr. Hypertheos later stated the silence itself was more disturbing than anything LD-088 had done.</p>
      </div>

      <div class="dialogue entity">
        <div class="speaker">LD-088 — Speaking directly through the glass to Dr. Hypertheos</div>
        "Watch what you seek, Doctor."
      </div>

      <div class="incident-body">
        <p>Its head withdrew. All sound returned simultaneously.</p>
      </div>
    </div>

    <!-- AFTERMATH -->
    <div class="section-label">// Aftermath — Research Shift //</div>
    <div class="content-block">
      <p>Dr. Hypertheos changed dramatically following Incident OH-088. His previous research was abandoned entirely. He began constructing increasingly elaborate correlation maps that eventually covered entire laboratory walls — connecting individual LDs, historical events, anomalous pulses, unexplained disappearances, and recovered artifacts.</p>
      <p>Several researchers described the resulting diagrams as: "A family tree for something that shouldn't have a family."</p>
    </div>

    <div class="section-label">// Anomalies Under Active Study //</div>
    <div class="ld-grid">
      <div class="ld-tag">D</div>
      <div class="ld-tag">LD-069</div>
      <div class="ld-tag">LD-088</div>
      <div class="ld-tag">LD-089</div>
      <div class="ld-tag">LD-090</div>
      <div class="ld-tag">LD-091</div>
      <div class="ld-tag">LD-092</div>
      <div class="ld-tag">LD-095</div>
    </div>

    <!-- MANARINE HYPOTHESIS -->
    <div class="section-label">// The Manarine Hypothesis //</div>
    <div class="hypothesis-box">
      <div class="hypothesis-title">Ω The Manarine Hypothesis — Reconstitution</div>
      <div class="hypothesis-body">
        <p>Dr. Hypertheos theorizes that the second Omega-tier entity does not simply control its associated LDs — it may have created them intentionally. Each anomaly displaying ΕΤΔ correlation may represent a distinct conceptual fragment of the entity's total existence.</p>
        <p>The exact purpose of these creations remains unknown. Dr. Hypertheos believes their existence may be part of a larger process. He has referred to this process only once:</p>
        <p style="color:#ce7adb; font-style: italic; text-align: center; padding: 10px; font-size: 14px; letter-spacing: 2px;">"Reconstitution."</p>
        <p>No further explanation has been given. As of current assessment, Dr. Manarine has determined that ΕΤΔ is likely not an Omega-tier anomaly — but something of extremely high classification approaching that threshold.</p>
      </div>
    </div>

    <!-- SELF EXPERIMENTATION -->
    <div class="section-label">// Unauthorized Self-Experimentation //</div>
    <div class="content-block">
      <p>D.I.V.I.D.E. discovered that Dr. Hypertheos had been experimenting with his own biology. Initially believed to involve anomalous resistance testing — further investigation revealed the doctor was attempting to determine whether a human body could be modified into a vessel capable of sustaining anomalous properties beyond human limits.</p>
      <p>Several unauthorized procedures were discovered. Anomalous materials had been implanted into his own body. All removed samples were immediately confiscated.</p>
    </div>

    <div class="dialogue hypertheos">
      <div class="speaker">Dr. Hypertheos — When questioned</div>
      "I don't want power."
    </div>
    <div class="dialogue hypertheos">
      <div class="speaker">Dr. Hypertheos — When asked what he was trying to accomplish</div>
      "Understanding."
    </div>

    <!-- POTENTIAL OBJECTIVE -->
    <div class="section-label">// Potential Objective — Unconfirmed //</div>
    <div class="content-block">
      <p>D.I.V.I.D.E. suspects Dr. Hypertheos may be attempting to reproduce the process by which the Omega-tier entity created or divided its power. Whether his goal is to become an anomaly, create one, or something else entirely remains unknown.</p>
    </div>

    <div class="objective-item"><span class="q">?</span>Become an anomaly himself.</div>
    <div class="objective-item"><span class="q">?</span>Create a new anomaly through artificial means.</div>
    <div class="objective-item"><span class="q">?</span>Reconstruct or reassemble an Omega-tier entity.</div>
    <div class="objective-item"><span class="q">?</span>Reunite existing ΕΤΔ fragments into their original form.</div>
    <div class="objective-item"><span class="q">?</span>Become something no existing classification covers.</div>

    <!-- NICKNAME -->
    <div class="section-label">// The Nickname //</div>
    <div class="content-block">
      <p>Personnel initially began calling Dr. Hypertheos "The Doctor Trying To Be God" as an insult. It eventually became an officially recognized internal designation. Dr. Hypertheos is aware of the title.</p>
    </div>

    <div class="internal-quote">
      <p>God already made the mistake.</p>
      <div class="attribution">— Dr. Manarine Hypertheos — Upon being informed of his official nickname</div>
    </div>

    <!-- SURVEILLANCE -->
    <div class="section-label">// Current Protective Surveillance //</div>
    <div class="content-block">
      <p>Despite repeated concerns about his mental state and unauthorized research, D.I.V.I.D.E. has elected not to terminate or permanently detain Dr. Hypertheos. He may be the single person with the greatest understanding of the Omega phenomenon. Removing him could permanently eliminate D.I.V.I.D.E.'s best chance of understanding the second Omega-tier entity.</p>
    </div>

    <div class="surveillance-item"><div class="dot"></div>24-hour continuous surveillance — all facilities</div>
    <div class="surveillance-item"><div class="dot"></div>Restricted laboratory access — Director authorization required</div>
    <div class="surveillance-item"><div class="dot"></div>Mandatory psychological evaluation — ongoing</div>
    <div class="surveillance-item"><div class="dot"></div>Continuous biometric monitoring — unexplained bodily changes logged</div>
    <div class="surveillance-item"><div class="dot"></div>Prohibited from unauthorized human experimentation</div>

    <!-- FINAL ASSESSMENT -->
    <div class="section-label">// Final Assessment //</div>
    <div class="content-block">
      <p>Dr. Manarine Hypertheos is currently classified as human. This classification is provisional. Repeated scans have identified unexplained changes within his body — none currently sufficient to reclassify him as anomalous. His condition is being monitored continuously.</p>
      <p>The doctor has demonstrated an unusual ability to predict anomalous behavior before it occurs. Whether this is the result of research, intuition, or an unidentified anomalous influence is unknown.</p>
      <p>The possibility that Dr. Hypertheos is intentionally attempting to become something other than human remains under active investigation.</p>
    </div>

    <div class="internal-quote">
      <p>He was the first person to ask what these anomalies had in common. Then he found the answer. Now I'm afraid he wants to become part of it.</p>
      <div class="attribution">— Senior Researcher ███████</div>
    </div>

    <!-- DIRECTIVE -->
    <div class="directive-box">
      <div class="directive-title">D.I.V.I.D.E. DIRECTIVE — S.I.-001</div>
      <div class="directive-line"><span class="warn">◈</span>Do not kill Dr. Hypertheos.</div>
      <div class="directive-line"><span class="warn">◈</span>Do not trust Dr. Hypertheos.</div>
      <div class="directive-line"><span class="warn">◈</span>Do not allow Dr. Hypertheos to continue his research without supervision.</div>
      <div class="directive-line"><span class="warn">◈</span>Do not permit unsupervised access to LD-069, LD-088, LD-089, or any ΕΤΔ-correlated anomaly without Director-Level authorization.</div>
      <div class="directive-final">And above all — do not let him discover what the second Omega-tier entity actually wants.</div>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited.</p>
    </div>

  </div>

</body>
</html>
