
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — AT-Class Designation</title>
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
      background-color: #3a3a3a;
      color: #888;
      text-align: center;
      padding: 6px;
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      border-bottom: 1px solid #555;
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
    .back-link:hover { color: #888; }

    /* Header — deliberately muted/gray for AT-Class */
    .file-header {
      border: 1px solid #2a2a2a;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #0d0d0d 0%, #080808 100%);
    }

    .file-header::before {
      content: '// EXPENDABLE CLASSIFICATION //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #444;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #333;
      border-right: 2px solid #333;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #555;
      letter-spacing: 5px;
      margin-bottom: 6px;
    }

    .file-designation {
      font-size: 11px;
      color: #444;
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
      background: #0a0a0a;
      border: 1px solid #1a1a1a;
      font-size: 11px;
    }

    .meta-label { color: #444; letter-spacing: 1px; white-space: nowrap; }
    .meta-value { color: #666; letter-spacing: 1px; }
    .meta-value.none { color: #cc0000; }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #444;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a1a1a;
    }

    .content-block {
      background: #0a0a0a;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #2a2a2a;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      line-height: 1.9;
      color: #777;
    }

    .content-block p { margin-bottom: 8px; }
    .content-block p:last-child { margin-bottom: 0; }

    /* Purpose items */
    .purpose-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0a0a0a;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #2a2a2a;
      font-size: 12px;
      color: #777;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .purpose-item .arrow { color: #444; flex-shrink: 0; margin-top: 2px; }

    /* Selection criteria */
    .criteria-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .criteria-grid { grid-template-columns: 1fr; } }

    .criteria-card {
      padding: 14px 16px;
      background: #0a0a0a;
      border: 1px solid #1a1a1a;
      border-top: 3px solid #2a2a2a;
      font-size: 11px;
      color: #666;
      line-height: 1.7;
    }

    .criteria-card .crit-name {
      font-family: 'Rajdhani', sans-serif;
      font-size: 12px;
      font-weight: 700;
      color: #555;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    /* Quote blocks */
    .quote-block {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #333;
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
      color: #444;
      font-size: 24px;
      font-family: serif;
      line-height: 1;
    }

    .quote-block p {
      font-size: 12px;
      color: #666;
      font-style: italic;
      line-height: 1.7;
    }

    /* Stamp */
    .stamp {
      display: inline-block;
      border: 2px solid #cc0000;
      color: #cc0000;
      font-family: 'Rajdhani', sans-serif;
      font-size: 22px;
      font-weight: 700;
      letter-spacing: 6px;
      padding: 6px 20px;
      transform: rotate(-3deg);
      opacity: 0.6;
      margin: 20px 0;
      text-transform: uppercase;
    }

    .footer {
      border-top: 1px solid #1a1a1a;
      padding-top: 20px;
      margin-top: 30px;
      font-size: 10px;
      color: #2a2a2a;
      letter-spacing: 1px;
      line-height: 1.8;
      text-align: center;
    }
  </style>
</head>
<body>

  <div class="warning-bar">
    ASSET TERMINATION CLASS — NO CLEARANCE — EXPENDABLE DESIGNATION
  </div>

  <div class="container">

    <a href="personnel.html" class="back-link">← RETURN TO PERSONNEL INDEX</a>

    <div class="file-header">
      <div class="file-title">AT-CLASS</div>
      <div class="file-designation">Asset Termination-Class Personnel — Expendable Registry</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">FULL TERM</span>
          <span class="meta-value">Asset Termination-Class Personnel</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value none">Level 0 — None</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">NICKNAMES</span>
          <span class="meta-value">"Test Rats" / "Absolute Trash"</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">RIGHTS</span>
          <span class="meta-value none">None. Stripped by classification.</span>
        </div>
      </div>
    </div>

    <!-- DEFINITION -->
    <div class="section-label">// Definition //</div>
    <div class="content-block">
      <p>AT-Class refers to human subjects forcibly drafted into D.I.V.I.D.E.'s internal testing and anomaly experimentation programs. These are usually violent criminals, deserters, or individuals stripped of all rights under international law.</p>
      <p>Their only purpose is to <strong style="color:#aaa">die for science</strong>.</p>
    </div>

    <div class="stamp">EXPENDABLE</div>

    <!-- PURPOSE -->
    <div class="section-label">// Purpose //</div>
    <div class="purpose-item"><span class="arrow">▶</span>Used to test anomaly behavior, infection spread, and psychic corruption under controlled observation.</div>
    <div class="purpose-item"><span class="arrow">▶</span>Deployed to observe how an entity kills or reacts to live human presence.</div>
    <div class="purpose-item"><span class="arrow">▶</span>Their deaths are often broadcast to higher-ranking personnel for analysis — or entertainment.</div>

    <!-- SELECTION CRITERIA -->
    <div class="section-label">// Selection Criteria //</div>
    <div class="criteria-grid">
      <div class="criteria-card">
        <div class="crit-name">Criminal Profile</div>
        Life sentence or worse. Violent offenders, deserters, and individuals with no remaining legal standing.
      </div>
      <div class="criteria-card">
        <div class="crit-name">Social Profile</div>
        No family. No nation. No identity that registers as significant to any monitoring authority.
      </div>
      <div class="criteria-card">
        <div class="crit-name">Psychological Profile</div>
        Broken. Irredeemable. Expendable. Stability is not required — only presence.
      </div>
    </div>

    <!-- QUOTES -->
    <div class="section-label">// D.I.V.I.D.E. Internal Quotes //</div>

    <div class="quote-block">
      <p>They're already dead — we're just putting it to use.</p>
    </div>

    <div class="quote-block">
      <p>If they scream, it means the anomaly works.</p>
    </div>

    <div class="quote-block">
      <p>Cheaper than drones, and twice as dumb.</p>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
